#KWF_MODEL

Kwf_Model is an ORM (Object-relational mapping) implementation used in Koala Framework.

It's unique feature is that it can be used to access various data sources using the same API.

##Inspiration

The API is inspired by Zend_Db_Table - and Zend_Db_Table is actually used behind the scenes by Kwf_Model_Db.

##Model Types

###Data access

These Models provide access underlaying data using various techniques.

* Kwf_Model_Db (SQL Database)
* Kwf_Model_Xml (XML File)
*  Kwf_Model_Service (Webservice)
* Kwf_Model_CSV (read CSV files)
* Kwf_Model_Mongo (MongoDb (WIP))
*  Kwf_Model_FnF (Fire and Forget, in memory data)
*  Kwf_Model_Session (Data stored in Session)

###Proxies

These models add additional features to other models by using the proxy pattern.

* Kwf_Model_Proxy (abstract base class for all proxies)
* Kwf_Model_MirrorCache (Cache; fast (eg. Model_Db) model caches slow (eg. Model_Service) model)
* Kwf_Model_RowCache (Cache; specified columns are cached per row in memory)

Another common use case is to implement some logic in a Model_Proxy inherited Model and be able to use `Model_Db` or alternatively - for unit tests - `Model_FnF`.