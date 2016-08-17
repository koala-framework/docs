#ADD AN EDITDIALOG TO A CONTROLLER

Using an editDialog in a AutoGrid you can edit grid entries using a form that will be shown in a modal dialog.

##Create a new AutoForm Controller

You have to define a model the controller has to use. Also add permissions what's possible with this controller. 
Define how the form looks like.

###Examplecode:

    <?php
    class Example_FooController extends Kwf_Controller_Action_Auto_Form
    {
        protected $_model = 'Foos';
     
        protected $_permissions = array('add','save');
     
        protected function _initFields()
        {
            parent::_initFields();
            $this->_form->add(new Kwf_Form_Field_TextField('name', trl('Name')));
        }
    }
    
    
##Add editDialog to AutoGrid controller
    
Depending on your super-class there exists an field called `$_editDialog` which holds a reference to the controller used to edit a single item.

Just set it like this:    

    protected $_editDialog = array(
            'controllerUrl' => '/admin/example/foo',
            'width' => '400'
        );
        
        
You can simply create an "edit-button" in your grid by adding a new `Kwf_Grid_Column_Button()` to the  columns.    
    
    
##Add AutoForm entry to Acl

(Describe why we have to add this to the Acl.php file)

Add this line of code to the `__construct()-function:`

    $this->addResource(new Zend_Acl_Resource('example_foo'),
             'example_foos');
             
             
##Advanced: custom AutoForm class
             
If you need a [custom form class](custom-form-grid-class.md) as editDialog first create a Window class that uses this AutoForm:    

    Example.FooFormWindow = Ext.extend(Kwf.Auto.Form.Window, {
        initComponent : function() {
            this.autoForm = 'Example.FooForm';
            Example.FooFormWindowsuperclass.initComponent.call(this);
        }
    });
    
and set that class for the _editDialog setting in the AutoGrid:    


    protected $_editDialog = array(
        'controllerUrl' => '/admin/example/foo',
        'type' => 'Kwf.Auto.FormPanelEx'
    );