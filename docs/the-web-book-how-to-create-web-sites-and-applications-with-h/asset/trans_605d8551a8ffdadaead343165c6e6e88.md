

If ($cb_beans == "Y")
{
  echo "beans<br>";
}

If ($cb_bacon == "Y")
{
  echo "bacon<br>";
}

If ($cb_sausages == "Y")
{
  echo "sausages<br>";
}

If ($cb_eggs == "Y")
{
  If ($eggs_style == "F") { echo "Fried eggs<br><br>"; }
  If ($eggs_style == "P") { echo "Poached eggs<br><br>"; }
  If ($eggs_style == "S") { echo "Scrambled eggs<br><br>"; }
}

echo "</p>";

?>

你可能会注意到，在此之前你还没有见过使用哈希符号（#）来表示注释的开头。此外，请注意我们如何使用 `$_POST["something"]` 来检索每个表单变量。

数据以两种方式发送到 PHP 程序。一种是通过 URL，例如：

www.yoursite.com/breakfast.php?meal=breakfast&eggs=fried

在这种情况下，PHP 程序必须使用 `$_GET` 来检索数据。但如果数据来自表单（正如这里的情况），你需要使用 `$_POST`。没错，这就是我们在表单标签中添加 `method="POST"` 的原因。

顺便说一下，不要尝试将表单标签中的方法改为 `method="get"`，然后使用 `$_GET` 来检索表单的内容。虽然有时这样也能工作，但表单的内容会显示在 URL 中。这样做存在严重的安全隐患。

请注意，我在输出周围生成了 `<p>` 标签，这样页面就能整齐地采用你在所选 CSS 样式表中指定的 `<p>` 标签布局。为此，你需要添加另一组生成 `<head>` 和 `<body>` 部分的 "echo" 语句，以及指向样式表的链接。该链接应放在 head 部分，如下所示：

<LINK href="style.css" rel="stylesheet" type="text/css">

然而，如果你打算用 PHP 生成这一行，请注意以下内容将无法正常工作：

echo "<LINK href="style.css" rel="stylesheet" type="text/css">";

问题在于，引号（"）在这里被用于两个不同的目的。最前面的一个和最后一个是 PHP 代码的一部分，指定输出到访客浏览器的文本的起止位置。其他的引号，则是输出文本的一部分。

当你想向访客的浏览器输出字面引号时，规则是需要在其前面加一个反斜杠。如下所示：

echo "<LINK href=\"style.css\" rel=\"stylesheet\" type=\"text/css\">";

另外，请注意我在一些 if... 语句中使用了不同的布局。如果访客想要鸡蛋，我随后使用单行表单来测试鸡蛋类型，其中一行用于比较，另一行用于显示消息。如果测试后需要执行的代码量很少，这种做法很有用，也能让代码更整洁。

## 测试表单

将上述 PHP 程序输入或粘贴到一个名为 breakfast.php 的文件中。将此文件上传到 Web 服务器，连同 form.html 文件（或你给它的其他名称）。确保两个文件都上传到服务器上的同一文件夹，并且 PHP 文件的名称与表单标签 "action" 部分中指定的名称相同。在某些服务器上，这是区分大小写的，因此 breakfast.php 与 BREAKFAST.PHP 不同。

上传两个文件后，浏览包含表单的页面，你应该看到以下内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_246_0.png)

检查是否可以在 Name 框中输入内容，以及是否可以选择一组食物项目和一种鸡蛋类型。按你的意愿填写表单，然后单击 Submit。如果运气好，你应该看到类似这样的结果：

![](img/50e1558b8202f19b96c1cc386ea5ec66_246_1.png)

它有效。表单中的数据已传输到我们的 breakfast.php 程序，并被正确处理和显示。此外，由于对表单输入进行了清理，该程序也以安全的方式编写。

能够创建表单并编写处理表单数据的 PHP 程序，是开发基于 PHP 的 Web 应用程序的关键部分。只有通过使用表单，你才能向你的网站的访客请求信息。

表单最有用的功能之一是你可以从数据库中自动填充它们，这一点我们将在后面详细讨论。但想象一下，例如，早餐项目列表（鸡蛋、培根等）存储在数据库表中。在访问数据库并获取项目列表后，你希望将它们呈现为一个菜单供用户选择。

以下是我们在 form.html 中最初用于创建菜单的代码：

Eggs <input type="checkbox" name="cb_eggs" value="Y" />
Bacon <input type="checkbox" name="cb_bacon" value="Y" />
Sausages <input type="checkbox" name="cb_saus" value="Y" />
Beans <input type="checkbox" name="cb_beans" value="Y" />

下面是它的 PHP 版本，基于我们已从数据库读取的项目数组。

<?php
for ($i = 0; $i <= count($items); $i++)
{
    echo $items[$i];
    echo "<input type=\"checkbox\" name=\"cb_" ;
    echo $items[$i] . "\" value=\"Y\" />";
}
?>

对于包含 "bacon"、"sausage" 和 "beans" 值的数组 $items[]，此代码将产生：

<input type="checkbox" name="cb_bacon" value="Y" />
<input type="checkbox" name="cb_sausage" value="Y" />
<input type="checkbox" name="cb_beans" value="Y" />

瞧，一个动态创建的复选框集合。现在，希望你可以开始看到 PHP 和 MySQL 如何协同工作，让你创建功能强大的基于 Web 的应用程序。你可能迫不及待想开始数据库相关的内容了。别担心，很快就到了。

请注意，当我要将引号输出到访客浏览器时（即它们不是 PHP 代码本身的一部分时），我在引号前加了反斜杠。这一点在第 246 页有更详细的讨论。

## 检索文本区域和下拉框数据

到目前为止，我已经展示了如何使用 PHP 检索文本框、复选框和单选按钮的内容。为了完整性，也值得解释如何检索文本区域和下拉框的值。

文本区域的内容的检索方式与文本框相同。只需使用 `$_POST["xyz"]`，其中 xyz 是在表单中定义的文本区域的名称。不过请记住，如果用户在输入文本区域内容时按下了回车键，它可能包含回车字符。从安全角度来看，回车字符是无害的，但如果你不想要它们，可以使用与清理所用的同类型的 `ereg_replace` 命令将它们移除。回车字符的 `ereg` 代码是 \r，但通常还跟着一个“换行”字符（\n）。因此，你需要查找 \n 和 \r 并将它们都删除。

至于下拉框，检索起来也容易。只需使用带有表单中指定的下拉框名称的 `$_POST[]`。例如，这是一个简单下拉框的 HTML 代码。如你所见，它是通过 `<select>` 标签创建的，尽管很少有人将其称为 select box：

<select name="dd_season">
<option>Spring</option>
<option>Summer</option>
<option>Autumn</option>
<option>Winter</option>
</select>

这在表单上产生以下内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_248_0.png)

在 PHP 中使用 `$_POST["dd_season"]` 将返回季节的名称。但是，还有一个你可能觉得有用的选项。考虑一下这个：

<select name="dd_season">
<option value="1">Spring</option>
<option value="2">Summer</option>
<option value="3">Autumn</option>
<option value="4">Winter</option>
</select>

现在，`$_POST[]` 返回的值不再是 Spring、Summer、Autumn 或 Winter。相反，返回的值将分别是 1、2、3 或 4。

想象你正在从数据库填充表单，如上所述。你想生成一个包含当前所有入住酒店客人的下拉列表。因此，你从数据库中检索他们的 ID 号和姓名。在我上面列出季节名称的地方，你显示客人的姓名。在我上面显示 1、2、3、4 的地方，你输出客人的 ID 号。现在，当酒店前台工作人员从下拉列表中选择一个特定姓名时，PHP 代码知道的是客人的数据库 ID 号，而不是他们的名字。重读关于数据库规范化的章节（第 183 页）时，请思考一下这一点，看看这是多么有用。

## 复选框数组

在创建 HTML 表单时，你经常会发现自己需要创建大量的复选框。例如，暂时沿用酒店管理系统的类比，也许你想显示一个屏幕，按编号列出每个卧室，并配有一个复选框，以便系统操作员可以选择哪些房间需要标记为需要清洁。

一种方法是做类似这样的事情：

Room 1 <input type="checkbox" name="room1" value="Y" /> <br>
Room 2 <input type="checkbox" name="room2" value="Y" /> <br>
Room 3 <input type="checkbox" name="room3" value="Y" /> <br>
Room 4 <input type="checkbox" name="room4" value="Y" /> <br>

当然，这样是可以工作的，但当接收复选框的 PHP 代码需要执行其操作时会带来问题。可能会有几十个复选框变量需要检查，每个都有一个不同但又略相似的名称。没有简单的方法使用循环
