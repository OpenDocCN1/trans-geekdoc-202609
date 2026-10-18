
```
<a href="javascript:changeDisplay('jsdetail')">JavaScript</a>
</div>
<div id="jsdetail">
JavaScript is a scripting language that can be run inside the browser to enable client-side processes.
</div>
<div>
<a href="javascript:changeDisplay('dhtmldetail')">
DHTML (Dynamic HTML)</a>
</div>
<div id="dhtmldetail">
DHTML is a label given to techniques that use JavaScript, CSS and the DOM to make web pages more dynamic and interactive.
</div>
</body>
</html>
```

图 7.7 显示页面在初始加载到浏览器时的情况，此时两个 div 元素样式均处于 ‘none’ 显示状态。

图 7.8 显示当两个 ‘div’ 元素样式均处于 ‘block’ 状态（即可见）时页面的外观。

**图 7.7 通过将样式的 display 属性设置为 ‘none’ 来隐藏 ‘div’ 元素**

![](img/b2471264f405d17994ef173e4b9cec92_219_0.png)

**图 7.8 通过将样式的 display 属性设置为 ‘block’ 使 ‘div’ 元素可见**

![](img/b2471264f405d17994ef173e4b9cec92_219_1.png)

## 7.4 客户端表单验证

JavaScript 在 Web 应用中能发挥的最有用的作用之一是对用户输入到网页表单中的数据进行客户端验证。我们只能在客户端提供表面验证。例如，我们可以检查信用卡号码是否符合信用卡号码的正确格式，或检查特定类型的卡，如 Visa 卡，是否以该类型的正确号码开头，但我们无法在浏览器中实际检查信用卡本身的有效性。那必须由服务器端进程来完成。表面验证包括检查空字段、检查是否已做出选择（例如来自单选按钮或下拉列表），而不是保留空默认值，检查数字、日期、电子邮件或信用卡字段是否包含正确类型的字符，等等。

### 处理表单的函数

对于普通的 HTML 表单，按下 ‘submit’ 按钮会将 HTTP 请求发布到表单元素的 ‘action’ 属性定义的 URI。例如，此简单表单包含用户 ID 和密码的输入字段，并提交到名为 ‘customerLogin’ 的服务器端应用程序：

```html
<form action="customerLogin" method="post">
<table>
<tr>
<td><label for="loginid">Login Name:</label></td>
<td><input type="text" id="loginid"/></td>
</tr>
<tr>
<td><label for="pword">Password:</label></td>
<td><input type="password" id="pword"/></td>
</tr>
<tr>
<td></td>
<td><input type="submit" value="Login"/>
<input type="reset" value="Clear form"/></td>
</tr>
</table>
</form>
```

表单一旦提交到服务器，就为时已晚，无法在浏览器中验证任何表单数据。因此，JavaScript 为我们提供了一个特殊的 ‘onsubmit’ 事件，让我们在按下按钮时调用函数，而不是直接提交到服务器。我们可以使用该函数来验证表单，并根据表单内容是否有效返回 ‘true’ 或 ‘false’。如果返回 ‘true’，则表单数据将提交到服务器端应用程序。如果返回 ‘false’，则取消提交，我们可以给用户机会纠正他们输入的数据。

JavaScript 函数可以通过以下两种方式访问表单的组件以检查其有效性：

- The function can use the DOM to access the form’s components via the document object.
- The form can be passed as a parameter to the function.

作为第一种方法的示例，此表单标签包含 ‘onsubmit’ 事件处理程序，调用一个名为 ‘validate’ 的 JavaScript 方法，该方法不带参数：

```html
<form action="customerLogin" method="post" onsubmit="return validate()">
```

如果未将表单的引用传递给函数，则可以使用 DOM 的 ‘getElementById’ 方法定位表单的输入字段，只要它们具有 ‘id’ 属性。在此示例中，函数使用 DOM 访问 ‘loginid’ 文本字段，检查它是否为空字段（使用双引号中间什么都没有表示空字符串，这将是空文本输入字段的内容）。

```javascript
function validate()
{
    if(document.getElementById("loginid").value==""
    ...
```

相比之下，此版本的表单元素采用第二种方法，将表单作为参数传递给 ‘validate’ 方法。表单使用保留字 ‘this’ 引用（即把此表单传递给函数）：

```html
<form action="customerLogin" method="post" onsubmit="return validate(this)">
```

如果将表单的引用作为参数传递给函数，则可以通过参数对象的子元素访问表单控件。在此示例中，我们通过表单而不是 document 对象导航到同一个文本字段（‘loginid’）。

```javascript
function validate(loginForm)
{
    if(loginForm.loginid.value=="")
    ...
```

使用哪种方法取决于你，但将表单传递给函数似乎在验证例程中更常用。

### 弹出对话框

到目前为止，本节我们研究了一些检查表单组件状态的 JavaScript 代码，但如果我们想向用户指示存在问题怎么办？我们可以使用前面介绍的技术通过 DOM 向页面写入，但指示应用程序中出现问题的更常见方法是显示弹出对话框。JavaScript 提供了三种类型的弹出对话框，即 alert、confirm 和 prompt 对话框。这些是模态对话框，这意味着在关闭它们之前你无法在浏览器中执行其他任何操作。它们是通过使用 window 对象的 ‘alert’、‘confirm’ 和 ‘prompt’ 方法调用的。

alert 用于简单地向用户显示消息。alert 上的唯一按钮是 ‘OK’ 按钮，点击后对话框会消失。创建 alert 非常简单；我们只需将要显示的文本作为参数（在括号中）传递给 alert 函数：

```javascript
alert("message");
```

confirm 对话框与 alert 相似，因为它会包含某种类型的消息。然而它有两个按钮，‘OK’ 和 ‘Cancel’。如果用户点击 ‘OK’，框返回 true。如果用户点击 ‘Cancel’，框返回 false。

```javascript
confirm("message");
```

与另外两种对话框不同，prompt 对话框会要求用户输入值。除了文本输入字段外，它还包含 ‘OK’ 和 ‘Cancel’ 按钮。如果用户点击 ‘OK’，框返回输入值，但如果用户点击 ‘Cancel’，框返回 null。JavaScript 中的 null 值意味着变量没有值。

```javascript
var returnValue=prompt("prompt text", "default value");
```

这里有一个简单的 JavaScript 函数，按顺序创建这三种对话框类型。当调用该函数时，对话框会一个接一个地出现。

```javascript
// File: showdialogs.js
function showDialogs()
{
  alert("This is an alert");
  confirm("This message wants confirmation");
  prompt("Please enter something in the text area", "I'm a default");
}
```

这里有一个在加载时调用此函数的 XHTML 页面：

```html
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<meta http-equiv="Content-Script-Type" content="text/javascript"/>
<title>JavaScript Dialogs</title>
<script type="text/javascript" src="showdialogs.js">
</script>
</head>
<body onload="showDialogs()">
<!-- File: example7-9.htm -->
</body>
</html>
```

图 7.9 显示了 Mozilla Firefox 2 浏览器中显示这三个对话框时的外观。它们在其他浏览器中看起来略有不同，但内容和按钮基本相同。

### 在验证例程中使用对话框

这三种对话框类型都可以在验证例程中使用。然而，也许最简单的方法是使用 alert 来通知用户表单数据中存在错误。

这里有一个完整的 ‘validate’ 函数，使用表单参数和 alert。该函数检查登录表单中用户名或密码文本字段是否为空。在每个
