#ADVANCED JAVASCRIPT

###Example for an advanced component that loads data using ajax

####components/Basic/Example/Component.php:

    public function getTemplateVars()
    {
        $ret = parent::getTemplateVars();
        $ret['config'] = array(
            'controllerUrl' => Kwc_Admin::getInstance($this->getData()->componentClass)->getControllerUrl('Foo'),
            'componentId' => $this->getData()->dbId
        );
        return $ret;
    }
    
####components/Basic/Example/Component.tpl:

    <div class="<?=$this->cssClass?>" data-config="<?=htmlspecialchars(json_encode($this->config))?>">
    </div>
    
####components/Basic/Example/FooController.php:

    public function jsonFooAction()
    {
        $this->view->bar = 123;
    }
    //To set the right permissions (Warning: this overrules the Acl):
    protected function _isAllowedComponent()
    {
        return true;
    }
    
####components/Basic/Example/Component.js:

    Kwf.onJElementReady('.cssClass', function(el) {
        var config = el.data('config');
        $.ajax({
            dataType: "json",
            url: config.controllerUrl+'/json-foo',
            data: {},
            success: function(data) {
                el.append(data.bar);
            }
        });
    });