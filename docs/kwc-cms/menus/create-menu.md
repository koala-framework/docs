#CREATE A MENU

To create a menu you need to know "`Kwc_Menu_Component`".

You will also want to place the menu on a specified area on your website. 
To do so you have to add a box-generator into getSettings of your `Root/Component.php`.

    <?php
    class Root_Component extends Kwc_Root_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
     
            $ret['generators']['box']['component']['mainMenu'] = 'Menu_Main_Component';
            // other initialisation stuff
            return $ret;
        }
    }
    
The last array index defines how to access this component in your `Root/Master.tpl`

####Just add this at any location (in html) in your Master.tpl:

    <?=$this->doctype('XHTML1_STRICT');?>
    <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
           YOUR STUFF
        </head>
        <body class="frontend">
     
            <?=$this->component($this->boxes['topMenu']);?>
     
        </body>
    </html>
    
**Line 8 is needed to show the menu.**

The last step is to add the menu to your `config.ini` file.
####Add the following line:

    kwc.pageCategories.main = NAMEOFMENU
    
the part after pageCategories (main) has to be set in the `getSettings-Method` of the component.

    <?php
    class Menu_Main_Component extends Kwc_Menu_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['level'] = 'main';
            $ret['cssClass'] .= ' webListNone';
            $ret['generators']['subMenu'] = array(
                'class' => 'Kwc_Menu_Generator',
                'component' => 'Menu_Sub_Component'
            );
            return $ret;
        }
    }
    
    
`$ret['generators']['subMenu']` is used to define a submenu component. Class defines the generator and component which 
component class should be used. The whole submenu is optional and can be nested as deep as you whish. 
Just add a generator into the subclass component to get another level.

    <?php
    class Menu_Sub_Component extends Kwc_Menu_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['level'] = 2;
            $ret['cssClass'] .= ' webListNone';
            $ret['generators']['subMenu'] = array(
                'class' => 'Kwc_Menu_Generator',
                'component' => 'Menu_SubSub_Component'
            );
            return $ret;
        }
    }
    
.


    <?php
    class Menu_SubSub_Component extends Kwc_Menu_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['level'] = 3;
            $ret['cssClass'] .= ' webListNone';
            return $ret;
        }
    }
    
    
This is now a three-leveled menu.

You can now style the component like any other component.

Configuration happens in backend. There every menu has its own entry in sitetree.