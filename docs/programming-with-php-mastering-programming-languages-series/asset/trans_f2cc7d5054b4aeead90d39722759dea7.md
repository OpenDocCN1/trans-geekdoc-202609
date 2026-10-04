

`class Dog extends Animal`

```php
public $breed;

public function __construct($species, $breed) {
    parent::__construct($species); // Call the superclass constructor
    $this->breed = $breed;
    echo "It's a {$this->breed} dog.";
}
```

// Creating a Dog object
`$dog = new Dog("Canine", "Labrador")`;

*   使用 parent 关键字：在 `Dog` 类的构造函数中，`parent::__construct($species)` 行用于调用 `Animal` 超类的构造函数。这确保了在执行任何子类特定初始化之前，先执行超类的初始化逻辑。
*   构造函数链：通过使用 `parent::__construct($species)` 调用超类构造函数，你维护了继承层级的完整性。这种方法被称为构造函数链。
*   输出：创建 `Dog` 对象时，`Animal` 和 `Dog` 构造函数会按正确顺序执行。这会产生以下输出：

`A new Canine is created.`

`It's a Labrador dog.`

理解如何在继承中使用 `parent` 关键字和构造函数对于构建结构良好、可维护且高效的 PHP 代码至关重要。它确保对象得到正确初始化，并且子类特定功能能够正确地集成到继承层级中。

# Module 12: PHP 中的访问修饰符和封装

## 使用访问修饰符和封装保护和构建你的代码

在综合课程“PHP 编程”中，模块“PHP 中的访问修饰符和封装”标志着你掌握 PHP 面向对象能力之旅中的关键一步。本模块深入探讨访问修饰符和封装的世界，使你能够创建安全、有序且可维护的 PHP 应用。

### 访问修饰符的力量

访问修饰符决定了类属性和方法的可见性和可访问性。在本模块中，你将探索 `public`、`private` 和 `protected` 等访问修饰符的重要性。理解这些修饰符对于控制数据和功能在 PHP 类中的暴露和操作至关重要，有助于促进结构化和安全的代码库。

### 精通封装

封装是面向对象编程的基本原则，它将数据和行为封装在类中。本模块向你介绍封装作为保护数据完整性和控制对类成员访问的一种手段。你将学习如何使用访问修饰符来实现封装，创建不仅更安全而且更具适应性和可维护性的类。

### 创建健壮且安全的 PHP 应用

访问修饰符和封装是构建和保护 PHP 代码的工具。通过掌握这些概念，你将能够创建防止数据未授权访问并在代码库中强制执行清晰关注点分离的 PHP 应用。

### 提升你的面向对象技能

当你开始本模块时，你将深入理解访问修饰符和封装，这些是掌握安全且有序 PHP 代码的基本要素。“PHP 中的访问修饰符和封装”是你创建不仅功能齐全而且安全、可维护和可适应的代码的入口。加入我们这段变革之旅，提升你的 PHP 开发技能，创建在功能和安全性方面都出色的应用。

## 理解 PHP 中的访问修饰符

PHP 中的访问修饰符是用于控制类属性和方法可见性和可访问性的关键字。它们决定了类的哪些部分可以从类外部访问，并有助于强制执行封装原则，这是面向对象编程中的一个基本概念。

```php
class BankAccount {
    private $balance; // Private property
    public function __construct($initialBalance) {
        $this->balance = $initialBalance;
    }
    public function deposit($amount) {
        $this->balance += $amount;
    }
    public function withdraw($amount) {
        if ($this->balance >= $amount) {
            $this->balance -= $amount;
        } else {
            echo "Insufficient funds.";
        }
    }
    public function getBalance() {
        return $this->balance;
    }
}
```

*   私有属性：在 `BankAccount` 类中，`$balance` 属性被声明为 `private`。这意味着它只能在类内部访问，不能从外部直接访问。
*   公共方法：像 `deposit`、`withdraw` 和 `getBalance` 这样的公共方法提供了对 `$balance` 属性的受控访问。它们允许与属性交互，同时强制执行约束和业务逻辑。

通过使用 `private`、`protected` 和 `public` 等访问修饰符，你可以为应该从类外部访问的内容和应该保持封装的内容定义清晰的边界。这确保数据和功能得到良好保护，并有助于防止对类内部的非预期操作，从而带来更健壮和可维护的 PHP 代码。

## 私有、受保护和公共属性

PHP 中的访问修饰符允许你控制类属性的可见性和可访问性，确保它们能够安全地并且按照你的设计使用。这些修饰符——`private`、`protected` 和 `public`——决定了属性在类内部和外部如何被访问。

```php
class BankAccount {
    private $balance;   // Private property
    protected $owner;   // Protected property
    public $accountNumber; // Public property
    public function __construct($owner, $initialBalance) {
        $this->owner = $owner;
        $this->balance = $initialBalance;
    }
    public function deposit($amount) {
        $this->balance += $amount;
    }
    public function withdraw($amount) {
        if ($this->balance >= $amount) {
            $this->balance -= $amount;
        } else {
            echo "Insufficient funds.";
        }
    }
}
```

*   私有属性：`$balance` 属性被标记为 `private`。它只能在 `BankAccount` 类内部访问。这封装了余额并防止直接外部操作。
*   受保护属性：`$owner` 属性被标记为 `protected`。它可以在类及其子类中访问，确保内部使用所需属性仍可被扩展类利用。
*   公共属性：`$accountNumber` 属性是 `public`，使其可以从任何地方访问。虽然公共属性提供了最开放的访问，但应谨慎使用以避免非预期的外部干扰。

通过使用这些访问修饰符，你可以在 PHP 类中实现封装和可用性之间的平衡。私有属性非常适合应保持隐藏的数据，受保护属性允许继承，公共属性在需要时提供无限制访问。理解和应用这些修饰符增强了代码的安全性和可维护性。

## 封装和数据隐藏

封装是面向对象编程的核心原则，它促进将数据和方法捆绑到一个单元中，即类。PHP 中的访问修饰符，如 `private`、`protected` 和 `public`，通过定义类成员的可见性和可访问性来实现封装，有助于实现数据隐藏和访问控制。

```php
class BankAccount {
    private $balance; // Private property
    public function __construct($initialBalance) {
        $this->balance = $initialBalance;
    }
    public function deposit($amount) {
        $this->balance += $amount;
    }
    public function withdraw($amount) {
        if ($this->balance >= $amount) {
            $this->balance -= $amount;
        } else {
            echo "Insufficient funds.";
        }
    }
    public function getBalance() {
        return $this->balance;
    }
}
```

*   私有属性：在 `BankAccount` 类中，`$balance` 属性被声明为 `private`。这意味着它被封装在类内部，外部代码无法直接访问或修改它。相反，类通过 `deposit`、`withdraw` 和 `getBalance` 等方法提供受控访问。

