
### Based on the customer entity class, here is how `Application\Entity\Purchase` might look. Note that not all getters and setters are shown:

```php
namespace Application\Entity;

class Purchase extends Base
{
    const TABLE_NAME = 'purchases';

    protected $transaction = '';
    protected $date = NULL;
    protected $quantity = 0;
    protected $salePrice = 0.0;
    protected $customerId = 0;
    protected $productId = 0;

    protected $mapping = [
        'id'            => 'id',
        'transaction'   => 'transaction',
        'date'          => 'date',
        'quantity'      => 'quantity',
        'sale_price'    => 'salePrice',
        'customer_id'   => 'customerId',
        'product_id'    => 'productId',
    ];

    public function getTransaction() : string
    {
        return $this->transaction;
    }

    public function setTransaction($transaction)
    {
        $this->transaction = $transaction;
    }

    // NOTE: other getters / setters are not shown here
}
```

### We are now ready to define `Application\Entity\Product`. Here is the database definition for the `products` table:

```sql
CREATE TABLE `products` (
`id` int(11) NOT NULL AUTO_INCREMENT,
`sku` varchar(16) DEFAULT NULL,
`title` varchar(255) NOT NULL,
`description` varchar(4096) DEFAULT NULL,
`price` decimal(10,2) NOT NULL,
`special` int(11) NOT NULL,
`link` varchar(128) NOT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `UNIQ_38C4` (`sku`)
);
```

### Based on the customer entity class, here is how `Application\Entity\Product` might look:

```php
namespace Application\Entity;

class Product extends Base
{
    const TABLE_NAME = 'products';
    protected $sku = '';
    protected $title = '';
    protected $description = '';
    protected $price = 0.0;
    protected $special = 0;
    protected $link = '';

    protected $mapping = [
        'id'          => 'id',
        'sku'         => 'sku',
        'title'       => 'title',
        'description' => 'description',
        'price'       => 'price',
        'special'     => 'special',
        'link'        => 'link',
    ];

    public function getSku() : string
    {
        return $this->sku;
    }
    
    public function setSku($sku)
    {
        $this->sku = $sku;
    }

    // NOTE: other getters / setters are not shown here
}
```

### Next, we need to implement a way to embed related objects. We will start with the `Application\Entity\Customer` parent class. For this section, we will assume the following relationships, illustrated in the following diagram:

- One customer, many purchases
- One purchase, one product

![](img/39390f6d56c5a83b28db083a8bd5185c_443_0.png)

### Accordingly, we define a getter and setter that process purchases in the form of an array of objects:

```php
protected $purchases = array();

public function addPurchase($purchase)
{
    $this->purchases[] = $purchase;
}

public function getPurchases()
{
    return $this->purchases;
}
```

### Now we turn our attention to `Application\Entity\Purchase`. In this case, there is a 1:1 relationship between a purchase and a product, so there’s no need to process an array.

```php
protected $product = NULL;

public function getProduct()
{
    return $this->product;
}

public function setProduct(Product $product)
{
    $this->product = $product;
}
```

Notice that in both entity classes, we do not alter the $mapping array. This is because implementing object relational mapping has no bearing on the mapping between entity property names and database column names.

### Since the core functionality of obtaining basic customer information is still needed, all we need to do is to extend the `Application\Database\CustomerService` class described in Chapter 5, "Interacting with a Database," in the "Tying entity classes to RDBMS queries" recipe. We can create a new `Application\Database\CustomerOrmService_1` class, which extends `Application\Database\CustomerService`:

```php
namespace Application\Database;
use PDO;
use PDOException;
use Application\Entity\Customer;
use Application\Entity\Product;
use Application\Entity\Purchase;

class CustomerOrmService_1 extends CustomerService
{
    // add methods here
}
```

### We then add a method to the new service class that performs a lookup and embeds the results, in the form of `Product` and `Purchase` entities, into the core customer entity. This method performs a lookup in the form of a JOIN. This is possible because there is a 1:1 relationship between purchase and product. Because the `id` column has the same name in both tables, we need to add the purchase ID column as an alias. We then loop through the results, creating `Product` and `Purchase` entities. After overriding the ID, we can then embed the `Product` entity into the `Purchase` entity, and then add the `Purchase` entity to the array in the `Customer` entity:

```php
protected function fetchPurchasesForCustomer(Customer $cust)
{
    $sql = 'SELECT u.*, r.*, u.id AS purch_id '
         . 'FROM purchases AS u '
         . 'JOIN products AS r '
         . 'ON r.id = u.product_id '
         . 'WHERE u.customer_id = :id '
         . 'ORDER BY u.date';
    
    $stmt = $this->connection->pdo->prepare($sql);
    $stmt->execute(['id' => $cust->getId()]);
    
    while ($result = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $product = Product::arrayToEntity($result, new Product());
        $product->setId($result['product_id']);
        
        $purch = Purchase::arrayToEntity($result, new Purchase());
        $purch->setId($result['purch_id']);
        $purch->setProduct($product);
        $cust->addPurchase($purch);
    }
    
    return $cust;
}
```

### Next, we provide a wrapper for the original `fetchById()` method. This block of code needs to not only get the original `Customer` entity, but needs to look up and embed `Product` and `Purchase` entities. We can call the new `fetchByIdAndEmbedPurchases()` method and accept a customer ID as an argument:

```php
public function fetchByIdAndEmbedPurchases($id)
{
    return $this->fetchPurchasesForCustomer(
        $this->fetchById($id)
    );
}
```

## Technique #2 – embedding secondary lookups

Now we will cover embedding secondary lookups into the related entity classes. We will continue to use the same illustration as above, using the entity classes defined that correspond to three related database tables: `customer`, `purchases`, and `products`:

### The mechanics of this approach are quite similar to those described in the preceding section. The main difference is that instead of doing the database lookup, and producing entity classes right away, we will embed a series of anonymous functions that will do the same thing, but called from the view logic.

### We need to add a new method to the `Application\Entity\Customer` class that adds a single entry to the purchases property. Instead of an array of `Purchase` entities, we will be supplying an anonymous function:

```php
public function setPurchases(Closure $purchaseLookup)
{
    $this->purchases = $purchaseLookup;
}
```

### Next, we will make a copy of the `Application\Database\CustomerOrmService_1` class, and call it `Application\Database\CustomerOrmService_2`:

```php
namespace Application\Database;
use PDO;
use PDOException;
use Application\Entity\Customer;
use Application\Entity\Product;
use Application\Entity\Purchase;

class CustomerOrmService_2 extends CustomerService
{
    // code
}
```

### We then define a `fetchPurchaseById()` method, which looks up a single purchase based on its ID and produces a `Purchase` entity. Because we will ultimately be making a series of repetitive requests for single purchases in this approach, we can regain database efficiency by working off the same prepared statement, in this case, a properly called `$purchPreparedStmt`:

```php
public function fetchPurchaseById($purchId)
{
    if (!$this->purchPreparedStmt) {
        $sql = 'SELECT * FROM purchases WHERE id = :id';
        $this->purchPreparedStmt = 
            $this->connection->pdo->prepare($sql);
    }
    $this->purchPreparedStmt->execute(['id' => $purchId]);
    $result = $this->purchPreparedStmt->fetch(PDO::FETCH_ASSOC);
    return Purchase::arrayToEntity($result, new Purchase());
}
```

### After that, we need a `fetchProductById()` method that looks up a single product based on its ID and produces a `Product` entity. Given that a customer may have purchased the same product several times, we can introduce an additional level of efficiency by storing acquired product entities in a `$products` array. In addition, as with purchases, we can perform lookups on the same prepared statement:

```php
public function fetchProductById($prodId)
{
    if (!isset($this->products[$prodId])) {
        if (!$this->prodPreparedStmt) {
            $sql = 'SELECT * FROM products WHERE id = :id';
            $this->prodPreparedStmt = 
                $this->connection->pdo->prepare($sql);
        }
        $this->prodPreparedStmt->execute(['id' => $prodId]);
        $result = $this->prodPreparedStmt
            ->fetch(PDO::FETCH_ASSOC);
        $this->products[$prodId] = 
            Product::arrayToEntity($result, new Product());
    }
    return $this->products[$prodId];
}
```
