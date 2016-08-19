#COPY / DUPLICATE WEB

    # copy git repository
    ssh git.vivid-planet.com
    cd /git
    cp -r oldname newname
     
    # clone new web
    cd /var/www
    vps clone newname
     
    # copy database
    mysql -e "CREATE DATABASE newname"
    mysqldump oldname | mysql newname
     
    # copy uploads
    cp -r /var/uploads/oldname /var/uploads/newname
     
    # change config.ini
    application.id etc...