

```php
$form->setStyle(new ExtraNetStyle());
$form->display();
```

如果我们想将颜色改为稍有不同的颜色，我们只需更改下面所示的代码行：

```php
$form->setStyle(new NewStyle());
$form->display();
```

并且我们不需要更改表单引擎的任何逻辑。

用于输出表单引擎的倒数第二段代码是一个数据验证对象。我们在讨论委托时已经构建过一个。其对象模型如下所示：

![](img/9cf7789dba9b16ef3f8576d5aea89186_174_0.png)

要管理多个表单，我们需要实际的 FormEngine 对象，这是我们的最后一个对象。这个 FormEngine 将是我们管理多个表单的工具，并在使用多个表单时作为重现 JavaScript 库代码的向导。这个对象也充当工厂类，因为我们可以通过它创建表单。以下是对象模型：

![](img/9cf7789dba9b16ef3f8576d5aea89186_174_1.png)

让 FormEngine 对象创建表单的原因是，它可以列出 JavaScript 代码所需的详细信息。这样我们就可以拥有具有客户端数据验证的多个表单。这几乎完成了我们的表单。以下是一些示例代码，展示构建先前显示的表单是多么容易：

```php
$formEngine = new FormEngine();
$form = $formEngine->create("form", "Form Name", $PHP_SELF, "post");
$form->addElement(new FormHeader('General Information'));
$form->addElement(new TextField('name', '', 'Name', ALPHA,
"You have failed to enter your name", true));

$form->addElement(new HiddenField('userID', '1'));

$form->addElement(new PasswordField('password', '', 'Password',
PASSWORD,
"You have failed to choose a password larger than 4 characters",
true));

$form->addElement(new TextField('email', '', 'Email Address', EMAIL,
"You have entered your email address incorrectly", true));

$form->addElement(
new TextArea('description', '', 'Description', ALPHANUMERIC,
"You have failed to enter any description about yourself",
false, array("rows" => 10, "cols" => 40,)));

$form->addElement(new DateField('startdate', '', 'Start Date',
false));

$form->addElement(new FileBrowser('file', 'File', false));

$combo = new ComboBox('wagetype', 'S', 'Wage Type', true);
$combo->add('Hourly', 'H');
$combo->add('Salary', 'S');
$form->addElement($combo);

$combo = new MultiComboBox('position', $position, 'Position', false);
$combo->add('Planner', 'P');
$combo->add('Manager', 'M');
$combo->add('Engineer', 'E');
$combo->add('Analyst', 'A');
$form->addElement($combo);

$form->addButton(new SubmitButton('submit', 'Submit'));
$form->addButton(new ResetButton('reset', 'Reset'));

if ($submit == 'Submit') {
$isValid = $form->validate();

if ($isValid) {
echo("everything okay");
// start processing info into database or whatever
} else {
echo($form->getErrorMessage());
$form->display();
$formEngine->displayJavascriptLibraryCode();
echo($form->generateJavaScriptCode());
}
} else {
$formEngine->displayJavascriptLibraryCode();
$form->display();
echo($form->generateJavaScriptCode());
}
```

喂，没有关于实现的代码吗？我该怎么办？这是个好回答的问题；去写它。如果你打算学习面向对象编程并体会你所学的所有概念，你的第一个尝试应该是完成这个模块。这并非完全浪费时间，因为你将能够在你的程序中*大量*使用它。向网上的那些免费模块说再见，使用你亲手创建的东西，你可以说你理解其基础，而不仅仅是代码。

## 摘要

在本章中，你了解到面向对象编程对 PHP 作为未来 Web 平台的生存至关重要。在解释了“软件危机”（程序变得庞大、复杂且难以管理，因此需要更好的软件构建方式）之后，我们讨论了 OOP 的发展和优势。随后，我们讨论了它与函数式编程的区别，并探讨了 OO 为我们程序员和架构师带来的好处——提高可重用性和可维护性。

在梳理完所有基础知识后，我们深入探讨了面向对象程序的基本构建块——类和对象。我们了解到对象包含方法、成员和构造函数，并且当我们使用 PHP 的 new 运算符时，它们会被实例化以在程序中使用。我们了解到，通过提供客户端可用的有用服务并隐藏对象中的数据，我们可以提高代码的可重用性和可维护性。这一特性被称为封装，因为实现的所有细节都隐藏在类中，对使用该类的任何客户端都不可见。

然后，我们讨论了如何通过使用继承和多态为对象添加更多结构和含义。我们发现，继承使我们能够通过向对象添加更多行为和数据来对其进行专业化，使我们的代码更易于追踪，同时也更可重用。通过在继承的对象上使用多态，我们可以开发通用、优雅的解决方案，在 PHP 解释器的帮助下在运行时处理详细信息。这也提高了可维护性，因为我们可以向继承模型中添加新类，而无需修改任何多态代码中的逻辑。

最后，我们通过讨论内聚性和耦合性来结束此次讨论。内聚性是指对象内部元素和功能之间的紧密程度，而耦合性是指两个或多个对象之间的关联程度。高度内聚的模块能产生更小、更易维护的模块，而松耦合的对象则为我们提供了更大的可重用性。我们了解到，创建高度内聚且松耦合的模块是一种良好实践，可以构建高度可重用且易维护的程序。

接下来，我们研究了使用 UML 进行对象建模。我们意识到 UML 为我们制定自己的设计以及向其他程序员传达想法提供了一种简便、一致的方式。随后，我们讨论了不同类型的包含，并发现物理包含与称为委托的复用包含之间存在区别。

我们进一步研究了一些设计启发式规则和良好实践，即逻辑必须位于合适的位置。我们了解到，如果逻辑散布在程序的各处，将更难使用我们的对象，从而使重用和维护它们变得更加困难。

最后，我们研究了为关系数据库创建对象模型以及为非常先进的表单引擎创建对象模型。我们举例说明了继承、多态、良好的设计启发式规则、委托和 UML 的各种情况。

## 6 调试

编程项目中一个经常被忽视的方面是调试和优化程序所需的时间。PHP 编程项目也不例外。事实上，PHP 脚本开发和部署的独特环境带来了特定的挑战，也为调试和优化程序提供了新的途径。然而，规划调试和优化的核心概念与传统编程工具相同。

在本章中，我们将深入探讨各种编程陷阱、避免方法，以及可用于最大限度减少和阻止错误代码的工具。在本章中，我们将探讨：

- 编程错误概述
- PHP 中的错误级别：
  - 语法解析错误
  - 致命错误
  - 警告和通知
  - 核心错误和编译错误
  - 用户错误级别
  - 设置错误报告级别
- 以防御性编程方式最大限度减少错误：
  - 抑制错误消息
  - 错误恢复
  - 自定义错误检查
  - 记录错误
- 调试和测试工具：
  - 类似 telnet 客户端和嗅探服务器的 HTTP 调试实用程序
  - 使用 phpCodesite 进行跟踪调试
  - 诸如 BODY 和 Zend IDE 之类的远程调试器
  - 使用 phpUnit 进行脚本测试

## 编程错误概述

作为一种脚本语言，PHP 为我们提供了在程序解释过程中发现错误的机会，但也带来了问题，因为脚本通常在服务器上执行，因此不像传统的独立程序那样易于调试。然而，在脚本解释过程中可以发现的错误类别，通常只是潜入脚本中的编程错误的一个很小子集。编写 PHP 脚本时遇到的一些常见编程错误包括：

- 语法错误
- 语义错误
- 逻辑错误
- 环境错误

现在让我们更仔细地看看这些错误。

## 语法错误

语法错误是最常见且最容易检测的错误类别。这些错误是由于不正确使用语言结构而导致的。语法错误的发生情况在 PHP3 和 PHP4 之间发生了显著变化。这是因为，在 PHP3 中，每一行在遇到时都会被解释，而在 PHP4 中，语句在执行前会被编译。

使用 PHP3 时，程序的一次成功运行并不能保证所有语法错误都已排除。通常，脚本所走的特殊代码路径会暴露出尚未发现的语法错误。为了说明这一点，让我们来看看以下 PHP3 脚本：

```php
<?php
//Simple_Leap.php

if ($year % 4) {
    // simplified test for a non-leap year
    echo("February has 28 days");
} else {
    echo("February has 29 days");
}
?>
```

