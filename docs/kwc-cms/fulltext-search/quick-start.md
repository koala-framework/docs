#QUICK START

##Create Search Index

For initial indexing run following command in your project folder:

`php bootstrap.php fulltext rebuild --debug`

##Test Search

Run following command in your project folder:

`php bootstrap.php fulltext search --query=QUERY --subroot=root`

##Create a search page
 
To access the search in the frontend you need a search page that using that component:

`Kwc_FulltextSearch_Search_Directory_Component`

##Create a search box

Just add it as a box. It's displayed as a textfield and a button to start the search.

`Kwc_FulltextSearch_Box_Component`

