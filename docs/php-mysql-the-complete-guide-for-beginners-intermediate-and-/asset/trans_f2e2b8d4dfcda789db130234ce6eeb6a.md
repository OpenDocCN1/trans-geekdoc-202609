
# 类常量

作为一个例子，在整个程序中拥有一个 π 值的简写表示可能会很方便。一个包含 `const` 值的类提供了一种简单的方式来保存此类值。

![](Image00625.jpg)

| MathValues :: PI |
| --- |

![](Image00626.jpg)

类常量可以通过在类上使用双冒号操作符（即所谓的作用域解析操作符）来访问，这很像静态变量。然而，与静态变量不同的是，类常量的值在编译时固定，不能重新赋值（例如 `= 7` 会产生致命错误）。

类常量对于定义类内部可能稍后需要更改的内容也很有用（但更改频率不足以值得存储在数据库中）。我们可以在内部使用 `self` 作用域解析器来引用它（它在实例化和静态实现中均有效）。

![](Image00627.jpg)

在版本 < 5.6 中，类常量只能包含标量值。

自 PHP 5.6 起，我们可以在常量中使用表达式，这意味着数学语句和带有连接的字符串都是可接受的常量。

![](Image00628.jpg)

自 PHP 7.0 起，用 `define` 声明的常量现在可以包含数组。

![](Image00629.jpg)

类常量不仅用于存储数学概念。例如，如果准备做派，拥有一个单一的 `Pie` 类来接收不同种类的水果可能会很方便。

![](Image00630.jpg)

然后我们可以这样使用 `Pie` 类：

![](Image00631.jpg)

这里出现的问题是，实例化 `Pie` 类时，没有提供关于可接受值的指导。例如，制作“boysenberry”派时，可能会拼写成 "boisenberry"。此外，我们可能不支持李子派。相反，如果在一个合理的地方预先定义好可接受的水果类型列表，那将很有用。比如一个名为 `Fruit` 的类：

![](Image00632.jpg)

| new Pie('aple') | Pie('apple') 均可通过编译器检查 | new Pie(Fruit::APLE) |
| --- | --- | --- |

将可接受的值列为类常量，为方法接受的可接受值提供了有价值的提示。它还能确保拼写错误无法通过编译器检查。虽然 `new Pie('aple')` 和 `new Pie(Fruit::APLE)` 会产生编译器错误。

最后，使用类常量意味着常量的实际值可以在单一位置修改，任何使用该常量的代码都会自动获得修改的效果。

| MyClass::CONSTANT_NAME |
| --- |

虽然访问类常量最常用的方法是 `MyClass::CONSTANT_NAME`，但也可以通过以下方式访问：

![](Image00633.jpg)

PHP 中的类常量按照惯例通常全部大写，单词之间以下划线分隔，尽管任何有效的标签名都可用作类常量名。

自 PHP 7.1 起，类常量现在可以定义为不同于默认 `public` 作用域的可见性。这意味着现在可以定义 `protected` 和 `private` 常量，以防止类常量不必要地泄露到公共作用域中（请参阅方法和属性可见性）。例如：

![](Image00634.jpg)

![](Image00635.jpg)

## `define` 对比 类常量

虽然这是一个有效的结构：

![](Image00636.jpg)

如果你尝试对类常量做同样的事情，会得到一个错误：

![](Image00637.jpg)

但你可以这样做：

![](Image00638.jpg)

更多信息，请参阅手册中的 [constants](http://php.net/manual/en/language.constants.php)。

## 使用 `::class` 获取类名

| ::class |
| --- |

PHP 5.5 引入了 `::class` 语法来获取完整的类名，会考虑命名空间作用域和 `use` 语句。

![](Image00639.jpg)

即使类未定义，上述代码也有效（即这段代码片段可以单独运行）。

当函数需要类名时，此语法很有用。例如，它可以与 `class_exists` 一起使用来检查类是否存在。无论返回值如何，此片段都不会生成错误：

![](Image00640.jpg)

# 第 26.2 节：抽象类

抽象类是不能被实例化的类。抽象类可以定义抽象方法，这些方法没有任何主体，只有定义：

![](Image00641.jpg)

![](Image00642.jpg)

抽象类应由子类继承，子类随后可以提供这些抽象方法的实现。

此类类的主要目的是提供一种模板，允许子类继承，“强制”遵循一种结构。让我们通过一个例子详细说明：

在本例中，我们将实现一个 `Worker` 接口。首先定义接口：

![](Image00643.jpg)

| run() |
| --- |

为了简化后续 `Worker` 实现的开发，我们将创建一个抽象 Worker 类，它已经提供了来自接口的 `run()` 方法，但指定了一些需要由任何子类填充的抽象方法：

![](Image00644.jpg)

| getMemoryLimit() |
| --- |

首先，我们提供了一个抽象方法 `getMemoryLimit()`。任何继承自 `AbstractWorker` 的类都需要提供此方法并返回其内存限制。然后 `AbstractWorker` 设置内存限制并记录日志。

| prepareMain() 和 main() |
| --- |

其次，`AbstractWorker` 在记录日志后调用 `prepareMain()` 和 `main()` 方法。

最后，所有这些方法调用都被归组在一个 `try-catch` 块中。因此，如果子类定义的任何抽象方法抛出异常，我们将捕获该异常，记录日志并重新抛出。这防止了所有子类都必须自行实现此逻辑。

现在让我们定义一个继承自 `AbstractWorker` 的子类：

![](Image00645.jpg)

正如你所见，`TransactionProcessorWorker` 实现起来相当容易，因为我们只需指定内存限制并担心它需要执行的实际操作。`TransactionProcessorWorker` 中不需要错误处理，因为这在 `AbstractWorker` 中已处理。

## 重要提示

![](Image00646.jpg)

继承自抽象类时，父类声明中标记为 `abstract` 的所有方法都必须由子类定义（或者子类本身也必须标记为 `abstract`）；此外，这些方法必须用相同（或限制更宽松）的可见性来定义。例如，如果抽象方法定义为 `protected`，函数实现必须定义为 `protected` 或 `public`，但不能是 `private`。

摘自 [PHP 文档 - 类的抽象](http://php.net/manual/en/language.oop5.abstract.php)。

如果你不在子类中定义父抽象类的方法，将会抛出如下致命 PHP 错误。

![](Image00647.jpg)

```
Fatal error: Class X contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (X::x) in
```

# 第 26.3 节：静态后期绑定

| self:: |
| --- |

在 PHP 5.3+ 及以上版本中，你可以利用[静态后期绑定](http://php.net/manual/en/language.oop5.late-static-bindings.php)来控制从哪个类调用静态属性或方法。它的加入是为了克服 `self` 作用域解析器固有的问题。请看以下代码：

![](Image00648.jpg)

| whatToSay() |
| --- |

你可能期望 `MrEd` 类会覆盖父类的 `whatToSay()` 函数。但当我们运行它时，会得到意想不到的结果：

![](Image00649.jpg)

| self::whatToSay() |
| --- |

| static:: |
| --- |

问题在于 `self::whatToSay()` 只能指向 `Horse` 类，意味着它不服从 `MrEd`。如果我们改用 `static::` 作用域解析器，就没有这个问题。这个较新的方法告诉类服从调用它的实例。因此我们得到了预期的继承行为：

![](Image00650.jpg)

# 第 26.4 节：命名空间和自动加载

