#COMPONENT TREE

Components are organized in a "Component Tree" - components can have arbitrary child components.

####The tree consists of three basic types of items:

* component (basic component)
* page (like a component but has it's own url)
* box (like a component but gets placed differently in the layout)

####This tree servers multiple purposes:

* generates hierarchical url for pages 
* resolves those hierarchical urls
* possibility to attach any component to any other component
* makes it possible to have a backend that shows the pages in a tree
* menus can get the relevant menu items out of it
* you can query the tree for a specific component class
* you can navigate the tree to find needed data