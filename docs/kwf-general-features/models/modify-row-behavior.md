#MODIFY ROW BEHAVIOR

It is not only possible to create own classes for models, but also for rows.

    <?php
    class Row_Product extends Kwf_Model_Db_Row
    {
    }
     
    <?php
    class Productrs extends Kwf_Model_Db
    {
        ....
        protected $_rowClass = 'Row_Product';
    }
    
####Using that technique you can:

* implement custom logic that gets executed before/after insert/update/delete by overriding eg. `_afterInsert`
*  implement [custom __toString method](row-tostring.md)
*  implement custom columns by overriding __get
*  implement helper methods and business logic as needed by your application

###Example for overriding __get:

    <?php
    class Row_Foo extends Kwf_Model_Db_Row
    {
        public function __get($column)
        {
            if ($column == 'foo_formated') {
                if ($this->foo_type == 'green') {
                    return trl('It\'s a green color');
                } else if ($this->foo_type == 'blue') {
                    return trl('It\'s a blue color');
                } else if ($this->foo_type == 'orange') {
                    return trl('It\'s a orange color');
                }
            }
            return parent::__get($column);
        }
     
        public function __isset($column)
        {
            if ($column == 'foo_formated') {
                return true;
            }
            return parent::__isset($column);
        }
    }