#BACKGROUND IMAGE DPR2

    @import "kwf/background-image-dpr2";
    

.


    .example {
        @include background-image-dpr2('/assets/web/images', 'example.png',
        100px, 100px, no-repeat left top transparent);
    }
    
    
####two file have to exist:

* images/example.jpg (100x100)
* images/dpr2/example.jpg (200x200)

the last parameter is for background settings like "repeat", "position" and "color", but its optional.