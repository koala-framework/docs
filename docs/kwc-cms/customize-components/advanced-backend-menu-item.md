#CREATE A BACKEND BUTTON FOR YOUR COMPONENT

1. Create a "`MenuConfig.php`" file in your component folder
2. Add an entry to your "`Component.php"=>"getSettings()`"-function

##Create MenuConfig.php

This php file is called on boot-time. Here you can change the backend depending on your component needs.

###Sample Code:

    <?php
    class Articles_Directory_MenuConfig extends Kwf_Component_Abstract_MenuConfig_SameClass
    {
        public function addResources(Kwf_Acl $acl)
        {
            parent::addResources($acl);
     
             $acl->add(new Kwf_Acl_Resource_ComponentClass_MenuUrl(
                 'articletags_authors', array('text'=>trl('Autoren'), 'icon'=>'user_red'),
                 Kwc_Admin::getInstance($this->_class)->getControllerUrl('Authors'),
                 $this->_class
                 ), 'settings'
             );
     
        }
     
    }
    
##Add entry to your Component.php

To get a connection between your component and the `MenuConfig.php` you will have to add this line to your `getSettings()-function`:

$ret['menuConfig'] = 'MENU_CONFIG_CLASS';

