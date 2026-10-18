
如下面的脚本所示：

```
<h2>Please select your favourite colors:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>Blue <input type='checkbox' name='strColorBlue' value='blue'/>
Green <input type='checkbox' name='strColorGreen' value='green'/>
Yellow <input type='checkbox' name='strColorYellow' value='yellow'/>
Red <input type='checkbox' name='strColorRed' value='red'/></p>
<p><input type='submit' name='SubmitQuery'/></p>
</form>
<?php
// File: example10-6.php
if (isset($_POST["submit"]) ) {
    $strColorBlue = $_POST["strColorBlue"];
    $strColorGreen = $_POST["strColorGreen"];
    $strColorYellow = $_POST["strColorYellow"];
    $strColorRed = $_POST["strColorRed"];
    echo "<p>Your favourite colors are $strColorBlue $strColorGreen $strColorYellow $strColorRed</p>";
}
?>
```

上述脚本输出一个表单，其中包含四个标签和复选框字段：

```
<label for="strBlue">Blue: </label>
<input type='checkbox' name='strColorBlue' value='blue' id='strBlue'/>
<label for="strGreen">Green: </label>
<input type='checkbox' name='strColorGreen' value='green' id='strGreen'/>
<label for="strYellow">Yellow: </label>
<input type='checkbox' name='strColorYellow' value='yellow' id='strYellow'/>
<label for="strRed">Red: </label>
<input type='checkbox' name='strColorRed' value='red' id='strRed'/></p>
```

由于用户可以选中任意一个或全部复选框，因此 PHP 脚本必须确保访问每个复选框中存储的所有数据值。这里通过以下代码实现：

```
$strColourBlue = $_POST["strColorBlue"];
$strColourGreen = $_POST["strColorGreen"];
$strColourYellow = $_POST["strColorYellow"];
$strColourRed = $_POST["strColorRed"];
```

图 10.11 展示了该脚本生成的输出。

## 选择结构

表单选择结构与迄今为止我们介绍过的那些使用 input 元素的表单元素不同。选择结构实际上使用两个独立的 (X)HTML 元素：select 元素和 option 元素。选择结构的格式如下：

### 图 10.11 访问复选框数据

![](img/b2471264f405d17994ef173e4b9cec92_313_0.png)

```
<select name='name'>
<option>option</option>
...
</select>
```

以下脚本展示了此元素的使用示例：

```
<h2>Please select your title:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><select name='strTitle'>
<option>Mr</option>
<option>Miss</option>
<option>Ms</option>
<option>Mrs</option>
<option>Dr</option>
</select></p>
<p><input type='submit' name='SubmitQuery' /></p>
</form>
<?php
// File: example10-7.php
if (isset($_POST["submit"]) ) {
$strTitle = $_POST["strTitle"];
echo "<p>Your title is $strTitle</p>";
}
?>
```

上述脚本输出的表单选择结构如下：

```
<p><select name='strTitle'>
<option>Mr</option>
<option>Miss</option>
<option>Ms</option>
<option>Mrs</option>
<option>Dr</option>
</select></p>
```

### 图 10.12 访问选择数据

![](img/b2471264f405d17994ef173e4b9cec92_314_0.png)

请注意，在此示例中，select 元素内包含五个 option 元素。访问所选数据项的值与之前的脚本相同：

```
$strTitle = $_POST["strTitle"];
```

上述脚本的输出如图 10.12 所示。

## 文本区域

另一个表单元素是 textarea，它是一个具有指定行数和列数的文本框，用户可以在其中输入文本。该元素的格式如下：

```
<textarea name='name' rows='num' cols='num'>
</textarea>
```

当表单显示时，位于 textarea 元素开始标签和结束标签之间的任何文本都会显示在字段中。

以下脚本演示了 textarea 元素的使用：

```
<h2>Please enter your address:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><textarea name='strAddress' rows='5' cols='30'></textarea></p>
<p><input type='submit' name='submit' /></p>
</form>
<?php
// File: example10-8.php
if (isset($_POST["submit"]) ) {
    $strAddress = $_POST["strAddress"];
    echo "<p>Your address is $strAddress</p>";
}
?>
```

### 图 10.13 访问 textarea 数据

![](img/b2471264f405d17994ef173e4b9cec92_315_0.png)

### 图 10.14 四种形状作为 input 元素

![](img/b2471264f405d17994ef173e4b9cec92_315_1.png)

该脚本显示一个 30 列、5 行的 textarea 字段：

```html
<p><textarea name='strAddress' rows='5' cols='30'></textarea></p>
```

输入到该字段中的地址与其他表单元素的访问方式相同：

```php
$strAddress = $_POST["strAddress"];
```

图 10.13 演示了 textarea 字段的使用。

## 图像字段

表单可以将图像作为输入字段进行处理。虽然这乍一看可能有些奇怪，但请看一下图 10.14 中的图像。该图像由四个形状组成，并以文件名 fourshapes.gif 保存。可以使用以下语法将表单的 input 元素指定为图像类型：

```
`<input type='image' src='image' name='name'/>`
```

当被点击时，图像元素会将鼠标点击的 X 和 Y 坐标返回给表单脚本。这些坐标以两个独立数据项（name_x 和 name_y）的形式返回，其中 name 是赋予图像元素的名称。图像的 (0,0) 位置位于左上角。图像大小为 300×300 像素，因此右下角坐标为 (300,300)。

以下脚本演示了此表单元素的一个使用示例：

```php
<h2>Please click the image:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><input type='image' src='graphics/fourshapes.gif'
name='intImage'/></p>
</form>
<?php
// File: example10-9.php
if (isset($_POST["intImage_x"])) {
    $intImageX = $_POST["intImage_x"];
    $intImageY = $_POST["intImage_y"];
    if ($intImageY < 150 && $intImageX < 150)
        echo "<p>You clicked on or near the Circle</p>";
    if ($intImageY < 150 && $intImageX >= 150)
        echo "<p>You clicked on or near the Square</p>";
    if ($intImageY >= 150 && $intImageX < 150)
        echo "<p>You clicked on or near the Triangle</p>";
    if ($intImageY >= 150 && $intImageX >= 150)
        echo "<p>You clicked on or near the Pentagon</p>";
}
?>
```

上述脚本在表单中包含一个 image 输入类型：

```
`<p><input type='image' src='graphics/fourshapes.gif' name='intImage'/></p>`
```

由于单击图像时表单即被提交，因此不需要提交按钮，需要将对提交按钮的检查替换为对 X 或 Y 坐标的检查：

```
`if (isset($_POST["intImage_x"])) {`
```

X 和 Y 坐标被复制到两个单独的变量中：

```php
$intImageX = $_POST["intImage_x"];
$intImageY = $_POST["intImage_y"];
```

使用四个 if 语句，通过判断返回的 X 和 Y 坐标来确定点击了哪个形状：

```
if ($intImageY < 150 && $intImageX < 150)
    echo "<p>You clicked on or near the Circle</p>";
if ($intImageY < 150 && $intImageX >= 150)
    echo "<p>You clicked on or near the Square</p>";
if ($intImageY >= 150 && $intImageX < 150)
    echo "<p>You clicked on or near the Triangle</p>";
if ($intImageY >= 150 && $intImageX >= 150)
    echo "<p>You clicked on or near the Pentagon</p>";
```

| 注意 | 由于单击图像时表单即被提交，因此无需在表单中包含提交按钮。 |

## 10.7 文件上传

表单可以使用一个元素，让用户从本地计算机选择文件并上传到服务器，供 PHP 脚本访问。这是一个复杂的过程，第 12 章将对此进行较为详细的介绍。

## 10.8 表单验证与数据保留

在与用户交互时，务必确保你认为用户输入的数据确实是你想要的数据。用户常常不会按你预期的内容输入，因此表单数据验证非常重要。如果检测到表单中输入的数据有误，则应重新向用户显示表单以供更正。然而，如果用户不得不重新输入所有表单数据，即使是那些最初正确的数据，也会非常令人恼火。因此，需要一种保留并重新显示表单数据的方法。

### 有无输入？

最简单的验证方式之一是判断用户在表单字段中是否输入了内容。检查文本或密码字段是否包含数据，只需检查由该表单字段创建的变量长度是否不为零即可。在大多数情况下，可以使用一个简单的 if 语句来完成，例如：

```
if (formvariable == NULL)
```

除了简单地检查字段中是否有数据外，还应在表单字段旁边生成适当的错误消息，向用户指出问题所在。

对于 select 表单字段，情况就有些不同了。默认情况下，菜单中的第一项会被自动选中。如果用户不想选择默认项，你需要一种方法来判断他们是否忘记输入。解决此问题的一种方法是
