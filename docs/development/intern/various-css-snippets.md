#VARIOUS CSS SNIPPETS

###Button-Padding in Firefox

Button-tag is bigger than the elements inside.

**Example**: VWPKW -> Jobportal -> Search Button

    button::-moz-focus-inner {
        border: 0;
        padding-right: 0;
    }


###Image-Tag Spacing in all Browsers

There is a tiny space (~3px) on the bottom of the element where the img-tag is inside. Example: Kwc -> Image Component 

**Solution**: display: block; on the IMG


    Box Shadow in all Browsers (including InternetExplorer!!!!)
    box-shadow: 5px 7px 14px #999999;
    -moz-box-shadow: 5px 7px 14px #999999;
    -webkit-box-shadow: 5px 7px 14px #999999;
    behavior: url(/assets/css3pie/pie.htc);
     
    //for IE 8 - when css3Pie isn´t working well: -ms-filter: "progid:DXImageTransform.Microsoft.Shadow(Strength=4, Direct