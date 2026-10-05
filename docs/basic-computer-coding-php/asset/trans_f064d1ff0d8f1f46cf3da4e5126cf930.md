

b. 有效资源为真（尽管某些在成功时返回资源的函数在失败时会返回 FALSE）。

c. 不要将双用作布尔值。

d. 以上所有。

# 复习习题

- 1. 解释数组函数。
- 2. 讨论 PHP 数组常量。
- 3. 什么是数值数组？
- 4. 你对关联数组如何理解？请描述。
- 5. 什么是多维数组？

# 检查结果

1. (b) 2. (c) 3. (a) 4. (a) 5. (d)

# 基础编程：PHP

# 参考文献

- 1. Chatzigeorgiou; Stephanides (2002). “Evaluating Performance and Power of Object-Oriented Vs. Procedural Programming Languages”. Inieberger; Strohmeier. Proceedings - 7th International Conference on Reliable Software Technologies - Ada-Europe’2002. Springer. p. 367. ISBN 978-3-540-43784-0.
- 2. http://www.twf.fr/tatroee.pdf
- 3. https://www.tutorialspoint.com/php/php_array_functions.htm
- 4. https://www.tutorialspoint.com/php/php_arrays.htm
- 5. John Mitchell, Concepts of Programming Languages. Cambridge University Press.
- 6. K. Jensen and Niklaus Wirth, PASCAL User Manual and Report. Springer. Paperback edition (2007) 184 pages, ISBN 978-3540069508
- 7. Robert W. Sebesta (2001) Concepts of Programming Languages. Addison-Wesley. 4th edition (1998), 5th edition (2001), ISBN 97802001385960.
- 8. Stéfan der Walt; S. Chris Colbert & Gaël Varoquaux (2011). “The NumPy array: a structure for efficient numerical computation”. Computing in Science and Engineering. IEEE.
- 9. Surana P (2006). “Meta-Compilation of Language Abstractions (PDF). Archived from the original (PDF) on 2015-02-17. Retrieved 2008-03-17.

# 第 6 章

# 对象

> “在寻找代码错误时，发现错误已经足够困难；当你假设你的代码没有错误时，发现错误就更难了。”

—Steve McConnell

# 学习目标

学习本章后，你将能够：

- 解释 PHP 对象和类
- 讨论创建对象
- 描述类的声明

# 引言

面向对象编程（OOP）是一种更高效组织代码的方法，它利用了现代 PHP 版本中的一些非常棒的特性。OOP 的基本概念之一并不意外，就是对象。与操作对象直接相关的是理解 PHP 类。

面向对象语言的核心思想是将一组变量和函数封装进单个单元中，并保护变量和函数免受外部干扰和误用。这种单元被称为对象，它作用于数据。将数据和函数绑定在一起的机制被称为封装。这一特性使得在各种项目中复用代码变得简单。在对象中声明的函数提供了访问数据的方法。对象的方法被称为对变量的访问，这些变量被称为属性。

下图显示了对象的组件。

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_171_0.png)

# 6.1 PHP 对象和类

面向对象编程的基础构建模块是类和对象。在我们深入研究面向对象的方法之前，理解对象、类以及对象与类之间的区别是非常重要的。

# 6.1.1 PHP 对象 vs. 类

在现实世界中，对象有自己的特征和行为。我们可以将具有相同特征和行为的相似对象归为一类。因此我们可以说类是对象的蓝图。看下面的图片：

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_172_0.png)

从同一个 Car（汽车）类中，我们创建了三个独立的对象，分别为：Mercedes、Bmw 和 Audi。

尽管所有对象都是从同一个类创建的并因此拥有类的方法和属性，但仍然是不同的。这不仅是因为它们有不同的名称，还因为它们的属性可能被赋予了不同的值。例如，在上面的图中，它们在颜色属性上不同——Mercedes 是绿色的，Bmw 是蓝色的，而 Audi 是橙色的。

> 注意 getter 和 setter 的名称与关联的属性名称匹配。

# 6.1.2 定义类和对象

在创建任何新对象之前，你需要一个对象的类或蓝图。在 PHP 中定义新类非常简单。在 PHP 中定义新类，你使用 `class` 关键字，如下所示：

# 基础编程：PHP

```php<?php
class BankAccount{
}
```

我们定义了一个名为 BankAccount 的新空类。从 BankAccount 类，我们可以使用 `new` 关键字创建新的银行账户对象，如下所示：

```php
<?php
class BankAccount{
}
// 创建一个新的银行账户对象
$account = new BankAccount();
var_dump($account);
```

注意，我们使用 `var_dump()` 函数来查看银行账户的内容。

# 6.1.3 属性

在面向对象的术语中，对象的特征被称为属性。例如，银行账户有账号和总余额。所以让我们把这些属性添加到 BankAccount 类中：

```php
<?php
class BankAccount{
private $accountNumber;
private $totalBalance;
```

你看到我们在属性前面使用了 `private` 关键字。这被称为属性可见性。每个属性可以有三种可见性级别之一，即 `private`、`protected` 和 `public`。

- private: 类私有属性只能由类内部的方法访问。稍后将介绍类的方法。
- protected: 受保护属性与私有属性相似，但受保护属性可以被子类访问。你稍后将学习子类和继承。

- public: 公有属性不仅可以被类内部访问，还可以被类外部的代码访问。

# 记忆

类内部的数据/变量（例如 `var $name;`）被称为“属性”。

在 BankAccount 类中，我们可以访问这些属性。

# 6.1.4 方法

对象的行为被称为方法。与类属性类似，方法有不同的可见性：private、protected 和 public。

通过银行账户，我们可以存款、取款并获取余额。

为类创建一个方法，使用 `function` 关键字，后跟名称和括号。方法与函数相似，但方法与类关联并具有可见性。

方法方法，方法可以有一个或多个参数并返回值。

函数最初是取决于另一个数量的理想化。

让我们为 BankAccount 类添加方法：

```php
<?php
class BankAccount

/**
 * 账号
* @var string 账号
 */
private $accountNumber;
/**
 * 总余额
* @var float 总余额
 */
private $totalBalance;

/**
 * 向银行账户存款
 * @param float $amount 存款金额
 */
public function deposit($amount){
  $this->totalBalance += $amount;
}

/**
 * 从银行账户取款
 * @param double $amount 取款金额
 */
public function withdraw($amount) {
  if($amount > $this->totalBalance)
    die('余额不足，无法取款');

  $this->totalBalance -= $amount;
}

/**
 * 返回总余额
 * @return float 总余额
 */
public function getBalance() {
```
return $this->totalBalance;
}

/**
 * 返回账号
 */
public function getAccountNumber(){
return $this->accountNumber;
}

/**
 * 设置账号
 * @param string $accountNumber 账号
 */
public function setAccountNumber($accountNumber) {
$this->accountNumber = $accountNumber;
}
```

注意我们使用特殊的 `$this` 变量来访问对象的属性。PHP 使用 `$this` 变量来引用当前对象。访问属性时，使用箭头运算符 (->)，如下所示：

```
object->property
```

