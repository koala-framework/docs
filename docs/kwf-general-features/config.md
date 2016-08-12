#CONFIG.INI

ini files are used to configure central parts of a Koala Framework app.

**There is a layer of ini files that are put on top of each other:**


     [kwf/config.ini]
             |
     [kwf/config.local.ini]
             |
    ([vkwf/config.ini] Internal) 
             |
    ([vkwf/configPoi.ini] Internal)
             |
    ([vkwf/config.local.ini] Internal, not under version control) 
             |
     [web/config.ini] 
             | 
     [web/config.local.ini] (not under version control, contains passwords etc)
 
 
The lower ones override values from above. 
That way it's possible to define a sensible default in ``kwf/config.ini`` that can be overridden if required.

#CONFIG SECTION

Using the config sections you can easily configure the web for multiple servers, like for example production server, 
test server and a local development server.

When another config section is used the relevant section from config files are used. 
Usually you inherit from the default (production) section and override required settings.

##Example
    [production]
    application.id = mytestapp
    debug.benchmark = false
    
    [test : production]
    debug.benchmark = true
    
##Used config section
The default config section is production, by creating a config_section (not under version control) file you can switch to another section: 
simply insert the name of the wished section. eg. test

##Additional config section
When you need an additional config section eg. `local` or `development` you can create it by adding:

    [local : test]
    kwfConfigSection = test
    
`: test` is for inheriting in web, kwfConfigSection = test is for the used kwf config section.