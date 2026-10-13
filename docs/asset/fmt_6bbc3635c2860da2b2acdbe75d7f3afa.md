
要预设单选按钮或复选框的状态（即预先选中它们），请将代码 `checked="checked"` 添加到它们的 `input` 标签中。使用 PHP，你可以这样写：

```html
<input type="radio" name="gender" value="F" <?php if ($gender == 'F') { echo 'checked="checked"'; } ?>/>
```

（正如你所见，语法很快就会变得复杂；你可能会发现先创建表单元素，然后作为第二步添加 PHP 代码会更容易。）

要预设文本域的值，请在 `textarea` 标签之间输出该值：

```html
<textarea name="comments" rows="10" cols="50"><?php echo $comments; ?></textarea>
```

请注意，`textarea` 标签不像标准的 `text` 输入框那样拥有 `value` 属性。

要预选下拉菜单，请向相应的 option 添加 `selected="selected"`。如果你也使用 PHP 来生成菜单，这会变得非常简单：

```php
echo '<select name="year">';
for ($y = 2011; $y <= 2021; $y++) {
    echo "<option value=\"$y\"";
    if ($year == $y) {
        echo ' selected="selected"';
    }
    echo ">$y</option>\n";
}
echo '</select>';
```

掌握了这些新信息后，让我们重写 `calculator.php` 使其具有粘性。与上述示例不同，现有的值将存在于 `$_POST` 变量中。此外，由于最好不引用不存在的变量，条件语句将在输出变量值之前检查该变量是否已设置。

### 创建粘性表单

**1.** 在文本编辑器或 IDE 中打开 `calculator.php`（参考 脚本 3.5），如果尚未打开的话。

**2.** 修改距离输入框，使其如下所示（**脚本 3.6**）：

```html
<input type="text" name="distance" value="<?php if (isset($_POST['distance'])) echo $_POST['distance']; ?>" />
```

第一处更改是向输入框添加 `value` 属性。然后，输出提交的距离变量（`$_POST['distance']`）的值。由于页面首次加载时 `$_POST['distance']` 没有值，条件语句确保在尝试输出之前变量已设置。设置输入框值的最终 PHP 代码结果为：

```php
<?php
if (isset($_POST['distance'])) {
    echo $_POST['distance'];
}
?>
```

这可以精简为脚本中使用的更简洁形式（如果条件块中只有一条语句，可以省略大括号，尽管我极少建议这样做）。

**脚本 3.6。** 计算器的表单现在可以回忆之前输入和选择的值（创建了一个粘性表单）。

```php
<?php # 脚本 3.6 - calculator.php #2

$page_title = '行程成本计算器';
include ('includes/header.html');

// 检查表单提交：
if ($_SERVER['REQUEST_METHOD'] == 'POST') {

    // 最小化表单验证：
    if (isset($_POST['distance'], $_POST['gallon_price'], $_POST['efficiency']) &&
        is_numeric($_POST['distance']) && is_numeric($_POST['gallon_price']) && is_numeric($_POST['efficiency'])) {

        // 计算结果：
        $gallons = $_POST['distance'] / $_POST['efficiency'];
        $dollars = $gallons * $_POST['gallon_price'];
        $hours = $_POST['distance'] / 65;

        // 输出结果：
        echo '<h1>总预估成本</h1>
<p>驾驶 ' . $_POST['distance'] . ' 英里，平均每加仑 ' . $_POST['efficiency'] . ' 英里，平均每加仑支付 $' . $_POST['gallon_price'] '，总成本为 $' . number_format($dollars, 2) '。如果你以平均每小时 65 英里的速度驾驶，该行程将耗时约 ' . number_format($hours, 2) ' 小时。</p>';

    } else { // 提交的值无效。
        echo '<h1>错误！</h1>
<p class="error">请输入有效的距离、每加仑价格和燃油效率。</p>';
    }

} // 主提交 IF 结束。

// 离开 PHP 部分并创建 HTML 表单：
?>

<h1>行程成本计算器</h1>
<form action="calculator.php" method="post">
    <p>距离（英里）： <input type="text" name="distance" value="<?php if (isset($_POST['distance'])) echo $_POST['distance']; ?>" /></p>
    <p>平均每加仑价格： <span class="input">
        <input type="radio" name="gallon_price" value="3.00" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '3.00')) echo 'checked="checked" '; ?>/> 3.00
        <input type="radio" name="gallon_price" value="3.50" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '3.50')) echo 'checked="checked" '; ?>/> 3.50
        <input type="radio" name="gallon_price" value="4.00" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '4.00')) echo 'checked="checked" '; ?>/> 4.00
    </span></p>
    <p>燃油效率： <select name="efficiency">
        <option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '10')) echo ' selected="selected"'; ?>>极差</option>
        <option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '20')) echo ' selected="selected"'; ?>>尚可</option>
        <option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '30')) echo ' selected="selected"'; ?>>很好</option>
        <option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '50')) echo ' selected="selected"'; ?>>卓越</option>
    </select></p>
    <p><input type="submit" name="submit" value="计算！" /></p>
</form>

<?php include ('includes/footer.html'); ?>
```

**3.** 修改单选按钮为：

```html
<input type="radio" name="gallon_price" value="3.00" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '3.00')) echo 'checked="checked" '; ?>/> 3.00
<input type="radio" name="gallon_price" value="3.50" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '3.50')) echo 'checked="checked" '; ?>/> 3.50
<input type="radio" name="gallon_price" value="4.00" <?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == '4.00')) echo 'checked="checked" '; ?>/> 4.00
```

对于这三个单选按钮中的每一个，必须在 `input` 标签内添加以下代码：

```php
<?php if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == 'XXX')) echo 'checked="checked" '; ?>
```

对于每个按钮，比较值（XXX）会相应更改。

**4.** 修改下拉菜单选项为：

```html
<option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '10')) echo ' selected="selected"'; ?>>极差</option>
<option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '20')) echo ' selected="selected"'; ?>>尚可</option>
<option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '30')) echo ' selected="selected"'; ?>>很好</option>
<option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == '50')) echo ' selected="selected"'; ?>>杰出</option>
```

对于每个选项，在开始的 `option` 标签内，添加了以下代码：

```php
<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] == 'XX')) echo ' selected="selected"'; ?>
```

同样，只需将特定的比较值 (`XX`) 更改为与每个选项匹配即可。

**5.** 将文件保存为 `calculator.php`，将其放在您的 Web 目录中，并在 Web 浏览器中测试它。

![Image](img/03_figure_10_a.jpg)

表单现在会回显先前提交的值...

![Image](img/03_figure_11_b.jpg)

...无论表单是否已完全填写。

***

### 提示

由于每加仑价格和燃油效率值均为数字，因此您可以在添加的条件语句中给比较值加引号，也可以不加。我选择给它们加引号，因为从技术上讲，它们是具有数字值的字符串。

***

### 提示

由于本示例中添加的 PHP 代码位于 HTML 表单元素标签内部，因此错误消息可能不明显。如果出现问题，请检查页面的 HTML 源代码，查看 PHP 错误是否打印在 `value` 属性和标签本身中。

***

### 提示

您应该始终为 HTML 属性加上双引号，特别是文本输入框的 `value` 属性。如果不这样做，像 *Elliott Smith* 这样的多词值在 Web 浏览器中将仅显示为 *Elliott*。

***

### 提示

某些 Web 浏览器也会为您记录输入表单的值；这是一个独立的问题，但可能与使用 PHP 实现此功能的问题有重叠。

***

### 创建您自己的函数

PHP 拥有大量内置函数，几乎涵盖了您可能需要的所有功能。但更重要的是，PHP 允许您为任何目的定义并使用自己的函数。创建自己的函数的语法是：

```php
function function_name() {
    // Function code.
}
```

您的函数名称可以是字母、数字和下划线的任意组合，但必须以字母或下划线开头。您也不能将现有函数名用于您的函数（`print`、`echo`、`isset` 等）。一个完全有效的函数定义是：

```php
function do_nothing() {
    // Do nothing.
}
```

在 PHP 中，正如第一章所述，函数名不区分大小写（这与变量名不同），因此您可以使用 `do_Nothing()`、`DO_NOTHING()` 或 `Do_Nothing()` 等来调用该函数，但不能使用 `donothing()` 或 `DoNothing()`。

函数内的代码几乎可以做任何事情，从生成 HTML 到执行计算，再到调用其他函数。

创建自己的函数最常见的原因有：

* 将重复的代码与一次函数调用关联起来。
* 将敏感或复杂的过程与其他代码分离开来。
* 使常用代码片段更易于重用。

本章将介绍几个示例，您将在本书的其余部分看到其他示例。在第一个示例中，将定义一个输出生成理论广告所需 HTML 代码的函数。然后将在主页上调用该函数两次。

![Image](img/03_figure_12_a.jpg)

这两个“广告”是通过调用同一个用户定义函数生成的。

#### 创建您自己的函数

**1.** 在文本编辑器或 IDE 中打开 `index.php` (脚本 3.4)。

**2.** 在开始的 PHP 标签之后，开始定义一个新函数 (**脚本 3.7**)：

```php
function create_ad() {
```

此处要编写的函数理论上将生成向网页添加广告所需的 HTML。函数名称清楚地说明了其用途。

虽然不是必需的，但惯例是将函数定义放在脚本的最顶部附近或单独的文件中。

**3.** 生成 HTML：

```php
echo '<p class="ad">This is an annoying ad! This is an annoying ad! This is an annoying ad! This is an annoying ad!</p>';
```

**脚本 3.7.** 此版本的主页包含一个用户定义函数，用于输出理论广告。该函数在脚本中被调用了两次，从而创建了两个广告。
