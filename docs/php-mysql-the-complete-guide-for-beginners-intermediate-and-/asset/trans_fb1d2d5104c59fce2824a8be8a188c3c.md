

# PHP Traits 和 Composer 依赖管理器

## 第 40.1 节：Traits 简介

这里我们有 `MrEd`，它已经继承自 `Horse`。但并非所有马都会 `Talk`，所以我们为此定义了一个 `Trait`。让我们看看这在做什么。

首先，我们定义 `Trait`。我们可以配合自动加载和命名空间使用它（另请参阅在命名空间中引用类或函数）。然后我们使用关键字 `use` 将其包含到 `MrEd` 类中。

你会注意到 `MrEd` 直接使用了 `Talk` 的函数和变量，而无需定义它们。还记得我们说的复制粘贴吗？这些函数和变量现在都在类中定义了，就好像这个类自己定义了它们一样。

### Traits 对比 抽象类

Traits 与抽象类关系最为密切，因为你可以在其中定义变量和函数。你也无法直接实例化一个 `Trait`（即 `new Trait()`）。Traits 不能像抽象类或接口那样强制类隐式定义函数。Traits 仅用于显式定义（因为你可以实现任意数量的接口，请参阅接口）。

### 何时应该使用 Trait？

当考虑使用 `Trait` 时，首先要问自己这个重要问题：

**我能否通过重构代码来避免使用 Trait？**

在大多数情况下，答案是 **Yes**。Traits 是单继承导致的边缘情况。滥用或过度使用 Traits 的诱惑可能很大。但请考虑，`Trait` 为你的代码引入了另一个来源，这意味着又增加了一层复杂性。在本例中，我们只处理 3 个类。但 Traits 意味着你现在可能要处理更多的类。每增加一个 `Trait`，你的类就变得更难处理，因为你现在必须去引用每个 `Trait` 以了解它定义了什么（以及可能发生冲突的位置，请参阅冲突解决）。理想情况下，你应该在代码中保持尽可能少的 Traits。

## 第 40.2 节：Traits 促进水平代码复用

假设我们有一个用于日志记录的接口：

```php
interface Logger {
    public function log(string $message);
}
```

现在假设我们有 `Logger` 接口的两个具体实现：`FileLogger` 和 `ConsoleLogger`。

```php
class FileLogger implements Logger {
    public function log(string $message) {
        // 写入文件
    }
}

class ConsoleLogger implements Logger {
    public function log(string $message) {
        echo $message;
    }
}
```

现在如果你定义了另一个类 `Foo`，也想让它能够执行日志记录任务，你可以这样做：

```php
class Foo {
    private $logger;

    public function setLogger(Logger $logger) {
        $this->logger = $logger;
    }

    public function doSomething() {
        if ($this->logger) {
            $this->logger->log("Doing something");
        }
    }
}
```

`Foo` 现在也是一个 `Logger`，但其功能依赖于通过 `setLogger()` 传递给它的 `Logger` 实现。如果我们现在想让类 `Bar` 也拥有这个日志记录机制，我们就必须在 `Bar` 类中复制这段逻辑。

我们可以定义一个 trait 来代替复制代码：

```php
trait Loggable {
    private $logger;

    public function setLogger(Logger $logger) {
        $this->logger = $logger;
    }

    public function log(string $message) {
        if ($this->logger) {
            $this->logger->log($message);
        }
    }
}
```

现在我们已在 trait 中定义了逻辑，可以使用该 trait 将逻辑添加到 `Foo` 和 `Bar` 类中：

```php
class Foo {
    use Loggable;
    // ...
}

class Bar {
    use Loggable;
    // ...
}
```

## 第 40.3 节：冲突解决

尝试在一个类中使用多个 trait 可能会导致涉及冲突方法的问题。你需要手动解决此类冲突。

例如，让我们创建这个层级结构：

```php
trait Cat {
    public function say() {
        echo "Meow";
    }
}

trait Dog {
    public function say() {
        echo "Woof";
    }
}
```

现在，尝试创建以下类：

```php
class TalkingParrot {
    use Cat, Dog;
}
```

PHP 解释器将返回致命错误：

```
Fatal error: Trait method say has not been applied, because there are collisions with other trait methods on TalkingParrot
```

解决冲突：

```php
class TalkingParrot {
    use Cat, Dog {
        Cat::say insteadof Dog;
        Dog::say as dogSay;
    }
}

$parrot = new TalkingParrot();
$parrot->say();    // 输出: Meow
$parrot->dogSay(); // 输出: Woof
```

## 第 40.4 节：使用 Traits 实现单例模式

**免责声明**：此例绝不提倡使用单例模式。单例模式必须谨慎使用。

在 PHP 中实现单例有一种相当标准的方式：

```php
class Singleton {
    private static $instance = null;

    private function __construct() {}

    private function __clone() {}

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }
}
```

为了防止代码重复，将此行为提取到 trait 中是个好主意。

```php
trait SingletonTrait {
    private static $instance = null;

    private function __construct() {}

    private function __clone() {}

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    public function __wakeup() {
        throw new \Exception("Cannot unserialize a singleton.");
    }
}
```

现在任何想作为单例运行的类只需使用该 trait：

```php
class MyService {
    use SingletonTrait;
    // ...
}

$service = MyService::getInstance();
```

即使现在无法序列化单例，禁用反序列化方法仍然很有用。

## 第 40.5 节：Traits 保持类整洁

随着时间的推移，我们的类可能会实现越来越多的接口。当这些接口拥有许多方法时，我们类中的方法总数将变得非常庞大。

例如，假设我们有两个接口和一个实现它们的类：

```php
interface Printable {
    public function print();
    public function printPreview();
}

interface Savable {
    public function save();
    public function saveAs();
}

class Article implements Printable, Savable {
    // ... 此处有许多方法
}
```

我们可以使用单独的 Traits 来实现这些接口，而不是在 `Article` 类中实现所有接口方法，从而保持类的精简，并将接口实现的代码与类分离。

例如，要实现 `Printable` 接口，我们可以创建这个 trait：

```php
trait PrintableTrait {
    public function print() {
        // 实现
    }

    public function printPreview() {
        // 实现
    }
}
```

并让类使用该 trait：

```php
class Article implements Printable, Savable {
    use PrintableTrait;
    use SavableTrait; // 假设 SavableTrait 存在
    // ...
}
```

主要好处是我们的接口实现方法将与类的其余部分分离，并存储在一个 trait 中，该 trait 承担为该特定类型对象实现接口的唯一责任。

## 第 40.6 节：多 Traits 使用

```php
trait Hello {
    public function sayHello() {
        echo "Hello ";
    }
}

trait World {
    public function sayWorld() {
        echo "World";
    }
}

class MyClass {
    use Hello, World;
}

$obj = new MyClass();
$obj->sayHello();
$obj->sayWorld();
```

上例将输出：

```
Hello World
```

## 第 40.7 节：修改方法可见性

```php
trait HelloWorld {
    public function sayHello() {
        echo "Hello World";
    }
}

class MyClass1 {
    use HelloWorld;
}

class MyClass2 {
    use HelloWorld { sayHello as protected; }
}

class MyClass3 {
    use HelloWorld { sayHello as private myPrivateHello; }
}
```

运行此例：

```php
$obj1 = new MyClass1();
$obj1->sayHello(); // 正常: public

$obj2 = new MyClass2();
// $obj2->sayHello(); // 致命错误: 调用受保护方法

$obj3 = new MyClass3();
// $obj3->sayHello(); // 致命错误: 调用私有方法
// $obj3->myPrivateHello(); // 致命错误: 调用私有方法
```

**注意**：因此请注意，在 `MyClass2` 的最后一个例子中，来自 `HelloWorld` 的原始未别名方法仍按原样可访问。

# 第 41 章：Composer 依赖管理器

## 参数详情

| 参数 | 描述 |
| :--- | :--- |
| `license` | 定义项目中要使用的许可证类型。 |
| `authors` | 定义项目的作者及作者详细信息。 |
| `support` | 定义支持邮箱、IRC 频道和各种链接。 |
| `require` | 定义实际依赖及包版本。 |
| `require-dev` | 定义开发项目所需的包。 |
| `suggest` | 定义包建议，即安装后可能有帮助的包。 |
| `autoload` | 定义项目的自动加载策略。 |
| `autoload-dev` | 定义开发项目的自动加载策略。 |

[Composer](https://getcomposer.org/) 是 PHP 最常用的依赖管理器。它类似于 Node 中的 `npm`、Python 的 `pip` 或 .NET 的 `NuGet`。

## 第 41.1 节：什么是 Composer？

[Composer](https://getcomposer.org/) 是 PHP 的依赖/包管理器。它可用于安装、跟踪和更新项目依赖。Composer 还负责自动加载应用程序所依赖的依赖项，让你轻松在项目中使用依赖，而无需担心在任何给定文件顶部包含它们。

### `composer.json`

项目的依赖列在 `composer.json` 文件中，该文件通常位于项目根目录。此文件保存关于生产环境和开发环境所需包版本的信息。

`composer.json` 模式的完整大纲可在 [Composer 官网](https://getcomposer.org/doc/04-schema.md) 找到。

### 安装包

```bash
composer require <package>
# 或用于开发依赖
composer require --dev <package>
```

此文件可使用任何文本编辑器手动编辑，或通过命令行自动编辑，命令如上所示。

### 初始化项目

要在项目中开始使用 composer，你需要创建 `composer.json` 文件。你可以手动创建，或直接运行 `composer init`。在终端运行 `composer init` 后，它会询问你关于项目的一些基本信息：

*   **包名** (vendor/package - 例如 `laravel/laravel`)
*   **描述** - 可选
*   **作者**
*   以及其他一些信息，如最低稳定性、许可证和所需包。

