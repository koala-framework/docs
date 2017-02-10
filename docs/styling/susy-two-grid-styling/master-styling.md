#MASTER STYLING

Once you have the master layout configured you can use the grid system for layouting elements in Master.


    @import "kwc-susy/master-layout-helper";
     
    @include set-master-layout(default);
     
    .kwcClass {
        &__header {
            @include kwf-breakpoints(sm md lg) {
                @include container();
            }
            @include kwf-breakpoints(md lg) {
                &__logo {
                    @include spans(6);
                }
            }
        }
    }