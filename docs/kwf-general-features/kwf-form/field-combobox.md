#KWF_FORM_FIELD_COMBOBOX & KWF_FORM_FIELD_SELECT

Select is like a standard HTML select where the user can select a value but not type text. Can be used in frontend forms.

ComboBox is a `Ext.formComboBox` based field where the user can also type in to do eg. filtering. Can not be used in frontend forms.

##Example 1:

load data from array

    $this->fields->add(new Kwf_Form_Field_Select('example', trl('Example')))
                ->setValues(array(
                     'foo' => trl('Foo'),
                     'bar' => trl('Bar'),
                 ))
                ->setListWidth(150)
                ->setWidth(100)
                ->setShowNoSelection(true)
                ->setAllowBlank(true);
                
##Example 2:
               
loads data from model.
             
Convenience method, saves the primary key and displays [row __toString](../models/row-tostring.md).
             
    $model = Kwf_Model_Abstract::getInstance('Example');
    $select = $model->select()->whereEquals('foo', 123)
    $this->fields->add(new Kwf_Form_Field_Select('example_id', trl('Example')))
                ->setValues($model)
                ->setSelect($select);
                
                
##Example 3:
               
Loads data from remote auto grid. This does not work in frontend forms.

Useful when selecting from many entries as it loads the data lazily using ajax. 
The AutoGrid needs to have a column id and name and has to be in the Acl as usual.               

    $this->fields->add(new Kwf_Form_Field_Select('example', trl('Example')))
                ->setValues('/url/to/auto-grid/json-data')
                ->setPageSize(25);
                

There are also a few Field_Select based classes:

* `Kwf_Form_Field_SelectCountry`
* `Kwf_Form_Field_PoolSelect`                