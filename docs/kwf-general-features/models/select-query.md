#SELECT

Use a Select Object to filter and query models.

    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
    }
     
    //simple usage
    $m = Kwf_Model_Abstract::getInstance('Products');
    $s = $m->select() //returns a Kwf_Model_Select object use new Kwf_Model_Select() alternatively
        ->whereEquals('color', 'blue')
        ->order('name', 'ASC')
        ->limit(10, 0);
    $rows = $m->getRows($s);
    foreach ($rows as $row) {
        var_dump($row->name);
    }
    
`Kwf_Model_Select` is inspired by `Zend_Db_Select` (though it doesn't inherit `Zend_Db_Select`) and can be used just like a `Zend_Db_Select`:

    $m = Kwf_Model_Abstract::getInstance('Products');
    $s = $m->select()
        ->where('name = ?', 'foo');
    $rows = $m->getRows($s);
    foreach ($rows as $row) {
        var_dump($row->name);
    }
    
    
Even eg. joins will be passed to `Zend_Db_Select`, tough it is not recommended to do that - as you will loose Model independence. 
Instead use [Expressions](expressions.md) for more complex selects.