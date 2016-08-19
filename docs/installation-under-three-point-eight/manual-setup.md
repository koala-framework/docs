Instead of using the setup script thru the browser you can also manually setup.

###1. Create config.local.ini

    [production]
    database.web.username = root
    database.web.password =
    database.web.dbname = example
    database.web.host = localhost
    
    server.domain = example.com

If the application is running in a subfolder configure it:

`server.baseUrl = "/sub"`

If configuring for development disable the error log:

`debug.error.log = false`

###2. Create initial database
Execute the following on commandline:

`php bootstrap.php setup`

Alternatively you can use an existing database.