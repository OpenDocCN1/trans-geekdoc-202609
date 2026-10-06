

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

## 第三部分：在实践中使用 PHP

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

## 第 20 章：编写高质量代码

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

