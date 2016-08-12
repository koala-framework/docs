#MENU ORDER

With` kwf 3.8` it is possible to set the setting "order" for resources.
The default order value is 0.
Negative and positive values are possible.

The order is not affected by priority (from component menuConfig).

Usage:

    $acl->add(new Kwf_Acl_Resource_MenuUrl('bar',
                    array('text'=> 'Bar', 'icon'=>'heart.png', 'order'=>1),