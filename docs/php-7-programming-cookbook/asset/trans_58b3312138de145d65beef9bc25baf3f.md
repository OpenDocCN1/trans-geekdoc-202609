

6. 我们现在可以重构 `fetchPurchasesForCustomer()` 方法，使其嵌入一个匿名函数，该函数同时调用 `fetchPurchaseById()` 和 `fetchProductById()`，然后将生成的产品实体赋值给新找到的购买实体。在此示例中，我们执行初始查找，仅返回该客户所有购买的 ID。然后，我们在 Customer::$purchases 属性中嵌入一系列匿名函数，将购买 ID 存储为数组键，将匿名函数作为其值：

```php
public function fetchPurchasesForCustomer(Customer $cust)
{
    $sql = 'SELECT id '
          . 'FROM purchases AS u '
          . 'WHERE u.customer_id = :id '
          . 'ORDER BY u.date';
    $stmt = $this->connection->pdo->prepare($sql);
    $stmt->execute(['id' => $cust->getId()]);
    while ($result = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $cust->addPurchaseLookup(
            $result['id'],
            function ($purchId, $service) {
                $purchase = $service->fetchPurchaseById($purchId);
                $product = $service->fetchProductById(
                    $purchase->getProductId());
                $purchase->setProduct($product);
                return $purchase; }
        );
    }
    return $cust;
}
```

### 工作原理…

根据本食谱的步骤，定义以下类如下：

| 类 | 技术 #1 步骤 |
| --- | --- |
| Application\Entity\Purchase | 1 - 2, 7 |
| Application\Entity\Product | 3 - 4 |
| Application\Entity\Customer | 6, 16, + 在第 5 章 *与数据库交互* 中描述的内容。 |
| Application\Database\CustomerOrmService_1 | 8 - 10 |

# 实现软件设计模式

这种方法的第二种实现方式如下：

| **类** | **技术 #2 步骤** |
|---|---|
| `Application\Entity\Customer` | **2** |
| `Application\Database\CustomerOrmService_2` | **3 – 6** |

为了实现方法 **#1**（其中嵌入了实体），定义一个名为 **chap_11_orm_embedded.php** 的调用程序，该程序设置自动加载并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Database\Connection;
use Application\Database\CustomerOrmService_1;
```

接下来，创建一个服务实例，并使用随机 ID 查找客户：

```php
$service = new CustomerOrmService_1(
    new Connection(include __DIR__ . DB_CONFIG_FILE));
$id = rand(1,79);
$cust = $service->fetchByIdAndEmbedPurchases($id);
```

在视图逻辑中，你将通过 `fetchByIdAndEmbedPurchases()` 方法获取一个完全填充的 `Customer` 实体。现在你只需要调用正确的 getter 方法来显示信息：

```html
<!-- Customer Info -->
<h1><?php echo $cust->getName() ?></h1>
<div class="row">
    <div class="left">余额：</div><div class="right">
        <?php echo $cust->getBalance() ?></div>
</div>
<!-- 等等 -->
```

显示购买信息所需的逻辑看起来像以下 HTML 代码。请注意，`Customer::getPurchases()` 返回一个 `Purchase` 实体数组。要从 `Purchase` 实体获取产品信息，在循环内部调用 `Purchase::getProduct()`，这将产生一个 `Product` 实体。然后你可以调用 `Product` 的任何 getter，在本例中为 `Product::getTitle()`：

```html
<!-- Purchases Info -->
<table>
    <?php foreach ($cust->getPurchases() as $purchase) : ?>
    <tr>
        <td><?php echo $purchase->getTransaction() ?></td>
        <td><?php echo $purchase->getDate() ?></td>
        <td><?php echo $purchase->getQuantity() ?></td>
        <td><?php echo $purchase->getSalePrice() ?></td>
        <td><?php echo $purchase->getProduct()->getTitle() ?></td>
    </tr>
    <?php endforeach; ?>
</table>
```

将注意力转向第二种方法，该方法使用二级查找，定义一个名为 `chap_11_orm_secondary_lookups.php` 的调用程序，该程序设置自动加载并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', './../config/db_config.php');
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Database\Connection;
use Application\Database\CustomerOrmService_2;
```

接下来，创建一个服务实例，并使用随机 ID 查找客户：

```php
$service = new CustomerOrmService_2(new Connection(include __DIR__ . DB_CONFIG_FILE));
$id = rand(1,79);
```

现在你可以检索 `Application\Entity\Customer` 实例并为此客户调用 `fetchPurchasesForCustomer()`，它会嵌入匿名函数的序列：

```php
$cust = $service->fetchById($id);
$cust = $service->fetchPurchasesForCustomer($cust);
```

显示核心客户信息的视图逻辑与之前描述的一样。显示购买信息所需的逻辑看起来像以下 HTML 代码片段。请注意，`Customer::getPurchases()` 返回一个匿名函数数组。每次函数调用返回一个特定的购买及相关产品：

```html
<table>
<?php foreach($cust->getPurchases() as $purchaseId => $function) : ?>
<tr>
    <?php $purchase = $function($purchaseId, $service); ?>
    <td><?php echo $purchase->getTransaction() ?></td>
    <td><?php echo $purchase->getDate() ?></td>
    <td><?php echo $purchase->getQuantity() ?></td>
    <td><?php echo $purchase->getSalePrice() ?></td>
    <td><?php echo $purchase->getProduct()->getTitle() ?></td>
</tr>
<?php endforeach; ?>
</table>
```

这是一个输出示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_450_0.png)

### 最佳实践

虽然循环的每次迭代代表两个独立的数据库查询（一个用于购买，一个用于产品），但通过使用预处理语句保留了效率。预先准备了两个语句：一个用于查找特定购买，另一个用于查找特定产品。然后多次执行这些预处理语句。此外，每个产品检索都独立存储在数组中，从而实现了更高的效率。

![](img/39390f6d56c5a83b28db083a8bd5185c_450_1.png)

### 另请参见

实现对象关系映射的库的最佳示例可能是 Doctrine。Doctrine 使用一种嵌入方法，其文档称之为代理。有关更多信息，请参见 http://www.doctrine-project.org/projects/orm.html。

你也许还可以考虑复习 *学习 Doctrine* 的培训视频，该视频可从 O'Reilly Media 获取，网址为 http://shop.oreilly.com/product/0636920041382.do。（免责声明：这是本书和该视频作者的无节制推销！）

# 实现发布/订阅设计模式

**发布/订阅（Pub/Sub）** 设计模式通常构成软件事件驱动编程的基础。这种方法允许不同的软件应用程序之间，或单个应用程序内的不同软件模块之间进行**异步**通信。该模式的目的允许方法或函数在发生重要操作时发布信号。然后一个或多个类会订阅，并在特定信号发布时采取相应行动。

此类操作的示例包括数据库被修改时，或用户登录时。这种设计模式的另一个常见用途是当应用程序发布新闻源时。如果紧急新闻项目已发布，应用程序会发布这一事实，允许客户端订阅者刷新他们的新闻列表。

## 实现方法...

- 1. 首先，我们定义我们的发布者类，`Application\PubSub\Publisher`。您会注意到我们正在使用两个有用的 **标准 PHP 库 (SPL)** 接口，`SplSubject` 和 `SplObserver`：

```php
namespace Application\PubSub;
use SplSubject;
use SplObserver;
class Publisher implements SplSubject
{
// 代码
}
```

- 2. 接下来，我们添加属性来表示发布者名称、传递给订阅者的数据以及订阅者数组（也称为监听器）。您还会注意到我们将使用链表（在*第 10 章，查看高级算法*中描述）来允许优先级：

```php
protected $name;
protected $data;
protected $linked;
protected $subscribers;
```

