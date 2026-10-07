
# 第三部分：在实践中使用 PHP

如果该方法捕获到 `InputException`，它会通过调用 `InputException::getInvalidWarpFactor()` 显示一条消息，包括请求的曲速因子。同样，如果捕获到 `FuelException`，该方法会显示不同的消息，通过 `FuelException::getMessage()` 获取消息，并从 `FuelException::getRemainingFuel()` 显示剩余燃料。最后，该方法会捕获任何可能抛出的其他 `Exception`，并显示通用的错误消息。在你可能创建的任何自定义 `Exception` 中，捕获通用 `Exception` 对象始终是一个好主意。

最后，脚本创建了一个新的 `Captain` 对象并使用其 `newWarpOrder` 方法设置各种速度。从图 20-2 中可以看到，随着脚本的执行，各种异常被抛出并显示。

## 分离应用逻辑与显示逻辑

当你第一次编写 PHP 脚本时，你可能会发现自己自然地想要将 PHP 代码（应用逻辑）和 HTML 标记（显示逻辑）混合在同一个脚本文件或页面中。事实上，本书中的大多数示例都遵循这种格式，因为这样在一个地方解释代码会更简单。

虽然这种方法对于小型脚本是可以接受的，但随着项目规模的扩大，它会变得难以维护。将逻辑与显示分离可以提高代码的可读性和可重用性。

## 第 20 章：编写高质量代码

```php

<input type="reset" name="resetButton" id="resetButton" value="Reset Form" style="margin-right:20px; />

<div>

</div>

</form>

```

<?php include "page_footer.php" ?>

现在来创建感谢页，

```php

<?php include "page_header.php" ?>

<h1>感谢您</h1>

<p>感谢您，我们已收到的您的申请。</p>

<?php include "page_footer.php" ?>

```

将 `registration_form.php` 和 `thanks.php` 都保存到你的 `templates` 文件夹中。

现在你已经创建了演示代码，是时候创建应用程序代码了。将以下代码保存为 `registration.php` 并放在你的文档根目录中：

```php

<?php

if ( isset($_POST["submitButton"] ) ) {

    processForm();

} else {

    displayForm(array());

}

function validateField($fieldName, $missingFields) {

    if (in_array($fieldName, $missingFields) ) {

        return ' class="error";

    }

}

function setValue($fieldName) {

    if (isset($_POST[$fieldName])) {

        return htmlspecialchars($_POST[$fieldName]);

    }

}

function setChecked($fieldName, $fieldValue) {

    if (isset($_POST[$fieldName]) && $_POST[$fieldName] == $fieldValue ) {

        return ' checked="checked";

    }

}

function setSelected($fieldName, $fieldValue) {

    if (isset($_POST[$fieldName]) && $_POST[$fieldName] == $fieldValue ) {

        return ' selected="selected";

    }

}

```

### 第三部分：在实践中使用 PHP

```php

function processForm() {

    $requiredFields = array("firstName", "lastName", "password1",

    "password2", "gender" => array());

    $missingFields = array();

    foreach ($requiredFields as $requiredField) {

        if (!isset($_POST[$requiredField]) || !isset($_POST[$requiredField])) {

            $missingFields[] = $requiredField;

        }

    }

    if ($missingFields) {

        displayForm($missingFields);

    } else {

        displayThanks();

    }

}

function displayForm($missingFields) {

    $results = array(

        "pageTitle" => "Membership Form",

        "scriptUrl" => "registration.php",

        "missingFields" => $missingFields,

        "firstNameAttr" => validateField("firstName", $missingFields),

        "firstNameValue" => setValue("firstName"),

        "lastNameAttr" => validateField("lastName", $missingFields),

        "lastNameValue" => setValue("lastName"),

        "gender" => validateField("gender", $missingFields),

        "genderChecked" => checked("gender", "M"),

        "genderFChecked" => checked("gender", "F"),

        "favoriteWidgetOptions" => array(

            "superWidget" => setSelected("favoriteWidget", "superWidget"),

            "megaWidget" => setSelected("favoriteWidget", "megaWidget"),

            "wonderWidget" => setSelected("favoriteWidget", "wonderWidget"),

        ),

        "newsletterChecked" => checked("newsletter", "yes"),

        "commentsValue" => setValue("comments")

    );

    require("templates/registration_form.php");

}

function displayThanks() {

    $results = array(

        "pageTitle" => "Thank You"

    );

    require("templates/thank.php");

}

?>

```

在 浏览器中打开 `registration.php` 的 URL 来运行该脚本。你应该能看到注册表单出现。尝试填写字段并点击“Send Details”（发送详情）。注意该脚本的行为与第 9 章中的对应代码非常相似。

### 它是如何工作的

功能上，该应用程序与第 9 章非常相似。主要的区别在于演示代码已从 `registration.php` 中分离出来，并存储在模板文件中。查看 `registration.php` 脚本，不再包含嵌入的 HTML，而是使用 `require()`。

```php

function displayForm($missingFields) {

  $results = array(

    "pageTitle" => "Membership Form",

    "scriptUrl" => "registration.php",

    "missingFields" => $missingFields,

    "firstNameAttr" => validateField("firstName", $missingFields),

    "firstNameValue" => setValue("firstName"),

    "lastNameAttr" => validateField("lastName", $missingFields),

    "lastNameValue" => setValue("lastName"),

    "gender" => validateField("gender", $missingFields),

    "genderChecked" => checked("gender", "M"),

    "genderFChecked" => checked("gender", "F"),

    "favoriteWidgetOptions" => array(

        "superWidget" => setSelected("favoriteWidget", "superWidget"),

        "megaWidget" => setSelected("favoriteWidget", "megaWidget"),

        "wonderWidget" => setSelected("favoriteWidget", "wonderWidget"),

    ),

    "newsletterChecked" => checked("newsletter", "yes"),

    "commentsValue" => setValue("comments")

  );

  require("templates/registration_form.php");

}

function displayThanks() {

  $results = array(

    "pageTitle" => "Thank You"

  );

  require("templates/thank.php");

}

?>

```

每个函数都创建一个包含要显示信息的 `$results` 数组。然后页面模板使用该数组来显示内容。例如，`registration_form.php` 使用 `firstNameAttr` 元素将任何属性（如 `class="error"`）插入到 firstName 标签中，并使用 `firstNameValue` 元素在 firstName 字段中显示经过处理的值：

```html

<label for="firstName"><?php echo $results["firstNameAttr"] ?? ""?></label>

<input type="text" name="firstName" id="firstName" value="<?php echo $results["firstNameValue"] ?? "" />

```

`registration.php` 中的表单辅助函数（如 `validateField()` 和 `setValue()`）已重写为返回输出值，而不是使用 `echo` 显示它们。这样这些值就可以被 `$results` 数组看到。

这些更改的结果是 `registration.php` 移除了所有的演示标记，而模板页面包含很少的 PHP ——事实上，它只有一个与显示结果相关的决策代码块。任何更复杂的逻辑都属于应用程序代码。

此示例可以进一步改进。例如，理想情况下 `registration.php` 不应该包含表单辅助函数 `validateField()`、`setValue()`、`setChecked()` 和 `setSelected()`，因为这些是特定于输出媒介（HTML）的。更好的方法是将演示代码与应用程序逻辑分离，使应用程序逻辑对输出媒介无感知（无论是 HTML、XML、纯文本、PDF 等）。

这种这种技术的一个良好示例是模型-视图-控制器（MVC）设计模式。这超出了本书的范围，但你可以在 http://en.wikipedia.org/wiki/Model-view-controller 找到概览。关于设计模式的一本好书是 Martin Fowler 编写的《Patterns of Enterprise Application Architecture》（Addison-Wesley）。

### 第 20 章：编写高质量代码

`PHPUnit` 是一个用于自动化单元测试的框架。你可以使用它在 PHP 中为应用程序的每个单元编写测试，然后自动运行测试并查看结果。

要安装 `PHPUnit`，请使用 `PEAR` 安装器（有关 `PEAR` 的更多信息请参见第 15 章）。由于 `PHPUnit` 不在标准的 `PEAR` 通道中，你首先需要运行（可能作为 root 或管理员用户）：

```
pear channel-discover pear.phpunit.de
```

随后你应该能看到：

```
Adding Channel "pear.phpunit.de" succeeded
Discovery of channel "pear.phpunit.de" succeeded
```

现在按照以下方式安装 `PHPUnit`（必要时再次使用 root）：

```
pear install --alldeps phpunit/PHPUnit
```

#### 编写一个简单的 PHPUnit 测试套件

现在你已经安装了 `PHPUnit`，尝试编写一些简单的测试。在这个示例中，你将测试第 8 章中 `car_simulator.php` 脚本创建的 `Car` 类的几个方法（该脚本在本章前面的“记录代码文档”部分已重打印）。

将以下脚本保存为文档根目录下的 `car_tests.php`：

```php

<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"

"http://www.w3.org/TR/xhtml/html-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

<title>Car Test Suite Example</title>

<link rel="stylesheet" type="text/css" href="common.css" />

</head>

<body>

<<h1>>Car Test Suite Example</h1>

<pre>

<?php

require_once ( "PHPUnit/Framework.php" );

require_once ( "PHPUnit/TextUI/TestRunner.php" );

class Car {

    public $color;

    public $manufacturer;

    public $model;

    private $_speed = 0;

    public function accelerate() {

        if ( $this->speed >= 100 ) return false;

        $this->speed += 10;

        return true;

    }

    public function brake() {

        if ($this->speed <= 0 ) return false;

        $this->speed -= 10;

        return true;

    }

    public function getSpeed() {

        return $this->speed;

    }

}

class CarTest extends PHPUnit_Framework_TestCase {

    public function testInitialSpeedIsZero() {

        $car = new Car();

        $this->assertEquals(0, $car->getSpeed() );

    }

    public function testAccelerate() {

        $car = new Car();

        $car->accelerate();

        $this->assertEquals(10, $car->getSpeed() );

    }

    public function testMaxSpeed() {

        $car = new Car();

        for ($i=0; $i < 10; $i ++) {

            $car->accelerate();

        }
