#FULLTEXT SEARCH

Koala Framework allows you to create a fulltext index of the whole component tree. Each component can have content that will be indexed. 
The indexer doesn't fetch the contents through http, it walks through the component tree as asks the components for their content.

####Multiple Backends are supported:

* Zend_Search_Lucene based (default, easy to setup, slow)
* [Solr based](fulltext-search/solr-backend.md) (needs solr server, fast)

##Indexed Contents

The standard components containing text have already return already their fulltext content. So usually no configuration is required.