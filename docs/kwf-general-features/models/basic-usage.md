#BASIC USAGE

To create a new model stored in mysql, [setup the database connection](https://github.com/koala-framework/koala-framework), create the table products and this class:

    <?php
    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
    }
    
It is not required to specify the columns in any form, Kwf_Model will automatically fetch those for you.

Usually those files are put into models/ folder which is in include path by default.

then you can start working with the model:

    <?php
    $m = Kwf_Model_Abstract::getInstance('Products');
     
    //get row and modify
    $row = $m->getRow(1);
    var_dump($row->name);
    $row->name = 'foo';
    $row->save();
     
    //create row
    $row = $m->createRow();
    $row->name = 'bar';
    $row->save();