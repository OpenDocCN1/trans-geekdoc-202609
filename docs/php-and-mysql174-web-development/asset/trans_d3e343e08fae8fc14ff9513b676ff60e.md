

在后续章节中，我们将讨论 PHP 的高级面向对象（OO）特性。

## 使用类常量

PHP

```php
<?php
class Math
{
    const pi = 3.14159;
}
echo "Math::pi = " ..Math::pi;
?>
```

你可以像示例所示，使用 `::` 运算符指定类常量所属的类，从而访问该常量。

## 实现静态方法

PHP 允许使用 `static` 关键字。它应用于方法，允许在不实例化类的情况下调用方法。这是类常量概念在方法上的等价实现。例如，考虑上一节中创建的 `Math` 类。你可以添加一个 `squared()` 函数并在不实例化类的情况下调用它，如下：

```php
<?php
class Math
{
    static function squared($input)
    {
        return $input*$input;
    }
}
echo Math::squared(8);
?>
```

注意，你不能在静态方法中使用 `$this` 关键字，因为可能没有可以引用的对象实例。

## 检查类类型和类型提示

`instanceof` 关键字允许你检查对象的类型。你可以检查一个对象是否是特定类的实例、是否继承自某个类，或者它是否

```php
($b instanceof B) 将为真。
($b instanceof A) 将为真。
($b instanceof Displayable) 将为假。
```

所有这些示例假设 `A`、`B` 和 `Displayable` 都在当前作用域内；否则将触发错误。

此外，你还可以使用类类型提示。通常在 PHP 中，当你向函数传递参数时，你不需要传递参数的类型。通过类型提示，你可以指定应该传递的类类型，如果实际传递的不是该类型，则会触发错误。这种类型检查等同于 `instanceof`。例如，考虑以下函数：

```php
function check_hint(B $someclass) {
    //...
}
```

此示例显示 `$someclass` 需要是类 `B` 的实例。如果你传递一个类 `A` 的实例，例如

```php
check_hint($a);
```

你将得到以下致命错误：

**Fatal error:** Argument 1 must be an instance of B

注意，如果你提示的是 `A` 并传递了类 `A` 和 `B` 的实例，则不会发生错误，因为 `B` 继承自 `A`。

你也可以对接口、数组和可调用（callable）使用类型提示，这意味着传递的项必须是一个函数。虽然这对接口有效，但请注意它对 trait（Traits）无效。

## 延迟静态绑定（Late Static Bindings）

在具有相同函数多个实现的继承层次中，我们可以使用延迟静态绑定来指定使用哪个类的方法。

考虑以下简单示例（基于 PHP 手册中的示例）：

```php
<?php
class A {
    public static function whichclass() {
        echo __CLASS__;
    }
}
```

```php
public static function test() {
    self::whichclass();
}
```

```php
class B extends A {
    public static function whichclass() {
        echo __CLASS__;
    }
}
```

```php
A::test();
B::test();
```

你预期输出是 B 吗？你可能会对代码输出两次 A 感到惊讶。这是因为 `A` 重写了 `whichclass()` 方法，当通过 `B` 调用 `test()` 方法时，它是在父类 `A` 的上下文中执行的。我们如何让 `test()` 使用 `B` 对 `whichclass()` 的实现，即使用我们实际使用的类内部的实现？

答案是延迟静态绑定。在之前的示例中，如果我们将此行代码：
`self::whichclass();`

改为
`static::whichclass();`

代码将不再输出 A 然后输出 B。`static` 修饰符让 PHP 使用运行时实际创建的类，这就是名称中“延迟（late）”的部分。

## 克隆对象

PHP 中也可以使用 `clone` 关键字，它允许你复制现有对象。例如，
`$c = clone $b;`

会创建一个与 `$b` 相同类的副本，并具有相同的属性值。

你也可以更改这种行为。如果你需要 `clone` 的默认行为，你需要在基类中创建一个 `__clone()` 方法。该方法类似于构造函数或析构函数，区别在于你不需要手动调用它。它在像这里使用 `clone` 关键字时被自动调用。在 `__clone()` 方法内部，你可以定义你精确所需的复制行为。

`__clone()` 的优点是它会在使用默认行为完成精确复制后被调用，因此在那个阶段，你只需要更改你想更改的内容。

为 `__clone()` 添加的最常见功能是编写代码以确保被作为引用处理的类属性被正确复制。如果你打算克隆一个包含对象的类，你可能期望得到该对象的第二个副本，而不是同一个对象的第二个引用，因此在 `__clone()` 中添加此逻辑是有意义的。

你也可以选择什么都不改，但执行某些其他操作，例如更新与类相关的底层数据库记录。

## 使用抽象类

PHP 提供了抽象类（abstract classes，不能被实例化）以及抽象方法（abstract methods，仅提供方法的签名但不提供实现）。例如，

```php
abstract class A {
    abstract function operationX($param1, $param2);
}
```

任何包含抽象方法的类本身必须是抽象的。抽象方法和类的主要用途是在类层次结构中，你想确保子类包含某些内容；这也可以通过接口（interface）实现。

```php
abstract operationX($param1, $param2);
```

## 使用 __call() 方法重载方法

我们之前查看了一些具有特殊含义的类方法，其名称以双下划线（_）开头，例如 `__get()`、`__set()`、`__construct()` 和 `__destruct()`。另一个例子是 `__call()`，它用于 PHP 实现方法重载。

方法重载在许多面向对象的语言中很常见，但在 PHP 中并不有用，因为你需要灵活的类型和（易于实现的）可选函数。要使用它，你需要实现一个 `__call()` 方法，如示例所示：

```php
public function __call($method, $p) {
    if ($method == "display") {
        if (is_object($p[0])) {
            $this->displayObject($p[0]);
        } else if (is_array($p[0])) {
            $this->displayArray($p[0]);
        } else {
            $this->displayScalar($p[0]);
        }
    }
}
```

`__call()` 方法接收两个参数。第一个包含被调用方法的名称，第二个包含传递给该方法的参数数组。你可以自己决定调用哪个方法。在这种情况下，如果传递给 `display()` 的对象，则调用底层的 `displayObject()` 方法；如果传递的是数组，则调用 `displayArray()`；如果是其他内容，则调用 `displayScalar()`。

要调用此代码，你首先需要实例化包含 `__call()` 方法的类（命名为 `overload`），然后调用 `display()` 方法，如下所示：

```php
$ov = new overload();
$ov->display(array(1, 2, 3));
$ov->display('cat');
```

第一次调用 `display()` 触发 `displayArray()`，第二次触发 `displayScalar()`。注意，你不需要 `display()` 方法的底层实现即可工作。

PHP 5.3 引入了一个名为 `__callStatic()` 的简单魔法方法。它的工作方式与 `__call()` 类似，但在通过静态上下文调用不可访问的方法时会被触发，例如：
`overload::display();`

## 使用 __autoload()

PHP 的另一个特殊函数是 `__autoload()`。它不是类方法而是一个独立函数；因此你在类声明之外声明它。如果你实现了它，当你尝试实例化一个未声明的类时，它会被自动调用。考虑此示例：

```php
function __autoload($name)
{
  include_once $name.".php";
}
```

`__autoload()` 的主要用途是尝试包含实例化所需类所需的任何文件。

