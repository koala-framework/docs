#CHILD CONTEXTS

When a component gives a child component less width (spans) it has to specify that.

Example with child paragraphs that span half width:

    class Example_Component extends Kwc_Abstract_Composite_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['generators']['child']['component']['paragraphs'] = 'Kwc_Paragraphs_Component';
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
    
.


    <div class="{{ rootElementClass }}">
        <div class="{{ "left"|bemClass }}">
            {{ renderer.component(paragraphs) }}
        </div>
    </div>
    
    
    
#Styling
####Give the paragraphs the half width:

    @import "kwc-susy/master-layout-helper";
    @include set-master-layout(default);
     
    .kwcClass {
        @include kwf-breakpoint((md lg)) {
            .kwcClass__left {
                @include span(6);
            }
        }
    }
    
    
##Layout

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
                )
            );
        }
     
        public function calcSupportedChildContexts()
        {
            return array(
                'child' => array(
                    array(
                        'masterLayout' => 'default',
                        'breakpoint' => 'sm',
                        'spans' => 6,
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
                )
            );
        }
     
        public function getChildContexts(Kwf_Component_Data $data, Kwf_Component_Data $child)
        {
            if ($child->id == 'paragraphs') {
                return array(
                    array(
                        'masterLayout' => 'default',
                        'breakpoint' => 'sm',
                        'spans' => 6,
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
            return parent::getChildContexts($data, $child);
        }
    }