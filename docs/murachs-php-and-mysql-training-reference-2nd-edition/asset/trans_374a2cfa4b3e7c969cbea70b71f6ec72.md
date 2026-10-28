

## 如何从复选框中获取数据

复选框允许用户选择一个选项。要创建复选框，可使用 `<input>` 标签，如图7-3所示。

该图中的HTML显示了三个复选框。与单选按钮不同，复选框的 name 属性值应互不相同，而且你不必设置 value 属性。在该图中，第一个复选框包含 checked 属性，因此网页加载时默认选中。

在许多情况下，你不希望复选框默认为选中状态。例如，你不应默认选中表示用户希望加入邮件列表的复选框。这样一来，如果该复选框被选中，你就能确定是用户手动勾选的，且确实希望加入邮件列表。

该图中的PHP演示了如何处理复选框的数据。对于每个复选框，它使用 isset 函数返回一个布尔值，以指示 `$_POST` 数组中是否设置了对应的键值对。如果复选框已被选中，则该键值对会存在于数组中，因此变量中存储 TRUE；否则存储 FALSE。

如果你使用 NetBeans IDE，它可能会在包含 isset 函数的代码行旁边显示警告图标。这是因为 NetBeans 不希望你直接操作 `$_POST` 数组，因为 `$_POST` 数组可能包含来自用户的恶意数据。然而，在这种情况下，你并不是在检索或处理 `$_POST` 数组中的数据，只是在检查某个值是否存在。因此，忽略 NetBeans 的警告是没有问题的。

### HTML `<input>` 标签的复选框属性

| 属性 | 描述 |
|---|---|
| `type` | 对于复选框，设置为“checkbox”。 |
| `name` | 每个复选框必须使用不同的名称。但是，如果要定义复选框数组，可以使用相同的名称，如下一图所示。 |
| `value` | 复选框被选中时使用的文本。只有在你处理下一图所述的复选框数组时，才需要此属性。 |
| `checked` | 该可选属性用于选中复选框。 |

### 三个复选框的HTML

```html
<input type="checkbox" name="pep" checked> Pepperoni<br>
<input type="checkbox" name="msh"> Mushrooms<br>
<input type="checkbox" name="olv"> Olives
```

### 浏览器中的复选框

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_238_0.png)

### 用于访问复选框数据的PHP

```php
<?php
    $pepperoni = isset($_POST['pep']);
    $mushrooms = isset($_POST['msh']);
    $olives = isset($_POST['olv']);
?>
```

### 说明

- *复选框*允许用户选择一个选项。
- 如果复选框被选中，isset 函数返回 TRUE，否则返回 FALSE。

## 如何从复选框数组获取数据

在上一图中，三个复选框具有唯一的名称，并分别进行处理。然而，由于这些复选框表示披萨的不同配料，它们实际上是相关的。此外，如果配料数量增加，分别处理每个复选框将变得繁琐。

幸运的是，PHP 提供了一种机制，可以将多个复选框的值合并到一个数组中。这样你可以使用循环来处理相关的复选框，从而使代码更易于扩展和维护。

图7-4展示了如何将多个复选框的值合并到一个数组中。为此，该代码对所有相关复选框使用相同的名称，并在名称末尾添加一对方括号，以表示这些复选框应存储在一个数组中。

当数据提交时，PHP 在读取第一个以方括号结尾的复选框名称时创建数组。然后，它将该复选框的值添加到数组中。当它读取另一个具有相同名称的复选框时，也会将该值附加到数组中。处理完成后，PHP 会将该数组嵌套在 `$_GET` 或 `$_POST` 数组中。

该图中的HTML将上一图中的三个复选框重写为一个复选框数组。与上一图不同，这段代码包含了这些复选框的值。PHP 使用这些值来标识复选框并指示其已选中。通常，该值对应数据库表中的主键。这样，该值就可用于查找有关所选复选框的更多信息。

如果你使用 NetBeans，它可能会警告你直接访问 `$_POST` 数组。在这种情况下，你将使用复选框的值，因此应留意该警告。要做到这一点，你可以使用 filter_input 函数获取指定数组中的所有项，并对它们应用过滤器以确保安全。然而，要使用 filter_input 函数获取数组，你必须将 `FILTER_REQUIRE_ARRAY` 常量作为第四个参数提供。否则，filter_input 函数将无法正确获取数组。

第一个 PHP 示例使用 filter_input 函数从 `$_POST` 数组中获取名为 top 的数组，并将其存储到名为 `$toppings` 的变量中。此外，这段代码为第三个参数提供了一个常量，该常量会将一些特殊字符（如 < 和 >）替换为 HTML 实体，从而有助于防范 XSS 攻击。然后，这段代码使用 if 语句检查 `$toppings` 数组是否至少包含一个元素。如果是，接下来的三条语句将访问 `$toppings` 数组中的前三个值。

然而，这种方法存在一个问题。如果只选中了两个或更少的复选框，访问数组中值的三条语句就会抛出错误。这是因为数组只包含与被选中复选框相对应的值。因此，通常使用 foreach 循环来处理复选框数组，如第二个示例所示。

这段代码使用与第一个示例相同的代码来获取 `$toppings` 数组。然后，如果 `$toppings` 数组包含元素，就使用 foreach 循环处理每个元素。在本例中，代码只是将每个元素的键和值发送到浏览器。然而，这段代码可以执行任何类型的处理。例如，它可以根据所选配料更新披萨的总价。

### 将三个相关复选框存储到数组中的HTML

```html
<input type="checkbox" name="top[]" value="pep"> Pepperoni<br>
<input type="checkbox" name="top[]" value="msh"> Mushrooms<br>
<input type="checkbox" name="top[]" value="olv"> Olives
```

### 浏览器中的复选框

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_240_0.png)

### 访问数组及其值的PHP

```php
<?php
    $toppings = filter_input(INPUT_POST, 'top',
                FILTER_SANITIZE_SPECIAL_CHARS, FILTER_REQUIRE_ARRAY);
    if ($toppings !== NULL) {
        $top1 = $toppings[0];       // $top1 is pep
        $top2 = $toppings[1];       // $top2 is olv
        $top3 = $toppings[2];       // $top3 is not set - throws an error
    }
?>
```

### 使用循环处理数组的PHP

```php
<?php
    $toppings = filter_input(INPUT_POST, 'top',
                FILTER_SANITIZE_SPECIAL_CHARS, FILTER_REQUIRE_ARRAY);
    if ($toppings !== NULL) {
        foreach($toppings as $key => $value) {
            echo $key . ' = ' . $value . '<br>';
        }
    } else {
        echo 'No toppings selected.';
    }
?>
```

### 浏览器显示的消息

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_240_1.png)

### 说明

- 如果复选框名称以 `[]` 结尾，PHP 会将该复选框添加到嵌套在 `$_GET` 或 `$_POST` 数组中的数组里。这样，多个值就可以使用相同的名称提交。
- 如果复选框数组中的所有复选框都没有被选中，则该数组不会在 `$_GET` 或 `$_POST` 数组中设置。
- 如果你打算使用复选框的值，应使用像 `filter_input` 这样的 PHP 函数来获取数组的值并确保其安全。为此，可以使用本图所示的过滤器。

图7-4  如何从复选框数组获取数据

## 如何从下拉列表中获取数据

*下拉列表*（又称*单选列表*）强制用户从列表中选择一个选项。要创建下拉列表，可使用 `<select>` 和 `<option>` 标签，如图7-5所示。

该图中的HTML创建了一个下拉列表，允许用户从三种信用卡选项中选择一种。这里，`<select>` 标签指定列表的名称。然后，在 `<select>` 标签内，三个 `<option>` 标签定义选项。当页面由浏览器渲染时，会显示 `<option>` 开闭标签之间的内容。当页面提交到服务器时，value 属性指定提交给服务器的值。例如，图中的第一个选项在列表中显示“Visa”，但向服务器提交“visa”。

该图中的PHP演示了如何获取所选选项的值。由于下拉列表强制用户选择一个选项，因此下拉列表的名称/值对总会提交到服务器。这意味着在你的代码中，无需检查 filter_input 函数是否返回 NULL。

如果你不为任何选项编写 selected 属性，页面加载时将默认选中第一个选项。但是，如果你想设置不同的默认选项，可以为该选项编写 selected 属性。例如，要使 MasterCard 成为默认选项，可以像图中第二个 HTML 示例那样编写其 `<option>` 标签。

对于下拉列表，你应该只为其中一个选项编写 selected 属性。如果你为多个选项编写该属性，浏览器会选择带有 selected 属性的最后一个选项。

