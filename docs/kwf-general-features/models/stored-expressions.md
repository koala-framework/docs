#STORED EXPRESSION

You can [create expressions on demand](expressions.md) when creating a query or store them in the model to make the reusable - 
which makes sense for a bit complexer ones.

Expressions can also be used for optimized sql queries instead of manual `$row->getChildRows('Childs')` and `$row->getParentRow('Parent');` 
especially when there are many levels.

    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
        protected function _init()
        {
            $this->_exprs['product_code'] = new Kwf_Model_Select_Expr_Concat(array(
                Kwf_Model_Select_Expr_String('P-'), //fixed string
                Kwf_Model_Select_Expr_Field('id'),
            ));
        }
    }
     
    $m = Kwf_Model_Abstract::getInstance('Products');
    $s = $m->select()
        ->order('product_code'); //yes, even sorting is possible
    $rows = $m->getRows($s);
    foreach ($rows as $row) {
        var_dump($row->product_code); //access the expression
    }
    
###There are two ways stored expressions can be used:

####As a part of the sql statement:

This way it's loaded with execution of the sql query to get the data, but it has to be part of the select object.

    $select->expr('example_expr');
    
Advantage of this technique is that it performs much better than lazy evaluation.


#### Lazy loaded

When you access the stored expression from row, and it was not included in your select to get the row it will be loaded lazy.

Advantage of this technique is that you can just access the expression.