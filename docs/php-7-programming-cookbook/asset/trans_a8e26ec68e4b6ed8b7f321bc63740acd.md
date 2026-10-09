

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

1. 首先，你需要了解将存在于 `$_POST` 中的数据。另外，也许更重要的是，你需要了解存储表单数据的数据库表所施加的限制。作为一个例子，请查看 `prospects` 表的数据库结构：

| COLUMN | TYPE | NULL | DEFAULT |
|---|---|---|---|
| first_name | varchar(128) | No | None |
| last_name | varchar(128) | No | None |
| address | varchar(256) | Yes | None |
| city | varchar(64) | Yes | None |
| state_province | varchar(32) | Yes | None |
| postal_code | char(16) | No | None |
| phone | varchar(16) | No | None |
| country | char(2) | No | None |
| email | varchar(250) | No | None |
| status | char(8) | Yes | None |
| budget | decimal(10,2) | Yes | None |
| last_updated | datetime | Yes | None |

2. 一旦你完成了对要发送和存储的数据的分析，你就可以确定需要执行何种类型的过滤，以及哪些 PHP 函数将服务于这一目的。

3. 作为一个例子，如果你需要去掉用户提供的表单数据中完全可能存在的前导和尾部空白，你可以使用 PHP 的 `trim()` 函数。所有字符数据根据数据库结构都有长度限制。相应地，你可能需要考虑使用 `substr()` 以确保长度不被超过。如果你想要移除非字母字符，你可能需要考虑使用带有适当模式的 `preg_replace()`。

