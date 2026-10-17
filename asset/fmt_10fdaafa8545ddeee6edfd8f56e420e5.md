
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

## 最佳实践

虽然循环的每次迭代代表两个独立的数据库查询（一个用于购买，一个用于产品），但通过使用预处理语句保留了效率。预先准备了两个语句：一个用于查找特定购买，另一个用于查找特定产品。然后多次执行这些预处理语句。此外，每个产品检索都独立存储在数组中，从而实现了更高的效率。

![](img/39390f6d56c5a83b28db083a8bd5185c_450_1.png)

### 另请参见

实现对象关系映射的库的最佳示例可能是 Doctrine。Doctrine 使用一种嵌入方法，其文档称之为代理。有关更多信息，请参见 http://www.doctrine-project.org/projects/orm.html。

你也许还可以考虑复习 *学习 Doctrine* 的培训视频，该视频可从 O'Reilly Media 获取，网址为 http://shop.oreilly.com/product/0636920041382.do。（免责声明：这是本书和该视频作者的无节制推销！）

## 实现发布/订阅设计模式

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

### 3. 构造函数用于初始化这些属性。我们还会加入 `__toString()`，以便在需要时快速访问该发布者的名称：

```php
public function __construct($name)
{
    $this->name = $name;
    $this->data = array();
    $this->subscribers = array();
    $this->linked = array();
}

public function __toString()
{
    return $this->name;
}
```

### 4. 为了将订阅者与发布者关联起来，我们定义了 `attach()`，该函数在 `SplSubject` 接口中有所规定。我们接受一个 `SplObserver` 实例作为参数。注意，我们需要向 `$subscribers` 和 `$linked` 属性中添加条目。随后，使用 `arsort()` 按值（即优先级）对 `$linked` 进行排序，`arsort()` 会进行降序排序并保留键值：

```php
public function attach(SplObserver $subscriber)
{
    $this->subscribers[$subscriber->getKey()] = $subscriber;
    $this->linked[$subscriber->getKey()] =
        $subscriber->getPriority();
    arsort($this->linked);
}
```

### 5. 接口还要求我们定义 `detach()`，用于从列表中移除订阅者：

```php
public function detach(SplObserver $subscriber)
{
    unset($this->subscribers[$subscriber->getKey()]);
    unset($this->linked[$subscriber->getKey()]);
}
```

### 6. 同样基于接口的要求，我们定义了 `notify()`，它会调用所有订阅者的 `update()`。注意，我们遍历链表以确保订阅者按优先级顺序被调用：

```php
public function notify()
{
    foreach($this->linked as $key => $value)
    {
        $this->subscribers[$key]->update($this);
    }
}
```

### 7. 接下来，我们定义相应的 getter 和 setter。为了节省篇幅，这里没有展示所有代码：

```php
public function getName()
{
    return $this->name;
}

public function setName($name)
{
    $this->name = $name;
}
```

### 8. 最后，我们需要提供一种按键设置数据项的方法，这些数据项将在调用 `notify()` 时供订阅者使用：

```php
public function setDataByKey($key, $value)
{
    $this->data[$key] = $value;
}
```

### 9. 现在我们可以查看 `Application\PubSub\Subscriber`。通常，我们会为每个发布者定义多个订阅者。在这种情况下，我们实现了 `SplObserver` 接口：

```php
namespace Application\PubSub;
use SplSubject;
use SplObserver;
class Subscriber implements SplObserver
{
    // code
}
```

### 10. 每个订阅者都需要一个唯一的标识符。在这里，我们使用 `md5()` 结合日期/时间信息以及一个随机数来创建键。构造函数按如下方式初始化属性。订阅者执行的实际逻辑功能形式为回调：

```php
protected $key;
protected $name;
protected $priority;
protected $callback;
public function __construct(
    string $name, callable $callback, $priority = 0)
{
    $this->key = md5(date('YmdHis') . rand(0,9999));
    $this->name = $name;
    $this->callback = $callback;
    $this->priority = $priority;
}
```

### 11. 当发布者的 `notify()` 被调用时，`update()` 函数会被触发。

我们传入一个发布者实例作为参数，并调用为该订阅者定义的回调：

```php
public function update(SplSubject $publisher)
{
    call_user_func($this->callback, $publisher);
}
```

### 12. 我们还需要定义 getter 和 setter 以方便使用。并非所有都展示于此：

```php
public function getKey()
{
    return $this->key;
}

public function setKey($key)
{
    $this->key = $key;
}

// other getters and setters not shown
```

## 工作原理...

为了说明目的，定义一个名为 `chap_11_pub_sub_simple_example.php` 的调用程序，它设置自动加载并使用适当的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\PubSub\{ Publisher, Subscriber };
```

接下来，创建一个发布者实例并分配数据：

```php
$pub = new Publisher('test');
$pub->setDataByKey('1', 'AAA');
$pub->setDataByKey('2', 'BBB');
$pub->setDataByKey('3', 'CCC');
$pub->setDataByKey('4', 'DDD');
```

现在你可以创建测试订阅者，它们从发布者读取数据并回显结果。第一个参数是名称，第二个是回调，最后一个是优先级：

```php
$sub1 = new Subscriber(
    '1',
    function ($pub) {
        echo '1:' . $pub->getData()[1] . PHP_EOL;
    },
    10
);
$sub2 = new Subscriber(
    '2',
    function ($pub) {
        echo '2:' . $pub->getData()[2] . PHP_EOL;
    },
    20
);
$sub3 = new Subscriber(
    '3',
    function ($pub) {
        echo '3:' . $pub->getData()[3] . PHP_EOL;
    },
    99
);
```

为了测试目的，乱序附加订阅者，并调用两次 `notify()`：

```php
$pub->attach($sub2);
$pub->attach($sub1);
$pub->attach($sub3);
$pub->notify();
$pub->notify();
```

接下来，定义并附加另一个订阅者，该订阅者检查订阅者 1 的数据，如果非空则退出：

```php
$sub4 = new Subscriber(
    '4',
    function ($pub) {
        echo '4:' . $pub->getData()[4] . PHP_EOL;
        if (!empty($pub->getData()[1]))
            die('1 is set ... halting execution');
    },
    25
);
$pub->attach($sub4);
$pub->notify();
```

以下是输出结果。注意，输出是按优先级顺序排列的（优先级较高的排在前面），并且第二块输出被中断了：

![](img/39390f6d56c5a83b28db083a8bd5185c_456_0.png)

## 更多内容...

一种密切相关的软件设计模式是**观察者（Observer）**模式。其机制相似，但通常公认的区别在于，观察者模式以同步方式运行，当接收到信号（通常也称为消息或事件）时，所有观察者方法都会被调用。相比之下，发布/订阅（Pub/Sub）模式是异步运行的，通常使用消息队列。另一个区别是，在发布/订阅模式中，发布者不需要知道订阅者的存在。

## 参见

关于观察者模式和发布/订阅模式之间差异的良好讨论，请参阅 [http://stackoverflow.com/questions/15594905/difference-between-observer-pub-sub-and-data-binding](http://stackoverflow.com/questions/15594905/difference-between-observer-pub-sub-and-data-binding) 上的文章。

# 12 提升 Web 安全性

在本章中，我们将涵盖以下主题：

- 过滤 `$_POST` 数据

- 验证 `$_POST` 数据

- 保护 PHP 会话

- 使用令牌保护表单

- 构建安全的密码生成器

- 使用 CAPTCHA 保护表单

- 不使用 `mcrypt` 进行加密/解密

## 介绍

在本章中，我们将向你展示如何设置一种简单但有效的机制来过滤和验证一组 POST 数据。然后，我们将介绍如何保护你的 PHP 会话免受潜在的会话劫持和其他形式的攻击。下一个食谱展示了如何使用随机生成的令牌来保护表单免受**跨站请求伪造（CSRF）**攻击。

关于密码生成的食谱展示了如何将 PHP 7 的 true randomization（真随机数生成）结合使用来生成安全的密码。然后我们向你展示了两种形式的**CAPTCHA**：一种基于文本，另一种使用扭曲图像。最后，有一个食谱涵盖了在不使用已被诟病且即将弃用的 `mcrypt` 扩展的情况下进行强加密。

## 过滤 `$_POST` 数据

数据过滤过程可以包含以下任何一项或全部内容：

- 移除不需要的字符（即移除 `<script>` 标签）

- 对数据执行转换（即把引号转换为 `&quot;`）

- 加密或解密数据

加密在本章的最后一个食谱中进行了讨论。除此之外，我们将展示一种基本机制，可用于过滤表单提交后到达的 `$_POST` 数据。

### 如何实现...
