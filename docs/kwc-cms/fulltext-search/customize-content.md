#CUSTOMIZE FULLTEXT CONTENT

Any component can add content to the fulltext index. To do that enable the `hasFulltext` flag and implement a getFulltextContent method. 
In that method you can return all values that will be stored in the relevant field.

Alternatively a getFulltextComponents method can be implemented that allows indexing other components than on the current page. 
This can be used if a component embeds another one.

###Example:

    public static function getSettings()
    {
        $ret = parent::getSettings();
        $ret['flags']['hasFulltext'] = true;
        return $ret;
    }
     
    public function getFulltextContent()
    {
        $ret = array();
        $ret['type'] = 'example';
        $ret['created'] = new Kwf_DateTime($this->getData()->row->date);
        return $ret;
    }
     
    public function getFulltextComponents()
    {
        $ret = array();
        $ret[] = Kwf_Component_Data_Root::getInstance()->
            getComponentById('root-example-'.$this->getRow()->example_id);
        return $ret;
    }