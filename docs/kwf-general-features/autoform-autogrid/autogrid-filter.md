#AUTOGRID: FILTERS

You can add multiple filters on top of an AutoGrid. Change the filters by setting the _filters member 
variable of the AutoGrid controller.

Defining your filters can be done in any subclass from `Kwf_Controller_Action_Auto_Abstract`.

The best way is to define them in preDispatch-function before calling `parent::preDispatch() `
or if you define them directly via

`protected $_filters = followed by your filter-definitions`

##Text

The simplest filter is a text filter that searches all displayed columns by default.

    //default text filter:
           $this->_filters = array('text' => true);
            
           //optionally define fields that should be search, defaults to all columns
           $this->_queryFields = array('foo');
            
           //text filter with custom settings:
           $this->_filters = array('text' => array(
               'type' => 'TextField',
               'width' => 90,
               'label' => 'Filter:',
               'queryFields' => array('foo', 'bar'), //search those fields
           ));
           
##Button
           
    $this->_filters = array('active' => array(
        'type' => 'Button'
        'text' => 'Only Active:',
        'icon'=>'/assets/silkicons/table_gear.png',
        'cls'=>'x-btn-text-icon'
    )); 

          
##ComboBox
          
If no data is provided it's working with the model set for controller 
and querying for the key used for filter in filter-array.    
      
      $this->_filters = array('type' => array(
          'type' => 'ComboBox',
          'label' => trl('Type'),
          'data' => array(
              'foo'=>trl('Foo'),
              'bar'=>trl('Bar'),
          ),
          'skipWhere' => true
      ));
      
      
##Date & DateRange
      
Additionally there are filters for Date and DateRange.
      
##Change filtering
      
If you want custom logic in your controller you first have to disable the default filtering by adding skipWhere:  
    
    $this->_filters = array('inactive' => array(
        'type' => 'Button'
        'skipWhere'=>true
    ));
    
    
and then implement your own logic in the controller:

    protected function _getSelect()
    {
        $ret = parent::_getSelect();
        if ($this->_getParam('query_inactive')) {
            //show only inactive
            $ret->whereEquals('active', false);
        } else {
            //show only active by default
            $ret->whereEquals('active', true);
        }
        return $ret;
    }
     
     
##Filter Class

    <?php
    class MyFilter extends Kwf_Controller_Action_Auto_Filter_ComboBox
    {
        protected function _init()
        {
            parent::_init();
            $this->setFieldName('column1');
            $this->setWidth(100);
            $this->setLabel('My Filter:');
            $data = array();
            //$data[] = array('ID', 'DisplayText');
            $data[] = array('1', 'Value 1');
            $data[] = array('2', 'Value 2');
            $this->setData($data);
        }
     
        public function formatSelect($select, $params = array())
        {
            if (isset($params['query_column1'])) {
                $column1 = $params['query_column1'];
                //configure the select object
            }
            return $select;
        }
    }
