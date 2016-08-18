#QUICK START 

##Create component

####create `components/Newsletter/Component.php:`

     <?php
       class Newsletter_Component extends Kwc_Newsletter_Component
       {
       }
         
    
##Create your component static on root level

####edit `components/Root/Component.php:`


    class Root_Component extends Kwc_Root_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            ........
            $ret['generators']['newsletter'] = array(
                'class' => 'Kwf_Component_Generator_Page_Static',
                'component' => 'Newsletter_Component',
                'name' => trlStatic('Newsletter')
            );
            .......
            return $ret;
        }
    }
    
    
Then execute `php bootstrap.php` update to automatically create required tables. After that you should see a Newsletter menu item in the backend.

To add additional components and style them see the mail component, which is in the newsletter.