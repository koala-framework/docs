#CREATE CUSTOM FORM/GRID CLASS

To customize a form or grid behavior you can create an own custom class that overrides methods or adds custom buttons/actions/whatever.

The example below is for a form, but works the same for a grid.

First you have to define the new class, inheriting from `Kwf.Auto.FormPanel`:

    Example.FooForm = Ext.extend(Kwf.Auto.FormPanel, {
        initComponent: function() {
            //add custom code here or override other methods
            Example.FooForm.superclass.initComponent.call(this);
        }
    });
    Ext.reg('example.fooform', Example.FooForm);
    
    
Then the class needs to be used:
    
1. Using xtype in indesAction()

    
        public function indexAction()
        {
            parent::indexAction();
            $this->view->xtype = 'example.fooform';
        }    
    
   
          
2. Create directly in javascript


        Example.FooPanel = Ext.extend(Ext.Panel, {
            initComponent: function() {
               //instead of creating a Kwf.Auto.FormPanel use custom class
                var fooForm = new Example.FooForm({
                     controllerUrl: '...'
                });
                Example.FooPanel.superclass.initComponent.call(this);
            }
        });

