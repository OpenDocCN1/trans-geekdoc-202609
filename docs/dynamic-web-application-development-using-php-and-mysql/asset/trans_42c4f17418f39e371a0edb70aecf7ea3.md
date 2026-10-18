
为了可读性和可重用性，我们将此函数保存为 JavaScript 文件：

```
getxmlhttprequest.js
```

然后我们使用以下 JavaScript 指令在每个脚本中加载此函数：

```
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
```

这意味着一旦我们创建了此函数，就可以在每个示例中一遍又一遍地使用它，而无需以任何方式重新创建或更改它。除了 ‘getxmlhttprequest.js’ 文件外，以下每个示例还都有一个唯一的 JavaScript 文件，其中包含两个函数，使用 xhrRequest.open() 函数打开与服务器上 PHP 脚本的连接，并处理服务器的响应。这些两个函数存储在一个 JavaScript 文件中，其名称适合示例脚本，例如：

- example18-1.js
- example18-2.js
- ...
- example18-6.js

由 xhrRequest.open() 函数调用的 PHP 脚本也根据示例赋予适当的文件名，例如：

- example18-1.php
- example18-2.php
- ...
- example18-6.php

而将所有内容包装在一起并由用户调用以启动示例的 (X)HTML 文件命名为：

- example18-1.htm
- example18-2.htm
- ...
- example18-6.htm

因此，每个示例都由四个文件组成：两个 JavaScript 文件、一个 PHP 服务器脚本和一个 (X)HTML 文件。我们将从最简单的示例开始，以说明这些文件如何协同工作。

## 18.2 一个简单的计算器

以下示例实现了一个简单的计算器。此计算器允许用户在几个表单字段中输入数字，然后通过从表单选择字段中选择运算符（加、减、乘和除）对输入的数字执行一些基本数学运算。以下是用户从浏览器调用的 (X)HTML 脚本，命名为 ‘example18-1.htm’：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```
```html
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Calculator Script</title>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />

<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-1.js">
</script>
</head>
<body>
<!-- File: example18-1.htm -->

<h2>Simple Calculator:</h2>
<form action="" method="post">
<p>
<input type="text" name="intValue1" id="intValue1"
onchange="startJS();" />
<select name="strOperator" id="strOperator" onchange="startJS();">
<option value="1">+</option>
<option value="2">-</option>
<option value="3">/</option>
<option value="4">*</option>
</select>
<input type="text" name="intValue2" id="intValue2"
onchange="startJS();"/>
<input type="button" value="=" onclick="startJS();" />
<input type="text" name="intResult" id="intResult" />
</p>
</form>
</body>
</html>
```

在初始文档声明和标题信息之后，脚本首先包含 'getxmlhttprequest.js' 和 'example18-1.js' JavaScript 文件，这些文件将用于形成 XMLHttpRequest 对象并处理用户事件（输入数字和选择要执行的运算）：

```
```html
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-1.js">
</script>
```
```

接下来，声明了一个表单，由五个表单元素组成。这些元素是用户输入用于计算的数字的两个输入文本字段、用于选择数学运算符的选择元素、用于强制更新计算（通过单击它）的输入按钮以及显示计算总和的输入文本字段：

```
```html
<form action="" method="post">
<p>
<input type="text" name="intValue1" id="intValue1"
onchange="startJS();" />
```
```
```
<select name="strOperator" id="strOperator" onchange="startJS();">
<option value="1">+</option>
<option value="2">-</option>
<option value="3">/</option>
<option value="4">*</option>
</select>
<input type="text" name="intValue2" id="intValue2"
onchange="startJS();"/>
<input type="button" value="=" onclick="startJS();" />
<input type="text" name="intResult" id="intResult" />
</p>
</form>
```

请注意，已在某些表单元素上包含三个 ‘onchange’ 事件，每当输入文本字段或选择字段更改时都会调用函数 startJS()。如果单击按钮，onclick 事件也会调用函数 startJS()。

函数 startJS() 以及另一个函数 changePage() 在 ‘example18-1.js’ 文件中定义如下：

```
function startJS() {
  xhrRequest = null;
  try {
    xhrRequest = getXMLHttpRequest();
  }
  catch(error) {
    document.write("Cannot run Ajax code using this browser");
  }

  if(xhrRequest != null) {
    // get form values
    var intValue1 = document.getElementById("intValue1").value;
    var intValue2 = document.getElementById("intValue2").value;
    var strOperator = document.getElementById("strOperator").value;
    var strUrl = "example18-1.php?intValue1=" + intValue1 + "&intValue2=" +
                intValue2 + "&strOperator=" + strOperator;

    xhrRequest.onreadystatechange = changePage;
    xhrRequest.open("GET", strUrl, true);
    xhrRequest.send(null);
  }
}
```

```
function changePage() {
  if (xhrRequest.readyState == 4 && xhrRequest.status == 200) {
    var intResponse = xhrRequest.responseText;
    document.getElementById("intResult").value = intResponse;
  }
}
```

函数 startJS() 首先通过尝试通过调用 ‘getxmlhttprequest.js’ 文件中的 getXMLHttpRequest() 函数来创建 getXMLHttpRequest 对象，从而确定浏览器是否支持 Ajax。如果生成错误，则显示一条消息并终止操作：

```
```javascript
xhrRequest = null;
try {
  xhrRequest = getXMLHttpRequest();
}
catch(error) {
  document.write("Cannot run Ajax code using this browser");
}
```
```

如果一切正常，则获取两个输入文本表单字段值中的值以及来自选择字段的运算符，并将其存储在单独的变量中：

```
```javascript
if(xhrRequest != null) {
  // get form values
  var intValue1 = document.getElementById("intValue1").value;
  var intValue2 = document.getElementById("intValue2").value;
  var strOperator = document.getElementById("strOperator").value;
}
```
```

接下来，创建了一个定义与服务器上 PHP 脚本连接的字符串。它由脚本名称和从计算器表单获得的数据创建的三个变量组成：

```
```javascript
var strUrl = "example18-1.php?intValue1=" + intValue1 +
  "&intValue2=" + intValue2 + "&strOperator=" + strOperator;
```
```

最后，调用了 XMLHttpRequest 对象的三个方法：

```
```javascript
xhrRequest.onreadystatechange = changePage;
xhrRequest.open("GET", strUrl, true);
xhrRequest.send(null);
```
```

这些方法定义了 PHP 脚本执行某些操作时应调用哪个函数、打开与 PHP 脚本的连接并将表单数据发送到脚本。在此示例中，当 PHP 脚本执行某些操作时，由 JavaScript 函数 changePage() 处理，该函数也包含在 ‘example18-1.js’ 文件中：

```
```javascript
function changePage() {
  if (xhrRequest.readyState == 4 && xhrRequest.status == 200) {
    var intResponse = xhrRequest.responseText;
    document.getElementById("intResult").value = intResponse;
  }
}
```
```

函数 changePage() 只是确定 PHP 脚本是否已执行完毕，如果是，则将脚本的输出存储在变量 intResponse 中。然后此值被注入到表单文本结果字段中，从而向用户显示计算的答案。

## **图 18.1** 简单计算器

![](img/b2471264f405d17994ef173e4b9cec92_550_0.png)

PHP 脚本 ‘example18-1.php’，它被调用并执行计算如下：

```
```php
<?php
// File: example18-1.php
$intValue1 = $_GET["intValue1"];
$intValue2 = $_GET["intValue2"];
$strOperator = $_GET["strOperator"];

switch ($strOperator){
    case 1: echo $intValue1 + $intValue2;
        break;
    case 2: echo $intValue1 - $intValue2;
        break;
    case 3: echo $intValue1 / $intValue2;
        break;
    case 4: echo $intValue1 * $intValue2;
}
?>
```
```

该脚本通过 GET 方法获取传递给它的三个变量的值，并使用 ‘switch’ 语句使用 ‘echo’ 结构输出数学计算的结果。

上述示例的输出如 图 18.1 所示。

总之，示例创建了一个简单的 Web 表单并等待用户触发事件。当触发事件时，会建立 Ajax 连接并调用 PHP 脚本。当 PHP 脚本完成后，脚本的输出会显示在表单上。

## 18.3 一个简单的数据库库存示例

本示例说明了一个简单的动态数据库库存检查，并演示了 Ajax 可用于运行获取存储在数据库中的最新信息的 PHP 脚本。使用 Ajax 进行此示例的优点是，当用户与应用程序交互时查询数据库，从而确保显示的信息准确，但用户不会因页面重新加载而感到不便：

```
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```
