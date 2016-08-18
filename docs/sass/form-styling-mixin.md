#FORM STYLING MIXIN

Are you annoyed about form styling? No problem - this is the solution!


1. You need to import the form-styles mixin in your scss file:

        @import "form/form-styles";
        
        
2. It's time for the default settings, outside the .cssClass {}. The wording speaks for itself.
         
        $form-label-position  : left, right, top;
        $form-label-align  : left, right;
        $form-label-width  : px or %;
        $form-input-width  : px or %;
        $form-margin  : px or %;
        $form-error-style  : bubbles, simple-right, simple;       
        
        
Now you have to choose the parameters to setup the style of your form. When you don't
need a setting you can simply set false.


3. To use the mixin copy this directly in .cssClass {}


        @include form;
    