#AUTOGRID

##Example Usage

    class ExampleController extends Kwf_Controller_Action_Auto_Grid
    {
        protected $_model = 'Members';
        protected $_paging = 20;
        protected $_buttons = array('add', 'save', 'delete');
     
        protected function _initColumns()
        {
            $this->_columns->add(new Kwf_Grid_Column('lastname', trl('Lastname'), 140));
            $this->_columns->add(new Kwf_Grid_Column('firstname', trl('Firstname')));
            $this->_columns->add(new Kwf_Grid_Column_Checkbox('visible', trl('Active'), 40));
        }
    }