#RELATIONS

You can specify relations between models and navigate using that between models.

    class ProductCategories extends Kwf_Model_Db
    {
        protected $_table = 'product_categories';
        protected $_dependentModels = array(
            'Products' => 'Products' //The second value is the modelname
        );
    }
    class Products extends Kwf_Model_Db
    {
        protected $_table = 'products';
        protected $_referenceMap = array(
            'Category' => array(
                'refModelClass' => 'ProductCategories',
                'column' => 'category_id',
            ),
            //alternative syntax: 'Category' => 'category_id->ProductCategories'
        );
    }
     
     
    //get category
    $m = Kwf_Model_Abstract::getInstance('Products');
    $row = $m->getRow(1);
    $category = $row->getParentRow('Category');
     
    //get products in category
    $m = Kwf_Model_Abstract::getInstance('ProductCategories');
    $category = $m->getRow(1);
    $products = $category->getChildRows('Products');
    foreach ($products as $product) {
        var_dump($product->name);
    }
     
    //create product in category
    $m = Kwf_Model_Abstract::getInstance('ProductCategories');
    $category = $m->getRow(1);
    $product = $category->createChildRow('Products');
    $product->name = 'bar';
    $product->save();