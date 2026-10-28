# The admin/product/index.php file

```
```php
<?php
require_once('../../util/main.php');
require_once('../../util/tags.php');
require_once('../../model/database.php');
require_once('../../model/product_db.php');
require_once('../../model/category_db.php');

$action = filter_input(INPUT_POST, 'action');
if ($action == NULL) {
    $action = filter_input(INPUT_GET, 'action');
    if ($action == NULL) {
        $action = 'list_products';
    }
}

switch ($action) {
    case 'list_products':
        $category_id = filter_input(INPUT_GET, 'category_id',
                FILTER_VALIDATE_INT);
        if ($category_id === FALSE) {
            $category_id = 1;
        }
        $current_category = get_category($category_id);
        $categories = get_categories();
        $products = get_products_by_category($category_id);
        include('product_list.php');
        break;
    case 'view_product':
        $categories = get_categories();
        $product_id = filter_input(INPUT_GET, 'product_id',
                FILTER_VALIDATE_INT);
        $product = get_product($product_id);
        include('product_view.php');
        break;
    case 'delete_product':
        $product_id = filter_input(INPUT_POST, 'product_id',
                FILTER_VALIDATE_INT);
        $category_id = filter_input(INPUT_POST, 'category_id',
                FILTER_VALIDATE_INT);
        delete_product($product_id);

        // display product list for the current category
        header("Location: .?category_id=$category_id");
        break;
    case 'show_add_edit_form':
        $product_id = filter_input(INPUT_GET, 'product_id',
                FILTER_VALIDATE_INT);
        if ($product_id == NULL) {
            $product_id = filter_input(INPUT_POST, 'product_id',
                    FILTER_VALIDATE_INT);
        }
        $product = get_product($product_id);
        $categories = get_categories();
        include('product_add_edit.php');
        break;
}
```
```

Figure 20-5 The Product Manager application (part 2 of 5)