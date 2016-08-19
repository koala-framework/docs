#INSTALL ON LOCAL PHP BUILT-IN WEBSERVER

###Requirements:

* Php (just installed)
* MySQL Server (running)
* git

The commands listed below work on Linux and Mac, but the whole procedure should also work on Winodws - just the commands are a bit different.

To get the code and put it in place execute the following commands on the commandline:

    #change directory to where you want to install
    cd kwf-cms-demo
     
    #clone kwf-cms-demo (replace with your repository)
    git clone git://github.com/vivid-planet/kwf-cms-demo.git .
     
    #set permissions
    chmod a+w uploads cache temp log log/* cache/*
     
    #clone koala framework
    git clone git://github.com/koala-framework/koala-framework.git kwf-lib
    #switch to correct branch
    cd kwf-lib
    git checkout `cat kwf_branch`
    cd ..
     
    #clone required libraries
    git clone git://github.com/vivid-planet/library.git library
     
    #set path to libraries
    echo "library/zend/%version%" > kwf-lib/include_path
    
Now it's time to start the webserver (this has to be done after every reboot):

    php -S localhost:8080 bootstrap.php

After that you can run the setup by opening the following url in a browser:

http://localhost:8080/kwf/maintenance/setup

Simply follow the steps.


After installing you can start hacking! To clear caches simply open a shell in the installation folder and execute `php bootstrap.php clear-cache`. (or [read more](../kwf-general-features/caching.md) about that)