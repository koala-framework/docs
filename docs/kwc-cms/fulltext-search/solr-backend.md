#CONFIGURE SOLR

Koala Framework supports different backends, one is [Apache Solr](http://lucene.apache.org/solr/).

###Folder-Structure:
Web

=> compontents, controllers, css ...

=> solr => solr.xml

=> solr => solrconfig_master.xml

=> solr => FOLDER => conf => schema.xml

=> solr => FOLDER => conf => solrconfig.xml

=> solr => FOLDER => data (folder has to be created and needs correct rights because solr stores indices)

###Folder-Structure example for multilanguage (de, en)
Web

=> compontents, controllers, css ...

=> solr => solr.xml

=> solr => solrconfig_master.xml

=> solr => master => conf => schema.xml

=> solr => master => conf => solrconfig.xml

=> solr => en => conf => schema.xml

=> solr => en => conf => solrconfig.xml


##Create a solr.xml

It's possible to define different configs in different folders. But they have to be defined in solr.xml

    <?xml version="1.0" encoding="UTF-8" ?>
    <solr persistent="false">
      <cores adminPath="/admin/cores">
          <core name="FOLDER1" instanceDir="FOLDER1" />
          <core name="FOLDER2" instanceDir="FOLDER2" />
      </cores>
    </solr>
    
    
#Create a solrconfig_master.xml

This file is used to define a default config for the different configs.

####This is a sample configuration:

    <?xml version="1.0" encoding="UTF-8" ?>
    <config>
      <abortOnConfigurationError>${solr.abortOnConfigurationError:true}</abortOnConfigurationError>
      <luceneMatchVersion>LUCENE_35</luceneMatchVersion>
      <dataDir>${solr.data.dir:}</dataDir>
      <directoryFactory name="DirectoryFactory" 
                        class="${solr.directoryFactory:solr.StandardDirectoryFactory}"/>
      <indexDefaults>
        <useCompoundFile>false</useCompoundFile>
        <mergeFactor>10</mergeFactor>
        <ramBufferSizeMB>32</ramBufferSizeMB>
        <!-- <maxBufferedDocs>1000</maxBufferedDocs> -->
        <maxFieldLength>10000</maxFieldLength>
        <writeLockTimeout>1000</writeLockTimeout>
        <lockType>native</lockType>
      </indexDefaults>
     
      <mainIndex>
        <useCompoundFile>false</useCompoundFile>
        <ramBufferSizeMB>32</ramBufferSizeMB>
        <mergeFactor>10</mergeFactor>
        <unlockOnStartup>false</unlockOnStartup>
        <reopenReaders>true</reopenReaders>
        <deletionPolicy class="solr.SolrDeletionPolicy">
          <!-- The number of commit points to be kept -->
          <str name="maxCommitsToKeep">1</str>
          <!-- The number of optimized commit points to be kept -->
          <str name="maxOptimizedCommitsToKeep">0</str>
          <!--
              Delete all commit points once they have reached the given age.
              Supports DateMathParser syntax e.g.
            -->
          <!--
             <str name="maxCommitAge">30MINUTES</str>
             <str name="maxCommitAge">1DAY</str>
          -->
        </deletionPolicy>
         <infoStream file="INFOSTREAM.txt">false</infoStream> 
      </mainIndex>
     
      <!-- The default high-performance update handler -->
      <updateHandler class="solr.DirectUpdateHandler2">
      </updateHandler>
     
      <query>
        <maxBooleanClauses>1024</maxBooleanClauses>
        <filterCache class="solr.FastLRUCache"
                     size="512"
                     initialSize="512"
                     autowarmCount="0"/>
        <queryResultCache class="solr.LRUCache"
                         size="512"
                         initialSize="512"
                         autowarmCount="0"/>
        <documentCache class="solr.LRUCache"
                       size="512"
                       initialSize="512"
                       autowarmCount="0"/>
        <enableLazyFieldLoading>true</enableLazyFieldLoading>
        <queryResultWindowSize>20</queryResultWindowSize>
        <queryResultMaxDocsCached>200</queryResultMaxDocsCached>
        <useColdSearcher>false</useColdSearcher>
        <maxWarmingSearchers>2</maxWarmingSearchers>
      </query>
     
      <requestDispatcher handleSelect="true" >
        <requestParsers enableRemoteStreaming="true" 
                        multipartUploadLimitInKB="2048000" />
        <httpCaching never304="true" />
      </requestDispatcher>
     
        <requestHandler name="/search" class="solr.SearchHandler" default="true">
            <lst name="defaults">
                <str name="defType">edismax</str>
                <str name="echoParams">explicit</str>
     
                <!-- query fields -->
                <str name="qf">title^10 normalContent^1 contentstrong^2 contenth1^5 contenth2^3 contenth3^2 contenth4^1.5 contenth5^1.3 contenth6^1.2 keywords^12</str>
     
                <str name="fl">componentId score</str>
            </lst>
        </requestHandler>
     
        <requestHandler name="/update"
                        class="solr.XmlUpdateRequestHandler" />
     
        <requestHandler name="/update/json"
                        class="solr.JsonUpdateRequestHandler"
                        startup="lazy" />
     
        <requestHandler name="/admin/"
                        class="solr.admin.AdminHandlers" />
     
        <queryResponseWriter name="json" class="solr.JSONResponseWriter" />
    </config>
    
    
##Create schema.xml

This configuration should be adjusted for your special language needs. The different filters can be found on the solr [documentation](http://wiki.apache.org/solr/AnalyzersTokenizersTokenFilters).

It's also possible to define fields where data should be stored or just referenced. This can be used to add special filters to the search-query.

    <?xml version="1.0" encoding="UTF-8" ?>
    <schema version="1.2">
     
        <types>
            <fieldType name="string" class="solr.StrField" sortMissingLast="true" omitNorms="true"/>
            <fieldType name="date" class="solr.TrieDateField" sortMissingLast="true" omitNorms="true"/>
            <fieldType name="bool" class="solr.BoolField" sortMissingLast="true" omitNorms="true"/>
        </types>
     
        <fields>
            <field name="componentId" type="string" indexed="true" stored="true" required="true" />
            <field name="created" type="date" indexed="true" stored="true" /> <!-- todo change stored to false -->
            <field name="lastModified" type="date" indexed="true" stored="false" />
            <field name="content" type="text" indexed="false" stored="true" required="true" />
            <field name="title" type="text" indexed="true" stored="true" required="true" />
            <field name="normalContent" type="text" indexed="true" stored="false" />
            <field name="contentstrong" type="text" indexed="true" stored="false" />
            <field name="contenth1" type="text" indexed="true" stored="false" />
            <field name="contenth2" type="text" indexed="true" stored="false" />
            <field name="contenth3" type="text" indexed="true" stored="false" />
            <field name="contenth4" type="text" indexed="true" stored="false" />
            <field name="contenth5" type="text" indexed="true" stored="false" />
            <field name="contenth6" type="text" indexed="true" stored="false" />
            <field name="keywords" type="text" indexed="true" stored="false" />
            <field name="type" type="string" indexed="true" stored="false" /> <!-- eg. news -->
        </fields>
     
        <types>
            <fieldType name="text" class="solr.TextField" positionIncrementGap="3">
                <analyzer>
                    <tokenizer class="solr.WhitespaceTokenizerFactory"/>
                    <filter class="solr.WordDelimiterFilterFactory" splitOnNumerics="0" generateWordParts="1"
                            generateNumberParts="1" catenateWords="1" catenateNumbers="1" catenateAll="0"
                            splitOnCaseChange="1"/>
                    <filter class="solr.LowerCaseFilterFactory"/>
                    <filter class="solr.GermanStemFilterFactory" />
                    <filter class="solr.SnowballPorterFilterFactory" language="German2" />
                    <filter class="solr.EdgeNGramFilterFactory" minGramSize="3" maxGramSize="25"/>
                </analyzer>
            </fieldType>
        </types>
     
        <uniqueKey>componentId</uniqueKey>
    </schema>
     
     
##Create solrconfig.xml

Change or adjust the master config for special needs in this file.
    
    <?xml version="1.0" encoding="UTF-8" ?>
    <xi:include href="../../solrconfig_master.xml" xmlns:xi="http://www.w3.org/2001/XInclude" />
    
##Start Solr

####For local development you can start solr manually:

`php bootstrap.php fulltext start-solr`

####After solr starts, run initial indexing:

`php bootstrap.php fulltext rebuild --debug`

On production server a tomcat running solr is recommended.

####Restart Solr/Tomcat on the vpn-server
`/www/bin/rc_tomcat restart solr`

##Access Solr

###You can open the solr web interface for debugging purposes:

`http://DOMAIN:8983/solr/FOLDER/admin/`

##Configure backend

To use solr backend add those lines to `config.ini`:

`fulltext.backend = Kwf_Util_Fulltext_Backend_Solr`

`;optional
fulltext.solr.port = 8983
fulltext.solr.path = /solr/example`


##Index refreshing controller

There should also be a controller/cronjob refreshing the index regularly to keep the search-results up-to-date.

To keep the index up-to-date use `php bootstrap.php fulltext update-changed`

And every day `php bootstrap.php fulltext check-contents` should be called.
