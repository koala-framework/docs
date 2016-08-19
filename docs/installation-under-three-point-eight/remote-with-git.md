#INSTALL ON REMOTE WEBSERVER WITH GIT

If you are lucky and can use git on the webserver you can use git for deployment. Updates are very easy to deploy.

###Requirements:

* Php
* Apache (configured with virtual host pointing to empty document root)
* MySQL Server (running)
* git
* shell access

####To get the code and put it in place execute the following commands on the commandline:

    #connect to the server
    ssh youruser@www.example.com
     
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
    
    
####As the webserver is already running you can now run the setup by opening the following url in a browser:

http://www.example.com/kwf/maintenance/setup

Simply follow the steps.


After installing you can start hacking! To clear caches simply open a shell in the installation folder and execute `php bootstrap.php clear-cache`. ([or read more about that](../kwf-general-features/caching.md))

##Update

####To update execute the following in the installation directory:

        # pull application changes
        git pull
         
        # pull kwf changes
        cd kwf-lib
        git pull
        cd ..
         
        # pull library changes
        cd library
        git pull
        cd ..
         
        # execute update scripts
        php bootstrap.php update