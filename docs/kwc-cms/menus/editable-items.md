#MENU_EDITABLEITEMS

You can use `Kwc_Menu_EditableItems_Component` for adding additional properties to menu items. 
This can be any component like an image (for an icon), a style select or a whole paragraphs.

####To add EditableItms to a menu define it as child component in the menu:

     $ret['generators']['editableItems'] = array(
                'class' => 'Kwf_Component_Generator_Static',
                'component' => 'ExampleMenu_EditableItems_Component'
            );
            $ret['editComponents'] = array('editableItems');
            
####The EditableItems Component itself, which defines the child component which it instantiate for every menu item:

    <?php
    class ExampleMenu_EditableItems_Component extends Kwc_Menu_EditableItems_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['generators']['child']['component'] = 'ExampleMenu_EditableItems_Child_Component';
            return $ret;
        }
    }
    
    
####The menu template needs to be overridden to output the child at the wanted position, like for example:

    {% extends renderer.getComponentTemplate("Kwc_Menu_Component") %}
     
    {% block menuLink %}
    {{ renderer.component(m.editable) }}
    {{ renderer.componentLink(m.data, "#{linkPrefix}#{m.text}") }}
    {% endblock %}
    
    
##Child Image

The Child can be a simple Image, allows adding an image for every menu item.

##Child Style

The Child can also be a custom component that outputs a style selected from a list:

    //Child/Component.php
    class ExampleMenu_EditableItems_Child_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['ownModel'] = 'Kwf_Component_FieldModel';
            $ret['extConfig'] = 'Kwf_Component_Abstract_ExtConfig_Form';
            $ret['componentName'] = trlStatic('Style');
            return $ret;
        }
    }
     
    //Child/Controller.php
    class ExampleMenu_EditableItems_Child_Controller extends Kwf_Controller_Action_Auto_Kwc_Form
    {
    }
     
    //Child/Form.php
    class ExampleMenu_EditableItems_Child_Form extends Kwc_Abstract_Form
    {
        protected function _initFields()
        {
            parent::_initFields();
            $this->add(new Kwf_Form_Field_Select('style', trl('Style')))
                ->setValues(array(
                    'blue' => trl('Blue'),
                    'red' => trl('Red'),
                ));
        }
    }
     
     
    //Child/Component.twig
    {{ row.style }}
     