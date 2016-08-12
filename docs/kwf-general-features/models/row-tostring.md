#ROW __TOSTRING

In different places of Koala Framework it is required to get a string representation of a row. 
Eg. a Products model would use "name" column for that.

One way to implement this would be to create a custom Row class and implement the __toString method. 

####The easier way is to use the toStringField setting in the model itself:

    <?php
    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
        protected $_toStringField = 'name';
    }
    $row = Kwf_Model_Abstract::getInstance('Products')->getRow(1);
    echo (string)$row; //will print name of the row
    

####Alternatively the __toString method can be overridden ([in a custom row class](modify-row-behavior.md)) manually which gives flexibility to implement any required code:

    <?php
    class Row_Product extends Kwf_Model_Db_Row
    {
        public function __toString()
        {
            return $this->code.' '.$this->name;
        }
    }
    

The downside of using that is that this column can not be used everywhere, eg. when sorting or filtering in an AutoGrid. 
Alternatively you can implement a [stored expression](stored-expressions.md).