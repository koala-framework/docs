#TRANSLATING (LOCALIZATION)

In koala-framework is a `trl.xml` file where strings with source from Koala can be translated.

Strings with source application must be translated in a `trl.xml` in the application.

You can either edit the xml files manually, or use the trl controllers available in koala.


To use the controllers just add the following resources to your acl:

    $this->add(new Kwf_Acl_Resource_MenuUrl('kwf_trl_web',
        array('text'=>trlKwf('Translation Web'), 'icon'=>'comment.png'),
        '/kwf/trl/web'), 'settings');
        $this->add(new Zend_Acl_Resource('kwf_trl_web-edit'), 'kwf_trl_web');
    $this->add(new Kwf_Acl_Resource_MenuUrl('kwf_trl_kwf',
        array('text'=>trlKwf('Translation Common'), 'icon'=>'comment.png'),
        '/kwf/trl/kwf'), 'settings');
        $this->add(new Zend_Acl_Resource('kwf_trl_kwf-edit'), 'kwf_trl_kwf');
        
        
and the following dependency to your `dependencies.ini`:        

    Admin.dep[] = KwfTrlAdmin