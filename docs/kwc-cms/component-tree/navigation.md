#NAVIGATION IN THE COMPONENT TREE

Every node in the component tree is represented by a `Kwf_Component_Data object`. This object is not the component itself 
(mainly for performance reasons to allow lazy loading).

##Access Component

Every Data object has a 1:1 relation to the component object:

* `$data->getComponent()`: returns component instance of data
* `$component->getData()`: returns data instance of component

##Data Properties

####Data objects are created by generators and the generators set various properties on them:

* `$data->componentClass`: string of component class name. Can contain arguments (separated by . from class name)
* `$data->componentId`: component id string: unique id for this data
* `$data->dbId`: db id string (use that when storing data for this component in database)
* `$data->generator`: generator object that created this data
* `$data->parent`: reference to parent data
* `$data->isPage`: if the data is a page
* `$data->isPseudoPage`: if the data is a pseudo page
* `$data->visible`: if this data object is visible. Always true for static generators, 'visible' column for table generators

####Data objects created by **page** generators have the following additional properties:

* `$data->name`: string used as name for this data
* `$data->filename`: string used in url for this data
* `$data->url`: full url of data
* `$data->rel`: rel that should be used together with url when linking the page
* `$data->showInMenu`: if this page should be shown in menus
* `$data->isHome`: if this page is the home page

####Data objects created by **table** generators have the following additional properties:

* `$data->id`: id used by the generator to create this data, is also the last part in componentId
* `$data->row`: row object that created this data

##Parent Data

A data object always knows about it's parents, accessing them is cheap as they usually exist in memory:
`$data->parent`

####Various helper methods exist:

* `$data->getPage()`: If $data is page itself return it, else go up the tree to the next page. If no page is found null
* `$data->getPageOrRoot()`: like getPage(), but if no page is found root data
* `$data->getParentPage()`: returns the parent page, if none is found null
* `$data->getParentPageOrRoot()`: like getParentPage(), but if none is found root data
* `$data->getPseudoPage()`: like getPage(), but look for pseudo page
* `$data->getPseudoPageOrRoot()`: like getPageOrRoot(), but look for pseudo page
* `$data->getParentByClass($class)`: go up the tree and stop at a given componentClass
* `$data->getParentComponent($numParents)`: go up the tree $numParents times
* `$data->getParentComponentId($numParents)`: go up the tree $numParents times but only return the componentId instead of a data object


##Kwf_Component_Select

When accessing the component tree, a select object can be used to filter the result. 
Think of it like an WHERE part in sql statements.

* `whereComponentClass($class)`: filter for specific component class. The class must be an exact match (inheritance is ignored)
* `whereComponentClasses(array $classes)`: filter for multiple component classes
* `whereGenerator($generatorKey)`: filter for a specific generator with key as it is defined in component settings
* `whereShowInMenu()`: filter for data objects with showInMenu=true
* `whereHome()`: filter for home page
* `wherePage()`: filter for pages
* `wherePseudopage()`: filter for pseudo pages
* `whereBox()`: filter for boxes
* `whereMultiBox()`: filter for multi boxes
* `whereFlags(array('exampleFlag'=>true))`: filter for components having given flags
* `whereFlag('exampleFlag', true)`: short form for whereFlags()
* `whereSubroot($data)`: filter for data objects only under given subroot. if $data is not a subroot it's subroot will be used
* `ignoreVisible(true)`: if visiblity should be ignored
* `limit($limit, $offset)`: limit the number of returned objects

####Other not so commonly used methods:

* whereFilename()
* whereComponentKey()
* whereGeneratorFlags(array('exampleFlag'=>true))
* whereGeneratorFlag('exampleFlag', true)
* wherePageGenerator()
* whereInherit()
* whereUnique()
* whereHasEditComponents()
* whereGeneratorClass()
* whereChildOf($data)

###Array form

As creating an select object requires quite some code there is also a convenience short form for passing a select:

    $s = new Kwf_Component_Select();
    $s->whereComponentClass('Example_Component');
    //can be written as:
    $s = array('componentClass' => 'Example_Component')
    
    
All other where...() methods are supported.

Other special forms: `array('ignoreVisible'=>true), array('limit'=>1)`

###Model select

`Kwf_Component_Select` inherits `Kwf_Model_Select`, so all those methods are also supported and used by table generators. 
Using that you can filter by any column existing in a model that is used by a table generator.

###Examples:

    $foo->getChildComponents(array('componentClass'=>'Example_Component'));
.

    s = new Kwf_Component_Select();
    $s->whereComponentClass('Example_Component');
    $foo->getChildComponents($s);
.

    $foo->getChildComponents(array('flag'=>'test'));
    
    
##Child Data

There are various ways to access child data. When accessing a table generator a database query has to be made. 
If you get hundreds of data objects this will obviously require memory.

* `$data->getChildComponents($select)`: returns child components of `$data` filtered by given `$select`
* `$data->getChildComponent($select)`: convenience method that returns a single child component. 
    If multiple exist any of those is returned.
* `$data->getChildComponent('-foo')`: convenience method that returns a single child component by a given id (+ separator)
* `$data->getChildIds($select)`: convenience method that returns ids of child components. Has better performance as 
    creating unnecessary data objects is avoided.
* `$data->countChildComponents($select)`: convenience method that returns the number of child components. Has better 
    performance as creating unnecessary data objects is avoided.
* `$data->getRecursiveChildComponents($select, $childSelect = array('page'=>false))`: Returns child components filtered
    by `$select` any level in the tree below `$data`, stopping at `$childSelect`. With the default value of `$childSelect` 
    children on the same page are returned. `$childSelect` can be array() which then results in all child components.
* `$data->getChildPages($select, $childSelect = array('page'=>false))`: convenience method that returns all child pages
* `$data->getChildPage($select, $childSelect = array('page'=>false))`: convenience method that returns one child page
* `$data->getChildPseudoPages($select, $childSelect = array('page'=>false))`: convenience method that returns all child 
    pseudo pages
* `$data->getChildPseudoPage($select, $childSelect = array('page'=>false))`: convenience method that returns one child 
    pseudo page
* `$data->getChildBoxes($select)`: convenience method that returns all child boxes


##Other Methods

* `$data->getLanguage()`: Returns the language code used by this data as string ('en' or 'de')
* `$data->getDomain()`: Returns the Domain name ('www.example.com') this data is in. Useful if multiple domains are used.
* `$data->getSubroot()`: Returns the [subroot](../subroot.md) this data is in, if none is found root is returned
* `$data->getBaseProperty($propertyName)`: Get [base property](../subroot/base-properties.md) for data
* `$data->isShownInMenu()`: returns if this data should be shown in menus
* `$data->isVisible()`: returns if this data is currently visible, also checks parents
* `$data->getTitle()`: returns title of this page, eg. "Pagename - Parent Page Name"
* `$data->getExpandedComponentId()`: returns the [expanded component id](../component-tree/component-ids.md)
* `$data->getAbsoluteUrl($useHttps = false)`: Returns the absolute url (including protocol and domain, eg. http://www.example.com/page/name)
* `$data->getPreviewUrl()`: Returns the preview url for this data
* `$data->trl`, `trlc`, `trlp`, `trlcp`, trlKwf,` trlcKwf`, trlpKwf, `trlcpKwf`, trlStaticExecute: translate wich data language as target language

##Root Component

The root component is the starting point of the component tree. There exists exactly one object per web and 
it can be accessed using:
`$root = Kwf_Component_Data_Root::getInstance(); `

* `$root->getComponentById($id, $select=array())`: Returns component by it's unique componentId. 
    To include invisible components use ignoreVisible in $select.
* `$root->getComponentsByDbId($dbId, $select=array())`: Returns component by it's dbId. As the dbId is not unique, 
    this method returns an array of found components. See [Component Ids](../component-tree/component-ids.md) for details.
* `$root->getComponentByDbId($dbId, $select=array())`: Convenience method that returns only a single component by id's 
    dbId. Use that if you expect only a single one. If multiple exist an exception is thrown in development mode.
* `$root->getComponentsByClass($class, $select = array())`: Returns all components in this web by their class. 
    Classes inheriting $class are also included.
* `$root->getComponentByClass($class, $select = array())`: Convenience method that reutrns only a single component. 
    Use that if you expect only a single one. If multiple exist an exception is thrown in development mode.
* `$root->getComponentsBySameClass($class, $select = array())`: Similar to getComponentsByClass but doesn't include 
    classes inheriting $class.
* `$root->getComponentBySameClass($class, $select = array())`: Convenience method like getcomponentsByClass.
* `$root->getPageByUrl($url, $acceptLanguage, &$exactMatch = true)`: Returns page by an url plus accapt language 
    (from http header, can be null). This method is used ro resolve urls.
    
####Other helper methods

* `$root->getPageGenerators()`: Returns all page generators (from kwf_pages)
* `$root->freeMemory()`: Tried to free as much memory as possible by clearing all cached data instances.