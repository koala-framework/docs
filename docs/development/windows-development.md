#WINDOWS DEVELOPMENT

Koala Framework is developed on Linux - and we recommend Linux for production usage.

However some people prefer to develop on windows - and we also support that.

To test windows compatibility without actually using windows can be done with wine.

###Dependencies

* wine
* php for win32
* at least those extensions: gd2, mbstring, pdo_mysql

###Database

Connect to a linux native mysql server. localhost might not work as host, use the public ip instead.

###Setup

`WINEDEBUG=fixme-all wine ~/php/php-5.4.10-win32/php.exe bootstrap.php setup`

###Cli Scripts

Cli scripts like clear-cache can be run just like setup:

`WINEDEBUG=fixme-all wine ~/php/php-5.4.10-win32/php.exe bootstrap.php clear-cache`

###Webserver

The easiest is to run the cli-server (new with Php 5.4):

`WINEDEBUG=fixme-all wine ~/php/php-5.4.10-win32/php.exe -S localhost:8000 bootstrap.php`