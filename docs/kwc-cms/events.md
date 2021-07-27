#EVENTS

Events are used to get informed when something happened. For example if data was inserted into a model and so on.

For this purpose there are several classes informing you about happenings. You can find them in `Kwf/Kwf/Component/Event` directory. 
Koala already uses this in it's core features like paragraphs, composite component and any sub-component. 
In this context it's used to clear the cache on changes to data.

To listen to events just create a new file called `Events.php` in your component folder and let the class extend `Kwf_Component_Abstract_Events.` 
If you take a short look into `Kwc_Abstract_Events` you will find a example getListeners-function which is used to define which events you want to listen to.

    <?php
    class Foo_Bar_Events extends Kwf_Component_Abstract_Events
    {
        public function getListeners()
        {
            $ret = array();
            $ret[] = array(
                'class' => 'ExampleModel',
                'event' => 'Kwf_Events_Event_Row_Updated',
                'callback' => 'onRowUpdate'
            );
            $ret[] = array(
                'class' => 'ExampleModel',
                'event' => 'Kwf_Events_Event_Row_Inserted',
                'callback' => 'onRowInsert'
            );
            return $ret;
        }
     
        public function onRowUpdate(Kwf_Events_Event_Row_Updated $event)
        {
            // do your logic
        }
     
        public function onRowInsert(Kwf_Events_Event_Row_Inserted $event)
        {
            // do your logic
        }
    }
    
    
The class you might want to listen should fire events. An example is every row-class and model. 
So if you want to listen to changes like `insert/update/delete` of rows of a specific model just put the models name at the `CLASS_TO_LISTEN` position.

**`'event'`** is used to define the event-class you are listening to.

**`'callback'`** references to the function in your events class which should be invoked.


To check if a concrete column has changed, because this is the only column shown by this component, you can use

`$event->isDirty('customColumn');`

or

`$event->isDirty(array('customColumn1', 'customColumn2');`
