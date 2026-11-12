

```php
$categories = array('PHP', 'MySQL', 'CSS');

// Check to see if we're viewing a valid category
if (isset($_GET['category']) &&
    in_array($_GET['category'], $categories)) {

    // Instantiate the subclass
    $header = new CategoryHeader($_GET['category'], $baseUrl);
} else {

    // Otherwise it's the home page. Instantiate the Parent class
    $header = new StandardHeader('Home');
}

// Display the header
echo $header->getHeader();
?>

<h2>Categories</h2>
<p><a href="?<?php echo $baseUrl; ?>?category=PHP">PHP</a></p>
<p><a href="?<?php echo $baseUrl; ?>?category=MySQL">MySQL</a></p>
<p><a href="?<?php echo $baseUrl; ?>?category=CSS">CSS</a></p>
</body>
</html>
```

如上所述，控制逻辑会查找 `$_GET['category']` 变量。如果存在，则会创建 `CategoryHeader` 的实例，显示导航以便用户能够找到返回主页的路径。但如果不存在，则会改为创建父类 `StandardHeader` 的实例，这适用于用户查看主页的情况（因此不需要面包屑导航来找到返回路径）。

换而言之，继承使我们能够添加所需的额外功能，而无需复制已存在于父类中的逻辑；现有的方法和逻辑可以通过子类复用。

继承提供了一种强大的机制，用于创建模块化的类来解决特定问题，同时仍可提供共享的方法和变量，无论我们处理的是哪个具体对象，都可以使用这些方法和变量。

## 避免深层继承结构

通常来说，使用继承构建类层次结构时，应避免超过两代。这样做通常是糟糕设计的表现，表明错过了让类以不同方式交互的机会（参见下一解决方案）。在实践中，超过两代的类往往会导致各种调试问题，并使代码难以维护。例如，很难跟踪层次结构中更高层使用的变量名。

## 对象如何交互？

除了继承之外，对象还有其他交互方式；例如，一个对象使用另一个对象。从许多方面来看，这种交互比继承更重要，面向对象范式正是在此处展现其真正威力。

一个对象使用另一个对象有两种方式：**聚合**和**组合**。

## 聚合

聚合是指一个对象将另一个对象以“临时借用”的方式交给自身。第二个对象通常会通过第一个对象的某个成员函数传递给第一个对象。随后，第一个对象可以调用第二个对象中的方法，从而为自己的目的使用第二个对象中存储的功能。

聚合的常见示例涉及数据库连接类。假设你将数据库连接类传递给另一个类，然后该类使用数据库连接类来执行查询。执行查询的类**聚合**了数据库连接类。

下面是使用 MySQL 类的简单示例（我们将在第 3 章中创建该类）：

```php
<?php
// Include the MySQL database connection class
require_once 'Database/MySQL.php';

// A class which aggregates the MySQL class
class Articles {
    var $db;
    var $result;

    // Accept an instance of the MySQL class
    function Articles(&$db)
    {
        // Assign the object to a local member variable
        $this->db = &$db;
        $this->readArticles();
    }

    function readArticles()
    {
        // Perform a query using the MySQL class
        $sql = "SELECT * FROM articles LIMIT 0,5";
        $this->result = &$this->db->query($sql);
    }

    function fetch()
    {
        return $this->result->fetch();
    }
}

// Create an instance of the MySQL class
$db = &new MySQL('localhost', 'harryf', 'secret', 'sitepoint');

// Create an instance of the Article class, passing it the MySQL
// object
$articles = &new Articles($db);
while ($row = $articles->fetch()) {
    echo '<pre>';
    print_r($row);
    echo '</pre>';
}
?>
```

在上述示例中，我们在 `Articles` 类之外实例化 `MySQL` 类，然后在实例化 `Articles` 时将其传递给 `Articles` 构造函数。随后，`Articles` 可以使用 `MySQL` 对象来执行特定查询。在此例中，`Articles` 聚合了 `MySQL` 对象。图 2.2 使用 UML 说明了这种关系。

### 图 2.2. 聚合

![](img/5b6cdf7cf4cf53e30b19e047895dc464_78_0.png)

## 组合

组合是指一个对象“完全拥有”另一个对象。也就是说，第一个对象负责创建（实例化）第二个对象。这种情况在许多场景下都很有用，但通常，当第一个对象可能是唯一需要使用第二个对象的对象时，会使用组合。

第 II 卷第 1 章中的一个示例是 `Auth` 类，它**组合**了 `Session` 类的一个实例，并在构造函数中创建它：

```php
class Auth {
    ...
    /**
     * Instance of Session class
     * @var Session
     */
    var $session;
    ...

    function Auth (&$dbConn, $redirect, $md5 = true)
    {
        $this->dbConn = &$dbConn;
        $this->redirect = $redirect;
        $this->md5 = $md5;
        $this->session = &new Session();
        $this->checkAddress();
        $this->login();
    }
}
```

由于 `Auth` 类需要读写会话变量，且应用程序中不太可能有很多其他不相关的类也需要使用 `Session`，因此由它创建自己的 `Session` 对象是合理的。

图 2.3 使用 UML 说明了本示例中的组合关系。

### 图 2.3. 组合

![](img/5b6cdf7cf4cf53e30b19e047895dc464_79_0.png)

## 分辨差异

判断对象 A 是聚合还是组合对象 B 的一般“思想实验”是问：“如果对象 A 消失，对象 B 还会存活吗？”如果对象 B 在对象 A 消失后仍然存活，则称对象 A 聚合对象 B。但如果对象 A 消失时对象 B 也随之消失，则称对象 A 组合对象 B。

从实际开发的角度来看，了解何时应用聚合或组合非常重要。

聚合的优势在于开销较低，因为单个对象会被许多其他对象共享。当然，聚合你的数据库连接类是个好主意；但如果将其与每个想要执行查询的对象组合，可能需要多个数据库连接，当你的网站吸引高流量时，这会迅速使应用程序停止响应。

组合的优势在于使类从外部使用时更加便捷。使用该类的代码无需担心向其传递所需的其他对象，在复杂应用程序中，这往往会变得棘手并导致设计上的“权宜之计”。组合还能让你确切知道哪个类可以访问被组合的对象。而在聚合中，共享被聚合对象的另一个对象可能会更改其状态，从而“破坏”该对象，使其他使用它的类无法正常工作。

## 多态

面向对象编程的另一个强大特性是多态——即不同类能够共享**接口**的能力。

接口是一个或多个方法，可让你为特定目的使用类。例如，你可以拥有两个数据库连接类——一个用于 MySQL，另一个用于 PostgreSQL。只要它们都提供查询方法，你就可以互换使用它们来在不同数据库上运行查询。查询方法是两个类共享的简单接口。

共享相同接口的类通常继承自提供常用方法的父类。再次强调，这最好通过示例来理解。

首先，我们定义一个**抽象**基类 `Message`，它提供常用方法 `getMessage`。在 `Message` 类之下，我们定义**具体**类，每个类创建特定消息。

“抽象”和“具体”这两个术语涉及类的用法，特别是类是否旨在被直接使用。抽象类是指某些功能或结构将由所有子类共享，但本身不打算直接使用的类；通常，它具有一个或多个空方法，这些方法没有任何实际用途。换句话说，你不应该从抽象类创建对象。具体类是抽象类的子类，你*可以*从中创建对象。某些语言（如 Java）在语法层面提供对抽象类的支持——这是 PHP 4 所不具备的。不过，在设计应用程序时，你仍然可以使用抽象类的*概念*，尽管你可以考虑添加文档，告知与代码协作的其他开发者该类是抽象类。

```php
<?php
class Message {
    var $message;

    function setMessage($message)
    {
        $this->message = $message;
    }

    function getMessage()
    {
        return $this->message;
    }
}
```

