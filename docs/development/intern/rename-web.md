#RENAME WEB

    # rename git repository
    ssh git.vivid-planet.com
    cd /git
    mv oldname newname
     
    # rename local git working copy
    cd /var/www
    mv oldname newname
    nano newname/.git/config #change oldname to newname
     
    # rename database
    mysql -e "CREATE DATABASE newname"
    mysqldump oldname | mysql newname
    mysql -e "DROP DATABASE oldname" #attention! only if previous command was successful
     
    # rename uploads
    mv /var/uploads/oldname /var/uploads/newname
     
    # change config.ini
    application.id etc...
    
    
    