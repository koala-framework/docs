#MOBILE BREAKPOINT

Using this mixin you can scope styles to mobile devices.

    a.phoneNumber {
        display: none; /* hide by default */
        @include mobile-breakpoint {
            display: block; /* show on mobile devices */
        }
    }


Technically a media query is used that checks for typical smartphone resolution.