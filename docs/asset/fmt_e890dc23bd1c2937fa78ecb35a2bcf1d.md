
```php
if ( $object instanceof PageElement )
    $body->appendChild( $object->getXML( $document ) );
```

接口的定义方式与类类似。只是用 `interface` 关键字代替 `class`。另外两个重要区别是，接口内的所有方法必须始终定义为 `public`，并且方法没有主体。请参阅列表 1-3，其中展示了一个名为 `ReadableNode` 的新接口：

### 列表 1-3：ReadableNode.interface.php

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_42_0.png)

```php
<?php
interface ReadableNode {
    public function isRead();
    public function markAsRead();
    public function markAsUnread();
};
?>
```

然后你可以创建一个可重用的实用函数 `markNodeAsRead()` 来检查节点是否可读，如果可读则调用 `markAsRead()` 方法。

```php
function markNodeAsRead( $node ) {
    if ( $node instanceof ReadableNode )
        $node->markAsRead();
}
```

当方法的实现方式不重要时，接口对于定义功能集合很有用。因为 PHP 没有多继承，所以它们也适用于定义具有不同功能集合的类，同时仍需要多态和类型提示的好处。与继承不同，类可以实现任意数量的接口。此外，接口可以扩展多个其他接口。例如，如果一个类同时可读和可删除：

```php
<?php
interface MessagingNode extends Readable, Deletable {
};

class ForumTopic extends Node implements Readable, Deletable {
    """
};

class BlogEntry extends Node implements MessagingNode {
    """
}
?>
```

在这种情况下，`ForumTopic` 和 `BlogEntry` 两个类都必须实现 `Readable` 和 `Deletable` 接口中的每个方法。在这种情况下，新的 `MessagingNode` 接口不过是简写。

## 魔术方法和常量

在深入设计模式之前，有必要回顾 PHP 中的魔术方法。魔术方法是可在任何类中定义并通过 PHP 内置功能执行的特殊命名方法。魔术方法总是以双下划线开头。事实上，魔术方法 `__destruct()` 和 `__construct()` 在本章中已多次使用。如果 PHP 在未来版本中实现同名方法，为避免冲突，不建议编写以双下划线开头的用户自定义函数和方法。

魔术常量用于访问 PHP 中的某些只读属性。魔术常量开头和结尾都有双下划线，并且始终大写。常量 `__CLASS__` 在本章中已多次使用，用于输出代码所在类的名称。

### 魔术常量的实际用途

通常很有用确定代码输出的来源位置。这就是所有魔术常量的目的，尤其是在编写自定义日志函数时非常有用。七个魔术常量如下：

- `__CLASS__` 等同于引用该常量的类。如前所述，此变量始终等于定义它的类，而不一定是实例化的类。在前面的示例中，`Node` 内部定义的 `__CLASS__` 总是返回 `Node`，即使该方法属于作为派生类实例化的对象的部分。除了调试之外，类常量对于静态回调函数也很有用。

- `__FILE__` 始终等于引用该常量的文件名。

- `__LINE__` 与 `__FILE__` 结合使用以输出代码中的位置。例如：

```php
error_log('Notice: Placeholder class. Don\'t forget to change before release! In \' . __FILE__ . \' on line \' . __LINE__);
```

> `__FILE__` 和 `__LINE__` 都相对于当前执行的脚本文件，无论该文件是从其他文件包含或 `require` 的。

- `__DIR__` 的功能与 `dirname(__FILE__)` 完全相同，并返回文件所在的绝对目录。它对于指定绝对路径很有用，绝对路径有时比相对路径更快；特别是在包含脚本时。

- `__FUNCTION__` 和 `__METHOD__` 可分别使用魔术常量确定函数或方法名称。尽可能时，应使用这些常量代替硬编码函数名。

- `__NAMESPACE__` 是第七个也是最后一个魔术常量。顾名思义，它等于当前命名空间。

作为调试机制，使用魔术常量非常基础。第 16 章深入讨论了更高级的调试技术。

## 为类添加魔术功能

尽管魔术方法 `__construct()` 和 `__destruct()` 是最常用的，但还有其他几种。在使用设计模式时，有必要扩展 PHP 的某些内置功能。本节首先介绍每种魔术方法有用的情况，然后说明该方法的使用。第一组方法与数据表示有关。

在许多情况下，有对象的字符串表示形式很有用，以便将其输出给用户或其他进程。默认情况下，将对象作为字符串引用会求值为对象在内存中的 ID，在大多数情况下这并不理想。PHP 提供了一种标准方法来覆盖此默认功能并返回任何期望的字符串表示形式。数字类可能将数字作为字符串返回，用户类可能返回用户名，节点类可能返回节点标题，XML 节点可能返回节点的文本内容，等等。用于此功能的魔术方法是 `__toString()`。当对象用作字符串时，无论何种情况都会触发该方法，例如：`echo "Hello $obj;"`。它也可以像任何其他普通公共方法一样直接调用，这比附加空字符串来强制类型转换之类的 hack 更可取。

序列化是存储状态或缓存整个对象的 PHP 应用程序中不可或缺的另一个过程。它生成对象的字符串表示形式。序列化通过手动调用 `serialize()` 完成，并通过 `unserialize()` 反转。这两种方法可在不修改的情况下作用于任何 PHP 变量（资源除外，例如 MySQL 句柄）。然而，有时在序列化之前需要清理复杂对象。

类可以实现魔术方法 `__sleep()`，该方法在序列化前立即调用。预计它会返回一个数组，其中值是要保存的成员变量。成员变量可以是 `public`、`private` 或 `protected`。同样，`__wakeup()` 在恢复对象时被调用。这些函数的一个用途是在 sleep 时忽略资源句柄，然后在恢复时重新打开句柄，如列表 1-4 所示。

### 列表 1-4：FileLog.class.php

```php
<?php
class FileLog {
    private $fpointer;
    private $filename;

    function __construct( $filename ) {
        $this->filename = $filename;
        $this->fpointer = fopen($filename,'a');
    }

    function __destruct() {
        fclose($this->fpointer);
    }

    function __sleep() {
        return array( "filename" );
    }

    function __wakeup() {
        $this->fpointer = fopen($this->filename,'a');
    }

    public function write( $line ) {
        fwrite( "$line\n", $this->fpointer );
    };

    /*
    Example usage:
        $log = new FileLog( "debug.txt" );
        $data = serialize( $log );
        $log = null;
        $log = unserialize($data);
        echo $data;
    Example output:
        O:7:"FileLog":1:{s:17:"FileLogfilename";s:9:"debug.txt"}
    */
?>
```

序列化数据，如前例注释中所见，包含数据类型、随后是数据的长度，然后是数据本身。分号分隔多个成员，每个成员有两个变量。第一个变量是名称，第二个是值。

在序列化时，私有成员变量前面会加上类名，而受保护的变量前面会加上星号。在这两种情况下，前缀都由两个空字节包围。然而，这些字节在打印时不可见。仔细查看字符串 `s:17:"FileLogfilename"` 可见，该字符串只有 15 个可打印字符长。剩下的两个字符是 `FileLog` 词前后方的空字节。

接下来的四个魔术方法与检索、检查和存储不可访问的成员变量有关。它们是 `__set()`、`__unset()`、`__get()` 和 `__isset()`。在尝试访问请求上下文中不可用的成员变量时，每个方法都会被调用。这可能意味着标记为 `private` 或 `protected` 的变量在作用域之外被访问，或者成员变量不存在。`__unset()` 和 `__isset()` 均由 PHP 中同名（不带下划线）的函数触发。这些方法在“设计模式”部分被广泛使用，因此在本节中不会再详细讨论。

类似地，当尝试调用未定义或不可访问的方法时，方法 `__call()` 会被调用。对于静态方法，会调用名为 `__callStatic()` 的类似方法。

本章不会介绍三个魔术方法。`__set_state()` 在通过调用 `var_export()` 导入类时使用，如果应用程序进行大量动态代码评估，则值得研究。`__clone()` 在尝试克隆对象时被调用，可用于各种处理。第三个方法 `__invoke()` 在对象被当作函数调用时使用；它在第 2 章中有更详细的介绍。

下一节讨论可在应用程序中使用的八种设计模式，以实现更简洁、更易读的代码并解决软件设计中的常见问题。

## Design Patterns

本节介绍 PHP 中的设计模式。本节涵盖的八种模式是：

- Singleton
- Multiton
- Proxy
- Façade
- Decorator
- Factory
- Observer Pattern
- Publisher/subscriber

## Singleton and Multiton Patterns

单例和较少见的多例模式控制应用程序中类的实例数量。如名称所示，单例只能实例化一次，而多例可以实例化任意多次。在后者的情况下，对于任何给定的键只能有一个实例。

由于单例的特性，它们常用于配置以及需要在应用程序任何地方访问的变量。使用单例有时被认为是不良实践，因为它会创建全局状态，并且不会将系统的所有功能封装在单个根对象中。在许多情况下，这会使单元测试和调试变得更加困难。本书将这些模式的选择留给读者自行决定。总的来说，有一些面向对象总比没有好。列表 1-5 显示了单例模式的示例。

### 列表 1-5：SingletonExample.class.php

```php
<?php
class SingletonExample {
    public static function getInstance() {
        static $instance = null;
        if ( $instance == null ) {
            $instance = new SingletonExample();
        }
        return $instance;
    }
}
?>
```

单例类同时使用了关键字 `static` 的两个功能。第一个在方法定义中，表示该方法与类的任何特定实例无关。第二个在方法本身中。当关键字 `static` 放在函数或方法中的局部变量前面时，表示对该方法的每次调用，无论调用针对哪个对象，都将共享该变量。

在单例的情况下，变量 `$instance` 初始化为 `null`，并在对该方法的所有调用中保留设置给它的值。首次执行时它始终为 `null`。后续执行时它始终是 `SingletonExample` 对象的同一实例。进行一次静态方法调用可确保每次都检索到相同的实例：

```php
$singleton = SingletonExample::getInstance();
```

多例类似，只是它要求向 `getInstance()` 函数传递一个键。对于给定的键，只能有一个对象实例。该模式在处理具有唯一标识符且在单次执行中可能多次出现的多个节点时很有用（例如内容管理系统中的节点）。多例节省内存并确保不会出现同一对象的多个冲突实例。`SingletonExample` 类可以快速修改为多例，如列表 1-6 所示。

### 列表 1-6：MultitonExample.class.php

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_47_0.png)

```php
<?php
class MultitonExample {
    public static function getInstance( $key ) {
        static $instances = array();
        if ( !array_key_exists( $key, $instances ) ) {
            $instances[$key] = new MultitonExample();
        }
        return $instances[$key];
    }
}
?>
```

由于 PHP 对象始终按引用传递，因此可以确保从多例或单例对象返回的每个实例在整个应用程序中保持一致。使用这些模式时必须小心序列化或 `clone` 关键字，因为任何操作都可能导致本应相同的对象的多个版本。

多例和单例在概念上与延迟初始化相似。在延迟初始化中，需要大量处理或内存的对象初始化会延迟到对象需要时才进行。这通常包括一个条件检查对象是否存在，然后返回现有对象或新对象——与前面两种模式类似。本书有时对数据库句柄或数据集使用延迟初始化，以避免花费应用程序不需要的资源。

## Proxy and Façade Patterns

代理和外观模式被归为一组，因为它们各自为更复杂的功能提供抽象。两种模式实现抽象的方式不同。

在代理的情况下，所有方法和成员变量都路由到目标对象。代理如果需要，可以在数据通过时修改或检查数据。魔术方法使在 PHP 中实现此模式变得非常容易。该模式的一种用途是记录方法访问。它也可以用于确定代码覆盖率或只是调试问题（参见列表 1-7）：

### 列表 1-7：LoggingProxy.class.php

可在 Wrox.com 上下载

```php
<?php

class LoggingProxy {
    private $target;

    function __construct( $target ) {
        $this->target = $target;
    }

    protected function log( $line ) {
        error_log($line);
    }

    public function __set( $name, $value ) {
        $this->target->$name = $value;
        $this->log("Setting value for $name: $value");
    }

    public function __get( $name ) {
        $value = $this->target->$name;
        $this->log( "Getting value for $name: $value" );
        return $value;
    }

    public function __isset( $name ) {
        $value = isset($this->target->$name);
        $this->log( "Checking isset for $name: ".($value?"true":"false") );
        return $value;
    }

    public function __call( $name, $arguments ) {
        $this->log( "Calling method $name with: ".implode(",",$arguments) );
        return call_user_func_array( array($this->target,$name), $arguments );
    }

};

?>
```

`LoggingProxy` 示例在 `__call()` 方法中使用了回调函数。该方法的目的在于调用目标类中定义的函数。该类还大量使用了变量成员名。变量成员名和回调将在第 2 章中更详细地介绍。

代理可以像前面的那样简单，也可以根据需要复杂。在大多数情况下，代理不应改变其所代理的类的行为；不过也可以这样做。代理也可以作为完全不同系统的接口。例如，可能需要一个执行存储过程的 MySQL 数据库代理，或一个作为 XML 远程过程调用接口的代理。

代理的一个缺点是它与所代理的类的类型不同。因此它不能用于需要类型提示的情况，或代码检查对象是否属于特定类型时。

外观模式服务于不同的目的。它旨在抽象复杂功能，使应用程序无需知道哪个子系统处理每个请求的细节。例如，如果进行典型的 API 请求需要通过用户子系统对用户进行身份验证，然后通过 API 子系统向远程服务器发出请求，然后通过另一个 API 的函数解码响应，则 resulting 外观方法如下所示：
