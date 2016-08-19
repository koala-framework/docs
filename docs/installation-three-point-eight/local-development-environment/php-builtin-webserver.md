#INSTALL ON LOCAL PHP BUILT-IN WEBSERVER

###Requirements:

* Php (just installed)
* MySQL Server (running)
* git
* [composer](composer.md)
* [nodejs + npm](nodejs-npm.md)

To get the code and put it in place execute the following commands on the commandline:

    #change directory to where you want to install
    cd kwf-cms-demo
     
    #clone kwf-cms-demo (replace with your repository)
    git clone git://github.com/vivid-planet/kwf-cms-demo.git .
     
    #install dependencies
    composer install
     
    #start build
    php bootstrap.php clear-cache
    php bootstrap.php build
    
    
Now it's time to start the webserver (this has to be done after every reboot):
    
    php -S localhost:8080 bootstrap.php
    
    
The app is now installed and reachable in your browser under http://localhost:8080/. Now run [setup](../../setup/overview.md) to configure and create initial database.
    
    
