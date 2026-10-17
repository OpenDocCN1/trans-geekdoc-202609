
# PHP 可读代码 100 招：编写可读 PHP 代码的 100 技巧

## 引言

欢迎阅读编写更佳 PHP 代码的全面指南！

在接下来的页面中，你将发现 100 种强大的技术，用于提升你的编程技能并创建更具可读、易于维护的代码。

我们将探索 PHP 特有的特性和最佳实践，目标都是编写出让你的同事觉得阅读和编写起来愉快的代码。

每种技术都通过清晰的示例呈现，并将良好的实践与欠佳的方法进行对比。

这种结构允许你轻松地理解并将这些概念应用到你自己的项目中。

无论你是经验丰富的 PHP 开发者，还是刚刚起程，这本书都能为你提供宝贵的见解，以提升你的编码能力。

让我们开启这段精彩的冒险，掌握编写整洁、高效且易于阅读的 PHP 代码的艺术吧！

## 1. 为函数参数和返回值使用类型提示

通过为函数参数和返回值指定数据类型，来增强代码的可读性和可维护性。

以下代码演示了 PHP 函数中类型提示的使用：

### 良好的代码

```php
<?php
// 良好的示例：为参数和返回值使用类型提示

function calculateArea(float $length, float $width): float {
    // 计算矩形的面积
    $area = $length * $width;
    // 返回计算的面积
    return $area;
}

// 使用示例
$rectangleArea = calculateArea(5.5, 3.2);
echo "矩形的面积是：" . $rectangleArea;
?>
```

### 糟糕的代码

```php
<?php
// 糟糕的示例：没有使用类型提示

function calculateArea($length, $width) {
    // 计算矩形的面积
    $area = $length * $width;
    // 返回计算的面积
    return $area;
}

// 使用示例
$rectangleArea = calculateArea(5.5, 3.2);
echo "矩形的面积是：" . $rectangleArea;
?>
```

在良好的示例中，函数参数（`float $length`, `float $width`）和返回值（`: float`）都使用了类型提示。这清楚地表明该函数接收两个浮点数作为输入，并返回一个浮点数值。糟糕的示例缺乏类型提示，使得函数期望或返回什么类型的数据变得不再清晰。

> **Memo**: 类型提示在 PHP 5 中引入，并在后续版本中不断扩展，PHP 7 引入了返回类型声明。

## 2. 实现接口为类定义清晰的合约

使用接口为类建立清晰的合约，改进代码结构和可维护性。

以下代码演示了 PHP 中接口的实现：

### 良好的代码

```php
<?php
// 良好的示例：使用接口定义合约

interface ShapeInterface {
    public function calculateArea(): float;
    public function calculatePerimeter(): float;
}

class Rectangle implements ShapeInterface {
    private float $length;
    private float $width;

    public function __construct(float $length, float $width) {
        $this->length = $length;
        $this->width = $width;
    }

    public function calculateArea(): float {
        return $this->length * $this->width;
    }

    public function calculatePerimeter(): float {
        return 2 * ($this->length + $this->width);
    }
}

// 使用示例
$rectangle = new Rectangle(5.5, 3.2);
echo "矩形面积：" . $rectangle->calculateArea() . "\n";
echo "矩形周长：" . $rectangle->calculatePerimeter();
?>
```

### 糟糕的代码

```php
<?php
// 糟糕的示例：没有使用接口，结构不清晰

class Rectangle {
    private $length;
    private $width;

    public function __construct($length, $width) {
        $this->length = $length;
        $this->width = $width;
    }

    public function calculateArea() {
        return $this->length * $this->width;
    }

    public function calculatePerimeter() {
        return 2 * ($this->length + $this->width);
    }
}

// 使用示例
$rectangle = new Rectangle(5.5, 3.2);
echo "矩形面积：" . $rectangle->calculateArea() . "\n";
echo "矩形周长：" . $rectangle->calculatePerimeter();
?>
```

良好的示例使用接口（`ShapeInterface`）为形状类定义了清晰的合约。这确保了任何实现该接口的类必须提供 `calculateArea()` 和 `calculatePerimeter()` 方法。`Rectangle` 类随后实现了该接口，遵循了定义的合约。相比之下，糟糕的示例缺乏接口，使得形状类应该实现哪些方法变得不清晰。

> **Memo**: PHP 中的接口可以通过类使用 `implements` 关键字来实现，并且一个类可以实现多个接口。

## 3. 利用 Trait（特性）实现跨类代码复用

PHP 中的 Trait 允许水平代码复用，能够在不相关的类之间共享方法。

以下代码演示了如何使用 Trait 在多个类之间共享日志方法：

### 良好的代码

```php
// 定义一个用于日志的 trait
trait Logger {
    // 记录日志的方法
    public function log($message) {
        echo date('Y-m-d H:i:s') . ': ' . $message;
    }
}

// 使用 trait 的类
class User {
    use Logger;
    private $name;

    public function __construct($name) {
        $this->name = $name;
        $this->log("用户创建：{$this->name}");
    }

    public function getName() {
        return $this->name;
    }
}

// 使用 trait 的类
class Order {
    use Logger;
    private $orderId;

    public function __construct($orderId) {
        $this->orderId = $orderId;
        $this->log("订单创建：{$this->orderId}");
    }

    public function getOrderId() {
        return $this->orderId;
    }
}
```

### 糟糕的代码

```php
// 重复逻辑的类
class User {
    private $name;

    public function __construct($name) {
        $this->name = $name;
        echo date('Y-m-d H:i:s') . ': 用户创建：' . $this->name;
    }

    public function getName() {
        return $this->name;
    }

    public function log($message) {
        echo date('Y-m-d H:i:s') . ': ' . $message;
    }
}

// 另一个重复逻辑的类
class Order {
    private $orderId;

    public function __construct($orderId) {
        $this->orderId = $orderId;
        echo date('Y-m-d H:i:s') . ': 订单创建：' . $this->orderId;
    }

    public function getOrderId() {
        return $this->orderId;
    }

    public function log($message) {
        echo date('Y-m-d H:i:s') . ': ' . $message;
    }
}
```

良好的示例演示了使用 Trait 在多个类之间共享日志功能。这种方法促进了代码复用并减少了重复。`Logger` trait 包含一个单一的 `log()` 方法，任何包含 trait 的类都可以使用。

相比之下，糟糕的示例在 `User` 和 `Order` 类中重复了相同的逻辑。这会导致代码重复并增加了维护难度。

通过使用 Trait，我们可以保持代码 DRY（不要重复），并更容易地更新所有使用该 trait 的类的日志功能。

> **Memo**: Trait 在 PHP 5.4.0 中引入，为单继承语言（如 PHP）提供了一种代码复用机制。

## 4. 采用命名空间组织代码并避免命名冲突

PHP 中的命名空间有助于将代码组织成逻辑组，防止类、函数和常量之间的命名冲突。

以下代码演示了如何使用命名空间组织类并避免命名冲突：

### 良好的代码

```php
<?php
// 文件: User.php
namespace App\Models;

class User {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }
}
```

```php
// 文件: Order.php

namespace App\Models;

class Order {
    private $orderId;

    public function __construct($orderId) {
        $this->orderId = $orderId;
    }

    public function getOrderId() {
        return $this->orderId;
    }
}
```

```php
// 文件: UserController.php

namespace App\Controllers;

use App\Models\User;

class UserController {
    public function createUser($name) {
        $user = new User($name);
        return $user;
    }
}
```

```php
// 使用示例

use App\Models\User;
use App\Models\Order;
use App\Controllers\UserController;

$user = new User("John");
$order = new Order(1001);
$userController = new UserController();
```

### 糟糕的代码

```php
<?php

// All classes in global namespace
class User {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }
}

class Order {
    private $orderId;

    public function __construct($orderId) {
        $this->orderId = $orderId;
    }

    public function getOrderId() {
        return $this->orderId;
    }
}

class UserController {
    public function createUser($name) {
        $user = new User($name);
        return $user;
    }
}

// Usage
$user = new User("John");
$order = new Order(1001);
$userController = new UserController();
```

良好的代码示例演示了如何使用命名空间（`namespace`）将类组织成逻辑分组。`User` 和 `Order` 类被放在 `App\Models` 命名空间中，而 `UserController` 位于 `App\Controllers` 命名空间中。这种组织有助于避免命名冲突，并使代码结构更加清晰。

相比之下，糟糕的代码示例将所有类都放在全局命名空间中。这种方法在项目增长时会导致命名冲突，并更难以理解代码的逻辑结构。

使用命名空间可以实现更好的代码组织，提高可读性，并有助于防止大型项目中的命名冲突。它还允许在不同的上下文中使用相同的类名（例如，你可以同时拥有 `App\Models\User` 和 `App\Entities\User`）。

> **Memo**: 命名空间是在 PHP 5.3.0 中引入的，旨在解决你创建的代码与 PHP 内部类/函数/常量或第三方类/函数/常量之间的命名冲突问题。

## 5. 使用匿名函数（闭包）实现紧凑的内联功能

PHP 中的匿名函数提供了一种简洁的方式来创建内联的、单使用的函数。

以下代码演示了如何将匿名函数作为 `array_map()` 的回调函数：

### 良好的代码

```php
<?php
// 使用匿名函数对数组中的数字平方
$numbers = [1, 2, 3, 4, 5];

// 将匿名函数应用到每个元素
$squared = array_map(function($n) {
    return $n * $n;
}, $numbers);
// 输出: Array (0 => 1, 1 => 4, 2 => 9, 3 => 16, 4 => 25)
print_r($squared);
```

### 糟糕的代码

```php
<?php
// 没有使用匿名函数
$numbers = [1, 2, 3, 4, 5];

// 定义一个独立的函数
function square($n) {
    return $n * $n;
}

// 使用命名函数作为回调
$squared = array_map('square', $numbers);
// 输出: Array (0 => 1, 1 => 4, 2 => 9, 3 => 16, 4 => 25)
print_r($squared);
```

良好的代码示例直接在 `array_map()` 内部使用匿名函数，使代码更加紧凑且自包含。糟糕的代码定义了一个独立的函数，这可能会污染命名空间，并且对于简单操作来说可读性较低。

> **Memo**: 匿名函数是在 PHP 5.3 中引入的，也称为闭包（closures）。它们可以使用 `use` 关键字从父作用域中捕获变量。

## 6. 接口名称前缀加 'I'（例如 `ILogger`）

在接口名称前加上 `I` 是一种清晰区分接口与类的约定。以下代码演示了带有 `I` 前缀的接口用法：

### 良好的代码

```php
<?php
// 以 'I' 为前缀的接口
interface ILogger {
    public function log($message);
}

// 实现接口的类
class FileLogger implements ILogger {
    public function log($message) {
        // 实现细节
        file_put_contents('log.txt', $message, FILE_APPEND);
    }
}

// 使用
$logger = new FileLogger();
$logger->log('这是一条日志.');
```

### 糟糕的代码



```php
<?php
// 没有 'I' 的接口
interface Logger {
    public function log($message);
}

// 实现接口的类
class FileLogger implements Logger {
    public function log($message) {
        // 实现细节
        file_put_contents('log.txt', $message, FILE_APPEND);
    }
}

// 使用
$logger = new FileLogger();
$logger->log('这是一条日志.');
```

良好的代码示例使用 `ILogger` 作为接口名称，清晰地表明它是一个接口。这有助于开发者快速区分接口和具体类。坏代码在大型代码库可能会导致混淆。

> **Memo**: 在接口前加 `I` 在某些编程社区中很常见（例如有 C# 背景），但在 PHP 中并非通用标准。有些开发者认为这会增加代码冗余。

## 7. 布尔方法使用 'is' 前缀

为布尔方法添加 `is` 前缀以提高代码可读性。以下代码演示了在 PHP 中布尔方法使用 `is` 前缀：

#### Good Code

```php
class User {
    private $active;

    // 良好：方法名明确指示它返回布尔值
    public function isActive(): bool {
        return $this->active;
    }

    // 使用
    public function performAction() {
        if ($this->isActive()) {
            // 活跃用户执行操作
        }
    }
}
```

#### Bad Code

```php
class User {
    private $active;

    // 坏：方法名没有明确指示它返回布尔值
    public function active(): bool {
        return $this->active;
    }

    // 使用
    public function performAction() {
        if ($this->active()) {
            // 这是在检查用户是否活跃还是在做什么？
        }
    }
}
```

在良好的示例中，方法名 `isActive()` 明确指示它返回一个布尔值。这使得代码更易读且自解释。相反，坏示例使用 `active()`，可能会被误认为是执行操作的方法而不是返回状态。

## 8. 抽象类前缀加 'Abstract'

为抽象类使用 `Abstract` 前缀以增强代码清晰度。以下代码说明了 PHP 中抽象类使用 `Abstract` 前缀：

#### Good Code

```php
// 良好：类名明确指示它是一个抽象类
abstract class AbstractController {
    abstract public function index();

    public function render() {
        // 通用渲染逻辑
    }
}

class UserController extends AbstractController {
    public function index() {
        // 实现用户索引
    }
}
```

#### Bad Code

```php
// 坏：类名没有指示它是一个抽象类
abstract class Controller {
    abstract public function index();

    public function render() {
        // 通用渲染逻辑
    }
}

class UserController extends Controller {
    public function index() {
        // 实现用户索引
    }
}
```

在良好的示例中，在抽象类名前加上 'Abstract' 前缀（如 `AbstractController`）可以立即告知其他开发者这是一个抽象类。它在无需查看实现细节的情况下阐明了该类的性质。糟糕的示例没有提供这种即时的清晰度，可能会导致困惑。

> **Memo**
>
> 这种命名规范在许多框架和库中被广泛使用，包括像 Symfony 和 Laravel 等流行的 PHP 框架。

## 为实现能力的类使用 'able' 后缀

在实现特定能力或行为的类名后附加 'able'。

以下代码演示了在类命名中使用 'able' 后缀的方法，以提高类能力的可读性和对类理解的理解。

#### Good Code

```php
// 良好的示例：为实现能力的类使用 'able' 后缀

// 定义可排序行为的接口
interface Sortable {
    public function sort(): array;
}

// 实现 Sortable 接口的类
class SortableList implements Sortable {
    private $items = [];
    public function __construct(array $items) {
        $this->items = $items;
    }
    // sort 方法的实现
    public function sort(): array {
        sort($this->items);
        return $this->items;
    }
}

// 使用
$list = new SortableList([3, 1, 4, 1, 5, 9]);
$sortedList = $list->sort();
print_r($sortedList);
```

#### Bad Code

```php
// 糟糕的示例：为实现能力的类未使用 'able' 后缀

// 没有清晰命名规范的接口
interface DoSort {
    public function performSort(): array;
}

// 命名不清晰的类
class ListThing implements DoSort {
    private $stuff = [];
    public function __construct(array $stuff) {
        $this->stuff = $stuff;
    }
    // 不清晰的方法名
    public function performSort(): array {
        sort($this->stuff);
        return $this->stuff;
    }
}

// 使用
$thing = new ListThing([3, 1, 4, 1, 5, 9]);
$sortedStuff = $thing->performSort();
print_r($sortedStuff);
```

良好的示例在接口（`Sortable`）和实现类（`SortableList`）中都使用了 'able' 后缀。这种命名规范立即传达了类的能力。方法名也是清晰且一致的（`sort()`）。相比之下，糟糕示例使用了 `DoSort` 和 `ListThing` 等不清晰的名称，无法有效地交流接口的用途或能力。方法名 `performSort()` 也不如 `sort()` 直观。

> **Memo**
>
> 'able' 后缀通常用于各种语言的面向对象编程，而不是 PHP。它是命名规范的一部分，有助于开发者理解类的目的或能力。

## 在私有方法前加下划线

使用下划线前缀作为私有方法，在视觉上将其与公共方法区分开。以下代码示例演示了为私有方法使用下划线前缀以提高代码可读性和方法可见性。

#### Good Code

```php
// 良好的示例：为私有方法使用下划线前缀
class UserManager {
    private $users = [];
    public function addUser(string $username, string $email): void {
        if ($this->_isValidEmail($email)) {
            $this->users[] = [
                'username' => $username,
                'email' => $email
            ];
            $this->_notifyAdmin($username);
        }
    }
    // 带有下划线前缀的私有方法
    private function _isValidEmail(string $email): bool {
        return filter_var($email, FILTER_VALIDATE_EMAIL) !== false;
    }
    // 另一个带有下划线前缀的私有方法
    private function _notifyAdmin(string $username): void {
        // 模拟管理员通知
        echo "Admin notified about new user: $username";
    }
}
```

#### Bad Code

```php
// 糟糕示例：为私有方法未使用下划线前缀
class UserManager {
    private $users = [];
    public function addUser(string $username, string $email): void {
        if ($this->isValidEmail($email)) {
            $this->users[] = [
                'username' => $username,
                'email' => $email
            ];
            $this->notifyAdmin($username);
        }
    }
    // 未带下划线前缀的私有方法
    private function isValidEmail(string $email): bool {
        return filter_var($email, FILTER_VALIDATE_EMAIL) !== false;
    }
    // 另一个未带下划线前缀的私有方法
    private function notifyAdmin(string $username): void {
        // 模拟管理员通知
        echo "Admin notified about new user: $username";
    }
}
```

## 使用揭示意图的命名（例如，使用 `getByRole` 而不是 `getUsers`）

名称应当清晰地指示函数或变量的用途和行为。

在命名函数和变量时，选择能够揭示背后意图的名称至关重要。这有助于其他开发者快速理解代码预期的作用，而无需阅读整个实现过程。

#### Good Code



```php
<?php

// Good 示例：使用揭示意图的命名

// 根据角色获取用户的函数

function getUsersByRole($role) {
    // 假设 $db 是数据库连接
    global $db;
    $query = $db->prepare("SELECT \* FROM users WHERE role = :role");
    $query->bindParam(':role', $role);
    $query->execute();
    return $query->fetchAll();
}

// 获取所有管理员用户
$adminUsers = getUsersByRole('admin');
foreach ($adminUsers as $user) {
    echo $user['name'] . "<br>";
}
?>
```

<Bad Code>

```php
<?php

// 错误示例：使用不具描述性的名称

// 获取用户的函数
function getUsers($r) {
    // 假设 $db 是数据库连接
    global $db;
    $query = $db->prepare("SELECT \* FROM users WHERE role = :role");
    $query->bindParam(':role', $r);
    $query->execute();
    return $query->fetchAll();
}

// 获取所有管理员用户
$admins = getUsers('admin');
foreach ($admins as $u) {
    echo $u['name'] . "<br>";
}
?>
```

```

在良好的示例中，函数名 `getUsersByRole` 清晰地指示了函数根据角色检索用户。这使得代码更具可读性和维护性。在错误的示例中，函数名 `getUsers` 是模糊的，没有提供足够的关于函数作用的上下文，使得其他开发者难以理解其目的。

<Memo>
趣知识：揭示意图的命名是 SOLID 设计原则中的一个核心原则，特别是在单一职责原则 (SRP) 下。该原则规定，类或函数应该只有一个变更的原因，而清晰的命名通过使代码目的显化有助于实现这一点。
13

# 避免使用含义相似的名称

使用不同且有意义的变量名来提高代码的可读性。

以下代码演示了使用不同变量名的重要性：

< Good Code >
```php

// 良好的示例：使用不同且有意义的变量名

function calculateTotalPrice($basePrice, $taxRate, $shippingCost) {

    // 计算税额

    $taxAmount = $basePrice * ($taxRate / 100);

    // 计算包含税和运费的总价

    $totalPrice = $basePrice + $taxAmount + $shippingCost;

    return $totalPrice;

}

// 使用

$finalPrice = calculateTotalPrice(100, 8, 5);

echo "Total price: $" . $finalPrice;

```

<Bad Code>
```php

// 错误示例：使用含义不同的相似名称

function calc($price, $rate, $cost) {

    // 混淆的变量名

    $p = $price * ($rate / 100);

    $price = $price + $p + $cost;

    return $price;

}

// 使用

$price = calc(100, 8, 5);

echo "Price: $" . $price;

```
```

在良好的示例中，我们使用了如 `$basePrice`、`$taxRate` 和 `$shippingCost` 这样不同且有意义的变量名。这使得代码更易读且自解释。错误的示例使用了相似且模糊的名称，如 `$price` 和 `$p`，可能会导致混淆和潜在错误。

<Memo>

使用有意义的变量名是“自文档代码”原则的一部分，旨在使代码无需大量注释即可更容易理解。

14

# 一致地使用对立对（例如 start/stop，open/close）

对相反的操作保持命名一致性以增强代码清晰度。

以下代码说明了在方法中使用对立对的重要性：

< Good Code >

```php
// 良好的示例：使用一致的对立对
class FileHandler {
    private $fileHandle;
    public function openFile($filename) {
        $this->fileHandle = fopen($filename, 'r');
        echo "File opened successfully.\\n";
    }
    public function closeFile() {
        if ($this->fileHandle) {
            fclose($this->fileHandle);
            echo "File closed successfully.\\n";
        }
    }
    public function startProcessing() {
        echo "Starting file processing...\\n";
        // 处理逻辑
    }
    public function stopProcessing() {
        echo "Stopping file processing...\\n";
        // 清理逻辑
    }
}

// 使用
$handler = new FileHandler();
$handler->openFile('example.txt');
$handler->startProcessing();
$handler->stopProcessing();
```

<Bad Code>

```php
// 错误示例：不一致的命名
class FileHandler {
    private $fileHandle;
    public function initializeFile($filename) {
        $this->fileHandle = fopen($filename, 'r');
        echo "File initialized.\\n";
    }
    public function endFile() {
        if ($this->fileHandle) {
            fclose($this->fileHandle);
            echo "File ended.\\n";
        }
    }
    public function beginOperation() {
        echo "Beginning operation...\\n";
        // 处理逻辑
    }
    public function finish() {
        echo "Finishing operation...\\n";
        // 清理逻辑
    }
}

// 使用
$handler = new FileHandler();
$handler->initializeFile('example.txt');
$handler->beginOperation();
$handler->finish();
```

```

良好的示例使用了一致的对立对，如 `openFile`/`closeFile` 以及 `startProcessing`/`stopProcessing`。错误的示例使用了不一致的术语，如 `initializeFile`/`endFile` 以及 `beginOperation`/`finish`，这可能会导致混淆。





以下示例展示了如何在 PHP 中使用 `strict_types` ：

#### 良好的代码
```php

<?php

declare(strict_types=1);

// 带有类型提示和返回类型声明的函数

function addNumbers(int $a, int $b): int

{

    return $a + $b;

}

// 正确用法

$result = addNumbers(5, 10);

echo $result; // 输出: 15

// 这抛出一个 TypeError

// $result = addNumbers(5, "10");

```

#### 糟糕的代码
```php

<?php

// 没有使用 strict_types 声明

// 没有类型提示的函数

function addNumbers($a, $b)

{

    return $a + $b;

}

// 这可以工作，但可能会导致意想不到的结果

$result = addNumbers(5, "10");

echo $result; // 输出: 15

// 这也能“工作”，但可能不是初衷

$result = addNumbers("5", "10");

echo $result; // 输出: 15

```

在良好的示例中，我们在文件开头使用了 `declare(strict_types=1)`。这开启了严格类型检查。我们还对函数参数使用了类型提示，并声明了返回类型。这确保了只有整数可以传递给函数并返回。

在糟糕的示例中，如果没有严格类型，PHP 将尝试将值转换为相应的类型。这会导致意外的行为，就像传递字符串 `"10"` 而不是整数 `10` 一样。

> **备注**
> PHP 7.0 引入了严格类型提供了一种开启更严格类型检查的方法并提高了代码的可靠性。(17)

# 实现魔术方法以获得更简洁语法

使用 `__toString`、`__get` 和 `__set` 魔术方法来创建更直观、更具读性的代码。

以下代码演示了 `Person` 类中魔术方法的使用：

#### 良好的代码
```php

class Person {

    private $data = [];

    // 将对象转换为字符串的魔术方法

    public function __toString() {

        return $this->data['name'] ?? 'Unnamed Person';

    }

    // 获取属性的魔术方法

    public function __get($property) {

        return $this->data[$property] ?? null;

    }

    // 设置属性的魔术方法

    public function __set($property, $value) {

        $this->data[$property] = $value;

    }

}

// 使用

$person = new Person();

$person->name = "John Doe";  // 使用 __set

$person->age = 30;             // 使用 __set

echo $person;               // 使用 __toString

echo $person->name;         // 使用 __get

```

#### 糟糕的代码
```php

class Person {

    public $name;

    public $age;

    public function getName() {

        return $this->name;

    }

    public function setName($name) {

        $this->name = $name;

    }

    public function getAge() {

        return $this->age;

    }

    public function setAge($age) {

        $this->age = $age;

    }

    public function getPersonInfo() {

        return $this->name ?? 'Unnamed Person';

    }

}

// 使用

$person = new Person();

$person->setName("John Doe");

$person->setAge(30);

echo $person->getPersonInfo();

echo $person->getName();

```

良好的代码示例使用了魔术方法（`__toString`、`__get`、`__set`）来创建一个更直观、更灵活的接口。这允许动态属性的访问和设置，以及方便的字符串转换。糟糕的代码示例使用了传统的 getter 和 setter，这可能导致代码更加冗长且灵活性更低。

> **备注**
> PHP 中的魔术方法提供了一种开启更严格类型检查的方法并提高了代码的可靠性。(18)

# 实现魔术方法以获得更简洁语法

使用 `__toString`、`__get` 和 `__set` 魔术方法来创建更直观、更具读性的代码。

以下代码演示了 `Person` 类中魔术方法的使用：
...
*(注：由于原文此处似乎出现了重复或乱码，根据指令“不要重复输出原文”，此处已根据前文逻辑处理。由于提供的原文后半部分存在大量重复和无意义片段，已根据核心核心逻辑进行翻译。)*




```php

// 使用数组进行基于对象的存储

$storage = array();

$obj1 = new stdClass();

$obj2 = new stdClass();

$storage[spl_object_hash($obj1)] = 'data for obj1';

$storage[spl_object_hash($obj2)] = 'data for obj2';

// 检查对象是否存在于存储中

var_dump(isset($storage[spl_object_hash($obj1)])); // true

```

良好的示例演示了 SPL 数据结构（`SplFixedArray`、`SplQueue` 和 `SplObjectStorage`）的使用，这些结构针对其特定用途进行了优化。它们为预期的用例例提供了更好的性能和更合适的方法。糟糕的示例使用普通数组来完成相同的任务，这的效率可能较低，并且需要更多手动工作来维护预期的行为。

> **备忘**
> 标准 PHP 库 (SPL) 在 PHP 5.0.0 中引入，提供了一组用于解决常见问题的接口和类。
> 21

# 注释“为什么这样做”，而不是“做了什么”

解释代码背后的逻辑，而不仅仅是描述它的动作。

以下代码演示了如何在 PHP 中正确地注释“为什么”而不是“什么”：

**良好的代码**
```php

// 我们需要确保在访问敏感数据之前用户已登录

if (!$user->isLoggedIn()) {

    // 如果未身份验证，则重定向到登录页面

    header('Location: /login.php');

    exit;

}

// 获取用户的账户余额

$balance = $user->getAccountBalance();

// 检查余额是否低于最低阈值

if ($balance < MINIMUM_BALANCE) {

    // 通知用户余额低以防止透支

    sendLowBalanceNotification($user);

}

```

**糟糕的代码**
```php

// 检查用户是否已登录

if (!$user->isLoggedIn()) {

    // 重定向到登录页面

    header('Location: /login.php');

    exit;

}

// 获取余额

$balance = $user->getAccountBalance();

// 如果余额低

if ($balance < MINIMUM_BALANCE) {

    // 发送通知

    sendLowBalanceNotification($user);

}

```

良好的代码示例为采取每个操作的原因提供了清晰的解释，例如在访问敏感数据之前确保身份验证，以及通知用户余额低以防止透支。糟糕的代码示例仅描述了代码做了什么，而没有解释其背后的逻辑，这使得其他开发者难以理解每一步的目的和重要性。

> **备忘**
> 解释“为什么”的注释通常被称为“意图注释”，可以显著提高代码的可维护性。
> 22

# 为类、方法和属性使用 PHPDoc 块

利用 PHPDoc 块为类、方法和属性提供全面的文档。

以下示例演示了在 PHP 类中正确使用 PHPDoc 块的方法：

**良好的代码**
```php

/**

 * 代表系统中的用户账户。

 *

 * 此类处理用户相关的操作，如

 * 身份验证、配置管理和账户余额。

 */

class User

{

    /**

     * 用户当前的账户余额。

     *

     * @var float

     */

    private $balance;

    /**

     * 使用给定的凭据验证用户。

     *

     * @param string $username 用户名

     * @param string $password 用户密码

     * @return bool 如果身份验证成功为真，否则为假
```



# 解释临时解决方案或黑科技（hacks）

提供清晰的注释来解释你代码中的任何临时解决方案或黑科技。

当你在 PHP 代码中使用临时解决方案或黑科技时，添加注释来解释其必要性以及其工作原理至关重要。

**良好的代码**

```php
<?php

// 针对 PHP bug #23 的临时解决方案：array_merge_recursive() 不保留键
// 此黑科技通过使用自定义函数确保键被保留
function array_merge_distinct(array &$array1, array &$array2) {
    $merged = $array1;
    foreach ($array2 as $key => &$value) {
        if (is_array($value) && isset($merged[$key]) && is_array($merged[$key])) {
            $merged[$key] = array_merge_distinct($merged[$key], $value);
        } else {
            $merged[$key] = $value;
        }
    }
}
```

**糟糕的代码**

```php
<?php
function array_merge_distinct(array &$array1, array &$array2) {
    $merged = $array1;
    foreach ($array2 as $key => &$value) {
        if (is_array($value) && isset($merged[$key]) && is_array($merged[$key])) {
            $merged[$key] = array_merge_distinct($merged[$key], $value);
        } else {
            $merged[$key] = $value;
        }
    }
}
?>
```

*(注：由于原文代码块在示例中似乎存在排版错乱，翻译时保持了逻辑结构并修正了可读性)*

**纠正上述代码逻辑的翻译呈现：**

```php
<?php
// 针对 PHP bug #23 的临时解决方案：array_merge_recursive() 不保留键
// 此黑科技通过使用自定义函数确保键被保留
function array_merge_distinct(array &$array1, array &$array2) {
    $merged = $array1;
    foreach ($array2 as $key => &$value) {
        if (is_array($value) && isset($merged[$key]) && is_array($merged[$key])) {
            $merged[$key] = array_merge_distinct($merged[$key], $value);
        } else {
            $merged[$key] = $value;
        }
    }
    return $merged;
}
?>
```

良好的示例清晰地解释了临时解决方案的原因以及它是如何解决问题的。这使得代码更易于理解。糟糕的示例缺乏注释，导致临时解决方案的目的和功能不明确。

> **备忘**
> PHP 拥有很长的 bug 历史，开发者经常需要实现临时解决方案。记录这些临时解决方案有助于维护代码质量。

# 解释非直观的优化

添加清晰的注释来解释代码中非显而易见的优化。

当你实现并非显而易见的优化时，对它们进行注释是非常重要的，以帮助其他开发者理解你的选择。

**良好的代码**

```php
<?php
// 优化：使用 isset() 代替 strlen() 检查字符串
// isset() 更快，因为它是一个语言构造且不会产生函数调用开销
function isEmptyString($str) {
    return !isset($str[0]);
}
?>
```

**糟糕的代码**

```php
<?php
function isEmptyString($str) {
    return !isset($str[0]);
}
?>
```

良好的示例通过注释解释了为什么使用 `isset()` 代替 `strlen()`，为优化提供了背景。这有助于其他开发者理解性能优势。糟糕的示例缺乏注释，使得优化变得不直观且难以理解。

> **备忘**
> PHP 的 `isset()` 函数常用于性能优化，因为它是一个语言构造，运行速度比许多内置函数快。

# 使用 TODO 注释标记未来的改进或已知问题

TODO 注释有助于跟踪代码中的未来改进或已知问题。

在 PHP 代码中使用 TODO 注释是一种简单而有效的方法，可以提醒自己或告知他人需要进一步处理或存在已知区域。

**良好的代码**

```php
<?php
// TODO: 重构此函数以提高性能
function calculateSum($numbers) {
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}

// TODO: 处理空数组的边界情况
$result = calculateSum([1, 2, 3, 4, 5]);
echo $result;
?>
```

**糟糕的代码**

```php
<?php
function calculateSum($numbers) {
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}
$result = calculateSum([1, 2, 3, 4, 5]);
echo $result;
?>
```

在良好的示例中，TODO 注释清晰地指示了需要改进或额外处理的区域。这使得开发者更容易理解未来需要解决的问题。坏的示例缺少这些注释，使得跟踪必要的更改或改进变得更加困难。

> **备忘**
> “TODO”术语在许多编程语言和 IDE 中常用，用于标记需要完成的任务。某些 IDE 甚至提供了特殊功能来列出项目中所有的 `TODO` 注释。

# 保持注释随代码更改更新

确保注释准确反映代码的当前状态。

保持注释随代码更改更新对于维护代码的可读性以及防止开发者之间的混淆至关重要。

**良好的代码**

```php
<?php
// 此函数计算数字数组之和
function calculateSum($numbers) {
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}
// 计算给定数组之和
$result = calculateSum([1, 2, 3, 4, 5]);
echo $result;
?>
```

**糟糕的代码**

```php
<?php
// 此函数乘以数组中的所有数字
function calculateSum($numbers) {
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}
// 计算给定数组之和
$result = calculateSum([1, 2, 3, 4, 5]);
echo $result;
?>
```

在良好的示例中，注释准确地描述了函数及其目的，使得其他开发者更容易理解代码。在坏的示例中，注释错误地陈述函数是乘以数字，这可能会导致混淆和错误。

> **备忘**
> 在软件开发中持续更新注释是一种最佳实践。某些团队甚至将注释更新作为代码审查过程的一部分，以确保准确性和清晰度。

# 删除注释掉的代码

删除未使用的代码而不是将其注释掉，以提高代码的可读性和维护性。

以下示例演示了如何处理未使用的代码：

**良好的代码**

```php
<?php
function calculateTotal($price, $quantity) {
    $total = $price * $quantity;
    $tax = $total * 0.1;
    return $total + $tax;
}
$result = calculateTotal(10, 5);
echo "Total: $" . number_format($result, 2);
?>
```

**糟糕的代码**

```php
<?php
function calculateTotal($price, $quantity) {
    $total = $price * $quantity;
    $tax = $total * 0.1;
    return $total + $tax;
    // 旧的计算方法
    // $oldTotal = $price * $quantity;
    // return $total;
}
$result = calculateTotal(10, 5);
echo "Total: $" . number_format($result, 2);
// echo "Old total: $" . number_format($result, 2);
?>
```

良好的代码示例展示了清晰的实现，没有任何注释掉的代码。坏的代码示例包含了不必要的注释代码，这会弄乱函数并降低可读性。与其将旧代码作为注释保留，不如将其完全删除并依赖版本控制。

> **备忘**
> 像 Git 这样的版本控制系统允许开发者访问之前的版本，因此没有将旧代码作为注释保留。

# 在注释中使用清晰简洁的语言

编写简短、信息量丰富且易于理解的注释以增强理解。

以下示例展示了如何编写有效的注释：

**良好的代码**

```php
<?php
// 计算包含税的最终价格
function calculateFinalPrice($basePrice, $taxRate) {
    // 对基础价格应用税率
    $taxAmount = $basePrice * $taxRate;
    $finalPrice = $basePrice + $taxAmount;
    return $finalPrice;
}
// 使用示例
$basePrice = 100;
$taxRate = 0.08;
$result = calculateFinalPrice($basePrice, $taxRate);
echo "Final price: $" . number_format($result, 2);
?>
```

**糟糕的代码**

```php
<?php
// 此函数将基础价格和税率作为输入
// 它将通过在基础价格上加上税额来计算最终价格
// 税额是通过基础价格乘以税率计算的
function calculateFinalPrice($basePrice, $taxRate) {
    // 在这里我们计算税额
    $taxAmount = $basePrice * $taxRate;
    // 现在我们将税额加到基础价格上以获得最终价格
    $finalPrice = $basePrice + $taxAmount;
    // 最后，我们返回最终价格
    return $finalPrice;
}
// 现在我们将使用该函数
$basePrice = 100; // 基础价格
$taxRate = 0.08; // 税率 (8%)
$result = calculateFinalPrice($basePrice, $taxRate);
echo "Final price: $" . number_format($result, 2); // 输出结果
?>
```

良好的代码示例使用了简洁且有信息的注释，没有冗余。坏的示例包含了过度冗长的注释，使得代码难以阅读。良好的注释应该解释“为什么”这样做，而不是“在做什么”，代码本身应该是自解释的。

> **备忘**
> “自说明代码”的概念表明，良好的代码应该是清晰的，减少对解释性注释的需求。

# 避免重复代码的注释

编写自解释的代码，避免编写仅仅复述代码行为的注释。

以下示例演示了如何在 PHP 代码中避免冗余注释：

**良好的代码**

```php
function calculateTotalPrice($price, $quantity) {
    $subtotal = $price * $quantity;
    $tax = $subtotal * 0.1;
    return $subtotal + $tax;
}
```

**糟糕的代码**

```php
// 计算总价的函数
function calculateTotalPrice($price, $quantity) {
    // 计算小计
    $subtotal = $price * $quantity;
    // 计算税费
    $tax = $subtotal * 0.1;
    // 返回总价
    return $subtotal + $tax;
}
```

良好的代码示例是自解释的，不需要注释。函数名和变量清晰地传达了其目的。坏的代码示例包含了仅仅重复代码行为的冗余注释，没有提供额外的价值。

> **备忘**
> Robert C. Martin 的著作《清洁之道》强调，良好的代码应该是自说明的，减少对解释性注释的需求。

# 谨慎使用内联注释，仅在必要时

将内联注释用于解释复杂的逻辑或非显见的决策。

以下示例展示了 PHP 中适当和过度的内联注释：

**良好的代码**

```php
function processUserData($userData) {
    $cleanedData = array_map('trim', $userData);
    // 使用正则验证邮箱格式
    if (!preg_match('/[\w-]+@[\w-]+\.\w+$/', $cleanedData['email'])) {
        throw new InvalidArgumentException('Invalid email format');
    }
    return $cleanedData;
}
```

**糟糕的代码**

```php
function processUserData($userData) {
    // 从所有用户数据中去除空白
    $cleanedData = array_map('trim', $userData);
    // 检查邮箱是否有效
    if (!preg_match('/[\w-]+@[\w-]+\.\w+$/', $cleanedData['email'])) {
        // 如果邮箱无效，则抛出异常
        throw new InvalidArgumentException('Invalid email format');
    }
    // 返回清理后的数据
    return $cleanedData;
}
```



在良好的代码示例中，内联注释仅用于解释复杂的正则表达式模式的目的。糟糕的代码示例过度使用注释，解释了如修剪空白和返回数据等显而易见的操作。这些注释增加了不必要的冗余，并没有提高代码的可理解性。

> **自文档代码**的概念认为，良好的代码应该是易读易理解的，不需要大量的注释，依赖清晰的命名规范和逻辑结构。

# 使用依赖注入提高可测试性

依赖注入通过解耦组件和允许更容易地模拟（mock）依赖来提高代码的可测试性。

以下代码演示了 `UserService` 类中的依赖注入：

## 良好的代码

```php
// 良好的代码：使用依赖注入

class UserService {

    private $database;

    // 构造函数注入

    public function __construct(DatabaseInterface $database) {

        $this->database = $database;

    }

    public function getUserById($id) {

        // 使用注入的数据库对象

        return $this->database->query("SELECT * FROM users WHERE id = ?", [$id]);

    }

}

// 使用示例

$database = new MySQLDatabase();

$userService = new UserService($database);

$user = $userService->getUserById(1);
```

## 糟糕的代码

```php
// 糟糕的代码：紧耦合，难以测试

class UserService {

    private $database;

    public function __construct() {

        // 直接实例化，紧耦合

        $this->database = new MySQLDatabase();

    }

    public function getUserById($id) {

        return $this->database->query("SELECT * FROM users WHERE id = ?", [$id]);

    }

}

// 使用示例

$userService = new UserService();

$user = $userService->getUserById(1);
```

良好的代码示例通过在构造函数中接受 `DatabaseInterface` 来使用依赖注入。这使得测试变得更容易，因为你可以注入一个模拟数据库对象。糟糕的代码直接实例化 `database`，导致其难以进行隔离测试或更换实现类。

> 依赖注入是 SOLID 原则之一，具体来说是依赖倒置原则 (`DIP`)。

# 使用空合并运算符 (??) 进行简洁的空检查

空合并运算符 (`??`) 提供了一种处理空检查和默认值的简洁方式。

以下代码演示了空合并运算符的用法：

## 良好的代码

```php
// 良好的代码：使用空合并运算符

function getUserName($user) {

    // 如果设置了用户名则返回用户名，否则返回 'Guest'

    return $user['name'] ?? 'Guest';

}

// 使用示例

$user1 = ['name' => 'John'];

$user2 = [];

echo getUserName($user1); // 输出: John

echo getUserName($user2); // 输出: Guest
```

## 糟糕的代码

```php
// 糟糕的代码：冗长的空检查

function getUserName($user) {

    // 检查 'name'是否已设置且不为空，否则返回 'Guest'

    if (isset($user['name']) && $user['name'] !== null) {

        return $user['name'];

    } else {

        return 'Guest';

    }

}

// 使用示例

$user1 = ['name' => 'John'];

$user2 = [];

echo getUserName($user1); // 输出: John

echo getUserName($user2); // 输出: Guest
```

良好的代码使用空合并运算符 (`??`) 来简洁地检查 `$user['name']` 是否设置且不为空。糟糕的代码使用了冗长的 `if-else` 块来实现相同的结果。

> 空合并运算符 (`??`) 是在 PHP 7.0 中引入的。

# 为调用对象实现 `invoke()` 方法

`invoke()` 方法允许对象像函数一样被调用。

PHP 中的 `invoke()` 方法让对象变得可用。

## 良好的代码

```php
<?php

class Greeter {

    private $greeting;

    public function __construct($greeting) {

        $this->greeting = $greeting;

    }

    public function __invoke($name) {

        return $this->greeting . ', ' . $name;

    }

}

$greeter = new Greeter('Hello');

echo $greeter('World'); // 输出: Hello, World
```

## 糟糕的代码

```php
<?php

class Greeter {

    private $greeting;

    public function __construct($greeting) {

        $this->greeting = $greeting;

    }

    public function greet($name) {

        return $this->greeting . ', ' . $name;

    }

}

$greeter = new Greeter('Hello');

echo $greeter->greet('World'); // 输出: Hello, World
```

良好的代码使用 `__invoke()` 方法允许对象像函数一样被调用。糟糕的代码使用了具名的 `greet()` 方法，其灵活性较低。

> `__invoke()` 方法是在 PHP 5.5 中引入的。

# 使用 `yield from` 处理嵌套生成器

`yield from` 表达式简化了对嵌套生成器的操作。

`yield from` 允许将产生值的任务委托给另一个生成器，使代码更整洁。

## 良好的代码

```php
<?php

function innerGenerator() {

    yield 1;

    yield 2;

    yield 3;

}

function outerGenerator() {

    yield from innerGenerator();

}

foreach (outerGenerator() as $value) {

    echo $value . ' ';

} // 输出: 1 2 3 
```

## 糟糕的代码

```php
<?php

function innerGenerator() {

    yield 1;

    yield 2;

    yield 3;

}

function outerGenerator() {

    foreach (innerGenerator() as $value) {

        yield $value;

    }

}

foreach (outerGenerator() as $value) {

    echo $value . ' ';

} // 输出: 1 2 3 
```

良好的示例使用 `yield from` 将过程委托给 `innerGenerator()`。糟糕的示例使用 `foreach` 循环来手动产生值，这显得更加冗长。

> `yield from` 表达式是在 PHP 7.0 中引入的，用于简化嵌套的可迭代对象处理。

# 使用数组解包合并数组

在 PHP 7.4+ 中使用扩展运算符 (`...`) 高效地合并数组。

以下代码演示了如何使用数组解包合并数组：

## 良好的代码

```php
<?php

$fruits = ['apple', 'banana'];

$vegetables = ['carrot', 'tomato'];

// 使用扩展运算符合并数组

$combined = [...$fruits, ...$vegetables];

print_r($combined);

?>
```

## 糟糕的代码

```php
<?php

$fruits = ['apple', 'banana'];

$vegetables = ['carrot', 'tomato'];

// 使用 array_merge 合并数组

$combined = array_merge($fruits, $vegetables);

print_r($combined);

?>
```

良好的代码示例使用扩展运算符 (`...`) 将数组解包并合并到一个新数组。这种方法更具可读性且简洁。糟糕的代码使用了传统的 `array_merge()` 函数，它不够直观且需要输入更多的代码。

展开运算符 `(...)` 在 PHP `7.4` 中引入，它不仅可以用于数组，还可以用于函数调用中的参数解包。

# 使用一致的缩进（空格或制表符）

在整个 PHP 代码中保持一致的缩进，以提高可读性。

以下示例展示了 PHP 代码中一致缩进的重要性：

## 良好的代码

```php
<?php

// 良好的实践：一致的缩进（使用 4 个空格）

function calculateTotal($items) {

    $total = 0;

    foreach ($items as $item) {

        $price = $item['price'];

        $quantity = $item['quantity'];

        $total += $price * $quantity;

    }

    return $total;

}

$cart = [

    ['name' => 'T-shirt', 'price' => 15, 'quantity' => 2],

    ['name' => 'Jeans', 'price' => 50, 'quantity' => 1]

];

$totalCost = calculateTotal($cart);

echo "Total cost: $" . $totalCost;

?>
```

## 糟糕的代码

```php
<?php

// 糟糕的实践：不一致的缩进

function calculateTotal($items) {

$total = 0;

    foreach ($items as $item) {

 $price = $item['price'];

        $quantity = $item['quantity'];

    $total += $price * $quantity;

    }

return $total;

}

$cart = [

['name' => 'T-shirt', 'price' => 15, 'quantity' => 2],

    ['name' => 'Jeans', 'price' => 50, 'quantity' => 1]

];

$totalCost = calculateTotal($cart);

echo "Total cost: $" . $totalCost;

?>
```

良好的代码示例在整个脚本中使用一致的缩进（4 个空格）。这使得代码结构清晰且易于阅读。糟糕的代码示例缩进不一致，混合了不同数量的空格，甚至没有缩进。这使得代码更难以阅读和理解，特别是对于可能参与同一项目的其他开发者而言。一致的缩进有助于视觉化代码结构、嵌套块，并提高整体代码的可维护性。

> PHP-FIG（框架互操作小组）建议在 `PSR-12` 编码风格指南中使用 4 个空格或 1 个 tab 作为缩进，但强调项目内部的一致性。

# 限制行长度以提高可读性（例如 80-120 个字符）

将行长度保持在 80-120 个字符内使代码更容易阅读和维护。

过长的代码行很难阅读和理解。限制行长度有助于保持可读性，并让开发者更容易在代码中导航。

## 良好的代码

```php
<?php

// 限制行长的良好示例

function calculateTotalPrice($price, $taxRate, $discount) {

    $taxAmount = $price * $taxRate;

    $discountAmount = $price * $discount;

    $totalPrice = $price + $taxAmount - $discountAmount;

    return $totalPrice;

}

?>
```

## 糟糕的代码

```php
<?php

// 长行的糟糕示例

function calculateTotalPrice($price, $taxRate, $discount) { $taxAmount = $price * $taxRate; $discountAmount = $price * $discount; $totalPrice = $price + $taxAmount - $discountAmount; return $totalPrice; }

?>
```

在良好的示例中，代码被拆分成多行，使其更容易阅读和理解。在糟糕的示例中，整个函数被写在一行中，这使得难以追踪和维护。

> 80 个字符的限制源于早期计算机使用的打孔卡宽度。许多现代编码标准仍然为了可读性建议采用这一限制。

# 使用空行分隔代码的逻辑部分

空行有助于在视觉上区分不同的代码部分，使其更容易阅读和理解。

使用空行分隔代码的逻辑部分通过在代码的不同部分之间提供视觉间断，提高了可读性，使户更容易跟踪程序的流程。

## 良好的代码

```php
<?php

// 使用空行分隔逻辑部分的良好示例

function calculateTotalPrice($price, $taxRate, $discount) {

    // 计算税额

    $taxAmount = $price * $taxRate;

    // 计算折扣金额

    $discountAmount = $price * $discount;

    // 计算总价

    $totalPrice = $price + $taxAmount - $discountAmount;

}

?>
```

## 糟糕的代码

```php
<?php

// 没有空行的糟糕示例

function calculateTotalPrice($price, $taxRate, $discount) {

    $taxAmount = $price * $taxRate;

    $discountAmount = $price * $discount;

    $totalPrice = $price + $taxAmount - $discountAmount;

    return $totalPrice;

}

?>
```

良好的示例使用空行分隔逻辑部分，使得流程更容易追踪。糟糕的示例缺乏这些间断，使得代码更难以解析。

# 在声明变量时对齐赋值运算符

对齐赋值运算符有助于快速发现不一致之处。

在声明变量时，对齐运算符可以提高可读性和可维护性。

## 良好的代码

```php
<?php

// 对齐赋值运算符的良好示例

$firstName = "John";

$lastName  = "Doe";

$age       = 30;

$occupation = "Engineer";

?>
```

## 糟糕的代码

```php
<?php

// 运算符未对齐的糟糕示例

$firstName = "John";

$lastName = "Doe";

$age = 30;

$occupation = "Engineer";

?>
```

在良好的示例中，对齐有助于扫描变量和值。在糟糕的示例中，未对齐的运算符使得代码看起来混乱。

# 使用括号明确运算符优先级

使用括号明确运算符优先级可以确保代码按照预期运行，并且更容易理解。

运算符优先级有时会令人困惑。使用括号可以明确表示操作顺序。

## 良好的代码

```php
<?php

// 使用括号明确优先级的良好示例

$result = (2 + 3) * 4; // 明确表示 2 + 3 应该先计算

echo $result; // 输出 20

?>
```

## 糟糕的代码

```php
<?php
```



// 没有括号，导致潜在困惑的糟糕示例

```php
$result = 2 + 3 * 4; // 没有括号，先计算乘法
echo $result; // 输出 14
```

在良好的示例中，使用了括号来明确表示在执行乘法之前执行加法。在糟糕的示例中，缺少括号会导致误解。

## 41. 使用早期返回减少嵌套

在函数中使用早期返回（`early returns`）有助于减少嵌套层，使你的代码更易读且易于维护。

早期返回允许你在满足条件时立即退出函数，避免深层嵌套并使代码流程更加清晰。

### 良好的代码

```php
function processOrder($order) {
    // 检查订单是否有效
    if (!$order->isValid()) {
        return 'Invalid order';
    }
    // 检查订单是否已经处理
    if ($order->isProcessed()) {
        return 'Order already processed';
    }
    // 处理订单
    $order->process();
    return 'Order processed successfully';
}
```

### 糟糕的代码

```php
function processOrder($order) {
    // 检查订单是否有效
    if ($order->isValid()) {
        // 检查订单是否已经处理
        if (!$order->isProcessed()) {
            // 处理订单
            $order->process();
            return 'Order processed successfully';
        } else {
            return 'Order already processed';
        }
    } else {
        return 'Invalid order';
    }
}
```

在良好的示例中，使用了**早期返回（`early returns`）**来立即处理无效或已处理的订单，减少了对嵌套 `if` 语句的需求。这使得 `processOrder` 更容易阅读和理解。在糟糕的示例中，嵌套的 `if` 语句使得代码更难追踪。

> **Memo**
> 早期返回是许多编程语言中的常见做法，而不只是 PHP。它们有助于提高代码的可读性并降低复杂度。

## 42. 尽可能优先使用 foreach 循环而非 for 循环

在遍历数组或集合时，使用 `foreach` 循环代替 `for` 循环可以使你的代码更具可读性且不易出错。

`foreach` 循环专门为遍历数组和集合设计，与 `for` 循环相比，它提供了更简单、更直观的语法。

### 良好的代码

```php
$items = ['apple', 'banana', 'cherry'];

// 使用 foreach 循环
foreach ($items as $item) {
    echo $item . "\n"; // 输出每个项目
}
```

### 糟糕的代码

```php
$items = ['apple', 'banana', 'cherry'];

// 使用 for 循环
for ($i = 0; $i < count($items); $i++) {
    echo $items[$i] . "\n"; // 输出每个项目
}
```

在良好的示例中，`foreach` 循环直接遍历数组中的每个项目，使得代码更简洁且易读。在糟糕的示例中，`for` 循环需要管理循环计数器并调用 `count()` 函数，这更容易出错且可读性较差。

> **Memo**
> `foreach` 循环不仅更具读性，在某些情况下也更高效，因为避免了在循环条件中重复调用 `count()` 函数。

## 43. 对同一变量的多个条件使用 switch 语句

在处理单个变量的多个条件时，`switch` 语句可以提高代码的可读性。

以下代码演示了如何使用 `switch` 语句处理用户角色的不同情况：

### 良好的代码

```php
// 根据角色确定用户权限
function getUserPermissions($role) {
    switch ($role) {
        case 'admin':
            // 管理员拥有完全访问
            return ['read', 'write', 'delete', 'manage'];
        case 'editor':
            // 编辑员可以读、写、删
            return ['read', 'write', 'delete'];
        case 'author':
            // 作者可以读、写
            return ['read', 'write'];
        case 'subscriber':
            // 订阅者只能读
            return ['read'];
        default:
            // 未知角色的默认值
            return ['none'];
    }
}

// 使用
$userRole = 'editor';
$permissions = getUserPermissions($userRole);
print_r($permissions);
```

### 糟糕的代码

```php
// 根据角色确定用户权限
function getUserPermissions($role) {
    if ($role == 'admin') {
        return ['read', 'write', 'delete', 'manage'];
    } elseif ($role == 'editor') {
        return ['read', 'write', 'delete'];
    } elseif ($role == 'author') {
        return ['read', 'write'];
    } elseif ($role == 'subscriber') {
        return ['read'];
    } else {
        return ['none'];
    }
}

// 使用
$userRole = 'editor';
$permissions = getUserPermissions($userRole);
print_r($permissions);
```

良好的示例使用了 `switch` 语句，在处理单个变量的多个条件时，它更具可读性易于维护。每个 `case` 都有清晰的定义，使得添加或修改角色变得更容易。糟糕的示例使用了一系列 `if-elseif` 语句，这可能会变得难以阅读。

> **Memo**
> PHP 中的 `switch` 语句支持“穿透”行为，如果省略了 `break` 语句，执行将继续到下一个 case。这在某些场景下有用，但应该谨慎使用。

## 44. 使用守卫语句（guard clauses）处理边界情况

守卫语句通过在函数早期处理边界情况来提高代码的可读性，减少嵌套和复杂度。

以下代码演示了如何使用守卫语句在函数中验证输入：

### 良好的代码

```php
// 计算购买金额的折扣
function calculateDiscount($purchaseAmount) {
    // 守护语句：检查无效输入
    if (!is_numeric($purchaseAmount) || $purchaseAmount < 0) {
        throw new InvalidArgumentException("Invalid purchase amount");
    }

    // 守护语句：小额购买不予折扣
    if ($purchaseAmount < 100) {
        return 0;
    }

    // 计算折扣
    if ($purchaseAmount >= 500) {
        return $purchaseAmount * 0.1; // 10% 折
    } else {
        return $purchaseAmount * 0.05; // 5% 折
    }
}

// 使用
try {
    $discount = calculateDiscount(250);
    echo "Discount: $" . number_format($discount, 2);
} catch (InvalidArgumentException $e) {
    echo "Error: " . $e->getMessage();
}
```

### 糟糕的代码

```php
// 计算购买金额的折扣
function calculateDiscount($purchaseAmount) {
    if (is_numeric($purchaseAmount) && $purchaseAmount >= 0) {
        if ($purchaseAmount >= 100) {
            if ($purchaseAmount >= 500) {
                return $purchaseAmount * 0.1; // 10% 折
            } else {
                return $purchaseAmount * 0.05; // 5% 折
            }
        } else {
            return 0;
        }
    } else {
        throw new InvalidArgumentException("Invalid purchase amount");
    }
}

// 使用
try {
    $discount = calculateDiscount(250);
    echo "Discount: $" . number_format($discount, 2);
} catch (InvalidArgumentException $e) {
    echo "Error: " . $e->getMessage();
}
```

良好的代码示例使用了守卫语句来早期处理边界情况。这种方法减少了嵌套并使代码更易读。糟糕的代码使用了嵌套的 `if` 语句，随着条件的增加，它会变得更难以追踪和维护。

> **Memo**
> 守卫语句是“早期返回”模式的核心原则，可以显著提高代码的可读性并减少阅读代码开发者的认知负担。

## 45. 使用三元运算符进行简单的条件赋值

使用三元运算符简化条件赋值以提高可读性。

以下代码演示了如何使用三元运算符进行简单的条件赋值：

### 良好的代码

```php
// 良好的代码：使用三元运算符进行简单的条件赋值
$isAdult = ($age >= 18) ? true : false;

// 解释：
// 如果 $age 大于或等于 18，则 $isAdult 设置为 true
// 否则，$isAdult 设置为 false
```

### 糟糕的代码

```php
// 糟糕的代码：使用传统的 if-else 语句进行简单的条件赋值
if ($age >= 18) {
    $isAdult = true;
} else {
    $isAdult = false;
}

// 解释：
// 这段代码与良好的示例功能相同，
// 但它更冗长且可读性较差
```

良好的代码示例使用了三元运算符 `(?:)` 来根据条件简洁地为布尔值赋值。与糟糕代码示例中使用的传统 `if-else` 语句相比，这种方法更具可读性且更加紧凑。两个代码段实现了相同的结果，但三元运算符的版本更优雅，且更容易一目了然。

> **Memo**
> 三元运算符也称为条件运算符，它是 `PHP` 中唯一接受三个操作数的运算符。

## 46. 利用空合并运算符 (`??`) 设置默认值

使用空合并运算符来高效地分配默认值。

以下代码展示了如何使用空合并运算符来分配默认值：

### 良好的代码

```php
// 良好的代码：使用空合并运算符设置默认值
$username = $_GET['username'] ?? 'Guest';

// 解释：
// 如果 $_GET['username'] 已设置且不为 null，则将它的值赋值给 $username
// 否则，将 'Guest' 作为默认值赋值
```

### 糟糕的代码

```php
// 糟糕的代码：使用 isset() 和三元运算符设置默认值
$username = isset($_GET['username']) ? $_GET['username'] : 'Guest';

// 解释：
// 这段代码的功能与良好示例相同，
// 但它更冗长且效率较低
```

良好的代码示例使用了空合并运算符 `(??)` 在指定变量为 `null` 或未设置时分配默认值。与糟糕的代码示例相比，这种方法更简洁且易于阅读，而糟糕的示例使用了 `isset()` 和三元运算符来实现相同的结果。空合并运算符简化了代码，并使其更具可维护性。

> **Memo**
> 空合并运算符在 `PHP 7.0` 中引入，对于处理未定义的数组键或对象属性特别有用。

## 47. 使用太空运算符 (`<=>`) 进行简洁比较

太空运算符简化了 `PHP` 中的比较操作，使代码更具可读性且更简洁。

以下代码演示了如何使用太空运算符比较值并排序数组：

### 良好的代码

```php
// 使用太空运算符进行比较和排序
$fruits = ['apple', 'banana', 'cherry'];

// 使用太空运算符对数组进行排序
usort($fruits, function($a, $b) {
    // 太空运算符返回 -1, 0 或 1
    return $a <=> $b;
});

// 输出排序后的数组
foreach ($fruits as $fruit) {
    echo $fruit . "\n";
}

// 使用太空运算符比较数字
$result = 5 <=> 10;
echo "Comparison result: " . $result . "\n";
```

### 糟糕的代码

```php
// 未使用太空运算符进行比较和排序
$fruits = ['apple', 'banana', 'cherry'];

// 使用传统的比较函数对数组进行排序
usort($fruits, function($a, $b) {
    if ($a < $b) {
        return -1;
    } elseif ($a > $b) {
        return 1;
    } else {
        return 0;
    }
});

// 输出排序后的数组
foreach ($fruits as $fruit) {
    echo $fruit . "\n";
}

// 在不使用太空运算符的情况下比较数字
$a = 5;
$b = 10;
if ($a < $b) {
    $result = -1;
} elseif ($a > $b) {
    $result = 1;
} else {
    $result = 0;
}

echo "Comparison result: " . $result . "\n";
```

良好的代码示例使用太空运算符 `(<=>)` 同时用于排序和比较。该运算符在左操作数小于右操作数时返回 `-1`，当两者相等时返回 `0`，当左操作数大于右操作数时返回 `1`。糟糕的示例使用了传统的 `if-else` 逻辑，导致代码更冗长且不直观。太空运算符简化了处理 `null` 的情况，使代码更简洁且易于读。

> **Memo**
> 太空运算符在 `PHP 7.0` 中引入，也被称为组合运算符。

## 48. 使用空安全运算符 (`?->`) 进行安全访问

空安全运算符允许在处理 `null` 值时访问属性或方法而不会产生错误。

以下代码演示了如何使用空安全运算符安全地访问属性：

### 良好的代码

```php
// 良好的代码：使用空安全运算符访问属性/方法
class User {
    public $name;

    public function getEmail() {
        return 'user@example.com';
    }
}

$user = null;

// 安全访问属性
$name = $user?->name;
echo "Name: " . ($name ?? 'Unknown');

// 安全调用方法
$email = $user?->getEmail();
echo "Email: " . ($email ?? 'Not available');

// 链式调用
$user = new User();
$user->name = 'John';
```



echo "Name: " . $user->name;

<Bad Code>

```php
// 糟糕的代码：未使用空安全运算符访问属性/方法

class User {

    public $name;

    public function getEmail() {

        return 'user@example.com';

    }

}

$user = null;

// 不安全的访问

$name = $user->name;

echo "Name: " . $name;

// 不安全的调用

$email = $user->getEmail();

echo "Email: " . $email;

```

良好的代码示例使用了空安全运算符 `(?->)` 来访问属性和方法。该运算符在尝试访问前检查对象是否为 `null`，从而防止错误。糟糕的示例使用了传统的检查，这可能导致代码更加冗长。

## 使用 match 表达式实现简洁的 switch 功能

`PHP 8.0` 引入了 `match` 表达式，为 `switch` 语句提供了更简洁、强大的替代方案。

以下代码演示了如何根据值处理不同的情况：

<Good Code>

```php
// 使用 match 的良好示例

function getStatusMessage($statusCode) {

    // 使用 match 返回适当的消息

    return match ($statusCode) {

        200 => 'OK',

        404 => 'Not Found',

        500 => 'Internal Server Error',

        default => 'Unknown Status',

    };

}

// 使用

$message = getStatusMessage(404);

echo $message; // 输出: Not Found

```

<Bad Code>

```php
// 使用 switch 语句的糟糕示例

function getStatusMessage($statusCode) {

    // 使用 switch 语句返回适当的消息

    switch ($statusCode) {

        case 200:

            return 'OK';

        case 404:

            return 'Not Found';

        case 500:

            return 'Internal Server Error';

        default:

            return 'Unknown Status';

    }

}

// 使用

$message = getStatusMessage(404);

echo $message; // 输出: Not Found

```

`match` 表达式与 `switch` 语句相比提供了更简洁的语法。它会自动返回匹配表达式的结果，消除了对 `break` 语句的需求。`match` 表达式默认执行严格比较，减少了潜在的错误。良好的示例展示了更整洁、更易读的代码，实现了与坏的示例中 `switch` 语句相同的功能。

<Memo>
`match` 表达式在 PHP 8.0 中引入，灵感源于 Rust 和 Ruby 等语言中的类似结构。
</Memo>

## 为自定义对象遍历实现迭代器

实现 `Iterator` 接口允许自定义对象在 `foreach` 循环中被轻松遍历。

以下代码演示了如何为自定义对象实现迭代器：

<Good Code>

```php
// 实现 Iterator 接口的良好示例

class MyCollection implements Iterator {

    private $items = [];

    private $position = 0;

    public function __construct(array $items) {

        $this->items = $items;

    }

    // 必须的 Iterator 方法

    public function current() {

        return $this->items[$this->position];

    }

    public function key() {

        return $this->position;

    }

    public function next() {

        ++$this->position;

    }

    public function rewind() {

        $this->position = 0;

    }

    public function valid() {

        return isset($this->items[$this->position]);

    }

}

// 使用

$collection = new MyCollection(['apple', 'banana', 'cherry']);

foreach ($collection as $key => $value) {

    echo "$key: $value\n";

}

```

<Bad Code>

```php
// 未实现 Iterator 的坏示例

class MyCollection {

    private $items = [];

    public function __construct(array $items) {

        $this->items = $items;

    }

    public function getItems() {

        return $this->items;

    }

}

// 使用

$collection = new MyCollection(['apple', 'banana', 'cherry']);

$items = $collection->getItems();

foreach ($items as $key => $value) {

    echo "$key: $value\n";

}

```

良好的示例实现了 `Iterator` 接口，允许对象直接用于 `foreach` 循环。这种方法将迭代逻辑封装在类内部，促进了更好的面向对象设计。坏的示例暴露了内部数组，破坏了封装性，并且遍历项目时需要额外的步骤。实现 `Iterator` 使代码更加直观且易于使用，特别是在处理复杂的自定义对象时。

<Memo>
PHP 的 `Iterator` 接口是标准 PHP 库 (SPL)的一部分，提供了一种让对象可遍历的标准方法。
</Memo>

## 为类属性使用类型声明

通过在 PHP 类属性中使用类型声明，可以增强代码的可读性和维护性。

以下代码演示了在 PHP 7.4 及更高版本中为类属性使用类型声明的方法：

<Good Code>

```php
class User {

    // 使用类型提示声明公共属性

    public string $name;

    public int $age;

    public ?string $email; // 可空字符串类型

    // 带有类型提示参数的构造函数

    public function __construct(string $name, int $age, ?string $email = null) {

        $this->name = $name;

        $this->age = $age;

        $this->email = $email;

    }

    // 带有类型提示返回值的方法

    public function getInfo(): string {

        return "Name: {$this->name}, Age: {$this->age}";

    }

}

// 使用

$user = new User("John Doe", 30, "john@example.com");

echo $user->getInfo(); // 输出: Name: John Doe, Age: 30

```

<Bad Code>

```php
class User {

    // 缺少类型提示的属性

    public $name;

    public $age;

    public $email;

    // 缺少类型提示的构造函数

    public function __construct($name, $age, $email = null) {

        $this->name = $name;

        $this->age = $age;

        $this->email = $email;

    }

    // 缺少返回类型的方法

    public function getInfo() {

        return "Name: " . $this->name . ", Age: " . $this->age;

    }

}

// 使用

$user = new User("John Doe", 30, "john@example.com");

echo $user->getInfo(); // 输出: Name: John Doe, Age: 30

```

良好的示例使用了类型声明，使得代码更加清晰并能在运行时捕捉许多错误。坏的示例缺乏类型声明，这增加了类型错误的风险，并使维护变得更加困难。

```php
echo "Sum: " . $result; // 输出: Sum: 15
```

<Bad Code>

```php
// 没有扩展运算符的糟糕实现

function calculateSum() {

    $sum = 0;

    $args = func_get_args();

    for ($i = 0; $i < func_num_args(); $i++) {

        $sum += $args[$i];

    }

    return $sum;

}

$result = calculateSum(1, 2, 3, 4, 5);

echo "Sum: " . $result; // 输出: Sum: 15

```

良好的代码示例使用了扩展运算符 `(...)` 将所有参数收集到一个数组中，使函数更具灵活性且更易于读。它还利用了内置的 `array_sum()` 函数进行高效计算。糟糕的代码示例依赖于 `func_get_args()` 和 `func_num_args()` 等较旧方法，这些方法不那么直观，且需要更多的手动处理。

<Memo>
扩展运算符在 PHP 5.6 中引入，提供了一种简洁的方式将数组或可遍历对象解包为函数参数或数组元素。
</Memo>

## 使用命名参数提高函数调用的可读性

在函数调用中使用命名参数来增强代码清晰度，并使每个参数的意图显而易见。

以下代码展示了如何在函数调用中使用命名参数，提高了可读性并减少了错误。

<Good Code>

```php
/**

* 创建用户配置文件

* @param string $username 用户名

* @param string $email 电子邮箱地址

* @param int $age 用户年龄

* @param string $country 用户所在国家（可选）

* @return array 创建的用户配置文件

*/

function createUserProfile(

    string $username,

    string $email,

    int $age,

    string $country = 'Unknown'

) {

    return [

        'username' => $username,

        'email' => $email,

        'age' => $age,

        'country' => $country

    ];

}

// 使用命名参数

$profile = createUserProfile(

    username: 'john_doe',

    email: 'john@example.com',

    age: 30,

    country: 'USA'

);

print_r($profile);

```

<Bad Code>

```php
// 没有命名参数

function createUserProfile($username, $email, $age, $country = 'Unknown') {

    return [

        'username' => $username,

        'email' => $email,

        'age' => $age,

        'country' => $country

    ];

}

// 可能会引起混淆的参数顺序

$profile = createUserProfile('john_doe', 'john@example.com', 30, 'USA');

print_r($profile);

```

良好的代码示例使用了命名参数，清楚地显示了哪个值对应哪个参数。这种方法提高了可读性并降低了按错误传递参数的风险。糟糕的代码示例依赖位置参数，这很容易出错，特别是在处理多个参数或可选参数时。

<Memo>
命名参数在 PHP 8.0 中引入，允许开发者根据参数名称而不是位置向函数传递参数。
</Memo>

## 实现 __debugInfo() 以进行自定义对象的调试输出

使用 `__debugInfo()` 在调试期间控制对象的输出。

`__debugInfo()` 魔法方法允许你自定义在对对象调用 `var_dump()` 时显示的信息。

<Good Code>

```php
class User {

    private $id;

    private $name;

    private $email;

    private $password; // 敏感信息

    public function __construct($id, $name, $email, $password) {

        $this->id = $id;

        $this->name = $name;

        $this->email = $email;

        $this->password = $password;

    }

    // 实现 __debugInfo() 以控制输出

    public function __debugInfo() {

        return [

            'id' => $this->id,

            'name' => $this->name,

            'email' => $this->email,

            // 为了安全省略了密码

        ];

    }

}

// 使用

$user = new User(1, 'John Doe', 'john@example.com', 'secret23');

var_dump($user);

```

<Bad Code>

```php
class User {

    public $id;

    public $name;

    public $email;

    public $password; // 敏感信息

    public function __construct($id, $name, $email, $password) {

        $this->id = $id;

        $this->name = $name;

        $this->email = $email;

        $this->password = $password;

    }

}

// 使用

$user = new User(1, 'John Doe', 'john@example.com', 'secret23');

var_dump($user); // 转储包括敏感数据在内的所有属性

```

良好的示例实现了 `__debugInfo()` 来控制调试期间显示的内容。它省略了密码等敏感数据。糟糕的示例暴露了所有属性，存在安全风险。

<Memo>
`__debugInfo()` 方法在 PHP 5.6.0 中引入，为开发者提供了调试期间对对象表示的更多控制。
</Memo>

## 在靠近其使用的地方声明变量

在变量第一次使用的地方定义变量以提高代码的可读性。在靠近使用处声明变量有助于理解代码流，并减少读者的认知负担。

<Good Code>

```php
function processOrder($orderId) {

    // 获取订单详情

    $order = getOrderById($orderId);

    // 计算总计

    $total = 0;

    foreach ($order['items'] as $item) {
```



$itemPrice = $item['price'] * $item['quantity'];

$total += $itemPrice;

}

    // 如果适用则应用折扣

    $discountCode = getDiscountCode($orderId);

    if ($discountCode) {

        $discountPercentage = getDiscountPercentage($discountCode);

        $discountAmount = $total * ($discountPercentage / 100);

        $total -= $discountAmount;

    }

    // 处理支付

    $paymentResult = processPayment($orderId, $total);

    return $paymentResult;

}

```

<Bad Code>

```php

function processOrder($orderId) {

    $order = null;

    $total = 0;

    $itemPrice = 0;

    $discountCode = null;

    $discountPercentage = 0;

    $discountAmount = 0;

    $paymentResult = false;

    $order = getOrderById($orderId);

    foreach ($order['items'] as $item) {

        $itemPrice = $item['price'] * $item['quantity'];

        $total += $itemPrice;

    }

    $discountCode = getDiscountCode($orderId);

    if ($discountCode) {

        $discountPercentage = getDiscountPercentage($discountCode);

        $discountAmount = $total * ($discountPercentage / 100);

        $total -= $discountAmount;

    }

    $paymentResult = processPayment($orderId, $total);

    return $paymentResult;

}

```

良好的示例在靠近其使用的地方声明变量，使代码更容易追踪。糟糕的示例在开头声明了所有变量，这可能更难以理解每个变量的。

<Memo>
这种在靠近使用处声明变量的做法是编程中更广泛的“引用局部性”（locality of reference）概念的一部分，该概念认为相关元素应该保持在一起。
57

# 使用描述性的变量名

选择能够清晰解释其目的和内容的变量名。

以下代码演示了在计算购物车总价的函数中，使用描述性变量名与非描述性变量名的区别。

< Good Code >

```php

// 计算购物车总价的函数

function calculateTotalPrice($itemPrices, $taxRate, $discountPercentage) {

    // 计算小计

    $subtotal = array_sum($itemPrices);

    // 应用折扣

    $discountAmount = $subtotal * ($discountPercentage / 100);

    $discountedTotal = $subtotal - $discountAmount;

    // 添加税

    $taxAmount = $discountedTotal * ($taxRate / 100);

    $totalPrice = $discountedTotal + $taxAmount;

    return $totalPrice;

}

// 使用示例

$prices = [10.99, 24.99, 5.99];

$tax = 8.5;

$discount = 10;

$finalPrice = calculateTotalPrice($prices, $tax, $discount);

echo "Total price: $" . number_format($finalPrice, 2);

```

<Bad Code>

```php

// 计算某些内容的函数

function calc($a, $b, $c) {

    // Do some math

    $x = array_sum($a);

    // More calculations

    $y = $x * ($c / 100);

    $z = $x - $y;

    // Final step

    $w = $z * ($b / 100);

    $v = $z + $w;

    return $v;

}

// Usage

$p = [10.99, 24.99, 5.99];

$t = 8.5;

$d = 10;

$f = calc($p, $t, $d);

echo "Result: $" . number_format($f, 2);

```

良好的代码示例使用了具有描述性的变量名，清楚地指示了它们的用途，例如 `$itemPrices`、`$taxRate` 和 `$discountPercentage`。这使得代码更具可读性且自解释性。糟糕的代码示例使用了单字母变量，如 `$a`、`$b` 和 `$c`，这使得在没有额外上下文或注释的情况下很难理解每个变量的用途。

<Memo>
使用描述性变量名的做法是一个更广泛的概念——“自文档代码”的一部分，旨在旨在不严重依赖注释的情况下使代码更具可读性和可维护性。

58

# 避免全局变量，使用依赖注入

***

与其使用全局变量，不如将依赖作为参数传递给函数或方法。

***

以下代码演示了在简单的日志系统中使用全局变量和依赖注入的区别。

## < 良好的代码 >

```php

// 使用依赖注入的日志类

class Logger {

    private $logFile;

    public function __construct($logFile) {

        $this->logFile = $logFile;

    }

    public function log($message) {

        $timestamp = date('Y-m-d H:i:s');

        $logEntry = "$timestamp: $message\n";

        file_put_contents($this->logFile, $logEntry, FILE_APPEND);

    }

}

// 使用示例

$logger = new Logger('/path/to/app.log');

function processOrder($orderId, Logger $logger) {

    // 这里处理订单逻辑

    $logger->log("Order $orderId processed successfully");

}

// 使用日志

$orderId = 12345;

processOrder($orderId, $logger);

```

## < 糟糕的代码>

```php

// 用于日志文件的全局变量

$GLOBALS['logFile'] = '/path/to/app.log';

// 使用全局变量的日志函数

function logMessage($message) {

    global $logFile;

    $timestamp = date('Y-m-d H:i:s');

    $logEntry = "$timestamp: $message\n";

    file_put_contents($logFile, $logEntry, FILE_APPEND);

}

// 使用示例

function processOrder($orderId) {

    // 这里处理订单逻辑

    logMessage("Order $orderId processed successfully");

}

// 使用日志

$orderId = 12345;

processOrder($orderId);

```

良好的代码示例通过将 `Logger` 对象作为参数传递给 `processOrder` 函数使用了依赖注入。这种方法使代码更具模块化、可测试性且易于维护。糟糕的代码示例使用了全局变量 `$GLOBALS['logFile']` 和全局函数 `logMessage`，这会导致紧耦合并使其难以测试。

<Memo>
使用描述性变量名的做法是一个更广泛的概念——“自文档代码”的一部分，旨在旨在不严重依赖注释的情况下使代码更具可读性和可维护性。

59

# 使用常量处理固定值

***

使用常量处理固定值可以提高可读性和可维护性。

***

常量用于不改变的值。

## < 良好的代码 >

```php

<?php

define('TAX_RATE', 0.08);

// 计算税额的函数

function calculate($price) {

    return $price * TAX_RATE;

}

// 使用

$price = 100;

echo "Tax: " . calculate($price); // 输出: 8

```

## < 糟糕的代码>

```php

<?php

// 计算税额的函数

function calculate($price) {

    return $price * 0.08;

}

// 使用

$price = 100;

echo "Tax: " . calculate($price); // 输出: 8

?>

```

在良好的示例中，`TAX_RATE` 被定义为常量。在糟糕的示例中，值 `0.08` 是硬编码的，如果税率发生变化将难以维护。

60

# 使用静态变量处理状态

***

静态变量在函数调用之间保留状态。

***

静态变量常用于计数或缓存。

## < 良好的代码 >

```php

<?php

function incrementCounter() {

    static $count = 0;

    $count++;

    return $count;

}

// 使用

echo incrementCounter(); // 输出: 1

echo incrementCounter(); // 输出: 2

?>

```

## < 糟糕的代码>

```php

<?php

function incrementCounter() {

    $count = 0;

  $count++;

    return $count;

}

// 使用

echo incrementCounter(); // 输出: 1

echo incrementCounter(); // 输出: 1

?>

```

在良好的示例中，`$count` 变量在调用之间持久存在。在糟糕的示例中，变量每次调用函数时都会被重新初始化为 0。

61

# 将复杂条件提取为命名良好的方法

***

通过将复杂条件提取为命名良好的方法来提高代码的可读性。

***

以下代码演示了如何将复杂条件提取为命名良好的方法。

## < 良好的代码 >

```php

<?php

class Order {

    public function isEligibleForDiscount() {

        if ($this->isVIPCustomer() && $this->hasValidCoupon()) {

            return true;

        }

        return false;

    }

    private function isVIPCustomer() {

        // 逻辑

        return true;

    }

    private function hasValidCoupon() {

        // 逻辑

        return true;

    }

}

?>

```

## < 糟糕的代码>

```php

<?php

class Order {

    public function isEligibleForDiscount() {

        if ($this->customerType === 'VIP' && $this->couponStatus === 'ACTIVE') {

            return true;

        }

        return false;

    }

}

?>

```

良好的代码示例将复杂条件提取为命名良好的方法 `isEligibleForDiscount()`。它进一步将该条件拆分为两个独立的方法：`isVIPCustomer()` 和 `hasValidCoupon()`。这种方法使代码更具可读性和自解释性。

糟糕的代码示例虽然较较短，但将多个条件合并在一行中，使得一目难以理解，并且在未来可能更难以维护或修改。





以下代码演示了如何将不同级别的抽象分离到不同的方法中，以提高可读性和可维护性。

### 良好的代码

```php

class EmailSender {

    public function sendWelcomeEmail($user) {

        $emailContent = $this->prepareWelcomeEmailContent($user);

        $this->sendEmail($user->email, 'Welcome!', $emailContent);

    }

    private function prepareWelcomeEmailContent($user) {

        $template = $this->getWelcomeEmailTemplate();

        return str_replace('{USERNAME}', $user->name, $template);

    }

    private function getWelcomeEmailTemplate() {

        return "Hello {USERNAME},\n\nWelcome to our platform!";

    }

    private function sendEmail($to, $subject, $content) {

        // Code to actually send the email

    }

}

// Usage

$emailSender = new EmailSender();

$emailSender->sendWelcomeEmail($user);

```

### 糟糕的代码

```php

class EmailSender {

    public function sendWelcomeEmail($user) {

        $template = "Hello {USERNAME},\n\nWelcome to our platform!";

        $content = str_replace('{USERNAME}', $user->name, $template);

        // Code to send email

        // ...

    }

}

// Usage

$emailSender = new EmailSender();

$emailSender->sendWelcomeEmail($user);

```

良好的代码示例将不同层级的抽象分离到不同的方法中。`sendWelcomeEmail()` 方法提供了流程的高层概览，而低层细节则由 `prepareWelcomeEmailContent()`、`getWelcomeEmailTemplate()` 和 `sendEmail()` 等独立方法负责处理。这种分离使得代码更具模块化、更容易理解，并且更易维护或扩展。

糟糕的代码示例将所有操作合并在单个方法中，将高层逻辑与低层细节混合在一起。这种方法会导致代码更难以阅读、理解和维护，特别是当操作复杂性增加时。

<Memo>
该原则与 SOLID 原则中的单一职责原则 (SRP) 相关，该原则规定一个类或方法应该只有一个改变的原因。

</Memo>

63

# 使用不修改状态的纯函数

编写对于给定输入始终产生相同输出且不修改外部状态的函数。

以下代码演示了一个纯函数，它可以在不修改原始数据的情况下计算数组之和：

### 良好的代码

```php

/**

 * 计算数字数组之和

 *

 * @param array $numbers 待求和的数字数组

 * @return int 数组中所有数字之和

 */

function calculateSum(array $numbers): int

{

    // 使用 array_reduce 求和所有元素而不修改原始数组

    return array_reduce($numbers, function($carry, $item) {

        return $carry + $item;

    }, 0);

}

// 示例用法
```



$myNumbers = [1, 2, 3, 4, 5];

$sum = calculateSum($myNumbers);

echo "Sum: " . $sum; // Output: Sum: 15

// 原始数组保持不变

print_r($myNumbers); // Output: Array ([0] => 1 [1] => 2 [2] => 3 [3] => 4 [4] => 5 )

```

### 糟糕的代码

```php

/**

 * 计算数字数组之和（非纯函数）

 *

 * @param array $numbers 待求和的数字数组

 * @return int 数组中所有数字之和

 */

function calculateSum(array &$numbers): int

{

    $sum = 0;

    // 在计算和的同时修改原始数组

    foreach ($numbers as &$number) {

        $sum += $number;

        $number *= 2; // 修改数组中的每个数字

    }

    return $sum;

}

// 示例用法

$myNumbers = [1, 2, 3, 4, 5];

$sum = calculateSum($myNumbers);

echo "Sum: " . $sum; // Output: Sum: 15

// 原始数组被修改了

print_r($myNumbers); // Output: Array ([0] => 2 [1] => 4 [2] => 6 [3] => 8 [4] => 10 )

```

```

良好的代码示例演示了一个纯函数，它可以在不修改原始数据的情况下计算数组之和。它使用 `array_reduce` 遍历数组并对其元素求和。该函数对于相同的输入总是产生相同的输出，并且没有任何副作用。

糟糕的代码示例展示了一个非纯函数，它在计算和的同时修改了原始数组。它使用了引用参数并在计算过程中修改了数组的每个元素。这种方法会导致意外的行为，并使得代码难以推理和测试。

> **Memo**
> 纯函数是函数式编程中的核心概念，可以写出更可预测且更容易测试的代码。

---

# 为类和方法实现单一职责原则

设计具有单一、明确职责的类和方法，以改进代码组织和可维护性。

以下代码通过分离用户数据管理和电子邮件功能演示了单一职责原则：

### 良好的代码

```php

/**

 * 负责管理用户数据的类

 */

class User

{

    private $name;

    private $email;

    /**

     * 初始化用户数据的构造函数

     * @param string $name 用户名

     * @param string $email 用户邮箱

     */

    public function __construct(string $name, string $email)

    {

        $this->name = $name;

        $this->email = $email;

    }

    /**

     * 获取用户的邮箱

     * @return string 用户邮箱

     */

    public function getEmail()

    {

        return $this->email;

    }

}

/**

 * 负责发送电子邮件的类

 */

class EmailService

{

    /**

     * 向用户发送欢迎邮件

     * @param User $user 要发送的用户

     * @return bool 如果邮件发送成功返回 true，否则返回 false

     */

    public function sendWelcomeEmail(User $user)

    {

        $to = $user->getEmail();

        $subject = "欢迎来到我们的服务!";

        $message = "感谢您加入我们的平台。";

        // 邮件发送逻辑...

        return mail($to, $subject, $message);

    }

    // 其他相关方法...

}

// 用法

$user = new User("John Doe", "john@example.com");

$emailService = new EmailService();

$emailService->sendWelcomeEmail($user);

```

### 糟糕的代码

```php

/**

 * 混合了职责的用户类

 */

class User

{

    private $name;

    private $email;

    /**

     * 初始化用户数据的构造函数

     * @param string $name 用户名

     * @param string $email 用户邮箱

     */

    public function __construct(string $name, string $email)

    {

        $this->name = $name;

        $this->email = $email;

    }

    /**

     * 向用户发送欢迎邮件

     * @return bool 如果邮件发送成功返回 true，否则返回 false

     */

    public function sendWelcomeEmail()

    {

        $to = $this->email;

        $subject = "欢迎来到我们的服务!";

        $message = "感谢您加入我们的平台。";

        // 邮件发送逻辑...

        return mail($to, $subject, $message);

    }

    // 其他用户相关和邮件相关方法混合在一起...

}

// 用法

$user = new User("John Doe", "john@example.com");

$user->sendWelcomeEmail();

```

---

# 将查询操作与命令操作分离

通过将数据检索（查询）与数据修改（命令）分离，来提高代码的可读性。

以下代码演示了如何在用户管理系统中分离查询操作和命令操作：

### 好代码

```php

// UserRepository.php

class UserRepository {

    // 查询操作

    public function findUserById(int $id): ?User {

        // 查找用户的数据库查询

        // 返回 User 对象或 null

    }

    // 命令操作

    public function saveUser(User $user): void {

        // 保存用户的数据库操作

        // 无返回值

    }

}

// UserService.php

class UserService {

    private $userRepository;

    public function __construct(UserRepository $userRepository) {

        $this->userRepository = $userRepository;

    }

    public function updateUserEmail(int $userId, string $newEmail): void {

        // 查询

        $user = $this->userRepository->findUserById($userId);

        if ($user === null) {

            throw new UserNotFoundException();

        }

        // 修改

        $user->setEmail($newEmail);

        // 命令

        $this->userRepository->saveUser($user);

    }

}

```

### Bad 代码

```php

// UserManager.php

class UserManager {

    public function updateUserEmail($userId, $newEmail) {

        $db = new Database();

        $user = $db->query("SELECT * FROM users WHERE id = $userId")->fetch();

        if ($user) {

            $db->query("UPDATE users SET email = '$newEmail' WHERE id = $userId");

            return true;

        }

        return false;

    }

}

```

好代码示例通过使用仓库模式实现了关注点分离。它清晰地区分了查询操作（`findUserById`）和命令操作（`saveUser`）。`UserService` 使用这些操作来完成复杂任务。

坏代码示例在单个方法中混合了查询和更新，使其难以理解和维护。它也没有将数据库操作与业务逻辑分离。

> **Memo**
> 该原则是命令查询职责分离（CQRS）模式的一部分，该模式可以扩展到在大型复杂系统中分离读写模型。

---

# 使用 SplEnum 使用类型安全的枚举

通过对枚举类型使用 `SplEnum`，增强代码的清晰度和类型安全性。

以下代码展示了如何使用 `SplEnum` 创建类型安全的枚举：

### 好代码

```php

// UserStatus.php

class UserStatus extends SplEnum {

    const __default = self::ACTIVE;

    const ACTIVE = 1;

    const INACTIVE = 2;

    const SUSPENDED = 3;

}

// 使用

class User {

    private $status;

    public function setStatus(UserStatus $status) {

        $this->status = $status;

    }

    public function getStatus(): UserStatus {

        return $this->status;

    }

}

$user = new User();

$user->setStatus(UserStatus::ACTIVE);

if ($user->getStatus()->equals(UserStatus::ACTIVE)) {

    echo "User is active";

}

```

### Bad 代码

```php

// 没有使用枚举

class User {

    private $status;

    public function setStatus($status) {

        $this->status = $status;

    }

    public function getStatus() {

        return $this->status;

    }

}

$user = new User();

$user->setStatus(1); // 1 代表什么？

if ($user->getStatus() == 1) {

    echo "User is active"; // 不清楚 1 代表什么

}

```

好代码使用 `SplEnum` 为 `UserStatus` 创建了类型安全的枚举。这为状态提供了清晰、有意义的常量，并确保了在设置或检查状态时的类型安全。坏代码使用任意整数来表示状态，这可能导致困惑和错误。在没有额外文档的情况下，这一点是不清晰的。

> **Memo**
> `SplEnum` 是 PHP 标准库（SPL）的一部分，需要安装 SPL 扩展。在 PHP 8.1+ 中，原生枚举已作为语言特性可用，为枚举类型提供了更健壮的解决方案。

---

# 为方法链实现流式接口（Fluent Interfaces）

使用方法链来创建更具表现力的代码。

以下代码演示了如何为简单的 `User` 类实现流式接口：

### 好代码

```php

// 好示例：流式接口实现

class User {

    private $name;

    private $email;

    private $age;

    // 设置名字的方法，返回 $this 以支持链式

    public function setName($name) {

        $this->name = $name;

        return $this;

    }

    // 设置邮箱的方法，返回 $this 以支持链式

    public function setEmail($email) {

        $this->email = $email;

        return $this;

    }

    // 设置年龄的方法，返回 $this 以支持链式

    public function setAge($age) {

        $this->age = $age;

        return $this;

    }

    // 获取用户信息的方法

    public function getInfo() {

        return "Name: {$this->name}, Email: {$this->email}, Age: {$this->age}";

    }

}

// 流式接口的使用

$user = (new User())

    ->setName("John Doe")

    ->setEmail("john@example.com")

    ->setAge(30);

echo $user->getInfo();

```

### Bad 代码

```php

// 坏示例：没有流式接口

class User {

    private $name;

    private $email;

    private $age;

    // 设置名字的方法

    public function setName($name) {

        $this->name = $name;

    }

    // 设置邮箱的方法

    public function setEmail($email) {

        $this->email = $email;

    }

    // 设置年龄的方法

    public function setAge($age) {

        $this->age = $age;

    }

    // 获取用户信息的方法

    public function getInfo() {

        return "Name: {$this->name}, Email: {$this->email}, Age: {$this->age}";

    }

}

// 无流式接口的使用

$user = new User();

$user->setName("John Doe");

$user->setEmail("john@example.com");

$user->setAge(30);

```

好示例通过在每个 setter 方法中返回 `$this` 实现了流式接口。这允许方法链调用，使得代码更具可读性。坏示例没有使用方法链，导致了多次独立的方法调用。

> **Memo**
> 流式接口由 Martin Fowler 推广，在许多现代框架和库中广泛使用。

---

# 不需要继承时使用 final 类

在不需要或不打算被继承时，将类声明为 `final`。

以下代码展示了如何使用 `final` 类来防止意外的继承：

### 好代码

```php

// 好示例：使用 final 类

final class Configuration {

    private $settings = [];

    // 构造函数初始化设置

    public function __construct(array $initialSettings = []) {

        $this->settings = $initialSettings;

    }

    // 获取设置的方法

    public function getSetting($key) {

        return $this->settings[$key] ?? null;

    }

    // 设置设置的方法

    public function setSetting($key, $value) {

        $this->settings[$key] = $value;

    }

}

// final 类的使用

$config = new Configuration(['debug' => true]);

```



echo `$config->getSetting('debug');` // 输出：1 (true)

#### Bad 代码

```php
// 坏示例：没有使用 final 类

class Configuration {

    protected $settings = [];

    // 构造函数初始化设置

    public function __construct(array $initialSettings = []) {

        $this->settings = $initialSettings;

    }

    // 获取设置的方法

    public function getSetting($key) {

        return $this->settings[$key] ?? null;

    }

    // 设置设置的方法

    public function setSetting($key, $value) {

        $this->settings[$key] = $value;

    }

}

// 意之外的继承

class ExtendedConfiguration extends Configuration {

    // 这可能会破坏 Configuration 的预期行为

}

```

```php

public function overrideAllSettings(array $newSettings) {

    $this->settings = $newSettings;

}

}

```

// 非 final 类的用法

```php

$config = new ExtendedConfiguration(['debug' => true]);

$config->overrideAllSettings(['debug' => false, 'unsafe' => true]);

echo $config->getSetting('debug'); // 输出：(空)

```

良好的示例使用了 `final` 类，防止了任何继承。这确保了 `Configuration` 类的行为符合预期，且不会以可能破坏其功能的方式进行扩展。而糟糕的示例允许继承，如果该类被不恰当地扩展，可能会导致意料之外的行为。

<Memo>
使用 `final` 类还可以略微提高 PHP 的性能，因为引擎不需要检查子类中是否存在被重写的方法。
</Memo>

# 使用 PHPStan 等静态分析工具提高代码质量

使用 `PHPStan` 自动检测潜在错误并提高代码质量。

以下示例演示了如何使用 `PHPStan` 分析一个简单的 PHP 函数：

### 良好的代码

```php
<?php

// 文件: example.php

/**

 * 计算两个整数之和

 *

 * @param int $a 第一个数字

 * @param int $b 第二个数字

 * @return int $a 和 $b 的和

 */

function add(int $a, int $b): int

{

    return $a + $b;

}

// 用法

$result = add(5, 3);

echo $result; // 输出：8

```

### 糟糕的代码

```php
<?php

// 文件: example.php

function add($a, $b)

{

    return $a + $b;

}

$result = add("5", "3");

echo $result;

```

在良好的示例中，我们对参数和返回值使用了类型声明，`PHPStan` 可以对其进行分析。糟糕的示例缺少类型声明，容易出现与类型相关的错误。在良好的代码上运行 `PHPStan` 不产生错误，而糟糕的代码可能会生成关于潜在类型不匹配的警告。

使用 `PHPStan`：

安装 `PHPStan`：`composer require --dev phpstan/phpstan`

运行分析：`vendor/bin/phpstan analyse example.php`

<Memo>
`PHPStan` 具有不同的规则级别（0-9），对应不同严格程度的分析。级别 0 最松，级别 9 最严格。
</Memo>

# 对原生类型使用标量类型声明

使用标量类型声明强制执行 PHP 中原生数据类型的严格类型。

以下示例展示了如何在计算矩形面积的未使用标量类型声明：

### 良好的代码

```php
<?php

declare(strict_types=1);

/**

 * 计算矩形面积

 *

 * @param float $length 矩形的长度

 * @param float $width 矩形的宽度

 * @return float 矩形的面积

 */

function calculateRectangleArea(float $length, float $width): float

{

    return $length * $width;

}

// 用法

$area = calculateRectangleArea(5.5, 3.2);

echo "Area: " . $area; // 输出：Area: 17.6

```

### 糟糕的代码

```php
<?php

function calculateRectangleArea($length, $width)

{

    return $length * $width;

}

// 用法

$area = calculateRectangleArea("5.5", "3.2");

echo "Area: " . $area;

```

在良好的示例中，我们使用 `declare(strict_types=1)` 启用严格类型检查，并对参数和返回值使用 float 类型声明。这确保了只接受和返回 `float` 值。糟糕的示例缺少类型声明，允许任何类型的输入，这可能导致意外的结果或错误。

使用标量类型声明的好处：
- 提高代码可读性
- 运行时更好的错误检测
- 增强 IDE 对自动补全和类型提示的支持

<Memo>
PHP 7.0 引入了针对 `int`、`float`、`string` 和 `bool` 的标量类型声明。在此之前，仅允许类名、`self`、`array` 和 `callable` 作为类型提示。
</Memo>

# 将长方法链拆分为多行

通过将长方法链拆分到多行来提高代码可读性。

以下代码演示了如何拆分长方法链以提高可读性：

### 良好的代码

```php
// 良好：将长方法链拆分为多行

$result = $database->table('users')

    ->select('name', 'email')

    ->where('active', true)

    ->orderBy('created_at', 'desc')

    ->limit(10)

    ->get();

```

### 糟糕的代码

```php
// 糟糕：单行上的长方法链

$result = $database->table('users')->select('name', 'email')->where('active', true)->orderBy('created_at', 'desc')->limit(10)->get();

```

良好的代码示例将长方法链拆分为多行，每个方法调用都占新行并进行缩进。这通过更容易看到链中的每一步改进了可读性。糟糕的代码示例将所有内容放在同一行，使得更难阅读和理解单个方法调用。

<Memo>
许多现代 IDE 都有助于拆分长方法链。
</Memo>

# 使用中间变量解释复杂计算

通过为复杂计算使用中间变量来提高代码清晰度。

以下代码展示了如何使用中间变量使计算清晰：

### 良好的代码

```php
// 良好：使用中间变量

$basePrice = 100;

$taxRate = 0.08;

$discountPercentage = 0.1;

$priceAfterDiscount = $basePrice * (1 - $discountPercentage);

$taxAmount = $priceAfterDiscount * $taxRate;

$finalPrice = $priceAfterDiscount + $taxAmount;

echo "Final price: " . number_format($finalPrice, 2);

```

### 糟糕的代码

```php
// 糟糕：没有中间变量的复杂计算

echo "Final price: " . number_format(100 * (1 - 0.1) * 1.08, 2);

```

使用意义的变量不仅提高了可读性，还可以作为文档。

# 将复杂的正则表达式提取为命名常量

通过为正则表达式使用命名常量提高代码可读性。

以下代码演示了如何将复杂的正则表达式提取为命名常量，以提高可读性和维护性。

### 良好的代码

```php
<?php

// 为正则表达式定义命名常量

const EMAIL_REGEX = '/^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/i';

// 在代码中使用命名常量

function validateEmail($email) {

    // 检查邮箱是否匹配定义的模式

    if (preg_match(EMAIL_REGEX, $email)) {

        return true;

    }

    return false;

}

// 示例

$email = 'user@example.com';

if (validateEmail($email)) {

    echo "Valid email address";

} else {

    echo "Invalid email address";

}

```

### 糟糕的代码

```php
<?php

// 函数中直接使用复杂的正则表达式

function validateEmail($email) {

    // 直接在 preg_match 函数中使用复杂的正则表达式

    if (preg_match('/^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$/i', $email)) {

        return true;

    }

    return false;

}

// 示例

$email = 'user@example.com';

if (validateEmail($email)) {

    echo "Valid email address";

} else {

    echo "Invalid email address";

}

```

# 使用数组解构一次性为多个变量来简化代码

以下代码演示了如何在 PHP 中使用数组解构进行更整洁的多变量赋值。

### 良好的代码

```php
// 返回用户详情数组的函数

function getUserDetails() {

    return ['John Doe', 30, 'john@example.com'];

}

// 使用数组解构赋值多个变量

[$name, $age, $email] = getUserDetails();

// 使用赋值后的变量

echo "Name: $name, Age: $age, Email: $email";

```

### 坏的代码

```php
// 返回用户详情数组的函数

function getUserDetails() {

    return ['John Doe', 30, 'john@example.com'];

}

// 逐个赋值

$userDetails = getUserDetails();

$name = $userDetails[0];

$age = $userDetails[1];

$email = $userDetails[2];

// 使用赋值后的变量

echo "Name: $name, Age: $age, Email: $email";

```

良好的代码示例使用数组解构在单行内为多个变量赋值，使代码更加简洁且易于读。坏的代码示例逐个赋值每个变量，这过于冗长，并且当数组结构发生变化时容易出错。

### 备忘

数组解构是在 PHP 7.1 中引入的，提供了一种将数组拆分为独立变量的方便方法。

# 使用空合并赋值运算符 (??=) 实现简洁的默认赋值

在 PHP 7.4+ 中使用 `??=` 高效地分配默认值。

以下代码演示了如何使用空合并赋值运算符 (`??=`) 为变量设置默认值：

### 良好的代码

```php
// 使用空合并赋值运算符的良好代码

function getUserSettings($userId) {

    $settings = fetchUserSettings($userId);

    // 使用 ??= 设置默认值

    $settings['theme'] ??= 'light';

    $settings['notifications'] ??= true;

    $settings['language'] ??= 'en';

    return $settings;

}

```

### 坏的代码

```php
// 未使用空合并赋值运算符的坏代码

function getUserSettings($userId) {

    $settings = fetchUserSettings($userId);

    // 使用传统方法设置默认值

    if (!isset($settings['theme'])) {

        $settings['theme'] = 'light';

    }

    if (!isset($settings['notifications'])) {

        $settings['notifications'] = true;

    }

    if (!isset($settings['language'])) {

        $settings['language'] = 'en';

    }

    return $settings;

}

```

良好的代码示例使用 `??=` 简洁地为键设置默认值。该运算符仅在左侧变量为 null 或不存在时才分配右侧的值。与使用传统 `if` 语句的坏代码相比，它更具可读性并减少了代码行数。

### 备忘

空合并赋值运算符 (`??=`) 在 PHP 7.4 中引入的，作为检查并分配默认值常用模式的简写。

# 将配置提取到单独的文件

通过将配置与逻辑分离提高可维护性。

以下示例展示了如何将设置提取到单独的文件：

### 良好的代码

```php
// config.php

return [

    'database' => [

        'host' => 'localhost',

        'username' => 'user',

        'password' => 'password',

        'dbname' => 'myapp'

    ],

    'api_key' => 'your_api_key_here',

    'debug_mode' => true

];

// main.php

$config = require 'config.php';

// 使用配置

$dbHost = $config['database']['host'];

$apiKey = $config['api_key'];

```

### 坏的代码

```php
// 坏做法：将配置与应用逻辑混合

$dbHost = 'localhost';

$dbUsername = 'user';

$dbPassword = 'password';

$apiKey = 'your_api_key_here';

$debugMode = true;

// 应用逻辑

function connectToDatabase() {

    global $dbHost, $dbUsername, $dbPassword;

    // 此处进行数据库连接

}

function makeApiCall() {

    global $apiKey;

    // 此处调用 API

}

```

良好的代码示例将配置分离到专用的 `config.php` 中，该文件返回一个设置数组。这种方法使得在不修改主应用代码的情况下，更容易管理和更新配置。坏的代码将配置直接与应用逻辑混合，使得在整个应用程序中维护和更新设置变得困难。

### 备忘

将配置与代码分离是 12 要素应用方法中的核心原则，该方法旨在构建可扩展和可维护的软件服务（SaaS）应用。

# 将工具函数移动到单独的类或命名空间

将工具函数组织到专用的类或命名空间中，以提高代码的可读性和维护性。

工具函数通常应用于应用的多个部分。通过将它们移动到单独类或命名空间，你可以保持代码库的整洁和模块化，便于他人理解和维护。

### 良好的代码

```php
<?php

namespace App\Utils;

/**

 * 通用函数的工具类

 */

class StringUtils {

    /**

     * 将字符串转换为驼峰式

     *

     * @param string $string

     * @return string

     */
```



# 将工具函数封装在命名空间类中

将工具函数组织到命名空间类中，以避免全局命名空间污染并防止命名冲突。

## 良好的代码

```php
<?php

namespace App\Utils;

/**
 * 字符串工具类
 */
class StringUtils
{
    /**
     * 将字符串转换为驼峰式
     *
     * @param string $string
     * @return string
     */
    public static function toCamelCase(string $string): string
    {
        $result = strtolower($string);
        preg_match_all('/[a-zA-Z0-9]+/', $result, $matches);
        $result = $matches[0][0];
        for ($i = 1; $i < count($matches[0]); $i++) {
            $result .= ucfirst($matches[0][$i]);
        }
        return $result;
    }
}

// 使用
echo App\Utils\StringUtils::toCamelCase('hello_world'); // 输出：helloWorld
?>
```

## 坏的代码

```php
<?php

/**
 * 将字符串转换为驼峰式
 *
 * @param string $string
 * @return string
 */
function toCamelCase($string)
{
    $result = strtolower($string);
    preg_match_all('/[a-zA-Z0-9]+/', $result, $matches);
    $result = $matches[0][0];
    for ($i = 1; $i < count($matches[0]); $i++) {
        $result .= ucfirst($matches[0][$i]);
    }
    return $result;
}

// 使用
echo toCamelCase('hello_world'); // 输出：helloWorld
?>
```

在良好的示例中，工具函数 `toCamelCase` 被封装在 `App\Utils` 命名空间的 `StringUtils` 类中。这种组织方式使工具函数的位置清晰并避免了命名冲突。在坏示例中，函数定义在全局作用域，这会导致大型代码库变得混乱。

## 备忘

PHP 命名空间是在 5.3 版本引入的，有助于避免冲突并将代码组织成逻辑组。

---

# 使用 Trait 共享通用功能

使用 Trait 在不使用继承的情况下跨多个类复用方法。

## 良好的代码

```php
<?php

trait Logger
{
    /**
     * 记录消息
     *
     * @param string $message
     */
    public function log(string $message): void
    {
        echo "[LOG]: " . $message . "\n";
    }
}

class User
{
    use Logger;

    public function createUser(): void
    {
        // 用户创建逻辑
        $this->log("User created successfully.");
    }
}

class Product
{
    use Logger;

    public function createProduct(): void
    {
        // 产品创建逻辑
        $this->log("Product created successfully.");
    }
}

// 使用示例
$user = new User();
$user->createUser(); // 输出: [LOG]: User created successfully.

$product = new Product();
$product->createProduct(); // 输出: [LOG]: Product created successfully.
?>
```

## 坏的代码

```php
<?php

class User
{
    /**
     * 记录消息
     *
     * @param string $message
     */
    public function log(string $message): void
    {
        echo "[LOG]: " . $message . "\n";
    }

    public function createUser(): void
    {
        // 用户创建逻辑
        $this->log("User created successfully.");
    }
}

class Product
{
    /**
     * 记录消息
     *
     * @param string $message
     */
    public function log(string $message): void
    {
        echo "[LOG]: " . $message . "\n";
    }

    public function createProduct(): void
    {
        // 产品创建逻辑
        $this->log("Product created successfully.");
    }
}

// 使用示例
$user = new User();
$user->createUser(); // 输出: [LOG]: User created successfully.

$product = new Product();
$product->createProduct(); // 输出: [LOG]: Product created successfully.
?>
```

在良好的示例中，`Logger` trait 封装了日志记录功能，该功能被 `User` 和 `Product` 类共享。这促进了代码复用，并保持了不同类之间日志逻辑的一致性。在糟糕的示例中，日志方法在两个类中重复出现，导致了代码冗余和潜在的不一致性。

## 备忘

Traits 在 PHP 5.4 中引入，允许开发者在不使用继承的情况下跨多个类复用方法，为共享功能提供了一种灵活的方式。

---

# 将缓存机制实现为独立的类

将缓存逻辑分离到专门的类中以提高模块化和可维护性。

以下代码演示了如何在 PHP 中将缓存机制实现为独立的类：

## 良好的代码

```php
// CacheInterface.php
interface CacheInterface
{
    public function get($key);
    public function set($key, $value, $ttl = 3600);
}

// FileCache.php
class FileCache implements CacheInterface
{
    private $cacheDir;
    private $ttl = 3600; // 添加缺失的属性

    public function __construct($cacheDir)
    {
        $this->cacheDir = $cacheDir;
    }

    public function get($key)
    {
        $filename = $this->getCacheFilename($key);
        if (file_exists($filename) && (filemtime($filename) + $this->ttl) > time()) {
            return unserialize(file_get_contents($filename));
        }
        return null;
    }

    public function set($key, $value, $ttl = 3600)
    {
        $filename = $this->getCacheFilename($key);
        file_put_contents($filename, serialize($value));
    }

    private function getCacheFilename($key)
    {
        return $this->cacheDir . '/' . md5($key) . '.cache';
    }
}

// 使用
$cache = new FileCache('/path/to/cache');
$data = $cache->get('my_key');
if ($data === null) {
    $data = []; // ... 获取数据的昂贵操作
    $cache->set('my_key', $data, 3600); // 缓存 1 小时
}
```

## 坏的代码

```php
// 糟糕的示例：缓存逻辑与业务逻辑混合
function getUserData($userId)
{
    $cacheFile = '/tmp/user_' . $userId . '.cache';
    if (file_exists($cacheFile) && (filemtime($cacheFile) + 3600) > time()) {
        return unserialize(file_get_contents($cacheFile));
    }

    // 从数据库获取用户
    $userData = fetchFromDatabase($userId);

    // 缓存数据
    file_put_contents($cacheFile, serialize($userData));
    return $userData;
}
```

良好的示例将缓存机制分离到独立的类（`FileCache`），这允许轻松切换实现方式（例如 Redis 或 Memcached）。糟糕的示例将缓存逻辑与业务逻辑混合，使其难以维护和测试。

## 备忘

缓存对于性能至关重要，PHP 支持各种机制，包括 APCu。

---

# 将验证逻辑提取到类中

将验证逻辑分离到独立类以提高组织结构。

以下代码演示了如何将验证逻辑提取到独立类：

## 良好的代码

```php
// UserValidator.php
class UserValidator
{
    public function validateUsername($username)
    {
        if (strlen($username) < 3 || strlen($username) > 20) {
            throw new ValidationException("用户名长度在 3 到 20 字符之间。");
        }
        if (!preg_match('/^[a-zA-Z0-9_]+$/', $username)) {
            throw new ValidationException("用户名只能包含字母、数字和下划线。");
        }
    }

    public function validateEmail($email)
    {
        if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
            throw new ValidationException("邮箱格式无效。");
        }
        // 额外的验证逻辑（例如域名检查）可以放在此处
    }

    public function validatePassword($password)
    {
        if (strlen($password) < 8) {
            throw new ValidationException("密码至少需要 8 个字符。");
        }
        if (!preg_match('/[A-Z]/', $password) || !preg_match('/[a-z]/', $password) || !preg_match('/[0-9]/', $password)) {
            throw new ValidationException("密码必须包含一个大写字母、一个小写字母和一个数字。");
        }
    }
}

// 使用
$validator = new UserValidator();
try {
    $validator->validateUsername($username);
    $validator->validateEmail($email);
    $validator->validatePassword($password);
    // 继续注册
} catch (ValidationException $e) {
    // 处理验证错误
    echo $e->getMessage();
}
```

## 坏的代码

```php
// 糟糕的示例：验证与用户注册混合
function registerUser($username, $email, $password)
{
    // 用户名验证
    if (strlen($username) < 3 || strlen($username) > 20) {
        return "用户名长度在 3 到 20 字符之间。";
    }
    if (!preg_match('/^[a-zA-Z0-9_]+$/', $username)) {
        return "用户名只能包含字母、数字和下划线。";
    }

    // 邮箱验证
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        return "邮箱格式无效。";
    }

    // 密码验证
    if (strlen($password) < 8) {
        return "密码至少需要 8 个字符。";
    }
    if (!preg_match('/[A-Z]/', $password) || !preg_match('/[a-z]/', $password) || !preg_match('/[0-9]/', $password)) {
        return "密码必须包含一个大写字母、一个小写字母和一个数字。";
    }

    // 继续注册
    // ...
}
```

---

# 使用联合类型增强类型提示

联合类型允许为参数或返回值指定多种可能的类型，从而增强了代码的清晰性和类型安全。

以下代码演示了如何在 PHP 8.0+ 中使用联合类型来改进类型提示：

## 良好的代码

```php
/**
 * 计算订单总价
 *
 * @param array $items 订单项数组
 * @param float|int $taxRate 以小数或百分比表示税率
 * @return float 包含税费的价格
 */
function calculateTotalPrice(array $items, float|int $taxRate): float
{
    $subtotal = array_sum(array_column($items, 'price'));
    // 必要时将百分比转换为小数
    $taxRateDecimal = $taxRate > 1 ? $taxRate / 100 : $taxRate;
    $taxAmount = $subtotal * $taxRateDecimal;
    $total = $subtotal + $taxAmount;
    return round($total, 2);
}

// 使用示例
$orderItems = [
    ['name' => 'Widget A', 'price' => 10.99],
    ['name' => 'Widget B', 'price' => 15.50],
];

echo calculateTotalPrice($orderItems, 0.08); // 小数形式税率
echo calculateTotalPrice($orderItems, 8);     // 百分比形式税率
```

## 不良的代码

```php
function calculateTotalPrice($items, $taxRate)
{
    $t = 0;
    foreach ($items as $i) {
        $t += $i['price'];
    }
    return $t + $t * ($taxRate > 1 ? $taxRate / 100 : $taxRate);
}

$orderItems = [
    ['name' => 'Widget A', 'price' => 10.99],
    ['name' => 'Widget B', 'price' => 15.50],
];

echo calculateTotalPrice($orderItems, 0.08);
echo calculateTotalPrice($orderItems, 8);
```

良好的代码示例为 `$taxRate` 参数使用了联合类型（`float|int`），允许其接受小数和百分比值。它还包含了详细的 docblock、具描述性的变量名以及清晰的逻辑。不良的代码缺乏类型提示，使用了模糊的变量名，且逻辑可读性较低。

## 备忘

联合类型在 PHP 8.0 中引入，提供了为单个参数或返回值指定多种可能类型的方法。

---

# 为自定义对象序列化实现 `__serialize` 和 `__unserialize`

使用 `__serialize` 和 `__unserialize` 魔法方法可以对对象的序列化和反序列化过程进行更多控制。

以下代码演示了如何为自定义序列化实现 `__serialize` 和 `__unserialize`：

## 良好的代码

```php
/**
 * 系统中的用户
 */
class User
{
    private string $username;
    private string $email;
    private array $preferences;

    public function __construct(string $username, string $email)
    {
        $this->username = $username;
        $this->email = $email;
        $this->preferences = [];
    }

    /**
     * 序列化方法
     *
     * @return array
     */
    public function __serialize(): array
    {
        return [
            'username' => $this->username,
            'email' => $this->email,
            'preferences' => $this->preferences,
        ];
    }

    /**
     * 反序列化方法
     *
     * @param array $data
     */
    public function __unserialize(array $data): void
    {
        $this->username = $data['username'];
        $this->email = $data['email'];
        $this->preferences = $data['preferences'];
    }
}
```



# PHP 高级特性与最佳实践

## 使用 `__serialize` 和 `__unserialize` 进行自定义序列化

实现 `__serialize` 和 `__unserialize` 魔术方法以控制对象的序列化与反序列化过程。

### 良好的代码
```php
class User
{
    private $username;
    private $email;
    private $preferences;

    public function __construct(string $username, string $email)
    {
        $this->username = $username;
        $this->email = $email;
        $this->preferences = [];
    }

    public function __serialize(): array
    {
        return [
            'username' => $this->username,
            'email' => $this->email,
            'preferences' => $this->preferences,
        ];
    }

    /**
     * 反序列化方法
     * @param array $data
     */
    public function __unserialize(array $data): void
    {
        $this->username = $data['username'];
        $this->email = $data['email'];
        $this->preferences = $data['preferences'] ?? [];
    }

    // 其他方法...
}

// 使用
$user = new User('johndoe', 'john@example.com');
$serialized = serialize($user);
$unserialized = unserialize($serialized);
var_dump($unserialized);
```

### 不良好的代码
```php
class User
{
    public $u;
    public $e;
    private $p;

    function __construct($u, $e)
    {
        $this->u = $u;
        $this->e = $e;
        $this->p = [];
    }
}

$user = new User('johndoe', 'john@example.com');
$s = serialize($user);
$u = unserialize($s);
var_dump($u);
```

良好的代码示例实现了 `__serialize` 和 `__unserialize` 方法，提供了对哪些属性被序列化以及如何重建的控制。它使用了清晰的属性名并包含了类型声明。不良好的代码依赖 PHP 的默认序列化，可能会暴露内部属性且无法很好处理复杂对象。

**备忘**
`__serialize` 和 `__unserialize` 魔术方法在 PHP 7.4 中引入，作为旧 `Serializable` 接口更高效的替代方案。

## 使用 Reflection API 进行动态代码分析

利用 PHP 的反射（Reflection）API 在运行时分析并操作代码结构。

以下代码演示了如何使用 Reflection API 检查类及其方法：

### 良好的代码
```php
// 使用 Reflection API 的良好示例

class MyClass
{
    public function myMethod($param1, $param2 = null)
    {
        // 方法实现
    }
}

// 使用 Reflection 分析类
$reflection = new ReflectionClass('MyClass');

// 获取类信息
echo "Class name: " . $reflection->getName() . "\n";

// 分析方法
foreach ($reflection->getMethods() as $method) {
    echo "Method: " . $method->getName() . "\n";

    // 分析方法参数
    foreach ($method->getParameters() as $param) {
        echo $param->getName() . "\n";
    }
}
```

### 不良好的代码
```php
// 未使用 Reflection API 的良好示例

class MyClass
{
    public function myMethod($param1, $param2 = null)
    {
        // 方法实现
    }
}

// 手动尝试分析类
$className = 'MyClass';
echo "Class name: " . $className . "\n";

// 尝试获取方法
$methods = get_class_methods($className);
foreach ($methods as $method) {
    echo "Method: " . $method . "\n";
}
```

良好的示例使用 Reflection API 动态分析类。它提供了关于方法和参数的详细信息。不良好的示例尝试手动分析类，范围有限。

**备忘**
Reflection API 在 PHP 5 中引入并一直在不断改进，使其成为元编程和代码分析的强大工具。

## 使用 `__set_state` 魔术方法以兼容 `var_export`

实现 `__set_state` 魔术方法以确保使用 `var_export()` 时正确的对象重建。

以下代码展示了如何实现 `__set_state` 以获得更好的 `var_export()` 支持：

### 良好的代码
```php
// 实现 __set_state 的良好示例

class ConfigObject
{
    private $data;

    public function __construct(array $data)
    {
        $this->data = $data;
    }

    public static function __set_state($array)
    {
        return new self($array['data']);
    }

    public function getData()
    {
        return $this->data;
    }
}

// 使用
$config = new ConfigObject(['key' => 'value']);
$exported = var_export($config, true);
eval('$importedConfig = ' . $exported . ';');

// $importedConfig 现在是一个正确的 ConfigObject 实例
var_dump($importedConfig->getData()); // 输出: array(1) { ["key"]=> string(5) "value" }
```

### 不良好的代码
```php
// 未实现 __set_state 的良好示例

class ConfigObject
{
    private $data;

    public function __construct(array $data)
    {
        $this->data = $data;
    }

    public function getData()
    {
        return $this->data;
    }
}

// 使用
$config = new ConfigObject(['key' => 'value']);
$exported = var_export($config, true);
eval('$importedConfig = ' . $exported . ';');

// $importedConfig 不是正确的 ConfigObject 实例
// 尝试使用它会导致错误
var_dump($importedConfig->getData()); // 这会导致错误
```

良好的示例实现了 `__set_state` 魔术方法，这使得对象在配合 `var_export()` 使用时能够被正确地重构。该方法返回一个带有导出数据的新类实例，确保了对象的状态被正确恢复。

不佳的示例缺少 `__set_state` 方法。当对此对象使用 `var_export()` 并求值结果时，它会创建一个 `stdClass` 对象而不是 `ConfigObject` 实例。这会导致在尝试使用 `ConfigObject` 类特定的方法时发生错误。

**备忘**
`__set_state` 魔术方法是在 PHP 5.1.0 中引入的，专门用于解决 `var_export()` 和对象序列化的问题。

## 利用 `__clone` 魔术方法进行正确的对象克隆

实现 `__clone` 魔术方法以确保对象的深拷贝。

以下代码演示了用于对象克隆的 `__clone` 魔术方法的正确用法：

### 良好的代码
```php
class User
{
    public $name;
    public $address;

    public function __construct($name)
    {
        $this->name = $name;
        $this->address = new Address();
    }

    // 实现 __clone 魔术方法进行深拷贝
    public function __clone()
    {
        // 为克隆的 User 创建新的 Address 实例
        $this->address = clone $this->address;
    }
}

class Address
{
    public $street;
    public $city;
}

// 使用
$user1 = new User("John");
$user1->address->street = "123 Main St";
$user1->address->city = "New York";

$user2 = clone $user1;
$user2->name = "Jane";
$user2->address->street = "456 Elm St";

// 输出结果
echo $user1->name . " lives at " . $user1->address->street . "\n";
echo $user2->name . " lives at " . $user2->address->street . "\n";
```

### 不良好的代码
```php
class User
{
    public $name;
    public $address;

    public function __construct($name)
    {
        $this->name = $name;
        $this->address = new Address();
    }

    // 没有实现 __clone 方法
}

class Address
{
    public $street;
    public $city;
}

// 使用
$user1 = new User("John");
$user1->address->street = "123 Main St";
$user1->address->city = "New York";

$user2 = clone $user1;
$user2->name = "Jane";
$user2->address->street = "456 Elm St";

// 输出结果
echo $user1->name . " lives at " . $user1->address->street . "\n";
echo $user2->name . " lives at " . $user2->address->street . "\n";
```

在良好的代码示例中，`User` 类中实现了 `__clone` 魔术方法。这确保了在克隆对象时，会对像 `Address` 这样的嵌套对象创建深拷贝。不佳的代码示例缺少 `__clone` 方法，导致浅拷贝，使得两个 `User` 对象共享同一个 `Address` 实例。这在修改嵌套对象的属性时可能会导致意想不到的行为。

**备忘**
`__clone` 魔术方法是在 PHP 5 中引入的，旨在对对象克隆过程提供更多控制。

## 使用关联数组处理键值对

利用关联数组通过有意义的键来存储和访问数据。

以下代码演示了使用关联数组管理键值对的有效方法：

### 良好的代码
```php
// 使用关联数组存储用户信息
$user = [
    'name' => 'John Doe',
    'age' => 30,
    'email' => 'john@example.com',
    'roles' => ['admin', 'editor']
];

// 访问并显示用户信息
echo "Name: " . $user['name'] . "\n";
echo "Age: " . $user['age'] . "\n";
echo "Email: " . $user['email'] . "\n";
echo "Roles: " . implode(', ', $user['roles']) . "\n";

// 添加新的键值对
$user['location'] = 'New York';

// 检查键是否存在
if (isset($user['location'])) {
    echo "Location: " . $user['location'] . "\n";
} else {
    echo "Not provided";
}
```

### 不良好的代码
```php
// 使用独立变量存储信息
$name = 'John Doe';
$age = 30;
$email = 'john@example.com';
$role1 = 'admin';
$role2 = 'editor';

// 显示信息
echo "Name: " . $name . "\n";
echo "Age: " . $age . "\n";
echo "Email: " . $email . "\n";
echo "Roles: " . $role1 . ", " . $role2 . "\n";

// 添加新信息
$location = 'New York';

// 检查变量是否设置
if (isset($location)) {
    echo "Location: " . $location . "\n";
} else {
    echo "Not provided";
}
```

良好的代码示例使用关联数组来存储用户信息，使其易于管理和访问数据。键是有意义的。不佳的代码示例使用了独立变量，随着数据点的增加会变得非常臃肿。关联数组简化了添加新键值对和检查特定键的操作。

**备忘**
PHP 中的关联数组是作为有序映射实现的，它们保持元素的插入顺序。

## 采用 `SplFixedArray` 实现内存高效数组

使用 `SplFixedArray` 为数值数组提供更好的内存管理。

以下代码演示了如何使用 `SplFixedArray` 创建内存高效数组：

### 良好的代码
```php
// 使用 SplFixedArray 的良好示例
$size = 1000000;

// 创建固定大小的数组
$array = new SplFixedArray($size);

// 填充数组
for ($i = 0; $i < $size; $i++) {
    $array[$i] = $i * 2;
}

// 访问元素
echo "Element at index 500000: " . $array[500000] . "\n";

// 内存占用
echo "Memory usage: " . memory_get_usage(true) / 1024 / 1024 . " MB";
```

### 不良好的代码
```php
// 使用标准数组的不佳示例
$size = 1000000;

// 创建标准数组
$array = array();

// 填充数组
for ($i = 0; $i < $size; $i++) {
    $array[$i] = $i * 2;
}

// 访问元素
echo "Element at index 500000: " . $array[500000] . "\n";

// 内存占用
echo "Memory usage: " . memory_get_usage(true) / 1024 / 1024 . " MB";
```

良好的示例使用了 `SplFixedArray`，对于大型数值数组来说更节省内存。它为固定数量的元素预分配了内存，减少了开销。不佳的示例使用了标准的 PHP 数组，虽然更灵活，但对于大型数据集会消耗更多内存。

**备忘**
`SplFixedArray` 是在 PHP 5.3 中引入的，是标准 PHP 库（SPL）的一部分。

## 使用 `SplObjectStorage` 基于对象的哈希表

实现 `SplObjectStorage` 以构建基于对象的哈希表。

以下代码说明了使用 `SplObjectStorage` 创建高效基于对象的哈希表：

### 良好的代码
```php
// 使用 SplObjectStorage 的良好示例
$storage = new SplObjectStorage();

// 创建示例对象
```



$obj1 = new stdClass();

$obj2 = new stdClass();

$obj3 = new stdClass();

// 存储关联数据的对象

$storage[$obj1] = 'Data for object 1';

$storage[$obj2] = 'Data for object 2';

$storage[$obj3] = 'Data for object 3';

// 检查对象是否存在并检索其数据

if ($storage->contains($obj2)) {

    echo "Data for obj2: " . $storage[$obj2] . "\n";

}

// 遍历存储器

foreach ($storage as $obj) {

    echo "Object data: " . $storage[$obj] . "\n";

}

// 计数对象

echo "Number of objects: " . count($storage) . "\n";

```

```php

echo "Data for obj2: " . $storage[spl_object_hash($obj2)] . "\n";

}

// 遍历存储（繁琐）

foreach ($storage as $hash => $data) {

    echo "Object data: " . $data . "\n";

}

// 计数对象

echo "Number of objects: " . count($storage) . "\n";

```

良好的示例使用了 `SplObjectStorage`，它是专门为了高效地存储和检索对象而设计的。它允许直接使用对象作为键，并提供了内置的对象管理方法。而糟糕的示例尝试使用标准数组和 `spl_object_hash()` 来模拟这种行为，这种效率较低且更容易出现错误。

> **Memo**
> `SplObjectStorage` 实现了 `Countable`、`Iterator`、`Serializable` 和 `ArrayAccess` 接口，使其适用于各种用例。

# 为类数组对象行为实现 ArrayAccess

实现 `ArrayAccess` 接口以允许像数组一样访问对象。

以下代码演示了如何实现 `ArrayAccess` 接口来创建一个行为像数组的对象：

### 良好的代码

```php

<?php

// 良好的示例：为自定义对象实现 ArrayAccess

class CustomArray implements ArrayAccess {

    private $container = array();

    // 检查偏移是否存在

    public function offsetExists($offset): bool {

        return isset($this->container[$offset]);

    }

    // 获取给定偏移处的值

    public function offsetGet($offset): mixed {

        return isset($this->container[$offset]) ? $this->container[$offset] : null;

    }

    // 在给定偏移处设置值

    public function offsetSet($offset, $value): void {

        if (is_null($offset)) {

            $this->container[] = $value;

        } else {

            $this->container[$offset] = $value;

        }

    }

    // 取消给定偏移处的值

    public function offsetUnset($offset): void {

        unset($this->container[$offset]);

    }

}

// 使用示例

$obj = new CustomArray();

$obj['key'] = 'value';

echo $obj['key']; // 输出: value

```

### 糟糕的代码

```php

<?php

// 糟糕的示例：没有实现 ArrayAccess，而是使用了魔术方法

class BadCustomArray {

    private $container = array();

    public function __set($name, $value) {

        $this->container[$name] = $value;

    }

    public function __get($name) {

        return $this->container[$name];

    }

}

// 使用示例

$obj = new BadCustomArray();

$obj->key = 'value'; // 可以用，但不是类数组语法

echo $obj->key; // 输出: value

```

良好的示例实现了 `ArrayAccess` 接口，允许使用数组语法操作对象。这使得代码更加直观，并与数组操作保持一致。糟糕的示例使用了魔术方法，虽然可行但没有提供真正的类数组语法，且性能可能较低。

> **Memo**
> `ArrayAccess` 接口在 PHP 5.0 中引入，是标准 PHP 库 (SPL) 的一部分。

# 使用 SplQueue 和 SplStack 实现高效的 FIFO 和 LIFO 操作

利用 `SplQueue` 和 `SplStack` 实现高效的先进先出（FIFO）和后进先出（LIFO）操作。

以下代码演示了使用 `SplQueue` 和 `SplStack` 进行高效的队列和栈操作：

### 良好的代码

```php

<?php

// 良好的示例：使用 SplQueue 和 SplStack 进行 FIFO 和 LIFO 操作

// 使用 SplQueue 进行 FIFO 操作

$queue = new SplQueue();

$queue->enqueue('First');

$queue->enqueue('Second');

$queue->enqueue('Third');

echo "Queue (FIFO):\n";

while (!$queue->isEmpty()) {

    echo $queue->dequeue() . "\n";

}

// 使用 SplStack 进行 LIFO 操作

$stack = new SplStack();

$stack->push('First');

$stack->push('Second');

$stack->push('Third');

echo "\nStack (LIFO):\n";

while (!$stack->isEmpty()) {

    echo $stack->pop() . "\n";

}

```

### 糟糕的代码

```php

<?php

// 糟糕的示例：使用数组实现队列和栈

// 使用数组进行 FIFO 操作

$queue = [];

array_push($queue, 'First');

array_push($queue, 'Second');

array_push($queue, 'Third');

echo "Queue (FIFO):\n";

while (!empty($queue)) {

    echo array_shift($queue) . "\n";

}

// 使用数组进行 LIFO 操作

$stack = [];

array_push($stack, 'First');

array_push($stack, 'Second');

array_push($stack, 'Third');

echo "\nStack (LIFO):\n";

while (!empty($stack)) {

    echo array_pop($stack) . "\n";

}

```

良好的示例使用了 `SplQueue` 和 `SplStack`，它们分别针对 FIFO 和 LIFO 操作进行了优化。这些类为队列和栈提供了更好的性能和更合适的方法。糟糕的示例使用了 `array_push`、`array_shift` 和 `array_pop`，在处理大型数据集时效率较低，且缺乏语义清晰度。

> **Memo**
> `SplQueue` 和 `SplStack` 是标准 PHP 库 (SPL) 的一部分。

# 为预期异常使用 try-catch

实现 `try-catch` 块以处理预期异常。

以下代码演示了如何使用 `try-catch` 来处理文件操作：

### 良好的代码

```php

<?php

// 良好的示例：对文件操作使用 try-catch

try {

    // 尝试打开文件

    $file = fopen('important_data.txt', 'r');

    if ($file === false) {

        // 如果打开失败，抛出异常

        throw new Exception('无法打开文件。');

    }

    // 读取文件内容

    $content = fread($file, filesize('important_data.txt'));

    // 关闭文件

    fclose($file);

    // 处理内容

    echo "File contents: " . $content;

} catch (Exception $e) {

    // 处理异常

    error_log("Error: " . $e->getMessage());

    echo "读取文件时发生错误。";

} finally {

    // 如果成功打开，则确保关闭

    if (isset($file) && $file !== false) {

        fclose($file);

    }

}

```

### 糟糕的代码

```php

<?php

// 糟糕的示例：对文件操作未使用 try-catch

$file = fopen('important_data.txt', 'r');

$content = fread($file, filesize('important_data.txt'));

fclose($file);

echo "File contents: " . $content;

```

良好的示例使用了 `try-catch` 块来处理文件操作潜在异常。它检查文件是否成功打开、读取内容并确保正确关闭。如果发生错误，异常会被捕获并处理。糟糕的示例没有处理潜在错误，如果文件无法打开或读取，可能会导致意外行为或崩溃。

```php

error_log("Query Execution Error: " . $e->getMessage());

return null;

}

}

```

### 使用

```php

$userData = fetchUserData(123);

if ($userData === null) {

    echo "An error occurred while fetching user data.";

} else {

    echo $userData;

}

```

### 错误代码

```php

// 错误示例：没有使用自定义异常类

function fetchUserData($userId) {

    // 模拟数据库连接

    if (rand(0, 1) == 0) {

        return "Database connection error";

    }

    // 模拟查询执行

    if (rand(0, 1) == 0) {

        return "Query execution error";

    }

    // 模拟成功获取数据

    return "User data for ID: " . $userId;

}

// 使用

$result = fetchUserData(123);

echo $result;

```

良好的示例为特定的错误类型定义了自定义异常类（`DatabaseConnectionException` 和 `QueryExecutionException`）。这允许进行精确的错误处理和记录。函数使用这些自定义异常来提供有关发生错误的详细信息。而错误示例简单地返回错误字符串，使得难以区分不同类型的错误并对其进行适当处理。

> **Memo**
> PHP 中的自定义异常可以扩展内置的 `Exception` 类或其任何子类，允许异常类型的分层结构。

# 使用 finally 块进行清理操作

实现 `finally` 块以确保无论是否发生异常，都能进行资源清理。

以下代码演示了如何在 PHP 中使用 `finally` 块进行妥善的文件处理：

### 良好的代码

```php

<?php

// 良好示例：使用 finally 块进行清理

try {

    // 打开文件

    $file = fopen('example.txt', 'r');

    // 对文件进行操作

    $content = fread($file, filesize('example.txt'));

    // 处理内容

    echo "File content: " . $content;

} catch (Exception $e) {

    // 处理任何异常

    echo "An error occurred: " . $e->getMessage();

} finally {

    // 无论是否发生异常，都确保文件关闭

    if (isset($file) && is_resource($file)) {

        fclose($file);

        echo "File closed successfully.";

    }

}

?>

```

### 错误代码

```php

<?php

// 错误示例：没有使用 finally 块

$file = fopen('example.txt', 'r');

try {

    // 对文件进行操作

    $content = fread($file, filesize('example.txt'));

    // 处理内容

    echo "File content: " . $content;

    // 关闭文件

    fclose($file);

} catch (Exception $e) {

    // 处理任何异常

    echo "An error occurred: " . $e->getMessage();

    // 尝试关闭文件，但不总能执行

    if (is_resource($file)) {

        fclose($file);

    }

}

?>

```

良好的代码使用 `finally` 块来确保无论是否发生异常，文件始终被关闭。这防止了泄漏并遵循了资源管理的最佳实践。错误代码尝试在 `try` 和 `catch` 块中都关闭文件，这可能导致代码重复，并且如果开发者忘记在所有地方添加清理代码，就会产生疏漏。

> **Memo**
> `finally` 块在 PHP 5.5 中引入，是异常处理机制的一部分，提供了一种无论是否抛出或捕获异常都能执行代码的方法。

# 在 catch 块中实现日志以便调试

使用 `catch` 块记录错误信息，以便调试和维护。

以下代码演示了如何在 `catch` 块中实现日志：

### 良好的代码

```php

<?php

// 良好示例：在 catch 块中实现日志

require_once 'path/to/library.php';

function processUserData($userId) {

    try {

        // 模拟数据库操作

        $userData = fetchUserDataFromDatabase($userId);

        // 处理用户数据

        $result = performComplexOperation($userData);

        return $result;

    } catch (DatabaseException $e) {

        // 记录数据库相关错误

        Logger::error("Database error occurred: " . $e->getMessage(), [

            'userId' => $userId,

            'errorCode' => $e->getCode(),

            'stackTrace' => $e->getTraceAsString()

        ]);

        throw $e; // 如果需要重新抛出异常

    } catch (Exception $e) {

        // 记录通用错误

        Logger::error("An unexpected error occurred: " . $e->getMessage(), [

            'userId' => $userId,

            'errorCode' => $e->getCode(),



'stackTrace' => $e->getTraceAsString()

        ]);

        throw $e; // 如果需要重新抛出异常

    }

}

```

### 错误代码

```php
<?php

// 错误示例：在 catch 块中没有实现适当日志

function processUserData($userId) {

    try {

        // 模拟数据库操作

        $userData = fetchUserDataFromDatabase($userId);

        // 处理用户数据

        $result = performComplexOperation($userData);

        return $result;

    } catch (Exception $e) {

        // 没有适当日志记录的糟糕错误处理

        echo "An error occurred: " . $e->getMessage();

        return false;

    }

}

?>
```

良好的代码实现了 `catch` 块，记录了错误消息、用户 ID、错误代码和堆栈跟踪等重要信息。这有助于追踪和分析。错误代码仅仅输出错误消息而没有适当的日志记录，使得在生产环境中难以追踪和调试问题。

<Memo>
许多 PHP 框架和应用程序使用如 Monolog 等日志库。
</Memo>

## 在 catch 块中使用类型提示

通过在 `catch` 块中使用类型提示来处理特定异常，可以提高代码的可读性和错误处理能力。

以下代码演示了如何在 `catch` 块中使用类型提示进行更好的异常处理：

### 良好的代码

```php
try {

    // 可能会抛出异常的代码

    $result = someRiskyOperation();

} catch (InvalidArgumentException $e) {

    // 处理特定的 InvalidArgumentException

    error_log("Invalid argument: " . $e->getMessage());

} catch (RuntimeException $e) {

    // 处理特定的 RuntimeException

    error_log("Runtime error: " . $e->getMessage());

} catch (Exception $e) {

    // 处理其他任何异常

    error_log("Unexpected error: " . $e->getMessage());

}
```

### 错误代码

```php
try {

    // 可能会抛出异常的代码

    $result = someRiskyOperation();

} catch (Exception $e) {

    // 以相同的方式处理所有异常

    error_log("An error occurred: " . $e->getMessage());

}
```

良好的示例在 `catch` 块中使用类型提示来分别处理特定异常。这种方法允许更精确的错误处理和日志记录。错误代码在不区分类型的情况下捕获所有异常，可能导致错误处理信息不足。

<Memo>
PHP 7.1 引入了使用管道符号 `|` 在单个 `catch` 块中捕获多种异常类型的能力。
</Memo>

## 为常用功能创建可重用的 traits

通过为跨类共享的常用功能创建 traits，提高代码的组织结构和可重用性。

以下代码演示了如何创建并使用用于日志功能的 trait：

### 良好的代码

```php
// 定义一个用于日志功能的 trait

trait Loggable {

    protected function log($message) {

        // 日志逻辑实现

        error_log("[" . date('Y-m-d H:i:s') . "] " . $message);

    }

}

// 在类中使用 trait

class UserManager {

    use Loggable;

    public function createUser($username) {

        // 创建用户逻辑

        $this->log("User created: " . $username);

    }

}

// Use the trait in another class

class OrderProcessor {

    use Loggable;

    public function processOrder($orderId) {

        // Order processing logic

        $this->log("Order processed: " . $orderId);

    }

}
```

### 错误代码

```php
// Duplicate logging functionality in multiple classes

class UserManager {

    protected function log($message) {

        error_log("[" . date('Y-m-d H:i:s') . "] " . $message);

    }

    public function createUser($username) {

        // User creation logic

        $this->log("User created: " . $username);

    }

}

class OrderProcessor {

    protected function log($message) {

        error_log("[" . date('Y-m-d H:i:s') . "] " . $message);

    }

    public function processOrder($orderId) {

        // Order processing logic

        $this->log("Order processed: " . $orderId);

    }

}
```

良好的代码示例定义了一个 `Loggable` trait，它封装了日志记录功能。该 trait 可以在多个类中复用，减少了代码重复并提高了可维护性。糟糕的代码示例在每个类中重复了日志逻辑，导致了代码重复和潜在的不一致性。

<Memo>
Traits 在 PHP 5.4 中引入，用于促进 PHP 这种单继承语言中的代码复用。
</Memo>

## 在类层次级中为共享行为实现抽象类

使用抽象类为相关类定义通用行为和结构。

以下代码演示了如何使用抽象类为不同类型的车辆定义共享行为。

### 良好的代码

```php
// 车辆抽象类

abstract class Vehicle {

    protected $brand;

    protected $model;

    // 构造函数

    public function __construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    // 子类需要实现的抽象方法

    abstract public function getType();

    // 所有车辆共享的方法

    public function getInfo() {

        return "This is a " . $this->getType() . " - " . $this->brand . " " . $this->model;

    }

}

// 继承 Vehicle 的 Car 类

class Car extends Vehicle {

    public function getType() {

        return "Car";

    }

}

// 继承 Vehicle 的 Motorcycle 类

class Motorcycle extends Vehicle {

    public function getType() {

        return "Motorcycle";

    }

}

// 使用

$car = new Car("Toyota", "Corolla");

echo $car->getInfo(); // 输出: This is a Car - Toyota Corolla

$motorcycle = new Motorcycle("Honda", "CBR");

echo $motorcycle->getInfo(); // 输出: This is a Motorcycle - Honda
```

### 错误代码

```php
// 没有抽象类，重复重复

class Car {

    private $brand;

    private $model;

    public function __construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    public function getInfo() {

        return "This is a Car - " . $this->brand . " " . $this->model;

    }

}

class Motorcycle {

    private $brand;

    private $model;

    public function __construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    public function getInfo() {

        return "This is a Motorcycle - " . $this->brand . " " . $this->model;

    }

}

// 使用

$car = new Car("Toyota", "Corolla");

echo $car->getInfo();

$motorcycle = new Motorcycle("Honda", "CBR");

echo $motorcycle->getInfo();
```

良好的代码示例使用抽象的 `Vehicle` 类来定义共享属性和方法。这减少了代码重复并强制了一致的结构。`getType()` 方法被声明为抽象，确保每个子类都实现了它。相比之下，糟糕的代码在 `Car` 和 `Motorcycle` 类中重复了代码，导致了维护问题并违反了 DRY（不要重复自己）原则。

<Memo>
PHP 中的抽象类是在 2004 年 7 月发布的 PHP 5.0 中引入的。
</Memo>

## 使用依赖注入容器创建对象

实现一个依赖注入容器来管理对象的创建和依赖。

以下代码演示了如何使用依赖注入容器来管理对象的创建和依赖。

### 良好的代码

```php
// 简单的注入容器

class Container {

    private $services = [];

    public function register($name, $callback) {

        $this->services[$name] = $callback;

    }

    public function resolve($name) {

        if (!isset($this->services[$name])) {

            throw new Exception("Service not found: $name");

        }

        return call_user_func($this->services[$name], $this);

    }

}

// Database 类

class Database {

    private $connection;

    public function __construct($connection) {

        $this->connection = $connection;

    }

    public function query($sql) {

        // 模拟查询

        return "Executed query: " . $sql . " on connection: " . $this->connection;

    }

}

// UserRepository 类

class UserRepository {

    private $db;

    public function __construct(Database $db) {

        $this->db = $db;

    }

    public function findUser($id) {

        return $this->db->query("SELECT * FROM users WHERE id = $id");

    }

}

// 设置容器

$container = new Container();

$container->register('database', function($c) {

    return new Database('mysql:host=localhost;dbname=myapp');

});

$container->register('userRepository', function($c) {

    return new UserRepository($c->resolve('database'));

});

// 使用

$userRepo = $container->resolve('userRepository');

echo $userRepo->findUser(1);
```

### 错误代码

```php
// 没有依赖注入，硬编码依赖

class Database {

    private $connection;

    public function __construct() {

        $this->connection = 'mysql:host=localhost;dbname=myapp';

    }

    public function query($sql) {

        return "Executed query: " . $sql . " on connection: " . $this->connection;

    }

}

class UserRepository {

    private $db;

    public function __construct() {

        $this->db = new Database();

    }

    public function findUser($id) {

        return $this->db->query("SELECT * FROM users WHERE id = $id");

    }

}

// 使用

$userRepo = new UserRepository();

echo $userRepo->findUser(1);
```

良好的代码示例实现了一个简单的依赖注入容器来管理对象的创建。这种方法允许更好的可测试性、灵活性关注点分离。依赖项注册在容器中并在需要时解析。相比之下，糟糕的代码硬编码了依赖，使得代码缺乏活性且难以测试或修改。

<Memo>
依赖注入是面向对象设计 SOLID 原则中的关键概念，特别是依赖倒置原则。
</Memo>

## 使用工厂模式进行对象实例化

工厂模式是一种设计模式，它为父类中的创建对象提供接口，但允许子类更改将创建对象的类型。

在 PHP 中使用工厂模式可以在不指定具体对象类的情况下创建对象。这促进了松耦合，并增强了代码的可读性和可维护性。

### 良好的代码

```php
// Shape 接口

interface Shape {

    public function draw();

}

// 具体圆形类

class Circle implements Shape {

    public function draw() {

        echo "Drawing a Circle";

    }

}

// 具体正方形类

class Square implements Shape {

    public function draw() {

        echo "Drawing a Square";

    }

}

// 抽象工厂

abstract class ShapeFactory {

    abstract public function createShape(): Shape;

}

// 具体工厂

class CircleFactory extends ShapeFactory {

    public function createShape(): Shape {

        return new Circle();

    }

}

class SquareFactory extends ShapeFactory {

    public function createShape(): Shape {

        return new Square();

    }

}

// 客户端代码

function clientCode(ShapeFactory $factory) {

    $shape = $factory->createShape();

    $shape->draw();

}

// 使用工厂

clientCode(new CircleFactory()); // 输出: Drawing a Circle

clientCode(new SquareFactory()); // 输出: Drawing a Square
```

### 错误代码

```php
<?php

// 未使用工厂模式直接实例化

class Circle {

    public function draw() {

        echo "Drawing a Circle";

    }

}

class Square {

    public function draw() {

        echo "Drawing a Square";

    }

}

// 直接实例化

$circle = new Circle();

$circle->draw();

$square = new Square();

$square->draw();

?>
```



# 实现工厂模式以创建对象

工厂模式是一种创建型设计模式，它提供了一种创建对象的接口，但允许子类决定实例化哪个类。这使得代码更加灵活且易于维护。

## Good Code

```php
<?php

// 产品接口
interface Shape {
    public function draw();
}

// 具体产品
class Circle implements Shape {
    public function draw() {
        echo "Drawing a Circle";
    }
}

class Square implements Shape {
    public function draw() {
        echo "Drawing a Square";
    }
}

// 工厂类
class ShapeFactory {
    public function createShape($shapeType) {
        if ($shapeType == 'circle') {
            return new Circle();
        } elseif ($shapeType == 'square') {
            return new Square();
        }
        return null;
    }
}

// 客户端代码
$factory = new ShapeFactory();

$circle = $factory->createShape('circle');
$circle->draw(); // 输出: Drawing a Circle

$square = $factory->createShape('square');
$square->draw(); // 输出: Drawing a Square

?>
```

## Bad Code

```php
<?php

// 未使用工厂模式的直接实例化
class Circle {
    public function draw() {
        echo "Drawing a Circle";
    }
}

class Square {
    public function draw() {
        echo "Drawing a Square";
    }
}

// 客户端代码
$circle = new Circle();
$circle->draw(); // 输出: Drawing a Circle

$square = new Square();
$square->draw(); // 输出: Drawing a Square

?>
```

在良好的示例中，使用了工厂模式来创建对象，这使得代码更加灵活且易于维护。客户端代码不需要知道它所创建对象的确切类，从而促进了松耦合。在糟糕的示例中，使用了直接实例化，这使得代码灵活性降低且更难维护，因为对象创建过程的任何更改都需要对客户端代码进行修改。

<Memo>
工厂模式是面向对象编程中最常用的设计模式之一。它是“四人帮”（Gang of Four）设计模式的一部分，由 Erich Gamma、Richard Helm、Ralph Johnson 和 John Vliss 在其著作《设计模式：可复用面向对象软件的要素》中引入。
</Memo>

# 实现策略模式以支持可交换的算法

策略模式是一种设计模式，允许在运行时选择算法的行为。它定义了一族算法，对每个算法进行封装，并使它们可以相互替换。

在 PHP 中使用策略模式允许你定义一个算法族，对每个算法进行封装，并使它们可以相互替换。这种模式允许算法独立于使用它的客户端发生变化，从而提高了灵活性和代码复用。

## Good Code

```php
<?php

// 策略接口
interface PaymentStrategy {
    public function pay($amount);
}

// 信用卡支付的具体策略
class CreditCardPayment implements PaymentStrategy {
    public function pay($amount) {
        echo "Paying $amount using Credit Card";
    }
}

// PayPal 支付的具体策略
class PayPalPayment implements PaymentStrategy {
    public function pay($amount) {
        echo "Paying $amount using PayPal";
    }
}

// 上下文类
class ShoppingCart {
    private $paymentStrategy;

    public function __construct(PaymentStrategy $paymentStrategy) {
        $this->paymentStrategy = $paymentStrategy;
    }

    public function checkout($amount) {
        $this->paymentStrategy->pay($amount);
    }
}

// 客户端代码
$cart = new ShoppingCart(new CreditCardPayment());
$cart->checkout(100); // 输出: Paying 100 using Credit Card

$cart = new ShoppingCart(new PayPalPayment());
$cart->checkout(200); // 输出: Paying 200 using PayPal

?>
```

## Bad Code

```php
<?php

// 未使用策略模式的直接实现
class ShoppingCart {
    public function checkout($amount, $paymentType) {
        if ($paymentType == 'credit_card') {
            echo "Paying $amount using Credit Card";
        } elseif ($paymentType == 'paypal') {
            echo "Paying $amount using PayPal";
        }
    }
}

// 客户端代码
$cart = new ShoppingCart();
$cart->checkout(100, 'credit_card'); // 输出: Paying 100 using Credit Card
$cart->checkout(200, 'paypal'); // 输出: 200 using PayPal

?>
```

在良好的示例中，使用了策略模式来封装算法，使它们可以交换并促进了代码复用。上下文类 `ShoppingCart` 不需要感知具体的支付方法，这使得代码更加灵活且易于维护。在糟糕的示例中，支付逻辑被硬编码在 `checkout` 方法中，导致代码灵活性降低且更难维护，因为支付逻辑的任何更改都需要修改 `ShoppingCart` 类。

<Memo>
策略模式也是“四人帮”设计模式的一部分。它特别适用于多个算法适用于场景，且最佳算法可能会根据上下文而变化。
</Memo>

# 使用观察者模式实现对象间的松耦合

实现观察者模式以创建一个灵活的系统，使得对象可以订阅并接收主题的更新，而不会产生紧耦合。

以下代码演示了观察者模式在 PHP 中的实现，展示了一个 `Subject` 类和一个 `Observer` 接口。

## Good Code

```php
<?php

// Subject 类
class Newsletter {
    private $observers = [];
    private $content;

    // 附加观察者
    public function attach(Subscriber $observer) {
        $this->observers[] = $observer;
    }

    // 设置内容并通知观察者
    public function setContent($content) {
        $this->content = $content;
        $this->notify();
    }

    // 通知所有观察者
    private function notify() {
        foreach ($this->observers as $observer) {
            $observer->update($this->content);
        }
    }
}

// 观察者接口
interface Subscriber {
    public function update($content);
}

// 具体观察者
class EmailSubscriber implements Subscriber {
    private $email;

    public function __construct($email) {
        $this->email = $email;
    }

    public function update($content) {
        echo "Sending email to {$this->email}: {$content}\n";
    }
}

// 使用
$newsletter = new Newsletter();
$subscriber1 = new EmailSubscriber("user1@example.com");
$subscriber2 = new EmailSubscriber("user2@example.com");

$newsletter->attach($subscriber1);
$newsletter->attach($subscriber2);

$newsletter->setContent("New article published!");

?>
```

# 使用装饰器模式动态扩展对象功能

装饰器模式允许在不修改现有代码的情况下，动态地为对象添加新功能。它通过将对象包装在装饰器类中来实现。

## 组件接口

```php
<?php

// Component interface
interface Coffee {
    public function getCost();
    public function getDescription();
}

?>
```

## 具体组件

```php
<?php

// Concrete component
class SimpleCoffee implements Coffee {
    public function getCost() {
        return 10;
    }

    public function getDescription() {
        return "Simple Coffee";
    }
}

?>
```

## 抽象装饰器基类

```php
<?php

// Base decorator
abstract class CoffeeDecorator implements Coffee {
    protected $decoratedCoffee;

    public function __construct(Coffee $coffee) {
        $this->decoratedCoffee = $coffee;
    }

    public function getCost() {
        return $this->decoratedCoffee->getCost();
    }

    public function getDescription() {
        return $this->decoratedCoffee->getDescription();
    }
}

?>
```

## 具体装饰器

```php
<?php

// Concrete decorators
class Milk extends CoffeeDecorator {
    public function getCost() {
        return $this->decoratedCoffee->getCost() + 2;
    }

    public function getDescription() {
        return $this->decoratedCoffee->getDescription() . ", Milk";
    }
}

class Sugar extends CoffeeDecorator {
    public function getCost() {
        return $this->decoratedCoffee->getCost() + 1;
    }

    public function getDescription() {
        return $this->decoratedCoffee->getDescription() . ", Sugar";
    }
}

?>
```

## 使用示例

```php
<?php

// Usage
$coffee = new SimpleCoffee();
echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\n";

$coffee = new Milk($coffee);
echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\n";

$coffee = new Sugar($coffee);
echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\n";

?>
```

## Bad Code

```php
<?php

class Coffee {
    public $cost = 10;
    public $description = "Simple Coffee";

    public function addMilk() {
        $this->cost += 2;
        $this->description .= ", Milk";
    }

    public function addSugar() {
        $this->cost += 1;
        $this->description .= ", Sugar";
    }

    public function getInfo() {
        echo "$this->description costs $$this->cost\n";
    }
}

$coffee = new Coffee();
$coffee->getInfo();

$coffee->addMilk();
$coffee->getInfo();

$coffee->addSugar();
$coffee->getInfo();

?>
```

良好的代码示例正确地实现了装饰器模式。它定义了一个 `Coffee` 接口、一个基础 `SimpleCoffee` 类，以及装饰器类（`Milk` 和 `Sugar`），这些类用于封装并扩展咖啡对象的功能。这种方法允许对装饰器进行灵活组合，并且可以在不修改现有代码的情况下轻松添加新的装饰器。

坏的代码示例没有使用装饰器模式。相反，它通过添加添加配料的方法直接修改 `Coffee` 类。这种方法违反了“开闭原则”，因为添加新功能需要修改现有的 `Coffee` 类。它的灵活性较低，且更难维护或扩展。

### 备忘录

装饰器模式是一种结构性设计模式，它允许静态或动态地为单个对象添加行为，而不会影响同类中其他对象的行为。它通常用于遵循“单一职责原则”，因为它允许将功能划分到具有不同关注点的类之间。

# 结语

◆

感谢你与我一起开启这段 PHP 编程世界的旅程。

正如你所发现的，这本书不仅仅是编码技巧的集合——它是一份路线图，帮助你编写出让机器和开发者都能清晰理解的 PHP 代码。

在这些页内容中，我们探索了 100 种独特的方法，让你的 PHP 代码从“可用”提升到“卓越”。

我们深入研究了 PHP 特有的功能和最佳实践，目标始终是创建出高效的代码。

我希望这些优坏代码的对比示例能给你带来启发。在良好的代码和运行完美的代码之间往往存在着微妙的界限，我信任这些说明有助于提升你的判断力。

现在，我有一个小请求。

你对这本书的意见对我来说非常重要。无论你觉得它有用、有趣、失望还是难以阅读，我都想听听你的想法。你的反馈塑造着我未来的写作，并帮助我更好地服务 PHP 社区。

如果你能抽出一点时间，请考虑留下评论。分享那些让你产生共鸣的内容、你想看到更多的内容，甚至是令你不符合预期的地方。即使你很忙，一个简单的星级也会让我感激不尽。

我会阅读每一条评论，你的见解往往会为未来的作品带来灵感。也许你对想要涵盖的主题有建议？我洗耳倾听！你的声音对于塑造全球 PHP 开发者可资源至关重要。

感谢你的时间、信任以及对编程艺术的奉献。祝代码更整洁、更优雅——也期待未来在广阔的编程文学世界再次相遇。

在此之前，祝编码愉快！
