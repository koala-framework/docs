#STYLING

To style a component you simply need to create a `Component.css` file in the component's folder. 
It will be picked up automatically. All `Component.css` files of parent component classes will also be used.

Styling should only be done scoped for only this component, this can be achieved by adding `.kwcClass` (or `.cssClass` before version 4.0) as the main selector. 
This will be replaced by a unique selector for this specific component.

###Example:

    .kwcClass h1 { color: red; }
    
##Scss

Alternatively you can also use [sass/scss](http://sass-lang.com/) for styling, simply create a `Component.scss` file instead.

###Example:

    .kwcClass {
        h1 { color: red; }
    }
