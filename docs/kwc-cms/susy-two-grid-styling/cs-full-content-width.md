#FULL CONTENT WIDTH

If a component is only styled for full content width and doesn't work correctly in eg. 
columns with half content width you have to specify that.

    @import "kwc-susy/master-layout-helper";
     
    @include set-master-layout(default);
     
    .kwcClass {
        @include kwf-breakpoints(md lg) {
            &__foo {
                //foo should span over 6 columns (of 12)
                @include span(6);
            }
        }
    }
     
.


    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['layoutClass'] = 'Example_Layout';
            return $ret;
        }
    }
    
    
####You have to specify all supported context layouts:


    class Example_Layout extends Susy_Layout
    {
        public function calcSupportedContexts()
        {
            return array(
                array(
                    'masterLayout' => 'default',
                    'breakpoint' => 'sm',
                    'spans' => 12,
                ),
                array(
                    'masterLayout' => 'default',
                    'breakpoint' => 'md',
                    'spans' => 12,
                ),
                array(
                    'masterLayout' => 'default',
                    'breakpoint' => 'lg',
                    'spans' => 12,
                ),
            );
        }
    }