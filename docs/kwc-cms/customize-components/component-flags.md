#COMPONENT FLAGS

A component can have a different flags in it's static settings (getSettings function). The main advantage of those flags is that they are static and so can be cached for efficient usage.

###Example:

    public static function getSettings()
    {
        $ret = parent::getSettings();
        ...
        $ret['flags']['hasFulltext'] = true;
        return $ret;
    }
    
###This is a list of available component flags:

* hasFulltext (component can add custom contents to the fulltext index)
* skipFulltext (skip fulltext indexing for complete page when this component exists)
* skipFulltextRecursive (skip fulltext indexing for complete page and child pages when this component exists)
* usesFulltext (component uses the fulltext index, if set events are processed)
* hasLanguage (component has getLanguage method, used by translation system)
* hasAvailableLanguages (component has static getAvailableLanguages)
* hasBaseProperties (component has getBaseProperty($propertyName), used eg. by language)
* subroot
* noIndex (add noindex meta tag)
* hasHome
* metaTags
* hasAlternativeComponent
* processInput (component has processInput method)
* forwardProcessInput (component has getForwardProcessInputComponents method)
* chainedType
* menuCategory
* resetMaster (component has own Master.tpl and master templates above won't be used)
* hasIsVisibleDynamic (component has isVisibleDynamic method implemented to get hidden dynamically)
* hasAnchors (if set to true getAnchors() has to be implemented so that Kwc_Basic_LinkTag_Intern_Component can link to an anchor)
* assetsPackage (to split assets in multiple packages) (since 4.1)
* searchContent (deprecated)
* processMailRedirectInput (for Mails to get recipient data passed as GET parameter) (since 4.3)


##Flags in Detail

###hasFulltext-Flag:

Return an array of keys like defined in for example schema.xml of your solr config.

Implement function in `Component.php`:

    public function getFulltextContent()
    {
        $ret = array();
        $ret['type'] = 'publicdownloads';
        $ret['title'] = $this->getData()->getRow()->title;
        $ret['contenth2'] = $this->getData()->getRow()->teaser;
        return $ret;
    }