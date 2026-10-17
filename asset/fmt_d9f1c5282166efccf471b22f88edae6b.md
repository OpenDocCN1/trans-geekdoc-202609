
```php
class Database {
    private static $instance = null;
    private $connection;
    
    private function __construct() {
        $this->connection = new PDO('mysql:host=localhost;dbname=test', 'user', 'pass');
    }
    
    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }
    
    public function getConnection() {
        return $this->connection;
    }
}
```

正如你在示例代码中所见，我们定义了一个私有静态属性 `$instance` 来保存对象引用。由于这是静态的，此引用在该类型的**所有**对象间共享。

### `getInstance`

`getInstance()` 方法使用一种称为惰性实例化的方法，将创建对象延迟到最后可能的时刻，因为你不希望内存中躺着从未打算使用的未使用对象。它还节省了页面加载时不必加载不必要对象的时间和 CPU。该方法检查对象是否已设置，如果没有则创建它，并返回它。这确保了永远只创建一个此类对象。

我们还将构造函数设为私有，以确保没有人从外部使用 `new` 关键字创建它。如果你需要从此类继承，只需将 `private` 关键字改为 `protected`。

要使用此对象，只需编写以下内容：

```php
$db = Database::getInstance();
$conn = $db->getConnection();
```

现在我**确实**恳请你在可能的地方使用依赖注入并以松耦合对象为目标，但有时这根本不合理，单例模式可能会有用。

### 第 26.12 节：定义基本类

PHP 中的对象包含变量和函数。对象通常属于一个类，该类定义了该类所有对象将包含的变量和函数。

定义类的语法是：

```php
class MyClass {
    public $property = 'value';
    
    public function myMethod() {
        return 'Hello World';
    }
}
```

一旦定义了类，你可以使用以下方式创建实例：

```php
$obj = new MyClass();
```

对象上的变量和函数这样访问：

```php
echo $obj->property; // Outputs 'value'
echo $obj->myMethod(); // Outputs 'Hello World'
```

#### 构造函数

#### `__construct`

类可以定义一个特殊的 `__construct()` 方法，它作为对象创建的一部分被执行。这通常用于指定对象的初始值：

```php
class Person {
    public $name;
    
    public function __construct($name) {
        $this->name = $name;
    }
}

$person = new Person('John');
echo $person->name; // Outputs 'John'
```

#### 扩展另一个类

类定义可以扩展现有的类定义，添加新的变量和函数，以及修改父类中定义的那些。

这是一个扩展前面示例的类：

```php
class Shape {
    public $color = 'red';
}

class Square extends Shape {
    public $sides = 4;
}
```

```php
$square = new Square();
echo $square->color; // Outputs 'red' (inherited from Shape)
echo $square->sides; // Outputs '4' (defined in Square)
```

`Square` 类包含 `Shape` 类和 `Square` 类的变量和行为：

```php
$square = new Square();
$square->color = 'blue';
echo $square->color; // Outputs 'blue'
```

### 第 26.13 节：匿名类

匿名类在 PHP 7 中引入，以便轻松创建快速的一次性对象。它们可以接受构造函数参数、扩展其他类、实现接口并使用 trait，就像普通类一样。

在其最基本的形式中，匿名类如下所示：

```php
$util = new class {
    public function sayHello() {
        echo "Hello";
    }
};

$util->sayHello(); // Outputs "Hello"
```

嵌套在另一个类内部的匿名类无法访问该外部类的 `private` 或 `protected` 方法或属性。可以通过让匿名类继承外部类来获得对外部类 `protected` 方法和属性的访问权限。可以通过构造函数将外部类的 `private` 属性传递给匿名类来获得访问权限。

例如：

![](img/Image00706.jpg)

![](img/Image00707.jpg)

## 第 27 章：命名空间

### 27.1 节：声明命名空间

命名空间声明如下所示：

| `namespace MyProject` |
| --- |

| `namespace MyProject\Security\Cryptography` |
| --- |

| `namespace MyProject` | `{` | `...` |
| --- | --- | --- |

![](img/Image00708.jpg)；`- 声明命名空间 MyProject`

`;` `- 声明嵌套命名空间`

`}` `- 使用大括号声明命名空间。`

建议每个文件只声明一个命名空间，尽管你可以在单个文件中声明任意数量：

![](img/Image00709.jpg)

每次声明命名空间后，随后定义的类都将属于该命名空间：

![](img/Image00710.jpg)

| `namespace MyProject\Shapes` |
| --- |

命名空间声明可以在不同文件中多次使用。上例在单个文件中于 `MyProject\Shapes` 命名空间下定义了三个类。最好将其拆分为三个文件，每个文件均以 `namespace MyProject\Shapes;` 开头。详见 PSR-4 标准示例。

### 27.2 节：引用命名空间中的类或函数

如“声明命名空间”所示，可按如下方式在命名空间中定义类：

![](img/Image00711.jpg)

引用该类需使用完整路径（含命名空间）：

![](img/Image00712.jpg)

可通过 `use` 语句导入类以简化引用：

![](img/Image00713.jpg)

PHP 7.0 起，可使用大括号在一条语句中分组多个 `use` 语句：

![](img/Image00714.jpg)

有时两个类同名。若处于不同命名空间则无问题，但若尝试用 `use` 语句导入则会冲突：

![](img/Image00715.jpg)

可用 `as` 关键字自定义别名解决：

![](img/Image00716.jpg)

引用当前命名空间外的类需用 `\` 转义，否则会假定为相对于当前命名空间的相对路径：

![](img/Image00717.jpg)

### 27.3 节：声明子命名空间

声明具有层级的单个命名空间示例：

![](img/Image00718.jpg)

![](img/Image00719.jpg)

上例创建了：

常量 `MyProject\Sub\Level\CONNECT_OK`、类 `MyProject\Sub\Level\Connection` 和函数 `MyProject\Sub\Level\connect`。

### 27.4 节：什么是命名空间？

PHP 社区开发者众多，代码量巨大。这意味着某库的 PHP 代码可能与另一库使用相同的类名。当两个库在同一命名空间下使用时，会发生冲突并导致问题。

命名空间解决了此问题。正如 PHP 参考手册所述，命名空间可类比为操作系统目录对文件的命名空间划分；同名文件可共存于不同目录。同理，同名 PHP 类可共存于不同 PHP 命名空间。

为代码添加命名空间至关重要，这样其他开发者使用时无需担心与其他库冲突。

## 第 28 章：会话

### 28.1 节：`session_start()` 选项

| [ph](http://php.net/manual/en/ini.list.php) [p](http://php.net/manual/en/ini.list.php) | [.](http://php.net/manual/en/ini.list.php) | [in](http://php.net/manual/en/ini.list.php) [i](http://php.net/manual/en/ini.list.php) |
| --- | --- | --- |

PHP 7 起，可向 `session_start` 函数传递包含[基于会话的](http://php.net/manual/en/ini.list.php)[选项](http://php.net/manual/en/ini.list.php)的数组。

示例

![](img/Image00720.jpg)

| `php` | `.` | `ini` | `setting named` | `session` | `.` | `lazy_write` |
| --- | --- | --- | --- | --- | --- | --- |

此特性还引入了 `session.lazy_write`，默认为 `true`，表示仅在会话数据变更时才重写。

参考：[`wiki.php.net/rfc/session-lock-ini`](https://wiki.php.net/rfc/session-lock-ini)

### 28.2 节：会话锁定

| `session_start` |
| --- |

| `session_start` |
| --- |

众所周知，PHP 将会话数据写入服务端文件。当请求调用 `session_start()` 的 PHP 脚本时，PHP 会锁定该会话文件，导致相同 `session_id` 的其他传入请求阻塞/等待，直到会话文件锁释放。

会话文件保持锁定直到脚本结束或手动关闭会话。为避免多请求阻塞，可启动会话后关闭会话，释放文件锁，允许后续请求继续。

![](img/Image00721.jpg)

即使会话关闭，仍可读取会话值，因会话数据仍可用。

![](img/Image00722.jpg)

PHP >= 7.0 支持 `read_only`、`read_write` 和 `lazy_write` 会话，可能无需使用 `session_write_close()`。

### 28.3 节：操作会话数据

`$_SESSION` 变量是数组，可像普通数组一样检索或操作。

![](img/Image00723.jpg)

更多数组操作参考“操作数组”。

注意：若在会话中存储对象，仅当有类自动加载器或类已加载时才能优雅恢复。否则对象会作为 `__PHP_Incomplete_Class` 类型返回，可能导致[崩溃](http://stackoverflow.com/q/1055728/3990767)。自动加载详见“命名空间与自动加载”。

警告：

会话数据可能被劫持。详见：《Pro PHP Security: From Application Security Principles to the Implementation of XSS Defense - Chapter 7: Preventing Session Hijacking》（https://books.google.com.au/books?id=EUc6NlZRDqcC&pg=PA97#v=onepage&q&f=false）

强烈建议切勿在 `$_SESSION` 中存储任何个人信息。最关键的是信用卡号、政府颁发的 ID、密码；也包括姓名、邮箱、电话等不太敏感但可让黑客冒充/攻破合法用户的数据。通用原则：会话数据仅使用无价值/非个人值，如数字标识符。

### 28.4 节：销毁整个会话

| [`session_destroy`](http://php.net/session_destroy) |
| --- |

若需销毁会话，可用 `session_destroy()`：

![](img/Image00724.jpg)

![](img/Image00725.jpg)

| `session_destroy()` | 与 `$_SESSION = array();` 不同 |
| --- | --- |

`session_destroy()` 会移除 SESSION 超全局变量中所有存储的值，但不会销毁实际存储的会话版本。

| `$_SESSION = array();` | 代替 `session_unset()` |
| --- | --- |

注意：用 `$_SESSION = array();` 是因[手册](http://php.net/session_destroy)规定：

![](img/Image00726.jpg) 仅在不使用 `$_SESSION` 的旧弃用代码中使用 `session_unset()`。

### 28.5 节：无错误的安全会话启动

许多开发者在处理大型项目时会遇到这个问题，特别是当他们在某些模块化 CMS 的插件、附加组件、组件等上工作时。这里提供了一种安全启动会话的解决方案：首先检查 PHP 版本以覆盖所有版本，然后检查会话是否已启动。如果会话不存在，则安全地启动会话。如果会话已存在，则不执行任何操作。

![](img/Image00727.jpg)

### 第 28.6 节：会话名称

#### 检查会话 Cookie 是否已创建

会话名称是用于存储会话的 Cookie 的名称。你可以用它来检测是否已为用户创建了会话的 Cookie：

![](img/Image00728.jpg)

请注意，除非你真的不想不必要地创建 Cookie，否则这种方法通常没有用处。

#### 更改会话名称

| `session_name` |
| --- |

你可以通过调用 `session_name()` 来更新会话名称。

![](img/Image00729.jpg)

| `session_name` |
| --- |

如果 `session_name()` 未提供参数，则返回当前的会话名称。

![](img/Image00730.jpg)

它应仅包含字母数字字符；应简短且具有描述性（即针对启用了 Cookie 警告的用户）。会话名称不能仅由数字组成，至少必须包含一个字母。否则，每次都会生成一个新的会话 ID。

## 第 29 章：Cookies

### 参数详情

Cookie 的名称。这也是你可以用来从 `$_COOKIE` 超全局变量中检索值的键。这是唯一的必需参数。

| name | value | expire | path | domain | secure | httponly |
| --- | --- | --- | --- | --- | --- | --- |
| Cookie 的名称。这也是你可以用来从 `$_COOKIE` 超全局变量中检索值的键。这是唯一的必需参数。 | 存储在 Cookie 中的值。此数据可被浏览器访问，因此请勿在此存储任何敏感信息。 | 一个 Unix 时间戳，表示 Cookie 何时过期。如果设置为零，Cookie 将在会话结束时过期。如果设置为小于当前 Unix 时间戳的数字，Cookie 将立即过期。 | Cookie 的作用域。如果设置为 `/`，Cookie 将在整个域名下可用。如果设置为 `/path/`，则 Cookie 仅在该路径及其子路径下可用。默认为设置 Cookie 的文件的当前路径。 | Cookie 可用的域名或子域名。如果设置为裸域名，则 Cookie 将在该域名及所有子域名下可用。如果设置为子域名，则 Cookie 仅在该子域名及其所有子子域名下可用。 | 当设置为 `TRUE` 时，仅当客户端和服务器之间存在安全的 HTTPS 连接时才会设置 Cookie。 | 指定 Cookie 仅应通过 HTTP/S 协议提供，不应提供给 JavaScript 等客户端脚本语言。仅在 PHP 5.2 或更高版本中可用。 |

HTTP Cookie 是网站发送的一小段数据，当用户浏览网页时，由用户的 Web 浏览器存储在用户的计算机上。

### 第 29.1 节：修改 Cookie

可以通过重置 Cookie 来修改其值。

![](img/Image00731.jpg)

### 第 29.2 节：设置 Cookie

| `setcookie` |
| --- |

使用 `setcookie()` 函数设置 Cookie。由于 Cookie 是 HTTP 头部的一部分，你必须在向浏览器发送任何输出之前设置 Cookie。

![](img/Image00732.jpg)

示例：`setcookie("user", "Tom", time() + 86400, "/");` // 检查函数参数的语法

说明：

![](img/Image00733.jpg)

创建一个名为 `user` 的 Cookie

（可选）Cookie 的值为 `Tom`

（可选）Cookie 将在 1 天后过期（86400 秒）
