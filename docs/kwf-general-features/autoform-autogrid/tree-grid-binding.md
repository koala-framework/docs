#MAKE A FORM WITH BINDING

When a form has to configure something for a special parent you will need something like binding.
1. Create your controller
2. define indexAction()
3. configure bindings
4. handle bindings in your controller

##Create your controller

This step can be read [here](../controllers/overview.md).

##Define indexAction()

The indexAction function is needed to... TODO

##Configure bindings

In your defined js-file you have to define the bindings field. Most of the time you will have a relation 
between some sort of list and a view of form. In the list you have to define the following:


    var lessonsGrid = new Kwf.Auto.GridPanel({
                controllerUrl: '/admin/lessons/category-lessons',//results in error
                region: 'center'
            });
     
     
    var categoriesGrid = new Kwf.Auto.SyncTreePanel({
                controllerUrl: '/admin/lessons/categories',
                region: 'west',
                width: 440,
                split: true,
                //this is used to set bindings
                bindings: [{
                    item: lessonsGrid, //this is the form or view to bound
                    queryParam: 'category_id' //this is the field of the controller which is the parameter
                }],
                title: 'Kategorien'
            });
            
##Handle bindings in your controller
            
You can access the binding value by typing:
            
     $this->_getParam('category_id');
            
Depending on your super class you can define the shown values by returning a customized select statement though 
the function `_getSelect(). `           