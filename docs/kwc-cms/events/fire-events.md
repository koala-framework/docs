#FIRE EVENTS

In some cases you will want to fire an event. There are several important standard events which are for example used to clear the cache of 
a component or do some other framework stuff.

To fire an event you need an instance of your event class.

In a Kwf_Component_Abstract_Events class you can simply call

`$this->fireEvent(new MyEvent());`

####To do this for example in a controller you will have to do it like this:

`Kwf_Component_Events::fireEvent(new MyEvent());`