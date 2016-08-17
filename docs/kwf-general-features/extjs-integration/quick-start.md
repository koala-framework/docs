#QUICK START    

Prerequisites for this are knowledge about Acl and Controllers.

This tutorial shows you the required steps to create a menu item that shows a custom ExtJS class (based on Ext.Panel)

##Create Ext.Panel based class

    Ext.ns('Example');
    Example.Foo = Ext.extend(Ext.Panel,
    {
        initComponent : function()
        {
            console.log(this.testParameter); //passed by indexAction
     
            this.html = 'foobar';
     
            Example.Foo.superclass.initComponent.call(this);
        }
    });
    Ext.reg('example.foo', Example.Foo);
    
    
##Create Controller

    class Example_FooController extends Kwf_Controller_Action
    {
        public function indexAction()
        {
             //pass any parameters that will end up in Panel config
            $this->view->testParameter = 123;
     
            $this->view->xtype = 'example.foo'; //refer to xtype registered with Ext.reg()
        }
    }
    
also see [start controller](start-controller.md)

##Create Menu Entry in Acl that links to new controller

    $this->addResource(new Kwf_Acl_Resource_MenuUrl('example_foo',
                    array('text'=>trl('Foo'), 'icon'=>'user.png'),
                    '/example/foo'));