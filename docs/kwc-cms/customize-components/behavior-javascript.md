#BEHAVIOR - JAVASCRIPT

By default `Component.js` files are automatically loaded.

####You can add additional JavaScript dependencies to a component like that:

    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['assets']['files'][] = 'web/js/Example.js';
            $ret['assets']['dep'][] = 'ExampleDependency';
            return $ret;
        }
    }
    
####In the `Component.js` you usually should use Kwf.onElementReady and work with the element you get:

    Kwf.onElementReady('.example', function(el) {
        el.child('a').on('click', function(ev) {
            ev.stopEvent();
            el.child('span').update('clicked');
        }, this);
    });
    
    
##Methods

Different methods exist to initialize a component with custom JavaScript.

The J version passes jQuery object, instead of Ext.Element.

`on(J)ElementReady(selector, callback, options)`

This gets called exactly once for every element matching the selector. 
Using that you can initialize the behavior of the component, like installing click/hover handlers.

####`options`

* `checkVisibility`: if true call only when element is visible, defaults to false
* `scope`: scope used for calling the callback function, defaults to window
* `priority`: priority to change order of callback execution, higher number means it's called after all with lower number, 
    defaults to 0
    
####callback parameters:

* `el`: Ext.Element, or jQuery element



`on(J)ElementHide(selector, callback, options)`

Similar to onJElementShow, just for hiding the element.

`on(J)ElementWidthChange(selector, callback, options)`

Similar to onJElementShow, just for changing the element width. This gets also called an browser window resize.

####options:

* `checkVisibility`: if true call only when element is visible, defaults to false
* `scope`: scope used for calling the callback function, defaults to window
* `priority`: priority to change order of callback execution, higher number means it's called after all with lower number, defaults to 0

`on(J)ContentReady(callback, options)`

Called for once for every element that gets rendered, gets shown/hidden or changes it's width. Usually using onElementReady has better performance and should be preferred.

The callback is called exactly once for every callOnContentReady.

`options`:

* scope: scope used for calling the callback function, defaults to window
* priority: priority to change order of callback execution, higher number means it's called after all with lower number, defaults to 0

####callback parameters:

* `el`: dom node of element that changed, initially body
* `options`: action: render/show/hide/widthChange


`callOnContentReady(renderedEl, options)`

####This method must be called if:

* an element gets rendered (options.action='render')
* an element gets shown (options.action='show')
* an element gets hidden (options.action='hide')
* an element changes it's width (options.action='widthChange')
* It gets automatically called on dom ready width renderedEl=body.


