#FRONTEND EVENTS

Component Events can be used in frontend by components to communicate. This is typically used to notify boxes about changes that happened in other components.


###Koala 4.0 and higher

    //import depency
    var ComponentEvent = require('kwf/component-event');
     
    //event handler for event
    ComponentEvent.on('customEventName', function(a) {
            console.log(a);
    });
     
    //fire an event
    ComponentEvent.trigger('customEventName', a);
    
    
###< Koala 4.0

    //event handler for event
    Kwf.onComponentEvent('fooChanged', function(a) {
        console.log(a);
    });
     
    //fire an event
    Kwf.fireComponentEvent('fooChanged', 1);
    
    
Examples where this can be used is an favorite articles feature where the count of favorites is shown in a box.