#FILTERS

Filters can be set for columns that will process (filter) the data before storing it to the database. 
Those filters are based on [Zend_Filter](https://framework.zend.com/manual/1.12/en/zend.filter.html), so you can use any Zend_Filter.

###Simple Example:

    <?php
    class Example extends Kwf_Model_Db
    {
        protected $_table = 'example';
        protected function _setupFilters()
        {
            parent::_setupFilters();
            $this->_filters['foo'] = new Zend_Filter_StringToLower();
        }
    }
    
    
#####Koala Framework also comes with own filters:

* Kwf_Filter_Ascii (converts value into ASCII representation, can be used for filenames etc.)
*  Kwf_Filter_Random (returns random string)
*  Plus row filters that operate on a row:
*  Kwf_Filter_Row_AutoFill (fills column with values from row based on a template)
*  Kwf_Filter_Row_CurrentDateTime (fills column with current date and time)
*  Kwf_Filter_Row_CurrentDateTimeUnique (fills column with current date and time and makes sure that value is unique)
*  Kwf_Filter_Row_CurrentIp (fills column with current REMOTE_ADDR)
*  Kwf_Filter_Row_Numberize (numberizes a column in a row and makes sure the numbers are in a sequence)
*  Kwf_Filter_Row_Random (fills column with random string, only if input value is emtpy)
*  Kwf_Filter_Row_UniqueAscii (like Ascii but makes sure the value is unique)

###Numberzize example:

    <?php
    class Example extends Kwf_Model_Db
    {
        protected $_table = 'example';
        protected function _setupFilters()
        {
            parent::_setupFilters();
            $this->_filters['pos'] = new Kwf_Filter_Row_Numberize();
            $this->_filters['pos']->setGroupBy(array('category_id')); //group number sequence by this field
        }
    }
    
    
###There are also a few shortcuts how filters can be set:
 
     protected $_filters = 'filename'; //uses Kwf_Filter_Ascii by default
     protected $_filters = array('filename') //uses Kwf_Filter_Ascii by default
     protected $_filters = array('pos');      //uses Kwf_Filter_Row_Numberize by default
     protected $_filters = array('pos' => 'MyFilter') //creates MyFilter instance