#KWF_SWITCH_HOVER_FADE: DROPDOWN MENU

##dependencies

Add this line to your `dependencies.ini` file: `Frontend.dep[] = KwfSwitchHoverFade`

##Create a special html css structure

You need to add a css class called "`kwfSwitchHoverFade`". This should contain a "`switchLink`" and a "`switchContent`" class. 
switchLink is used to show and hide switchContent on hover. Just place your data in the switchContent region.

###Example Html:

    <div class="kwfSwitchHoverFade">
        <div class="switchLink">
            Foo
        </div>
        <div class="switchContent">
            Bar
        </div>
    </div>