#CLONE WEB

    cd ~/www
    vps clone $WEBNAME
    cd $WEBNAME
     
    composer install
    ccb 
    vps import
