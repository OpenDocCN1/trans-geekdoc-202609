
这段代码定义了一个名为 `Employee` 的类，它扩展了父类 `Person`。以下是代码各部分的详细解释：

- `require_once 'Person.php';`：此行包含 `Person.php` 文件，该文件包含父类 `Person`。这使得 `Employee` 类能够扩展 `Person` 类。
- `class Employee extends Person {...}`：此类声明使用 `extends` 关键字，将 `Employee` 类创建为 `Person` 类的子类。这意味着 `Employee` 类将继承 `Person` 类的属性和方法。
- `private $salary;`：这是 `Employee` 类特有的一个新私有属性的声明。它存储员工的薪水。
- `public function __construct($name, $age, $salary) {...}`：这是 `Employee` 类的构造函数。它接受三个参数：员工的姓名、年龄和薪水。`parent::__construct()` 函数使用姓名和年龄调用父类 `Person` 的构造函数。请注意双冒号运算符 (`::`) 的使用，用于调用父构造函数。然后，员工的薪水使用作为参数传递的值进行初始化。
- `public function displayEmployeeDetails() {...}`：这是一个添加的方法，用于通过使用父类 `Person` 的 `displayDetails()` 方法来显示员工的详细信息，然后添加薪水的显示。`parent::displayDetails()` 方法调用父类 `Person` 的 `displayDetails()` 方法以显示员工的姓名和年龄，然后在显示中添加员工的薪水。

总之，这段代码创建了一个 `Employee` 类，它从 `Person` 类继承功能，并添加了一个额外的属性来存储员工的薪水。构造函数初始化所有必要的属性，而 `displayEmployeeDetails()` 方法显示员工的详细信息，包括他们的薪水。

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

![Image](img/image-182.png)

#### 重新定义方法

方法重新定义，也称为方法替换或方法重载，是面向对象编程中继承的一项特性，它允许子类为其父类中已定义的方法提供特定的实现。这意味着子类可以提供继承方法的自己的实现，当在子类对象上调用该方法时，该实现将替换父类的实现。

在 PHP 中，通过在子类中声明一个与父类具有相同签名（名称和参数）的方法来重新定义方法。当在子类对象上调用此方法时，执行的是子类的实现，即使该方法已从父类继承。

这允许子类添加或修改从父类继承的行为，同时为类用户保持相同的接口（方法签名）。这有利于代码复用，并使对象行为能够适应子类的特定需求。

例如，`Person` 类的 `displayDetails()` 方法可以在 `Employee` 类中重新定义，如下所示：

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

在这个 `Employee` 类中，`Person` 类的 `displayDetails()` 方法被重新定义以包含员工的薪水。当我们在 `Employee` 类的对象上调用此方法时，将使用 `Employee` 类中特定的重新定义，覆盖从 `Person` 类继承的方法。换句话说，当我们在从 `Employee` 类创建的对象上调用 `displayDetails()` 方法时，执行的是在 `Employee` 类中定义的该方法版本，而不是在 `Person` 类中定义的版本。

作为继承过程一部分的方法重新定义的优势在于，能够自定义继承方法的行为以适应子类的特定需求。这使得代码具有更大的模块性和可扩展性，因为子类可以在不更改父类代码的情况下扩展或修改继承方法的行为。这样，每个类都可以拥有自己的特定功能，同时受益于父类中定义的通用特性，这鼓励了代码复用并便于维护。

请注意，如果父类中的方法被声明为 `public` 或 `protected`，子类始终可以重新定义父类的方法。这允许子类自定义继承方法的行为以适应其特定需求。但是，如果父类方法被声明为 `private`，则不能在子类中重新定义它，因为它在父类之外不可访问。

然而，如果你希望防止某个方法在子类中被重新定义，只需在定义该方法时使用 `final` 关键字即可。事实上，当一个方法在父类中被声明为 final 时，这意味着它不能在继承自此父类的子类中被重新定义。这保证了该方法的行为不会在子类中被修改，从而在代码设计中确保了一定的稳定性和可预测性。

例如，如果 `displayDetails()` 方法是用 `final` 关键字声明的，你就不能重新定义它：

```php
final public function displayDetails() {

 echo "Name: " . $this->name . ", Age: " . $this->age . " years";

 }
```

在这种情况下，如果你在 `Employee` 类中重新定义此方法并运行 `index.php` 文件，你将得到一个错误，提示 `Employee` 类中的某个方法试图重新定义一个已在 `Person` 类中声明为 final 的方法。

![Image](img/image-183.png)

#### 连续继承

连续继承，也称为级联继承，是一种面向对象编程概念，指一个类不仅继承其直接父类的属性和方法，还继承该父类的所有父类的属性和方法，从而形成一个继承链。例如，类 D 可能继承自类 C，类 C 又继承自类 B，类 B 又继承自类 A。

##### 连续继承的目标

**代码复用性**：允许复用父类和祖父类中已编写的代码，这促进了模块化和代码维护。

**功能扩展**：允许通过添加新属性和方法来扩展类的功能，同时继承父类的功能。

**实际示例**：

让我们看一个例子，其中有 `Animal`、`Mammal` 和 `Dog` 类。`Animal` 类是基类，`Mammal` 类继承自 `Animal` 类，而 `Dog` 类又继承自 `Mammal` 类。这种关系构成了连续继承。

以下是代码示例：

**Animal.php**：

```php
<?php

 // 父类

 class Animal {

 public function eat() {

 echo "The animal eats. ";

 }

 }
```

**Mammal.php**：

```php
<?php

 require_once "Animal.php";

 // 继承自 Animal 的类

 class Mammal extends Animal {

 public function breastfeed() {

 echo "The mammal nurses. ";

 }

 }
```

**Dog.php**：

```php
<?php

 require_once "Animal.php";

 require_once "Mammal.php";

 // 继承自 Mammal 的类

 class Dog extends Mammal {

 public function bark() {

 echo "The dog barks. ";

 }

 }
```

**index.php**：

```php
<?php

require_once 'Animal.php';

require_once 'Mammal.php';

require_once 'Dog.php';

// 使用类

$dog = new Dog();

$dog->eat(); // 将显示：The animal is eating.

$dog->breastfeed(); // 将显示：The mammal is breastfeeding.

$dog->bark(); // 将显示：The dog is barking.

require_once 'Animal.php';

require_once 'Mammal.php';

require_once 'Dog.php';

// 使用类

$dog = new Dog();

$dog->eat(); // 将显示：The animal is eating.

$dog->breastfeed(); // 将显示：The mammal is breastfeeding.

$dog->bark(); // 将显示：The dog is barking.

?>
```

在本例中，`Dog` 类分别从其父类 `Mammal` 和 `Animal` 继承了 `eat()` 和 `breastfeed()` 方法。这演示了连续继承的实际应用。当执行 `index.php` 时，你将得到以下结果：

![Image](img/image-184.png)

##### 继承深度

在面向对象编程中，通常没有具体限制你可以连续继承类的次数。然而，重要的是要考虑你的系统设计，并避免过深的继承深度，因为这会使代码难以理解、维护和扩展。

过深的继承深度可能导致复杂性增加、类之间强依赖以及过于僵化的层级结构，这会使代码变得脆弱且难以修改。

简而言之，虽然你可以在技术上根据需要进行任意次数的连续继承，但最好设计你的系统以促进清晰度、灵活性和易维护性。

要停止连续继承，可以在类或方法的声明中使用 `final` 关键字。当一个类被声明为 final 时，这意味着它不能被其他类扩展。同样，当你声明一个方法为 final 时，意味着它不能在子类中被重新定义（或重载）。

以下是在 `Mammal` 类中使用 `final` 关键字停止连续继承的方法：

```php
<?php

 require_once "Animal.php";

 // 继承自 Animal 的类

 final class Mammal extends Animal {

 public function breastfeed() {

 echo "The mammal nurses. ";

 }

 }
```

在这段代码中，我们有 `Mammal` 类，它继承自 `Animal` 类。在 `Mammal` 类声明前使用关键字 `final` 意味着该类是 final 的，这意味着它不能被其他类扩展。换句话说，没有任何类可以继承自 `Mammal` 类。

#### 使用继承的目标和优势

在软件设计中使用继承提供了几个关键优势和目标：

**代码复用性**：继承允许复用父类中已实现的代码，从而减少代码重复，促进更高效和模块化的软件设计。

**模块化和结构**：通过继承父类的功能，子类可以按层级组织，便于逻辑结构化和代码维护。

**扩展和定制**：子类可以通过添加新功能或重新定义现有功能来扩展其父类的行为。这允许根据每个子类的特定需求灵活定制对象行为。

**抽象和多态**：正如我们将在后续章节中看到的，继承促进了代表应用程序中通用概念的抽象类层级的创建。通过使用抽象类和接口，继承也促进了多态的实现，即不同类的对象可以被统一处理。

总的来说，这些目标和优势使继承成为在 PHP 和其他面向对象编程语言中设计和实现健壮、可扩展且可维护软件的强大工具。

#### 结论

在本章中，我们深入探讨了面向对象编程中继承的概念。我们了解了类如何从其他类继承属性和方法，以及在 Web 设计中使用继承的优势和目标。

继承在类之间创建了层级关系，子类可以受益于父类的功能，同时扩展或定制其行为。这鼓励了代码复用，减少了冗余，并便于软件维护。

我们还涵盖了方法重新定义、使用 `final` 关键字防止后续继承以及连续继承等高级概念。

通过充分理解继承并适当应用，开发人员可以设计出灵活、模块化和可扩展的软件架构，有效满足开发项目不断变化的需求。

##### 练习 28（接练习 27）：

创建一个继承自 `Vehicle` 类的 `Car` 类，并增加一个 `number_doors` 属性。`Car` 类还应有一个构造函数，该构造函数考虑到这个额外属性。

`Car` 类应具有 `number_doors` 属性的 getter 和 setter，以及一个 `display()` 方法，该方法以字符串形式显示汽车的信息，并调用父类的 `display()` 方法。

然后，创建一个类型为 `Car` 的对象并带有初始信息，使用 `display()` 方法和 setter 来修改汽车的信息。

### 第 17 章：接口与抽象类

在 PHP 面向对象编程的世界里，接口和抽象类在模块化、灵活且可扩展软件的设计中扮演着至关重要的角色。这些概念为定义契约和基础结构提供了强大的机制，使开发者能够创建结构良好、易于维护的类层级结构。

在本章中，我们将深入探讨接口和抽象类，首先从这些概念的清晰定义入手。我们将考察它们的语法、特性和根本区别，以及它们在软件设计中提供的优势。此外，我们将通过具体示例来说明它们在实际场景中的应用，并讨论充分发挥其潜力的最佳实践。本章将为你提供掌握 PHP 中接口和抽象类所需的知识。

#### PHP 接口

PHP 中的接口是用于定义类必须遵守的契约的强大面向对象编程工具。它们提供了一种结构化的方式来声明类必须实现的方法，而无需提供这些方法如何实现的细节。换句话说，接口定义了类 *能做什么*（*what*），而不是 *如何做*（*how*）。

在本节中，我们将深入了解 PHP 中的接口。我们将发现如何声明和使用接口、PHP 中接口的语法、它们可以包含的方法，以及类如何实现这些接口。我们还将探讨在软件设计中使用接口的优势。

接口在创建模块化、灵活且可扩展的代码中起着至关重要的作用。它们的使用保证了系统中类的一致性和合规性，同时促进了类的替换和多态性。让我们更仔细地看看 PHP 中接口的不同侧面。

##### 接口声明与语法

接口使用 `interface` 关键字后跟接口名称来声明。它们提供了一个类必须实现的方法列表。要使用接口，类必须实现接口中定义的所有方法。

声明接口的语法如下：

![Image](img/image-185.png)

接口只能包含方法签名，而不能包含方法体。这意味着接口中声明的方法没有函数体，只有方法声明。下面是一个名为 `Connectable` 的接口的代码示例，你可以将其放入一个新的 `Connectable.php` 文件中。

```php
<?php

 // 接口声明

 interface Connectable {

 // 连接方法

 public function connect();

 // 断开连接方法

 public function disconnect();

 }

?>
```

在本例中，我们声明了一个名为 "Connectable" 的接口，它包含两个方法：`connect()` 和 `disconnect()`。该接口定义了一个契约，类在实现这些方法时必须遵守。实现此接口的类必须为这些方法中的每一个提供实现。

请注意，接口名称必须具有描述性，清晰地指示接口的角色或功能。接口名称通常为单数，且通常以大写字母开头，就像类一样。例如：`Connectable`、`Loggable`、`Calculable` 等。

##### 在类中实现接口

要使用接口，一个或多个类可以使用 `implements` 关键字实现一个或多个接口。当一个类实现一个接口时，它必须为接口中定义的所有方法提供具体的定义。

创建一个新的 `Database.php` 文件，并按如下方式实现 `Connectable` 接口：

```php
<?php

 require_once 'Connectable.php';

 class Database implements Connectable {

 public function connect() {

 echo "Database connection established.";

 }

 public function disconnect() {

 echo "Database disconnected.";

 }

 }

?>
```

这段代码定义了一个名为 `Database` 的类，它实现了 `Connectable` 接口。`Connectable` 接口包含两个方法：`connect()` 和 `disconnect()`，所有使用它的类都必须实现这两个方法。

这两个方法都在 `Database` 类中实现了。`connect()` 方法显示一条消息，指示数据库连接已建立，而 `disconnect()` 方法显示一条消息，指示数据库连接已关闭。
