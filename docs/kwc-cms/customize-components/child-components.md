#CHILD COMPONENTS

A component can create child components, and you can change the component class of created child components.

To do that you have to modify the generators setting of the component:

    class Example_Component extends Kwc_Abstract_Composite_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['generators']['child']['component']['text'] = 'Kwc_Basic_Text_Component';
            return $ret;
        }
    }
    
    
####There two several ways how generators are defined:

    //generator can have multiple child components
    $ret['generators']['child']['component']['text'] = 'Kwc_Basic_Text_Component';
     
    //generator can have single child component
    $ret['generators']['child']['component'] = 'Kwc_Basic_Text_Component';
    
  
Check the parent component class to see which is the correct way.