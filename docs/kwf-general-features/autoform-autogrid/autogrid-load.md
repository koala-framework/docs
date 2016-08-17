#LOAD AN ID IN BACKEND WITH GET PARAMETER

Sometimes you need to provide a link to a special item in backend handled by a controller. This approach can be handy if other controllers are connected via binding.

Just look in the indexAction function for parameters like this:

`$param = $this->getRequest()->getParam('param');`

Forward this information to your ExtJs form and add this field to your grid or other list of items:

    var fooGrid = new Kwf.Auto.GridPanel ({
                controllerUrl: '/admin/foo/foo',
                autoLoadId: this.param  //this line loads a start value
            });
            
            
If you call this controller with a parameter it will add a filter-field and insert your value. Maybe this behavior can differ if you use different key than 'id'.

It's also a good practice to add a filter to help search for an entry.

Just add this lines of code to your `_initColumns()` function:     
       
        $this->_filters['text'] = array(
                   'type'=>'TextField',
                   'width' => 90,
                   'label' => 'Filter:'
               );