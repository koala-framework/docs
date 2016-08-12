#MAPPINGS

It is possible to create something like "interfaces" for models, that contain the information which column defined in the interface maps to a concrete column in a model.


    class Model extends Kwf_Model_Db {
        protected $_columnMappings = array(
            'Kwc_Mail_Recipient_Mapping' => array(
                'firstname' => 'customer_firstname',
                'lastname' => 'customer_lastname',
                'email' => 'customer_email',
                'format' => null,
            )
        );
    }
    

###Usage Example:

    $model->getColumnMapping('Kwc_Mail_Recipient_ColumnMapping', 'firstname');
    $model->getColumnMappings('Kwc_Mail_Recipient_ColumnMapping');
    $row->getByColumnMapping('Kwc_Mail_Recipient_ColumnMapping', 'firstname');
