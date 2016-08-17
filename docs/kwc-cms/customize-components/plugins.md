#PLUGINS

Plugins provide ways the change the behavior of a component.

The baseclass is `Kwf_Component_Plugin_Abstract`. Additionally the plugin class must implement one of the plugin interfaces
 to do something useful.

To add a plugin to a component set it in getSettings-function like this:

    $ret['plugins'] = array('My_Plugin_Component', 'My_Second_Plugin_Component');
    
##Plugin Interfaces

* `Kwf_Component_Plugin_Interface_Login`: Media Output (eg. Image or Download) in a comonent below this plugin checks if the user is currently logged in.

* `Kwf_Component_Plugin_Interface_SkipProcessInput`: Allows (dynamically) skipping processInput for performance reasons. Example: Form

* `Kwf_Component_Plugin_Interface_UseViewCache`: Allows (dynamically) skipping view cache - with that it's possible to have one cached (default) version in view cache and disable it if required. Example: Form

* `Kwf_Component_Plugin_Interface_ViewAfterChildRender`: Allows changing rendered output after all child comonents are rendered. Example: placeholders

* `Kwf_Component_Plugin_Interface_ViewBeforeCache`: Allows modifying the the rendered output before saving it to view cache.

* `Kwf_Component_Plugin_Interface_ViewBeforeChildRender`: Allows changing rendered output before child components are rendered.

* `Kwf_Component_Plugin_Interface_ViewReplace`: gives the plugin the possibility to replace the (cached) view output with own content. Example: Login or Password