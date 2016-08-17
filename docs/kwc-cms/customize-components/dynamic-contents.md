#WAYS TO MAKE COMPONENTS DYNAMIC WITH ENABLED VIEWCACHE

The best way to ensure good performance is to let viewCache enabled and generate dynamically only the minimal amount needed. This can be done in different ways:

##disable ViewCache

`$ret['viewCache'] = false;`

This setting disables the view cache for the component, not including child components. You should avoid this as it's not good for performance.

##expire viewCache

**By default view cache never expires. If you have time dependent contents 
or want to refresh the contents after a specific time you can let the view cache contents expire automatically.**

    public function getViewCacheLifetime()
    {
        return 60*60; //expire after 1 hour
    }
     
.

    public function getViewCacheLifetime()
    {
        //expire at the end of the day (if contents is date dependent)
        return mktime(0, 0, 0, date('m'), date('d')+1, date('Y')) - time();
    }
    
##ProcessInput

    $ret['flags']['processInput'] = true;
    
##Plugin

    $ret['plugins'] = array('PLUGIN');
    
####TODO
   
##Partials

####TODO

##Kwc_Form_UseViewCachePlugin

####TODO
    
    