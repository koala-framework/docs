#MAINTENANCE

Once the application is installed you sometimes have to run maintenance scripts:

###setup

Initial setup

* commandline: php bootstrap.php setup

###php-info

Open the following url to get php-info output:

* http://www.example.com/kwf/debug/php-info

###apc console

Open the following url to get the apc console (useful if you use apc to check stats etc):

* http://www.example.com/kwf/debug/apc

###build

Refreshing build is needed if you make changes to code.

* commandline: php bootstrap.php build

###clear-cache

Clearing caches is needed if you make changes to code.

* commandline: php bootstrap.php clear-cache

###clear-view-cache

Clears view cache for specified components

* commandline: php bootstrap.php clear-view-cache
* http://www.example.com/admin/component/clear-cache

###clear-cache-watcher

Clear cache watcher automatically clears caches & build by watching the file system for changes

* commandline: php bootstrap.php clear-cache-watcher

###update

Running update scripts is needed after updating code that requires changes to the database. Will also clear all caches.

* commandline: php bootstrap.php update

###fulltext rebuild

The fulltext index can be built using:

* commandline: php bootstrap.php fulltext rebuild --debug
