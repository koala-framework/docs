#MULTIPLE COLUMNS IN A FORM

    $awesomeColumns = $this->_form->add(new Kwf_Form_Container_Columns('topColumns'));
    $leftColumn = $awesomeColumns->add(new Kwf_Form_Container_Column('leftColumn'));
    $leftColumn->add(new Kwf_Form_Field_TextField('foo', trl('Foo')));
    $rightColumn = $awesomeColumns->add(new Kwf_Form_Container_Column('rightColumn'));
    $rightColumn->add(new Kwf_Form_Field_TextField('bar', trl('Bar')));