# Custom backend component settings

This will show you how you can add custom settings to your component for the backend user.  
In this example you will see how to add a select-box where the backend user can set their desired background color for the component.

## Backend form

You need to add a Form.php to your component that has your settings for the backend users.  
In this case we are using `Kwf_Form_Field_Select` to create a select-box.

### Form.php
    <?php
    class MyComponent_Form extends Kwc_Abstract_Form
    {
        protected function _initFields()
        {
            parent::_initFields();
            $options = $this->add(new Kwf_Form_Container_FieldSet(trlKwf('Options')));
            
            $options->add(new Kwf_Form_Field_Select('background_color', trlKwf('Background Color')))
                ->setValues(array(
                    'red' => trlKwf('Red'),
                    'blue' => trlKwf('Blue')
                )
            );
        }
    }


## Styling

The following code shows you how you can add a css modifier class to your `rootElementClass` , based on the input of the backend user. This is done in `getTemplateVars()`.

### Component.php
    
    <?php
    class MyComponent_Component extends Kwc_Abstract_Component
    {
        public static function getSettings($param = null)
        {
            $ret = parent::getSettings($param);
            // My component settings
            return $ret;
        }
    
        public function getTemplateVars(Kwf_Component_Renderer_Abstract $renderer)
        {
            $ret = parent::getTemplateVars($renderer);
            $backgroundColor = $this->_getRow()->background_color;
            $ret['rootElementClass'] .= ' ' . $this->_getBemClass('--' . $backgroundColor);
            return $ret;
        }
    }

### Component.scss

    .kwcClass {
        &--red {
            background-color: Tomato;
        }
        
        &--blue {
            background-color: RoyalBlue;
        }
    }
