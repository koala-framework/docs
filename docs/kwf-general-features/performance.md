#POSSIBILITIES TO BOOST PERFORMANCE

Most important: **don't do premature optimization**. Always try to find a bottleneck using profiling tools and improve that. 
Everything else is wild guessing and/or just a waste of time.

##Enable viewcache

[Ways to enable viewcache even in dynamic components can be found here.](../kwc-cms/customize-components/dynamic-contents.md)

##Use stored expressions

[More about stored expressions and how they perform.](models/stored-expressions.md)

##When working with custom data objects

If you display expressions in a grid-controller and use a custom data object for a column the value is not calculated 
with the sql statement. So if the value is needed in the custom data object for instance it's a good idea
to add `$select->expr('EXPRS')`; in the `_getSelect()-function`. 
This way it's already calculated with the sql statement and therefore faster when used in your custom data object.