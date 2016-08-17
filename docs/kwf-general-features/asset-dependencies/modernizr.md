#MODERNIZR

Modernizr is fully integrated in koala. And it's easier than ever :-)

Just add the modernizr import to your scss-file and start using the modernizr-mixin

    @import "kwf/modernizr";
    html .kwcClass {
        @include modernizr-no(cssChecked, checked) {
              input.radio {
                ...
            }
        }
        @include modernizr(cssanimation) {
            ...
        }
    }