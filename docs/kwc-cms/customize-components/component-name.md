#COMPONENT NAME

Every Component has an important setting that is used in various places.

     public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['componentName'] = 'My Component';
            return $ret;
        }
        
##Categories

If the Component can be added as paragraph in Paragraphs_Component you 
can specify additional settings that help structuring the menu.

####Example:

     $ret['componentCategory'] = 'special';
     $ret['componentOrderPriority'] = 10;
     
####Available categories are:

* `'content'`: Content, won't be shown in submenu
* `'none'`: No category (the default)
* `'layout'`: Layout related
* `'media'`: Multimedia content eg. videos, image galleries, slideshows, etc.
* `'contact'`: Contact information and contact forms
* `'callToAction'`: Buttons/Links with custom styles
* `'childPages'`: List child pages
* `'special'`: Special components
* `'model'`: Related to eg. car models
* `'admin'`: components that should be added by admins only


The `'componentOrderPriority'` setting allows you to change the order within that category.