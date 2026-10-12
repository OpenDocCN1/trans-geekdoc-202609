

# PHP 8 类构造函数增强

在 PHP 8 中，类构造函数获得了多项增强，使对象初始化更加便捷灵活。这些改进简化了构造函数的定义和使用过程，从而产生更整洁、更易维护的代码。让我们来探索 PHP 8 中针对类构造函数所做的增强。

## 7.1.1 属性提升

PHP 8 的一项显著新增功能是类构造函数中的属性提升。属性提升允许你直接在构造函数的参数列表中声明类属性，减少了通常与定义属性并为其赋值相关的样板代码。

示例如下：

```php
class User {
    public function __construct(
        public string $name,
        public int $age,
        public ?string $email = null
    ) {}
}
```

在本例中，`User` 类直接在构造函数的参数列表中定义了三个属性（`$name`、`$age` 和 `$email`）。当创建 `User` 类的实例时，这些属性会自动被赋值。这种简洁的语法消除了在构造函数中单独声明属性并赋值的必要。

## 7.1.2 构造函数属性提升顺序

属性提升还引入了关于属性顺序的新灵活性。你可以重新排列构造函数参数列表中的属性，而不影响它们的赋值顺序：

```php
class User {
    public function __construct(
        public int $age,
        public string $name,
        public ?string $email = null
    ) {}
}
```

在修改后的示例中，构造函数参数列表中属性的顺序与前一个示例不同，但赋值顺序保持不变。该特性在设计和演进类构造函数时提供了更大的自由度。

## 7.1.3 可见性修饰符

你可以将可见性修饰符（例如 `public`、`protected`、`private`）应用于使用构造函数属性提升声明的属性。这使你能够在控制属性可见性的同时，仍能受益于简洁的属性提升语法：

```php
class User {
    public function __construct(
        public string $name,
        protected int $age,
        private ?string $email = null
    ) {}
}
```

在本例中，`$name` 属性为公有，`$age` 属性为受保护，`$email` 属性为私有。这演示了控制属性访问权限的灵活性。

## 7.1.4 使用默认值初始化

构造函数属性提升也支持默认值，允许你为属性指定初始值。创建实例时若未提供这些属性的值，则会使用默认值：

```php
class User {
    public function __construct(
        public string $name = 'Guest',
        public int $age = 0,
        public ?string $email = null
    ) {}
}
```

在修改后的示例中，属性 `$name`、`$age` 和 `$email` 的默认值分别为 `Guest`、`0` 和 `null`。如果创建 `User` 实例时未提供值，将使用这些默认值。

## 7.1.5 构造函数属性提升的优势

PHP 8 中的构造函数属性提升显著简化了定义和初始化类属性的过程。它减少了代码冗余，增强了可读性，并提供了对属性可见性和默认值的更多控制。该特性鼓励简洁明了的类定义，有助于提高代码可维护性。

---

# 7.2 PHP 8 中使用接口和 Trait

PHP 8 在使用接口和 Trait 方面带来了改进，增强了代码的通用性和可复用性。这些增强简化了代码组织，促进了最佳实践，并在使用这些基本语言特性时提供了新能力。

## 7.2.1 接口中的抽象方法

在 PHP 8 之前，接口中声明的所有方法均隐式为抽象方法。然而在 PHP 8 中，你可以在接口中显式地将方法标记为抽象，这提高了代码可读性并阐明了意图：

```php
interface Shape {
    public function area(): float;
    abstract public function perimeter(): float;
}
```

在本例中，`perimeter` 方法被显式标记为抽象，明确表明实现 `Shape` 接口的任何类都必须为 `perimeter` 方法提供实现。这种显式声明符合最佳实践，并增强了代码文档性。

## 7.2.2 接口中的默认方法实现

PHP 8 引入了接口中的默认方法实现，允许你为方法提供通用实现，实现类可选择性地覆盖该实现。此特性简化了接口演进，并提供了合理的默认行为：

```php
interface Logger {
    public function log(string $message);
    public function error(string $message) {
        $this->log("[ERROR] $message");
    }
}
```

在本例中，`Logger` 接口定义了一个带有默认实现的 `error` 方法，该实现会在消息前加上 `[ERROR]` 前缀，然后委托给 `log` 方法。实现类可在必要时选择覆盖 `error` 方法。

## 7.2.3 Trait 作为属性

在 PHP 8 中，Trait 可以在类中作为属性使用，提供了一种更具表现力的方式来包含和复用 Trait 功能：

```php
trait Loggable {
    public function log(string $message) {
        echo $message;
    }
}

class LoggerUser {
    use Loggable;
    public function performLogging() {
        $this->log("Logging from LoggerUser");
    }
}
```

在本例中，`Loggable` Trait 在 `LoggerUser` 类中作为属性使用，`performLogging` 方法利用了 Trait 提供的 `log` 方法。这种方法增强了代码组织性，并促进了更好的封装。

## 7.2.4 Trait 方法冲突解决

PHP 8 引入了当类中使用的多个 Trait 提供同名方法时解决冲突的能力。你现在可以显式指定应使用哪个 Trait 的方法：

```php
trait A {
    public function doSomething() {
        echo "Trait A";
    }
}

trait B {
    public function doSomething() {
        echo "Trait B";
    }
}

class MyClass {
    use A, B {
        A::doSomething insteadof B;
        B::doSomething as doSomethingFromB;
    }
}
```

在本例中，`MyClass` 类同时使用了 `A` 和 `B` Trait，它们都提供了 `doSomething` 方法。通过使用 `insteadof` 和 `as` 关键字，你可以指定使用 `A::doSomething` 而非 `B::doSomething`，并可将 `B::doSomething` 别名为 `doSomethingFromB` 以避免冲突。

## 7.2.5 Trait 方法的优先级顺序

在 PHP 8 中，Trait 方法冲突解决遵循一致且可预测的优先级顺序：

1. 当前类中的方法具有最高优先级。
2. 当前类使用的 Trait 中的方法其次被考虑，遵循其在 `use` 语句中声明的顺序。
3. 最后，如果类继承自另一个类，则考虑父类中的方法。

此优先级顺序确保了在 PHP 8 中使用 Trait 时，你能对方法解析拥有细粒度的控制。

PHP 8 对接口和 Trait 的增强提供了更具表现力、可维护性和冲突弹性的代码。这些特性在遵循最佳实践和促进代码复用的同时，改进了 PHP 应用的整体设计和灵活性。

---

# 7.3 对象继承：最佳实践与新特性

继承是面向对象编程（OOP）中的基本概念，允许一个类（子类或派生类）从另一个类（父类或基类）继承属性和方法。PHP 8 提供了多项与对象继承相关的最佳实践和新特性，增强了代码组织和可维护性。

## 7.3.1 final 关键字

在 PHP 8 中，你可以使用 `final` 关键字防止类被进一步继承。当你将一个类标记为 final 时，它不能作为父类，确保其保持不变，并明确传达其预期行为。示例如下：

```php
final class FinalClass {
```

