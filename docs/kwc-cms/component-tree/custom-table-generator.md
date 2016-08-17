#WRITING CUSTOM TABLE GENERATOR

Supporting `getComponentsByClass` and `getRecursiveChildComponents` across the whole component tree with sane performance is 
not an easy task. 
Especially as Koala can't cache in memory as php starts every request from scratch.

####Koala Framework implements this by querying components in two ways:

1. direct child: this is easy, only one generator has to be asked
   
2. indirect, generators can start somewhere in the tree and have to correctly find their location in the tree
    * `getChildData(null)`
    * `_formatSelect`
    * `_getParentByRow`