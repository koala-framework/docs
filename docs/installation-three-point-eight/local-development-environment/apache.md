#INSTALL ON LOCAL APACHE

###Requirements:

* Php
* Apache (configured with virtual host pointing to empty document root)
* MySQL Server (running)
* git
* [composer](php-builtin-webserver/composer.md)
* [nodejs + npm](php-builtin-webserver/nodejs-npm.md)

The commands listed below work on Linux and Mac, but the whole procedure should also work on Winodws - just the commands are a bit different.

To get the code and put it in place execute the following commands on the commandline:

    #change directory to document root
    cd /var/www/kwf-cms-demo
     
    #clone kwf-cms-demo (replace with your repository)
    git clone git://github.com/vivid-planet/kwf-cms-demo.git .
     
    #install dependencies
    composer install
     
    #create required files
    touch config.local.ini
    touch config_section
     
    #set permissions
    chmod a+w config.local.ini config_section
    chmod a+w uploads cache temp log log/* cache/*
     
    #start build
    php bootstrap.php clear-cache
    php bootstrap.php build


The app is now installed and reachable in your browser under http://localhost/ (depending on your apache config). Now [run setup](../setup) to configure and create initial database.