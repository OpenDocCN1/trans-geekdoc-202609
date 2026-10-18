
```
<input type="text" name="strFirstname" id="strFirstname"/>
</p><p>
<label for="strSurname">Surname: </label>
<input type="text" name="strSurname" id="strSurname"/>
</p><p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p><p>
<input type="submit"/>
</p>
</form>
```

您应该熟悉 XHTML 表单，但让我们花一点时间快速检查一下构成脚本的元素。

| 注 | 请注意示例网页表单脚本是一个 XHTML 文档，应保存为扩展名为 .htm 的文件。 |

‘form’ 元素由开始和结束标签组成，并包围表单内的所有其他元素：

```
<form action="filename" method="type">
...
</form>
```

开始的 form 标签包含两个属性，用于指定表单提交时要执行的操作（这通常是调用脚本的名称，在我们的例子中，是一个名为 ‘example10-1.php’ 的 PHP 脚本）以及数据应通过何种方式发送到脚本。PHP 支持 post 方法，因此该元素看起来如下：

```
<form action="example10-1.php" method="post">
...
</form>
```

不必担心 post 方法的确切含义是什么；我们很快就会解释如何访问通过 post 方法发送的数据。好在您不需要理解底层机制就能获得不错的结果。

在 ‘form’ 元素内还有许多其他元素。在本例中，这些主要是 ‘label’ 元素的配对，用于表示文本标签并将标签链接到特定的表单输入字段：

```
<label for="inputFieldId">textLabel</label>
```

标签后面跟着 ‘input’ 元素，其语法如下：

```
<input type="type" name="fieldname" id="inputFieldId"/>
```

‘input’ 元素包含一个 ‘type’ 属性，用于指定表单输入字段的类型，一个 ‘name’ 属性，用于指定字段中数据的唯一名称，以及一个 ‘id’ 属性，供 ‘label’ 元素引用。每个表单元素对都由一个 ‘paragraph’ 元素包围，以确保 ‘form’ 元素在网页上显示在单独的行上：

```
<p></p>
```

我们的表单字段如下所示：

```
<p>
<label for="strFirstname">Firstname: </label>
<input type="text" name="strFirstname" id="strFirstname"/>
</p><p>
<label for="strSurname">Surname: </label>
<input type="text" name="strSurname" id="strSurname"/>
</p><p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p>
```

上述 ‘input’ 元素是表单上的简单输入字段，用户可以在其中输入自由格式的答案。为了帮助指导用户输入内容，会使用一些附带文本来标记输入元素。

| 注 | 输入元素具有比我们上面提到的更多的属性，如果您不确定它们是什么以及如何使用，请查阅 XHTML 指南。 |

我们的最后一个输入元素类型为 ‘submit’，它允许提交表单数据。它在表单上显示为可点击的按钮：

```
<input type='submit' />
```

由于在本例中 ‘submit’ 按钮不会传输任何相关数据，我们选择不提供 ‘name’ 属性。

| 注 | 请注意，我们同时指定了 ‘text’ 和 ‘password’ 字段。唯一的区别是，在密码字段中，当用户输入任何内容时，文本会被隐藏。 |

我们之前提到过数组，并在上面再次提到了 $_POST 数组，但我们仍未详细解释它们。请耐心等待——我们在第 11 章中会进行说明。只是它们可能有点复杂，目前您可以访问它们而无需担心其工作原理。

图 10.4 说明了当值 ‘Simon’、‘Stobart’、‘myusername’ 和 ‘mypassword’ 输入到表单字段并点击提交按钮时，PHP 脚本产生的输出。

为了说明我们构建的脚本以及可能发生的交互，我们将引入一种图表约定。该图表由两种符号组成：表示网页或脚本的方框，以及表示操作的箭头。图 10.5 说明了我们的双脚本设计，上方方框代表调用 PHP 脚本的 (X)HTML 表单，并传递相关表单数据（由箭头表示）。然而，以这种方式分离 (X)HTML 表单和 PHP 脚本实际上并不是最佳做法。问题在于，如果您希望 PHP 脚本能够检查表单数据是否正确，并在有问题的字段旁边显示消息。

如果 PHP 脚本与 (X)HTML 表单分开，它就无法轻松修改它，因此前进的方向是将 (X)HTML 表单和 PHP 脚本合并到一个文件中。

### 图 10.4 显示 PHP 表单数据

![](img/b2471264f405d17994ef173e4b9cec92_302_0.png)

### 图 10.5 分离的 (X)HTML 和 PHP 脚本

![](img/b2471264f405d17994ef173e4b9cec92_302_1.png)

### 图 10.6 合并的 (X)HTML 表单和 PHP 脚本

![](img/b2471264f405d17994ef173e4b9cec92_303_0.png)

## 10.3 结合 PHP 和表单

我们要做的是将 (X)HTML 表单和 PHP 脚本合并为一个单一文档。当表单提交按钮被点击时，表单调用自身并处理其中的 PHP 脚本。这在图 10.6 中有所说明。

在图 10.6 中，有一个代表单一脚本的方框，以及一个代表数据提交回脚本的箭头。

如果脚本已经在运行，为什么我们需要将表单数据提交回脚本呢？因为您在表单中输入的数据只有在点击提交按钮并将表单数据提交到 Web 服务器后，PHP 脚本才能访问。

让我们看一个结合 PHP 和 (X)HTML 表单的示例脚本：

```
<h2>Please enter your personal details:</h2>
<form action='example10-2.php' method='post'>
<p>
<label for="strFirstname">Firstname: </label>
<input type="text" name="strFirstname" id="strFirstname"/>
</p><p>
<label for="strSurname">Surname: </label>
<input type="text" name="strSurname" id="strSurname"/>
</p><p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p><p>
<input type="submit"/>
</p>
</form>
```

```
<?php
// File: example10-2.php
$strFirstname = $_POST["strFirstname"];
$strSurname = $_POST["strSurname"];
$strUsername = $_POST["strUsername"];
$strPassword = $_POST["strPassword"];
echo "<p>Greetings $strFirstname $strSurname</p>";
echo "<p>Your username is $strUsername and your password is $strPassword</p>";
?>
```

上面的脚本是之前介绍的 (X)HTML 表单和 PHP 脚本的组合。然而，虽然语法正确且没有产生错误，但脚本产生的输出并不完全符合要求，如图 10.7 所示。

在图 10.7 中，我们看到首次查看页面时，PHP 脚本的输出是可见的，并且由于没有发送表单数据，变量未定义并显示不完整消息。

### 图 10.7 合并的 (X)HTML 和 PHP 问题

![](img/b2471264f405d17994ef173e4b9cec92_304_0.png)

此外，您可能会看到类似以下的警告通知：

```
Notice: Undefined index: strFirstname in C:\\wamp\\www\\PHPLessonExamples\\Lesson10\\
example10-2.php on line 35

Notice: Undefined index: strSurname in C:\\wamp\\www\\PHPLessonExamples\\Lesson10\\
example10-2.php on line 36

Notice: Undefined index: strUsername in C:\\wamp\\www\\PHPLessonExamples\\Lesson10\\
example10-2.php on line 37

Notice: Undefined index: strPassword in C:\\wamp\\www\\PHPLessonExamples\\Lesson10\\
example10-2.php on line 38
```

这些是在脚本首次运行时通知您这些变量尚未创建。默认情况下这些警告是关闭的，因此您可能在计算机上看不到它们显示。然而，这不是良好的编程实践（如第 20 章进一步所述），因此我们需要一种方法来确定表单数据是否已提交。

```
<h2>Please enter your personal details:</h2>
<form action='example10-3.php' method='post'>
<p>
<label for="strFirstname">Firstname: </label>
<input type="text" name="strFirstname" id="strFirstname"/>
</p><p>
<label for="strSurname">Surname: </label>
<input type="text" name="strSurname" id="strSurname"/>
</p><p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p><p>
<input type="submit" name="submit"/>
</p>
</form>
```

```
<?php
// File: example10-3.php

if (isset($_POST["submit"])) {
    $strFirstname = $_POST["strFirstname"];
    $strSurname = $_POST["strSurname"];
    $strUsername = $_POST["strUsername"];
    $strPassword = $_POST["strPassword"];

    echo "<p>Greetings $strFirstname $strSurname</p>";
    echo "<p>Your username is $strUsername and your password is
$strPassword</p>";
}
?>
```
