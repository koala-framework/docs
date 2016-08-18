#BASE PROPERTIES

If you want to retrieve a value of the current subroot, you can use the method getBaseProperty of the data object. 

####Examples:

`$data->getBaseProperty('domain'); // gets the domain when using multi domain webs (e.g. "at")`

`$data->getBaseProperty('language');`

####Also other config settings can be retrieved. Let's use the representation of money values as example. Koala Framework uses as default the following 
(`config.ini` in Koala Framework):

`money.format = "EUR {0}"`

####If a domain uses another format, it's possible to change it in the config.ini of the web:

`kwc.domains.us.money.format = "{0} US-Dollar";`

####To get the money format for the current page you're in, it's then possible to use the following statement:

`$data->getBaseProperty('money.format');`