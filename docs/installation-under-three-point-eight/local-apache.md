#INSTALL ON LOCAL APACHE

###Requirements:

* Php
* Apache (configured with virtual host pointing to empty document root)
* MySQL Server (running)
* git

The commands listed below work on Linux and Mac, but the whole procedure should also work on Winodws - just the commands are a bit different.

####To get the code and put it in place execute the following commands on the commandline:

    #change directory to document root
    cd /var/www/kwf-cms-demo
     
    #clone kwf-cms-demo (replace with your repository)
    git clone git://github.com/vivid-planet/kwf-cms-demo.git .
     
    #set permissions
    chmod a+w uploads cache temp log log/* cache/*
     
    #clone koala framework
    git clone git://github.com/koala-framework/koala-framework.git kwf-lib
    #switch to correct branch
    cd kwf-lib
    git checkout `cat ../kwf_branch`
    cd ..
     
    #clone required libraries
    git clone git://github.com/vivid-planet/library.git library
     
    #set path to libraries
    echo "library/zend/%version%" > kwf-lib/include_path
     
    #create required files
    touch config.local.ini
    touch config_section
    chmod a+w config.local.ini config_section
    
####As the webserver is already running you can now run the setup by opening the following url in a browser:

http://localhost/kwf/maintenance/setup

Simply follow the steps.

After installing you can start hacking! To clear caches simply open a shell in the installation folder and execute `php bootstrap.php clear-cache`. ([or read more about that](../kwf-general-features/caching.md))