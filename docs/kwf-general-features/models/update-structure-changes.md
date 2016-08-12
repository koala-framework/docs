##UPDATES / STRUCTURE CHANGES / MIGRATION

Koala Frameworks provides a system that manages changes to database structures - so called Update Scripts. 
Other frameworks call this sometimes Database Migration.

There are two different kinds of update scripts: php and sql. Using php scripts you can do basically anything, 
using sql scripts you can execute sql queries - like `ALTER TABLE ...`

##Create update scripts

simply put a numbered file into app/Update, examples are `app/Update/123.sql` or `app/Update/345.php`. 
The number is used to define the order in which the scripts need to get executed.

###SQL Update Scripts

basically just insert SQL commands, multiple commands in one file are supported. 
Usually you would copy the executed commands from phpMyAdmin or similar tools.

###PHP Update Scripts

Example update script:

    <?php
    class Update_123 extends Kwf_Update
    {
        public function update()
        {
            $db = Kwf_Registry::get('db');
             //$db is a Zend_Db_Adapter, you can do anything with it
        }
    }
    
##Execute Update Scripts

to execute update scripts execute this command:

`php bootstrap.php update`

this will execute all update scripts that not have been executed yet.

a table "kwf_update" will be created in the database where all executed update scripts are listed - so they get executed only once.

To execute (for testing) a single update script use one of the following parameters:

`php bootstrap.php update --rev=NUMBER`

`php bootstrap.php update --class=Update_NUMBER`

##Updates in Components

You can not only have Update scripts in app/Updates, you can also attach them to specific components. 
This makes especially sense for components shipped with Koala Framework - 
they will create all required tables in such a update script.

To create such an update script create an Update folder in the component and put the update script there.
`php bootstrap.php update` will go through all used components and collect their update scripts.

In practice when adding a new component you have to call  `php bootstrap.php update` to generate the required tables.

##Downgrade / go back / undo

Other Database Migration frameworks have ways to move the database up and down again. This is not supported by koala framework. Why? It just would add complexity for no real value.
Backup before deploy. Who will test all combinations of up & down scripts anyway?