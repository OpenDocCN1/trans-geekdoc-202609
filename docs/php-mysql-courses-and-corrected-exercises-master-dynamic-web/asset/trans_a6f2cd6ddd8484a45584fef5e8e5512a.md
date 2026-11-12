

```php
// Display employee details

$employee1->displayEmployeeDetails();

?>
```

此代码首先通过 require_once 指令包含 Person.php 和 Employee.php 类文件。有必要包含这些类，以便能够使用它们。

接下来，使用提供的详细信息（姓名、年龄和薪水）创建 Employee 类的一个实例。最后，在 $employee1 对象上调用 displayEmployeeDetails() 方法，以显示员工的详细信息，包括姓名、年龄和薪水。

执行此代码将产生以下结果：

![](img/caba2aa22f5409ba73dea47176330677_504_0.png)

## 重定义方法

方法重定义，也称为方法替换或方法重载，是面向对象编程中的一个继承特性，它允许子类为其父类中已定义的方法提供特定实现。这意味着子类可以提供继承方法的自己的实现，当在子类的对象上调用时，该实现将替换父类的实现。

在 PHP 中，通过在子类中声明与父类具有相同签名（名称和参数）的方法来重定义方法。当在子类的对象上调用此方法时，将执行子类的实现，即使该方法是从父类继承的。

这使得子类能够添加或修改从父类继承的行为，同时为类用户保持相同的接口（方法签名）。这有利于代码重用，并使对象行为能够适应子类的特定需求。

例如，"Person" 类的 displayDetails() 方法可以在 Employee 类中按如下方式重定义：

```php
<?php
require_once 'Person.php';

class Employee extends Person {
private $salary;

public function __construct($name, $age, $salary) {
parent::__construct($name, $age);
$this->salary = $salary;
}

public function displayDetails() {
parent::displayDetails();
echo ", Salary: $ " . $this->salary;
}
}
?>
```

在这个 Employee 类中，Person 类的 displayDetails() 方法被重定义以包含员工的薪水。当我们在 Employee 类的对象上调用此方法时，将使用 Employee 类中的特定重定义，覆盖从 Person 类继承的方法。换句话说，当我们在从 Employee 类创建的对象上调用 displayDetails() 方法时，将执行在 Employee 类中定义的此方法版本，而不是在 Person 类中定义的版本。

作为继承过程的一部分重定义方法的优势在于能够自定义继承方法的行为以满足子类的特定需求。这允许代码具有更大的模块化和可扩展性，因为子类可以扩展或修改继承方法的行为，而无需更改父类的代码。这样，每个类可以拥有自己的特定功能，同时受益于在父类中定义的常见功能，这鼓励代码重用并便于维护。

请注意，如果在父类中将方法声明为 public 或 protected，子类始终可以重定义父类的方法。这允许子类自定义继承方法的行为以满足其特定需求。但是，如果父类方法被声明为 private，则不能在子类中重新定义它，因为它在父类之外不可访问。

但是，如果你希望防止方法在子类中被重定义，只需在定义方法时使用 **最终** 关键字。事实上，当方法在父类中声明为最终时，这意味着它不能在继承自该父类的子类中被重新定义。这保证了方法的行为在子类中不会被修改，从而在代码设计中确保一定的稳定性和可预测性。

例如，如果使用最终关键字声明，则不能重新定义 displayDetails() 方法：

```php
final public function displayDetails() {
echo "Name: ". $this->name . ", Age: ". $this->age . " years";
}
```

在这种情况下，如果你在 Employee 类中重新定义此方法并运行 index.php 文件，你将得到一个错误，指示 Employee 类中的方法正在尝试重新定义在 Person 类中声明为最终的方法。

```
Fatal error: Cannot override final method Person::displayDetails() in /Applications/XAMPP/xamppfiles/htdocs/phppoo/Employee.php on line 12
```

## 连续继承

连续继承，也称为级联继承，是面向对象编程的一个概念，其中一个类不仅继承其直接父类的属性和方法，还继承该父类的所有父类的属性和方法，从而形成一个继承链。例如，类 D 可能从类 C 继承，而类 C 又从类 B 继承，类 B 又从类 A 继承。

### 连续继承的目标

- 代码重用性：允许重用父类和祖父类中已编写的代码，这有助于模块化和代码维护。
- 功能扩展：允许通过添加新属性和方法来扩展类的功能，同时继承来自父类的功能。

### 实际示例：

让我们看一个示例，其中包含 Animal、Mammal 和 Dog 类。Animal 类是基类，Mammal 类继承自 Animal 类，而 Dog 类又继承自 Mammal 类。这种关系创建了连续继承。

下面是代码示例：

### Animal.php：

```php
<?php

// Parent class
class Animal {
public function eat() {
echo "The animal eats. ";
}
}
```

### Mammal.php：

```php
<?php
require_once "Animal.php";
// Class inheriting from Animal
class Mammal extends Animal {
public function breastfeed() {
echo "The mammal nurses. ";
}
}
```

### Dog.php：

```php
<?php
require_once "Animal.php";
require_once "Mammal.php";
// Class inheriting from Mammal
class Dog extends Mammal {
public function bark() {
    echo "The dog barks. ";
}
}
```

### index.php：

```php
<?php
require_once 'Animal.php';
require_once 'Mammal.php';
require_once 'Dog.php';

// Using the classes
$dog = new Dog();
$dog->eat(); // Will display: The animal is eating.
$dog->breastfeed(); // Will display: The mammal is breastfeeding.
$dog->bark(); // Will display: The dog is barking.
?>
```

在这个示例中，Dog 类分别从其父类 Mammal 和 Animal 继承了 Eat() 和 Breastfeed() 方法。这说明了连续继承的实际应用。执行 index.php 时，你将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_511_0.png)

### 继承深度

在面向对象编程中，通常没有限制你可以从一个类进行连续继承的次数。但是，重要的是要考虑你的系统设计，并避免过度的继承深度，因为这会使代码难以理解、维护和扩展。

过度的继承深度可能导致复杂性增加、类之间的强依赖以及过于僵化的层次结构，这可能使代码变得脆弱且难以修改。

简而言之，尽管你在技术上可以进行任意多次的连续继承，但最好设计你的系统以促进清晰度、灵活性和易于维护。

要停止连续继承，可以在类或方法的声明中使用最终关键字。当类被声明为最终时，这意味着它不能被其他类扩展。同样，当你将方法声明为最终时，这意味着它不能在子类中被重新定义（或重载）。

以下是如何使用最终关键字在 Mammal 类中停止连续继承：

```php
<?php
require_once "Animal.php";

// Class inheriting from Animal
class Mammal extends Animal {
public function breastfeed() {
echo "The mammal nurses. ";
}
}
```

在这段代码中，我们有 Mammal 类，它继承自 Animal 类。在 Mammal 类声明前使用关键字 **最终** 表示该类是最终类，这意味着它不能被

