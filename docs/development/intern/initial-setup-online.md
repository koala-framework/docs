#INITIAL SETUP ONLINE

**set server.domain and server.path in config.ini to correct values (production + test section)**

##On Webflow Server

    vps setup-online --server=test,production


##On POI Server

1. Project pushed
2. search for provided directory (most of the time in div/)
3. delete existing files (error-folder, index.html and also hidden files!)
4. `$ ../library/kwfscripts/setup-web.php --section=[test|production|qa] --app-id=gitId --skip-db`
(Important: to setup qa, test or production this sections have to be defined in config.ini)
5. create config.local.ini with provided information
    [production]
    database.web.host =
    database.web.user =
    database.web.password =
    database.web.dbname =
6. On your local machine (your virtual server) in your project directory (if you need to populate the web with your test-data)
    `$ ../library/kwfscripts/copy-data-to-git.php --skip-encrypt`
    6.1. Do this again before every copy-data-from-git (for test and again for prod if you need initial test-data on prod)
7. At POI-Client (in Putty again):
    `$ ../library/kwfscripts/copy-data-from-git.php --skip-encrypt`
8. `$ kwf create-users`
9. TEST if everything works at this domain!


###Solr

workflow on POI-Server

    # 1. change to tomcat-solr conf directory (connect with web user)
    # for example:
    cd /www/tomcat-solr/conf/Catalina/localhost

    # 2. create a file that is named with the application id of the project
    # for example:
    vi WEBID.xml

    # 3. Write the below config with the correct project directory path to solr
    <?xml version"1.0" encoding="utf-8"?>
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
