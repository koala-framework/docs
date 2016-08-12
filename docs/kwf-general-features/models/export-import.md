#EXPORT / IMPORT

While rows are convenient to work with they are not optimized for best possible performance.

##Export

    <?php
    $select = new Kwf_Model_Select();
    $select->whereEquals('foo', 1);
    $options = array(
        'columns' => array('id', 'bar')
    );
    $model->export(Kwf_Model_Abstract::FORMAT_ARRAY, $select, $options);
    
##Import

    <?php
    $data = array(
        array('id'=>100, 'foo'=>1, 'bar'=>'xyz'),
        array('id'=>101, 'foo'=>1, 'bar'=>'xyz'),
    );
    $options = array(
        'columns' => array('id', 'bar')
    );
    $model->import(Kwf_Model_Abstract::FORMAT_ARRAY, $data, $options);
    
##Supported Formats

* FORMAT_ARRAY: import options: replace, ignore, buffer
* FORMAT_CSV
* FORMAT_SQL

##Import Buffer

Importing many rows is most efficient if multiple are inserted with a single sql statement. To use that models can buffer inserted rows:

    <?php
    $options = array(
        'buffer' => 1000 //write after 1000 rows
    );
    for($i=0; $i<10050; $i++) {
        $array = array(
            array('bar'=>'aaa'.$i),
        );
        $model->import(Kwf_Model_Abstract::FORMAT_ARRAY, $array, $options);
    }
    $model->writeBuffer();