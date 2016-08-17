#KEEP ALIVE

Koala Framework tried to avoid session timeouts by sending a keep alive request every 5 minutes to the server - while a backend page is opened.

##Manually enable

to enable this functionality on frontend pages call in javascript:

`Kwf.activateKeepAlive();`

##Modify action

You can also change what is done to keep alive the session: Overwrite the `Kwf.keepAlive` function. 
To disable it completely use:

`Kwf.keepAlive = function() {};`

