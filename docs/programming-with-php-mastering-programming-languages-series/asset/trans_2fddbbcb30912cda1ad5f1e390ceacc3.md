

## 创建对象

类的对象（实例）使用 `new` 关键字创建。在示例中，`$car1` 和 `$car2` 是 `Car` 类的实例。

## 访问属性和方法

属性使用箭头运算符 `->` 访问，方法也是以类似方式调用。这使你能够处理对象特定的数据和行为。

理解面向对象编程的概念，如类、对象、封装和继承，对 PHP 开发至关重要。OOP 促进代码可重用性、可维护性和关注点分离，使其成为构建复杂且可扩展 PHP 应用不可或缺的技术。

## 在 PHP 中创建类和对象

在 PHP 中，类是面向对象编程（OOP）的构建块。它们为创建对象提供了蓝图，对象封装了数据和行为。了解如何创建类和实例化对象是充分发挥 PHP 中 OOP 威力的基础。

```php
// Creating a class definition in PHP

class Student {

// Properties (attributes)

public $name;

public $age;

// Constructor method

public function __construct($name, $age) {

$this->name = $name;

$this->age = $age;

}

// Method (function)

public function introduce() {

echo "My name is {$this->name} and I am {$this->age} years old.";

}

}
```

```php
// Creating objects (instances) of the class

$student1 = new Student("Alice", 20);

$student2 = new Student("Bob", 22);

// Accessing object properties and calling methods

echo $student1->name; // Output: Alice

$student2->introduce(); // Output: My name is Bob and I am 22 years old.
```

### 类定义
PHP 中的类定义了对象的结构和行为。在此示例中，`Student` 类具有属性（`name` 和 `age`）、构造函数方法（`__construct`）和自定义方法（`introduce`）。

### 构造函数方法
构造函数方法是在创建对象时执行的特殊方法。它初始化对象属性。在此情况下，它在实例化 `Student` 对象时设置 `name` 和 `age` 属性。

### 创建对象
对象是类的实例。使用 `new` 关键字，你可以根据同一类创建多个对象。

### 访问属性和方法
对象属性和方法使用箭头运算符（`->`）访问。这使你能够操作对象特定的数据和行为。

创建类和对象是 PHP 中面向对象编程的基础。它使你能够模拟现实世界实体并构建模块化、可维护且有组织的代码。理解这些概念对于开发可扩展且健壮的 PHP 应用至关重要。

## 在类中定义方法和属性

在面向对象编程（OOP）中，类充当创建对象的蓝图。在这些类中，你定义属性（属性）和方法（函数），以封装对象的数据和行为。了解如何在 PHP 类中定义方法和属性对于构建模块化且有组织的代码至关重要。

```php
// Creating a class definition in PHP

class Product {

// Properties (attributes)

public $name;

public $price;

// Constructor method

public function __construct($name, $price) {

$this->name = $name;

$this->price = $price;

}

// Method (function)

public function displayInfo() {

echo "Product: {$this->name}, Price: {$this->price} USD";

}

}
```

```php
// Creating an object of the class

$product1 = new Product("Laptop", 899);

$product2 = new Product("Smartphone", 499);

// Accessing object properties and calling methods

echo $product1->name; // Output: Laptop

$product2->displayInfo(); // Output: Product: Smartphone, Price: 499 USD
```

### 属性（属性）
属性是在类内声明的变量，表示对象的数据。在此示例中，`Product` 类具有 `name` 和 `price` 等属性来存储产品信息。

### 构造函数方法
构造函数方法（`__construct`）是在创建对象时调用的特殊方法。它使用在对象实例化期间作为参数传递的值来初始化对象属性。

### 方法（函数）
方法定义对象的行为或操作。此类中的 `displayInfo` 方法显示产品信息。

### 创建对象
使用 `new` 关键字创建类的对象。每个对象都有自己的一组属性，并且可以执行类方法。

在类中定义方法和属性使你能够创建可重用、有组织且结构化的代码。当你定义方法来操作属性时，OOP 原则如封装和抽象变得更加明显，使你的代码更具模块化和可维护性。

## 封装和信息隐藏

封装是面向对象编程（OOP）的基本原则之一，它促进了信息隐藏的概念。它涉及将数据（属性）和操作该数据的 方法（函数）捆绑在类中。这个封装的单元通常被称为“类”。

```php
// Creating a class definition with encapsulation

class Student {

// Properties (attributes)

private $name;

private $age;

// Constructor method

public function __construct($name, $age) {

$this->name = $name;

$this->age = $age;

}

// Getter method for name

public function getName() {

return $this->name;

}

// Setter method for age

public function setAge($newAge) {

if ($newAge >= 0) {

$this->age = $newAge;

}

}

}
```

```php
// Creating an object of the class

$student1 = new Student("Alice", 20);

// Accessing properties using getter method

echo $student1->getName(); // Output: Alice

// Modifying properties using setter method

$student1->setAge(21);
```

### 封装
在此示例中，通过将属性（`$name` 和 `$age`）声明为 `private` 来实现封装。私有属性只能在类本身内部访问和修改。这将内部实现细节隐藏在外部代码之外。

### Getter 和 Setter 方法
像 `getName` 这样的 getter 方法允许受控地访问私有属性，为 `name` 属性提供只读访问。像 `setAge` 这样的 setter 方法使属性的受控修改成为可能，在更新 `age` 属性之前允许验证和逻辑。

封装和信息隐藏增强了代码的安全性、可维护性和灵活性。通过封装数据并通过方法提供受控访问，你可以确保对象的内部状态保持一致和有效，减少 PHP 应用中意外修改和错误的风险。

## 第 9 模块

| PHP 中的方法和函数定义 |
| --- |
| 解锁可重用代码的力量 |

在课程“PHP 编程”中，模块“PHP 中的方法和函数定义”代表了你成为熟练 PHP 开发人员之旅中的一个关键里程碑。本模块深入探讨方法和函数世界，使你能够在 PHP 应用中创建高效、模块化和可重用的代码。

### 函数的作用

函数是 PHP 中结构化和有组织代码的构建块。本模块指导你了解定义、声明和使用函数以封装逻辑的基本概念。函数允许你将代码分块，使其更易读、可维护，并且可在项目中轻松重用。

### 理解方法论

除了函数之外，你还将在面向对象编程（OOP）的上下文中探索方法。方法与对象关联的函数，使你能够定义特定于特定类的行为和操作。本模块向你介绍静态方法和实例方法，使你能够高效地操作数据和对象。

### 增强代码可重用性

