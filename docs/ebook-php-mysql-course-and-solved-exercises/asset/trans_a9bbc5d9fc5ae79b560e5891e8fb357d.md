

这段代码定义了一个名为 `Person` 的类。该类有两个由 `protected` 关键字定义的属性：`$name` 和 `$age`，分别代表人的姓名和年龄。`protected` 关键字是面向对象编程中的一种可见性级别，用于定义对类的属性和方法的访问权限。当一个成员（属性或方法）被声明为 `protected` 时，它可以在定义它的类内部访问，也可以在继承自此类的派生类（子类）中访问，但不能在这些类之外访问。

具体来说，这意味着 `protected` 成员不能在声明它们的类外部直接访问，但可以在继承自该父类的子类中使用。这提供了额外的封装性和安全性，因为 `protected` 成员不会暴露在类层级之外，但可以被子类用来扩展或专门化父类的行为。

`Person` 类的构造函数被定义用于在创建 `Person` 类型的新对象时初始化这些属性。它接受两个参数 `$name` 和 `$age`，并使用它们来初始化相应的对象属性。

`Person` 类还有一个公共的 `displayDetails()` 方法，它使用连接运算符 (`.`) 形成一个包含这些详细信息的字符串，以显示人的详细信息，如姓名和年龄。

现在让我们创建一个名为 `Employee.php` 的新文件，在其中定义一个同名类，该类继承自 `Person` 类：

```php
<?php

require_once 'Person.php';

class Employee extends Person {

    private $salary;

    public function __construct($name, $age, $salary) {

        parent::__construct($name, $age);

        $this->salary = $salary;

    }

    public function displayEmployeeDetails() {

        parent::displayDetails();

        echo ", Salary: $ " . $this->salary;

    }

}
```

这段代码定义了一个名为 "Employee" 的类，它扩展了父类 "Person"。以下是代码各部分的详细解释：

- `require_once 'Person.php';`：此行包含 "Person.php" 文件，该文件包含父类 "Person"。这使得 "Employee" 类能够扩展 "Person" 类。
- `class Employee extends Person {...}`：此类声明使用 `extends` 关键字，将 "Employee" 类创建为 "Person" 类的子类。这意味着 "Employee" 类将继承 "Person" 类的属性和方法。
- `private $salary;`：这是 "Employee" 类特有的一个新私有属性的声明。它存储员工的薪水。
- `public function __construct($name, $age, $salary) {...}`：这是 "Employee" 类的构造函数。它接受三个参数：员工的姓名、年龄和薪水。`parent::__construct()` 函数使用姓名和年龄调用父类 "Person" 的构造函数。请注意双冒号运算符 (`::`) 的使用，用于调用父构造函数。然后，员工的薪水使用作为参数传递的值进行初始化。
- `public function displayEmployeeDetails() {...}`：这是一个添加的方法，用于通过使用父类 "Person" 的 `displayDetails()` 方法来显示员工的详细信息，然后添加薪水的显示。`parent::displayDetails()` 方法调用父类 "Person" 的 `displayDetails()` 方法以显示员工的姓名和年龄，然后在显示中添加员工的薪水。

总之，这段代码创建了一个 "Employee" 类，它从 "Person" 类继承功能，并添加了一个额外的属性来存储员工的薪水。构造函数初始化所有必要的属性，而 `displayEmployeeDetails()` 方法显示员工的详细信息，包括他们的薪水。

要评估继承的功能，请将以下代码插入 `index.php` 文件中。

```php
<?php

require_once 'Person.php';

require_once 'Employee.php';

// 实例化 Employee 类

$employee1 = new Employee("John Dupont", 35, 50000);

// 显示员工详细信息

$employee1->displayEmployeeDetails();

?>
```

这段代码首先使用 `require_once` 指令包含 `Person.php` 和 `Employee.php` 类文件。有必要包含这些类才能使用它们。

接下来，使用提供的详细信息创建 `Employee` 类的一个实例：姓名、年龄和薪水。最后，在 `$employee1` 对象上调用 `displayEmployeeDetails()` 方法以显示员工的详细信息，包括姓名、年龄和薪水。

执行此代码将产生以下结果：

![Image](images/image-182.png)

## 重新定义方法

方法重新定义，也称为方法替换或方法重载，是面向对象编程中继承的一项特性，它允许子类为其父类中已定义的方法提供特定的实现。这意味着子类可以提供继承方法的自己的实现，当在子类对象上调用该方法时，该实现将替换父类的实现。

在 PHP 中，通过在子类中声明一个与父类具有相同签名（名称和参数）的方法来重新定义方法。当在子类对象上调用此方法时，执行的是子类的实现，即使该方法已从父类继承。

这允许子类添加或修改从父类继承的行为，同时为类用户保持相同的接口（方法签名）。这有利于代码复用，并使对象行为能够适应子类的特定需求。

例如，"Person" 类的 `displayDetails()` 方法可以在 Employee 类中重新定义，如下所示：

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

在这个 Employee 类中，Person 类的 `displayDetails()` 方法被重新定义以包含员工的薪水。当我们在 Employee 类的对象上调用此方法时，将使用 Employee 类中特定的重新定义，覆盖从 Person 类继承的方法。换句话说，当我们在从 Employee 类创建的对象上调用 `displayDetails()` 方法时，执行的是在 Employee 类中定义的该方法版本，而不是在 Person 类中定义的版本。

作为继承过程一部分的方法重新定义的优势在于，能够自定义继承方法的行为以适应子类的特定需求。这使得代码具有更大的模块性和可扩展性，因为子类可以在不更改父类代码的情况下扩展或修改继承方法的行为。这样，每个类都可以拥有自己的特定功能，同时受益于父类中定义的通用特性，这鼓励了代码复用并便于维护。

请注意，如果父类中的方法被声明为 `public` 或 `protected`，子类始终可以重新定义父类的方法。这允许子类自定义继承方法的行为以适应其特定需求。但是，如果父类方法被声明为 `private`，则不能在子类中重新定义它，因为它在父类之外不可访问。

