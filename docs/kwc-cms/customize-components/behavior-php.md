#BEHAVIOR - PHP

There are several ways to change the server side behavior of a component.

##getTemplateVars

Important is the separation of fuctionality and layout. Layout should be implemented in `Component.tpl`,
getTemplateVars should return variables that can be used in the template.

    class Example_Component extends Kwc_Abstract
    {
        public function getTemplateVars()
        {
            $ret = parent::getTemplateVars();
            $ret['foo'] = 123;
            return $ret;
        }
    }
    
##View Cache

By default the output of a component (the result of executing getTemplateVars and rendering Component.tpl) will be cached. 
(this is the so called view cache). That means it is not possible to generate dynamic content (like something user 
or time related) in getTemplateVars or Component.tpl.

One way to work around this is to disable the view cache for this component:

    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['viewCache'] = false;
            return $ret;
        }
        public function getTemplateVars()
        {
            $ret = parent::getTemplateVars();
            //will be executed for every request
            return $ret;
        }
    }
    
This will not disable the view cache for child components. 
(which is good as child components still will have good performance)

##processInput

Another way to change the behavior of a component (without having to disable the view cache) is the processInput functionality. 
It allows you to execute code for every request. This can be used to implement logging, permissions etc.

    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['flags']['processInput'] = true;
            return $ret;
        }
        public function processInput($postData)
        {
            //will be executed for every request
        }
    }