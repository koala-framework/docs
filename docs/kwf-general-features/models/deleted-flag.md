#DELETED FLAG

The Deleted Flag can be used to mark Rows as deleted, without removing them from the Model (e.g. mysql table).

This form of deleting can be used for any cases, where data should be able to be recovered.

##Usage

To use the deleted flag you have to

1. create a column named "deleted" in the model
2. set the hasDeletedFlag variable in the model:



       `protected $_hasDeletedFlag = true;`


##Behavior

Rows which are marked as deleted are excluded at the following methods:

    $model->getIds();
    $model->countRows();
    $model->getRow();
    $model->getRows();
    $model->updateRows();
    $model->export();
    
##Ignore Deleted

To get also the deleted marked rows you can simply use a ignoreDeleted within the select:

    $select = new Kwf_Model_Select();
    $select->ignoreDeleted();
    $model->getRows($select);