

## 如何创建静态属性和方法

### 带有静态属性和方法的类

```php
class Category {
    private $id, $name;
    private static $objectCount = 0;    // declare a static property

    public function __construct($id, $name) {
        $this->id = $id;
        $this->name = $name;
        self::$objectCount++;            // update the static property
    }

    // A public method that gets the static property
    public static function getObjectCount(){
        return self::$objectCount;
    }

    // The rest of the methods for the Category class
}
```

### 使用静态方法

```php
$brass = new Category(1, 'Guitars');
$brass = new Category(2, 'Bass');
echo '<p>Object count: ' . Category::getObjectCount() . '</p>';    // 2

$brass = new Category(3, 'Drums');
echo '<p>Object count: ' . Category::getObjectCount() . '</p>';    // 3
```

### 使用公共静态属性

```php
echo '<p>Object count: ' . Category::$objectCount . '</p>';
```

### 说明

- *静态属性*或*静态方法*是属于类的属性或方法，而不是属于由该类创建的对象。可以使用 `static` 关键字创建这些类型的属性和方法，它们也称为*类属性*和*类方法*。
- 在类的内部，可以通过编写 `self` 关键字、两个冒号以及属性名或方法名来访问静态属性或方法。
- 在类的外部，可以通过编写类名、两个冒号以及静态属性名或静态方法名来访问公共静态属性或方法。
- 访问静态属性时，必须在属性名称的开头包含美元符号。
- 在 PHP 应用程序中，每个用户都有独立的代码空间。因此，静态属性和方法不会在多个用户之间共享。

## 面向对象的 Product Manager 应用程序

第 5 章介绍了一个 Guitar Shop 网站，其中包含一个使用过程化技术而非面向对象技术的 Product Manager 应用程序。现在，本节将介绍重写后使用面向对象编程技术的 Product Manager 应用程序。为简洁起见，本节不会展示 Product Manager 应用程序的全部代码。不过，本节会展示一些代码片段，用于说明关键的面向对象技术。与往常一样，你可以通过下载本书的源代码来查看此应用程序的完整代码。

### 用户界面

为了帮助你回忆此应用程序，图 14.9 首先展示了用户界面。此管理应用程序允许用户通过 Product List 页面查看每个类别中的产品。它还允许用户通过 Add Product 页面向某个类别添加产品。

`getProduct` 方法接收产品 ID 作为参数。然后，它使用预处理的 SELECT 语句返回一个结果集，其中包含指定 ID 对应的行。接下来，它使用 `fetch` 方法将结果集转换为数组，并使用 CategoryDB 类的 `getCategory` 方法，根据类别 ID 获取一个 Category 对象。最后，它创建一个 Product 对象，将这些数据存储在该对象中，然后返回该对象。

`deleteProduct` 方法接收产品 ID 作为参数。然后，它使用预处理的 DELETE 语句从数据库中删除指定的产品。

`addProduct` 方法接收一个 Product 对象作为参数。然后，它从 Product 对象中获取 INSERT 语句所需的数据。接下来，它使用预处理的 INSERT 语句，将新产品添加到 products 表中。

请注意，这四个方法都会调用 Database 类的 `getDB` 方法，以获取数据库连接的引用。

### product_db.php 文件（续）

```php
public static function getProduct($product_id) {
    $db = Database::getDB();
    $query = 'SELECT * FROM products
              WHERE productID = :product_id';
    $statement = $db->prepare($query);
    $statement->bindValue(':product_id', $product_id);
    $statement->execute();
    $row = $statement->fetch();
    $statement->closeCursor();

    $category = CategoryDB::getCategory($row['categoryID']);
    $product = new Product($category,
                          $row['productCode'],
                          $row['productName'],
                          $row['listPrice']);
    $product->setID($row['productID']);
    return $product;
}

public static function deleteProduct($product_id) {
    $db = Database::getDB();
    $query = 'DELETE FROM products
              WHERE productID = :product_id';
    $statement = $db->prepare($query);
    $statement->bindValue(':product_id', $product_id);
    $statement->execute();
    $statement->closeCursor();
}

public static function addProduct($product) {
    $db = Database::getDB();

    $category_id = $product->getCategory()->getID();
    $code = $product->getCode();
    $name = $product->getName();
    $price = $product->getPrice();

    $query = 'INSERT INTO products
              (categoryID, productCode, productName, listPrice)
              VALUES
              (:category_id, :code, :name, :price)';
    $statement = $db->prepare($query);
    $statement->bindValue(':category_id', $category_id);
    $statement->bindValue(':code', $code);
    $statement->bindValue(':name', $name);
    $statement->bindValue(':price', $price);
    $statement->execute();
    $statement->closeCursor();
}
}
?>
```

### 控制器

index.php 文件包含 Product Manager 应用程序控制器的代码。此文件中的前五条语句使用 require 语句加载定义模型的所有文件。在这里，必须包含 category.php 和 product.php 文件，因为这两个文件存储了用于定义 Category 和 Product 对象的代码。

其余代码的工作方式与第 5 章中介绍的 Product Manager 应用程序类似。因此，你应该不会难以理解其工作原理。不过，仍有一些差异需要注意。

主要区别在于，此控制器使用面向对象技术处理数据库中的数据。为此，它调用 CategoryDB 类和 ProductDB 类中的静态方法。在这些方法中，用于获取数据的方法会返回一个对象或对象数组。例如，ProductDB 类的 `getProduct` 方法会返回指定类别 ID 对应的 Product 对象。同样，ProductDB 类的 `getProductsByCategory` 方法会返回一个 Product 对象数组。因此，视图中的代码可以调用这些对象的方法。

### index.php 文件

```php
<?php
require('../model/database.php');
require('../model/category.php');
require('../model/category_db.php');
require('../model/product.php');
require('../model/product_db.php');

$action = filter_input(INPUT_POST, 'action');
if ($action == NULL) {
    $action = filter_input(INPUT_GET, 'action');
    if ($action == NULL) {
        $action = 'list_products';
    }
}

if ($action == 'list_products') {
    $category_id = filter_input(INPUT_GET, 'category_id',
        FILTER_VALIDATE_INT);
    if ($category_id == NULL || $category_id == FALSE) {
        $category_id = 1;
    }
    $current_category = CategoryDB::getCategory($category_id);
    $categories = CategoryDB::getCategories();
    $products = ProductDB::getProductsByCategory($category_id);
    include('product_list.php');
} else if ($action == 'delete_product') {
    $product_id = filter_input(INPUT_POST, 'product_id',
        FILTER_VALIDATE_INT);
    $category_id = filter_input(INPUT_POST, 'category_id',
        FILTER_VALIDATE_INT);
    ProductDB::deleteProduct($product_id);
    header("Location: .?category_id=$category_id");
} else if ($action == 'show_add_form') {
    $categories = CategoryDB::getCategories();
    include('product_add.php');
} else if ($action == 'add_product') {
    $category_id = filter_input(INPUT_POST, 'category_id',
        FILTER_VALIDATE_INT);
    $code = filter_input(INPUT_POST, 'code');
    $name = filter_input(INPUT_POST, 'name');
    $price = filter_input(INPUT_POST, 'price');
    if ($category_id == NULL || $category_id == FALSE || $code == NULL ||
        $name == NULL || $price == NULL || $price == FALSE) {
        $error = "Invalid product data. Check all fields and try again.";
        include('../errors/error.php');
    } else {
        $category = CategoryDB::getCategory($category_id);
        $product = new Product($category, $code, $name, $price);
        ProductDB::addProduct($product);
        header("Location: .?category_id=$category_id");
    }
}
?>
```

