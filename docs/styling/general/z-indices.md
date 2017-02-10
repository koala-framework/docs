#Z-INDICES IN KOALA-FRONTEND

When using z-index in your css try to choose a not too high value. Find the correct position in this list where your element needs to be placed.

* 100 Lightbox (lightbox)
* 90 Lightbox Background (lightbox-background)
* 50 Header - (if content scrolls below the header when the header is fixed) (header)
* 45 Switch Content (switch-content)
* 40 Menu_Dropdown: dropdown (dropdown)
* 38 Menu_DropdownMask: content mask (content_mask)
* 35 ScrollUp Button in AjaxView (scroll-up-btn)
* 30 Form Error Bubbles (form-error)
* 25 Kwc_SocialMedia_2ClickButtons_Component (social-click)

You can use the z-index sass mixin to avoid a collision with the koala frontend z-indices. The mixin creates a z-index above or below the given koala layer. Optional you can set a offset to handle the z-indices between the given layers.


    @import "kwf/z-index";
     
    .cssClass {
        @include z-index(header, 'above', 2); // z-index: 52
        @include z-index(form-error, 'below'); // z-index: 29
    }