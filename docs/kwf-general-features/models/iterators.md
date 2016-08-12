#ITERTORS

####When working with a lot of rows there are a few iterators that help avoiding memory usage issues.

* Kwf_Model_Iterator_Rows: iterate over rows, basically the same as getRows()
*  Kwf_Model_Iterator_ExportArray: iterate over export data, basically the same as export()
*  Kwf_Model_Iterator_Packages: Iterate in packages to avoid high memory usage

##Example iterate Rows

    $select = new Kwf_Model_Select();
    $select->whereEquals('foo', '1');
    $it = new Kwf_Model_Iterator_Packages(
        new Kwf_Model_Iterator_Rows($model, $select)
    );
    foreach ($it as $row) {
        echo $row->bar."\n";
    }
    
##Example iterate exported Array

    $select = new Kwf_Model_Select();
    $select->whereEquals('foo', '1');
    $options = array(
        'columns' => array('id', 'bar'),
    );
    $it = new Kwf_Model_Iterator_Packages(
        new Kwf_Model_Iterator_ExportArray($model, $select, $options)
    );
    foreach ($it as $row) {
        echo $row['bar']."\n";
    }
    
    
####When executing this code on the command line you can also add a progress bar:

    $it = new Kwf_Iterator_ConsoleProgressBar($it);