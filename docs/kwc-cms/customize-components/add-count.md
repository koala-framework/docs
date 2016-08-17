#ADD COUNT TO SPECIFIC MENU PAGES

First you have to set in the component, that is initialized as page, 
in the settings the flag **hasComponentLinkModifiers**

    $ret['flags']['hasComponentLinkModifiers'] = true;
    
As next you have to initialize the function **getComponentLinkModifiers**. 
There you have 2 choices of type. First is to appendText. This will be cached is not very dynamic.

    public function getComponentLinkModifiers()
    {
        $cnt = $this->getItemDirectory()->countChildComponents($this->getSelect());
        return array(
            array(
                'type' => 'appendText',
                'text' => ' ('.$cnt.')'
            )
        );
    }
    
This example will count any child components of the item directory an appends the count of this to the component link that 
links to this component.

Second method is that you will defind a callback function. But this call the callback function on every reload.

    public function getComponentLinkModifiers()
    {
        return array(
            array(
                'type' => 'callback',
                'callback' => array(
                    __CLASS__, 'linkModifiersCallback'
                )
            )
        );
    }
     
    public static function linkModifiersCallback($ret, $componentId, $text)
    {
        $component = Kwf_Component_Data_Root::getInstance()->getComponentById($componentId)->getComponent();
        $cnt = $component->getItemDirectory()->countChildComponents($component->getSelect());
        $text = '<span class="appendText">(' . $cnt . ')</span>';
        $ret .= $text;
        return $ret;
    }
    
    
This example for the callback function will do the same as the first example. 
But here the count will not be cached and on every reload of the page this will load again and again. 
So if a new childComponent is added the count will increase, otherwise when anyone is deleted it will decrease.
