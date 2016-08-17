#AUTOGRID GROUPING

##Example Usage

    class ExampleController extends Kwf_Controller_Action_Auto_Grid
    {
        protected $_model = 'Members';
        protected $_paging = 20;
        protected $_buttons = array('add', 'save', 'delete');
        protected $_grouping = array(
            'groupField' => 'lastname',
            'noGroupSummary' => true
        );
     
        protected function _initColumns()
        {
            $this->_columns->add(new Kwf_Grid_Column('lastname', trl('Lastname'), 140));
            $this->_columns->add(new Kwf_Grid_Column('firstname', trl('Firstname')));
            $this->_columns->add(new Kwf_Grid_Column_Checkbox('visible', trl('Active'), 40));
        }
    }
    
    
You have todo only two things:

1. Set the protected attribute $_grouping as array.
    * With the key groupField for the db column
    * if you don't want a summary row at the end set noGroupSummary
2. Load the dependency ExtGroupingGrid