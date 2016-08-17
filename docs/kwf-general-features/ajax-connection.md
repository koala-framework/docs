#AJAX / EXT.CONNECTION

Koala Framework uses the ExtJS Connection class for all ajax request. Read [that documentation](https://dev.sencha.com/deploy/ext-2.3.0/docs/?class=Ext.data.Connection) for the basics.

####Koala Framework adds a few request options on top of that:

* `mask:` shows mask while the request is running. true to mask the whole body; element to mask this element
* `maskText:` text shown in the mask, default is 'Loading...'
* `progress:` show a progress bar for this request
* `progressTitle:` title of the progress bar, default is 'Progress'
* `ignoreErrors:` don't do any error handling for this request, failure callback will still be called

##Error Handling

When a request fails a error message will be displayed, in debug mode this will also contain debug information and give the user the possibility to resend the request.

##Progress Bar

For more time consuming actions you can show a progress bar that will automatically update from the server side.

    Ext.Ajax.request({
        timeout: 10*60*1000, //10min
        url: '/example/json-foo',
        progress: true
    });
    
And in the Php Action:
    
    public function jsonFooAction()
    {
        $progressBar = new Zend_ProgressBar(
            new Kwf_Util_ProgressBar_Adapter_Cache($this->_getParam('progressNum')),
                0,  //min
                10  //max
        );
        for($i=0; $i<10; $i++) {
            $progressBar->next(1, trl('doing nothing...'));
            sleep(1);
        }
    }