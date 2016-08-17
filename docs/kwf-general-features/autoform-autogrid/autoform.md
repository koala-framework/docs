#AUTOFORM

An auto form edits a single row of a model using a `Kwf_Form`.


##Example Usage

With form created in the controller:

    class ExampleController extends Kwf_Controller_Action_Auto_Form
    {
        protected $_modelName = 'Example';
     
        protected function _initFields()
        {
            $this->_form->add(new Kwf_Form_Field_TextField('foo', trl('Foo')));
            $this->_form->add(new Kwf_Form_Field_TextArea('bar', trl('Bar')));
        }
    }
    
    
Or, alternatively define the form as own class:

    class ExampleForm extends Kwf_Form
    {
        protected function _init()
        {
            parent::_init();
            $this->_form->add(new Kwf_Form_Field_TextField('foo', trl('Foo')));
            $this->_form->add(new Kwf_Form_Field_TextArea('bar', trl('Bar')));        
        }
    }
    class ExampleController extends Kwf_Controller_Action_Auto_Form
    {
        protected $_modelName = 'Example';
        protected $_formName = 'ExampleForm';
     
    }


An more advanced example can be found in the [kwf-app-demo](https://github.com/vivid-planet/kwf-app-demo/blob/master/controllers/MemberController.php) repository.