#COMPONENT SETTINGS

Components have static settings, to define/change them override the static getSettings method in the component class: 

    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['componentName'] = 'Example';
            return $ret;
        }
    }
    
    
These settings will be cached so you must not use any dynamic code in getSettings.  
(like accessing the session, time etc., also don't use trl(), use trlStatic() instead)

##Usage

    Kwc_Abstract::getSetting('Example_Component', 'componentName');
    Kwc_Abstract::hasSetting('Example_Component', 'componentName');
     
    //get setting for Kwf_Component_Data object
    Kwc_Abstract::getSetting($data->componentClass, 'componentName');
     
    //get setting for Component object:
    Kwc_Abstract::getSetting($component->getData()->componentClass, 'componentName');
    //or use this (protected) helper:
    $component->_getSetting('componentName');
    //don't do that: Kwc_Abstract::getSetting(get_class($component), 'componentName');