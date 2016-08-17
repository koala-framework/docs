#KWF_FORM_CONTAINER_COLUMNS

Using Kwf_Form_Container_Columns you can easily create multiple columns within a form.


    $columns = $this->_fields->add(new Kwf_Form_Container_Columns('Example')); 
    $column1 = $columns->add();
    $column1->add(new Kwf_Form_Field_TextField('foo_value', trl('Foo')));
     
    $column2 = $columns->add();
    $column2->add(new Kwf_Form_Field_TextField('bar_value', trl('Bar')));