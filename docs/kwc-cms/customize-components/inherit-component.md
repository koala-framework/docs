#INHERIT COMPONENT

The **first step** to customize a component is to create your own variant of it. This is done by creating a new component that inherits the original one.

`components/ParagraphsBlue/Component.php`

    class ParagraphsBlue_Component extends Kwc_Paragraphs_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['componentName'] = trlStatic('Paragraphs Blue');
            return $ret;
        }
    }
    
We now have a new component where we could add [custom Css](../../styling/general/styling/) that styles it blue. 
The componentName setting will be shown to the user when he can choose this specific component - 
like as page type or paragraph type.

**Next step** is to actually use the new component - by setting it as child component in another component. 
This depends on where the component is used:

###Page Type

To use the component as page type add that to `config.ini`:

    kwc.childComponents.Kwc_Root_Category_Component.paragraphsBlue = ParagraphsBlue_Component
    
###Paragraph Type

To use the component as paragraph type add that to `config.ini`:

    kwc.childComponents.Kwc_Paragraphs_Component.paragraphsBlue = ParagraphsBlue_Component
    
###Others

For other components you have to set the [child component](child-components.md) using the settings.


Sometimes it is necessary to inherit several components to change one at a deeper level.
