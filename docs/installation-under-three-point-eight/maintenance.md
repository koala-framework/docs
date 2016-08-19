#MAINTENANCE

Once the application is installed you sometimes have to run maintenance scripts:

###setup

####Open the following url to start the initial setup:

* http://www.example.com/kwf/maintenance/setup

####This script will:

* check requirements
* create database with initial content
* create admin user
* create config.local.ini containing database config

###php-info

####Open the following url to get php-info output:

* http://www.example.com/kwf/debug/php-info

###apc console

####Open the following url to get the apc console (useful if you use apc to check stats etc):

* http://www.example.com/kwf/debug/apc

###clear-cache

Clearing caches is needed if you make changes to code.

* commandline: php bootstrap.php clear-cache
* webserver: http://www.example.com/kwf/maintenance/clear-cache

###clear-view-cache

Clears view cache for specified components

* commandline: php bootstrap.php clear-view-cache
* http://www.example.com/admin/component/clear-cache

###update

Running update scripts is needed after updating code that requires changes to the database. Will also clear all caches.

* commandline: php bootstrap.php update
* webserver: http://www.example.com/kwf/maintenance/update

###fulltext rebuild
####The fulltext index can be built using:

* commandline: php bootstrap.php fulltext rebuild --debug
* webserver: http://www.example.com/kwf/maintenance/fulltext

###phpminiadmin

####To access the database you can use the built-in phpminiadmin (slim phpMyAdmin alternative) which is already configured with the correct database connection:

* http://www.example.com/kwf/pma