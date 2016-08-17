#START CONTROLLER

To start an ExtJS based application you must have an Action that refers to an Ext.Panel subclass. 
Optionally you can pass config that will end up in the Panel.

###Refer to panel xtype (preferred)

    class Example_FooController extends Kwf_Controller_Action
         {
             public function indexAction()
             {
                  //pass any parameters that will end up in Panel config
                 $this->view->testParameter = 123;
          
                 $this->view->xtype = 'example.foo'; //refer to xtype registered with Ext.reg()
             }
         }
         
         
###Refer to panel class name (deprecated)

    class Example_FooController extends Kwf_Controller_Action
         {
             public function indexAction()
             {
                 //pass any parameters that will end up in Panel config
                 $config = array(
                     'testParameter' => 123
                 );
                 $this->view->ext('Example.Foo', $config); //refer to class name, no need to register xtype with Ext.reg()
             }
         }