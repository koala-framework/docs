# Initial setup online

**Set server.domain and server.path in config.ini to correct values (production + test section)**

## On Webflow Server

##### 1. Run the setup-online command to build your project for the first time
```bash
$ vps setup-online --server=test,production
```


## On POI Server

##### 1. Run the setup-online command to build your project for the first time
```bash
$ vps setup-online --server=test,production
```

##### 2. Search for projects directory on the server (most of the time in div/)

##### 3. Delete all existing files inside this folder (error-folder, index.html and also hidden files)

##### 4. Setup the project on the server

```bash
$ ../library/kwfscripts/setup-web.php --section=[test|production|qa] --app-id=[git-id] --skip-db
```

The chosen section (test, qa or production) has to be defined in `config.ini`.


##### 5. Create a `config.local.ini` with the database information

```ini
[production]
database.web.host =
database.web.user =
database.web.password =
database.web.dbname =
```

##### 6. Copy your local data to the git-server (from your local virtual server)
```bash
$ ../library/kwfscripts/copy-data-to-git.php --skip-encrypt
```

This needs to be done every time before running `copy-data-from-git`.

##### 7. Copy the data from the git-server to the POI-server
```bash
$ ../library/kwfscripts/copy-data-from-git.php --skip-encrypt
```


##### 8. Add the projects [process-control](../../kwf-general-features/process-control.md) to the servers cronjobs 


### Solr

workflow on POI-Server

    # 1. change to tomcat-solr conf directory (connect with web user)
    # for example:
    cd /www/tomcat-solr/conf/Catalina/localhost

    # 2. create a file that is named with the application id of the project
    # for example:
    vi WEBID.xml

    # 3. Write the below config with the correct project directory path to solr
    <?xml version="1.0" encoding="utf-8"?>
    <Context docBase="/www/docs/vps/solr/3.6.0/webapps/solr.war" debug="0" crossContext="true">
        <Environment name="solr/home" type="java.lang.String" value="/www/docs/div/WEBFOLDER/solr/" override="true" />
    </Context>

    # 4. Set correct permissions of solr Directory in project with web user
    # for example:
    chmod 775 WEBFOLDER/solr/ WEBFOLDER/solr/CONFIGFOLDER WEBFOLDER/solr/CONFIGFOLDER/conf
    chmod 777 WEBFOLDER/solr/CONFIGFOLDER/data

    # 5. Restart tomcat solr
    # for example:
    /www/bin/rc_tomcat restart solr

    # 6. Index all your content to solr
    # change into project directory with your web user
    php bootstrap.php fulltext rebuild

    # 7. Activate the cronjobs also with your web user
    # for example
    * * * * *    php /www/docs/div/WEBFOLDER/bootstrap.php fulltext update-changed 2>&1
    30 02 * * *  time php /www/docs/div/WEBFOLDER/bootstrap.php fulltext check-contents 2>&1


On webflow server, step 1 - 5 is work for Andi. Step 6 - 7 is ours.
