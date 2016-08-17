#GENERATOR FLAGS

A generator can have a different flags. 
The main advantage of those flags is that they are static and so can be cached for efficient usage.

###Example:

    class Example_FooGenerator extends Kwf_Component_Generator_Static_Page
    {
        public function getGeneratorFlags()
        {
            $ret = parent::getGeneratorFlags();
            $ret['showInPageTreeAdmin'] = true;
            return $ret;
        }
    }
     
    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['generators']['foo'] = array(
                'class' => 'Example_FooGenerator',
                'component' => 'Example_Foo_Component',
                'name' => 'foo'
            );
            return $ret;
        }
    }
    
    
    
###This is a list of available generator flags:

* showInLinkInternAdmin (pages created by this generator should be shown when choosing link target)
* showInPageTreeAdmin (data created by this generator should be shown in page tree admin)
* pageGenerator (is the generator which creates main pages based on kwf_pages table)
* page (creates pages)
* pseudoPage (creates pseudo pages)
* box (creates boxes)
* multiBox (creates multiBox)
* table (creates child data based on model)
* static (creates static child data)
* staticSelect
* hasHome (can create a home)
* chainedType
* trlBase