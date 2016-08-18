#EXAMPLE

##Here is a simple example how to use directories in Kwf

###The example will build a simple ToDo list with detail view:

for this example we use a mysql table named todos with the following columns:

* id (int)
* component_id (int)
* todo (varchar)
* visible (tinyint)

###The Directory:

**create the `Component.php` for ToDos**


    class ToDos_Directory_Component extends Kwc_Directories_ItemPage_Directory_Component
       {
           public static function getSettings()
           {
               $ret = parent::getSettings();
               $ret['componentName'] = 'ToDos';
               $ret['generators']['detail']['component'] = 'ToDos_Detail_Component';
               $ret['childModel'] = 'ToDos_Directory_Model';
               $ret['extConfigControllerIndex'] = 'Kwc_Directories_Item_Directory_ExtConfigTabs';
               return $ret;
           }
       }
        
   
   
    
**create the ToDos model:**


    <?php
       class ToDos_Directory_Model extends Kwf_Model_Db_Proxy
       {
           protected $_table = 'todos';
           protected $_toStringField = 'text';
       }
        
   
     
###Now we have to override the Controller and Form

**Controller.php**


    <?php
            class ToDos_Directory_Controller extends Kwc_Directories_Item_Directory_Controller
            {
                protected function _initColumns()
                {
                    $this->_columns->add(new Kwf_Grid_Column('id'));
                    $this->_columns->add(new Kwf_Grid_Column('todo', 'tToDo'));
                    $this->_columns->add(new Kwf_Grid_Column_Visible('visible'));
                    parent::_initColumns();
                }
            }
  
    
**create a FormController.php**


    <?php
        class ToDos_Directory_FormController extends Kwc_Directories_Item_Directory_FormController
        {
            protected function _initFields()
            {
                parent::_initFields();
                $this->_form->add(new Kwf_Form_Field_TextField('todo', 'ToDo'));
            }
        }
    
     
     
###next we add the child component for the single ToDos created by the ToDos generator

**create the ToDos/Detail Component.php**


    <?php
        class ToDos_Detail_Component extends Kwc_Directories_Item_Detail_Component
        {
            public static function getSettings()
            {
                $ret = parent::getSettings();
                $ret['componentName'] = 'ToDo';
                return $ret;
            }
        }
        

    
###we finally create the ToDos / Deatil Component.tpl where we print out our ToDos text

    <div class="<?=$this->cssClass?>">
        <?=$this->row->todo?>
    </div>
