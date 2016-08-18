#MULTIPLE CONTEXTS

A component can support multiple layout contexts, for example in different columns.

    class Example_Component extends Kwc_Abstract
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['layoutClass'] = 'Example_Layout';
            return $ret;
        }
     
     
        public function getTemplateVars(Kwf_Component_Renderer_Abstract $renderer)
        {
            $ret = parent::getTemplateVars($renderer);
     
            //pass contexts into html
            foreach ($this->getMasterLayoutContexts() as $c) {
                $ret['rootElementClass'] .= " kwfUp-$c[masterLayout]-$c[breakpoint]-spans$c[spans]";
            }
     
            return $ret;
        }
     
    }
    
##Variant I
####use context class and specify `of` in span manually.

    @import "kwc-susy/master-layout-helper";
    @include set-master-layout(default);
     
    .kwcClass {
        @include kwf-breakpoints(md lg) {
            &.kwfUp-default-#{$breakpoint-name}-spans12 {
                .kwcClass__foo {
                    @include span(6 of 12); //"of 12" is optional as by default all columns are used
                }
            }
            &.kwfUp-default-#{$breakpoint-name}-spans6 {
                .kwcClass__foo {
                    @include span(3 of 6);
                }
            }
        }
    }

##Variant II
####use context class and specify context using span mixin.

    @import "kwc-susy/master-layout-helper";
    @include set-master-layout(default);
     
    .kwcClass {
        @include kwf-breakpoints(md lg) {
            &.kwfUp-default-#{$breakpoint-name}-spans12 {
                .kwcClass__foo {
                    @include span(6); //of 12, the default
                }
            }
            &.kwfUp-default-#{$breakpoint-name}-spans6 {
                @include nested(6) {
                    .kwcClass__foo {
                        @include span(3); //of 6, as defined by the span(6)
                    }
                }
            }
        }
    }
    
    
##Variant III
####use Kwf-breakpoints-spans

    @import "kwc-susy/master-layout-helper";
    @include set-master-layout(default);
     
    .kwcClass {
        @include kwf-breakpoint-spans(md lg, 12) {
            .kwcClass__foo {
                @include span(6); //of 12, as defined by kwf-breakpoint-spans
            }
        }
        @include kwf-breakpoint-spans(md lg, 6) {
            .kwcClass__foo {
                @include span(3); //of 6, as defined by kwf-breakpoint-spans
            }
        }
    }
    
    
####And finally you have to specify all supported layout contexts:

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
                array(
                    'masterLayout' => 'default',
                    'breakpoint' => 'md',
                    'spans' => 6,
                ),
                array(
                    'masterLayout' => 'default',
                    'breakpoint' => 'lg',
                    'spans' => 6,
                ),
            );
        }
    }