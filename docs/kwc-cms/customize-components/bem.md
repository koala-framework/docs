#BEM

[BEM](https://en.bem.info/) stands for "Block Element Modifier" is a standard how css is structured.
Starting with koala-framework 4.0 it can be activated with `application.uniquePrefix` in `config.ini` - then everything should follow the BEM standard.

When uniquePrefix is activated:

* there must be no class in html without the uniquePrefix prefixed
* there must be no selector in css starting without uniquePrefix

##Component.scss

    .kwcClass {
        &__subElement {
            color: red;
        }
        &--modifier {
     
        }
    }
    
##Component.tpl

    <div class="<?=$this->rootElementClass?>">
        <div class="<?=$this->bemClass('subElement')?>">
            Foo
        </div>
    </div>

       
##Component.twig

    <div class="{{ rootElementClass }}">
        <div class="{{ "subElement"|bemClass }}">
            Foo
        </div>
    </div>
    
    
##Component.php getTemplateVars

    public function getTemplateVars(Kwf_Component_Renderer_Abstract $renderer = null)
    {
        $ret = parent::getTemplateVars($renderer);
        $ret['subElementClass'] = $this->_getBemClass('subElement');
        $ret['modifier'] = $this->_getBemClass('--modifier');
        $ret['modifier2'] = $this->_getBemClass('subElement--modifier');
        return $ret;
    }