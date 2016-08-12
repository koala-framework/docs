#SETUP DATABASE

Setting up a database is normally done by the setup script during installation. For manual setup create a config.local.ini with the following contents in the application root:

    [production]
    database.web.host = localhost
    database.web.username = yourdbusername
    database.web.password = yourdbpassword
    database.web.dbname = yourdbname
    
Alternatively you could add it to config.ini - if you prefer to have it under version control.

##Database usage

getting the default database connection is easy:

    $db = Zend_Registry::get('db'); //will return a Zend_Db_Adapter
    
Or access the database trough `Kwf_Model_Db`

##Multiple Databases

You can also configure multiple database connections, use a different key than web in config:

    [production]
    database.foo.host = localhost
    database.foo.username = yourdbusername
    database.foo.password = yourdbpassword
    database.foo.dbname = foodbname
.

    $db = Zend_Registry::get('dao')->getDb('foo'); //will return a Zend_Db_Adapter