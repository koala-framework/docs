#EXPRESSIONS

Using expressions you can write advanced queries - similar to Sql - with the big difference that they can be run on different backends.

    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
    }
     
    $m = Kwf_Model_Abstract::getInstance('Products');
    $s = $m->select()
        ->where(new Kwf_Model_Select_Expr_Or(array(
            new Kwf_Model_Select_Expr_Equals('name', 'foo'),
            new Kwf_Model_Select_Expr_Equals('name', 'bar'),
        )));
    $row = $m->getRow($s);
    
##Expr_Sql

Expressions don't implement all possible SQL statements. If you are using `Model_Db` you can specify the needed SQL expression directly. 
Obviously you'll lose the possibility to use the expression with another Model (eg. FnF in unit test)

    $select = $m->select()
                    ->where(new Kwf_Model_Select_Expr_Sql("'start_date' > NOW() "
                                                           ."AND IFNULL(`end_date`, NOW()) >= NOW() "
                                                           ."AND `visible` = 1"));