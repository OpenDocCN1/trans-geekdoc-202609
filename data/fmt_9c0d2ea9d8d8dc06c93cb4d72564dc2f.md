
乍一看，Cookie 似乎解决了从页面到页面移动数据的整个问题。只需将 Cookie 存储在用户的计算机上，并在需要时获取它即可。事实上，Cookie 可以被存储，以便在用户离开你的网站后仍然保留，并在用户一个月后再次进入你的网站时仍然可用。问题解决了！好吧，不完全是。Cookie 不在你的控制之下：它们在用户的控制之下。用户可以随时删除 Cookie。事实上，用户可以设置浏览器以拒绝允许任何 Cookie。而且许多用户确实拒绝 Cookie 或定期删除它们。许多用户对陌生人将东西存储在他们的计算机上的整个想法并不感到舒服，尤其是文件在他们离开陌生人的网站后仍然保留。这是一种可以理解的态度。然而，它确实限制了 Cookie 的有用性。如果你的应用程序依赖于 Cookie 而用户已关闭 Cookie，则你的应用程序对该用户不起作用。

Cookie 最初设计用于在短时间内存储少量信息。除非你专门设置 Cookie 使其持续更长时间，否则 Cookie 将在用户离开你的网站时消失。虽然 Cookie 在某些情况下很有用，但你不太可能在你的 Web 数据库应用程序中需要它们，原因如下：

![](img/d82df0828cfbc6d6be1e9a991861f3b7_287_0.png)

- **用户可能会设置浏览器以拒绝 Cookie。** 除非你确信所有用户都会打开 Cookie，或者你可以要求他们打开 Cookie（并期望他们遵循你的请求），否则 Cookie 会成为问题。如果你的应用程序依赖于 Cookie，则在关闭 Cookie 时它将无法运行。

- **PHP 有比 Cookie 更好的功能。** 从 PHP 4 开始，PHP 包含创建会话并存储在整个会话中可用的信息的函数。这种会话功能比 Cookie 使信息可用于会话中的所有 Web 页面更可靠且更容易使用。会话不适用于长期存储信息，但 MySQL 数据库可用于此目的。

- **你可以在数据库中存储数据。** 你的应用程序包含一个数据库，你可以在其中存储和检索数据，这通常比 Cookie 更好的解决方案。用户不能意外删除你在数据库中的数据。由于你在该应用程序中使用数据库，因此你可以使用它进行任何所需的数据存储，尤其是长期数据存储。Cookie 对不使用数据库的应用程序更有用。

你通过使用 `setcookie` 函数来存储 Cookie。通用格式是

```
setcookie("variable","value");
```

变量是变量名，但不要包含美元符号（`$`）。此语句仅在用户离开你的网站之前存储信息。例如，以下语句

```
setcookie("state","CA");
```

将 CA 存储在名为 `state` 的 Cookie 变量中。设置 Cookie 后，信息对你的其他 PHP 程序在内置数组的元素中作为 `$_COOKIE[state]` 可用。你不需要做任何事情来从 Cookie 中获取信息。PHP 会自动执行此操作。Cookie 在设置它的程序中不可用。用户必须转到另一个页面或重新显示当前页面，然后才能使用 Cookie 信息。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_288_0.png)

Cookie 也可在名为 `$HTTP_COOKIE_VARS` 的数组中使用，变量名作为键。例如，上一示例中设置的 Cookie 中的值也可以用作 `$HTTP_COOKIE_VARS['state']`。如果使用早于 PHP 4.1 的 PHP 版本，则必须使用此内置数组。

如果你希望存储在 Cookie 中的信息在用户离开你的网站后仍保留在用户计算机上的文件中，请使用过期时间设置 Cookie，如下所示：

```
setcookie("variable","value",expiretime);
```

`expiretime` 值设置 Cookie 到期的时间。expire time 通常使用 `time` 或 `mktime` 函数按如下方式设置：

- ✓ `time`：此函数以计算机可理解的格式返回当前时间。你使用 `time` 函数加上秒数来设置 Cookie 的过期时间，如以下语句所示：

- ✓ `mktime`：此函数以计算机可理解的格式返回日期和时间。你必须按以下顺序提供所需的日期和时间：小时、分钟、秒、月、日和年。如果未包含任何值，则使用当前值。你使用 `mktime` 函数来设置 Cookie 的过期时间，如以下语句所示：

```
setcookie("state","CA",time()+3600); //expires in 1 hour
setcookie("Name",$Name,time()+(3*86400)) // exp in 3 days
```

```
setcookie("state","CA",mktime(3,0,0,4,1,2003));
//expires at 3:00 AM on April 1, 2003.
setcookie("state","CA",mktime(12,0,0,,));
//expires at noon today
```

你可以通过将其值设为空来删除 cookie。以下任一语句都可以删除 cookie：

```
setcookie("name");
setcookie("name","");
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_289_0.png)

然而，`setcookie` 函数有一个主要限制。`setcookie` 函数只能在发送任何其他输出之前使用。你不能在程序中间、在已经向网页输出了一些内容之后再设置 cookie。另请参阅本章其他地方的侧边栏“必须在输出之前出现的语句”。

## 使用 HTML 表单传递信息

从一页向另一页传递信息的最常见方式是使用 HTML 表单。HTML 表单会显示一个提交按钮。当用户点击提交按钮时，表单字段中的信息会被传递给 `form` 标签中包含的程序。通用格式如下

```
<form action="processform.php" method="POST">
    tags for one or more fields
    <input type="submit" value="string">
</form>
```

表单最常见的用途是从用户收集信息（我在第 8 章中详细讨论了这一点）。然而，表单也可以使用隐藏字段来传递其他类型的信息，这些隐藏字段会添加到表单中并与用户输入的信息一起发送。事实上，你可以创建一个仅包含隐藏字段的表单。你始终需要一个提交按钮，并且新页面要等到用户点击提交按钮后才会显示，但你不需要包含任何供用户填写的字段。

例如，以下语句会在用户点击名为 Next Page 的按钮时，将用户的首选背景颜色传递到下一页：

```
<?php
    $color = "blue"; //passed via a user form
    echo "<form action='nextpage.php' method='POST'>
        <input type='hidden' name='color' value='$color'>
        <input type='submit' value='Next Page'>
    </form>\n";
?>
```

网页显示一个标有 Next Page 的提交按钮，但它不会向用户索取任何信息。当用户点击该按钮时，`nextpage.php` 会运行，并且可以使用包含 "blue" 的数组元素 `$_POST[color]`。

## 使用 PHP 会话

会话是指用户在你的网站上花费的时间。用户在进入你的网站和离开它之间可以查看许多网页。通常你希望信息跟随用户在你的网站中浏览，以便在每个页面上都可用。从 4.0 版本开始，PHP 提供了实现此功能的方法。

### PHP 会话的工作原理

PHP 使你能够在一页 Web 页面上设置会话并将变量保存为会话变量。然后你可以在任何其他页面中打开会话，会话变量就可以在内置数组 `$_SESSION` 中供你使用。为此，PHP 执行以下操作：

- 1. **分配一个会话 ID 号：** 该数字是一个非常长、无意义的数字，对用户而言是唯一的，任何人都无法猜到。会话 ID 存储在名为 `PHPSESSID` 的 PHP 系统变量中。

- 2. **将会话变量存储在服务器上的文件中：** 文件以会话 ID 号命名。该文件存储在 Unix/Linux 上的 `\tmp` 中；在 Windows 中，它存储在 PHP 安装目录下的名为 `sessiondata` 的目录中。

- 3. **将会话 ID 号传递给每个页面：** 如果用户启用了 cookie，PHP 会使用 cookie 传递会话 ID。如果用户关闭了 cookie，PHP 会在链接的 URL 中传递会话 ID，或在使用 `post` 方法的表单的隐藏变量中传递会话 ID。

- 4. **为每个新的会话页面从会话文件获取变量：** 每当用户打开会话的一部分的新页面时，PHP 会使用从旧页面传递来的会话 ID 号从文件中获取变量，并将它们放入内置数组 `$_SESSION` 中。你可以使用变量名作为键的数组元素，它们具有你在上一页中分配的值。

如果你是 PHP 管理员，可以通过编辑配置文件 `php.ini` 来更改会话文件存储的位置。找到 `session.save_path` 的设置，并将路径更改为你想要存储文件的位置。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_290_0.png)

![](img/d82df0828cfbc6d6be1e9a991861f3b7_290_1.png)

除非启用了 `track_vars`，否则会话无法工作。自 PHP 4.0.3 起，`track_vars` 始终处于打开状态。对于 4.0.3 之前的版本，在安装 PHP 时应使用 `--enable-track-vars` 选项。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_291_0.png)

如果用户关闭了 cookie，除非打开了 `trans-sid`，否则会话无法工作。你将在后面的“使用 PHP 会话变量”一节中了解如何打开和关闭 `trans-sid`。

### 打开会话

你应该在每个 Web 页面上打开一个会话。使用 `session_start` 函数打开会话，如下所示：

```
session_start();
```

该函数首先检查是否存在会话 ID 号。如果找到一个，它会设置 `$_SESSION` 数组。如果没有找到，它会通过创建新的会话 ID 号来启动新会话。

由于会话在用户启用 cookie 时使用 cookie，因此 `session_start` 受到与 cookie 相同的限制。也就是说，`session_start` 函数必须在发送任何输出之前调用。有关完整详细信息，请参阅本章其他地方的侧边栏“必须在输出之前出现的语句”。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_291_1.png)

你可以告诉 PHP，你网站上的每个页面都应自动以 `session_start` 开始。为此，编辑配置文件 `php.ini`。如果你是 PHP 管理员，可以编辑此文件；否则，请管理员编辑它。查找变量 `session.auto_start` 并将其值设置为 1。在此生效之前，你可能需要重新启动 Web 服务器。启用 `auto_start` 后，你无需在每个页面的开头添加 `session_start`。

### 使用 PHP 会话变量

当你想将变量保存为会话变量时——也就是说，可供用户可能访问的其他 Web 页面使用——请按如下方式将其保存在 `$_SESSION` 数组中：

```
$_SESSION['variablename'] = value;
```

然后该变量值在其他 Web 页面的 `$_SESSION` 数组中可用。例如，你可以使用以下语句存储用户居住的州：

```
$_SESSION['state'] = "CA";
```

然后你可以在任何其他 Web 页面中使用 `$_SESSION['state']`，它将具有值 CA。

以下两个程序展示了如何使用会话将信息从一页传递到下一页。第一个程序，列表 9-2 中的 `sessionTest1.php`，显示了会话开始的第一页。列表 9-3 显示了会话中第二页的程序 `sessionTest2.php`。

### 列表 9-2：启动会话

```
<?php
    session_start();
?>
<html>
<head><title>Testing Sessions page 1</title></head>
<body>
<?php
    $_SESSION['session_var'] = "testing";
    echo "This is a test of the sessions feature.
        <form action='sessionTest2.php' method='POST'>
            <input type='hidden' name='form_var'
                value='testing'>
            <input type='submit' value='go to next page'>
        </form>";
?>
</body></html>
```

请注意，此程序中设置了两个变量以传递到第二页。会话变量 `session_var` 被创建。此外，还显示了一个表单，其中包含隐藏变量 `form_var`，当按下提交按钮时，它也会传递到第二页。两个变量都设置为 "testing"。

### 列表 9-3：会话的第二页

```
<?php
    session_start();
?>
<html>
<head><title>Testing Sessions page 2</title></head>
<body>
<?php
    echo "session_var = {$_SESSION['session_var']}<br>\n";
    echo "form_var = {$_POST['form_var']}<br>\n";
?>
</body></html>
```

将你的浏览器指向 `sessionTest1.php`，然后点击标有 Go to Next Page 的提交按钮。然后你将看到来自 `sessionTest2.php` 的以下输出：

```
session_var = testing
form_var = testing
```

因为会话对于启用Cookie的用户和禁用Cookie的用户有所不同，你应该在这两种条件下测试这两个程序。要在浏览器中关闭Cookie，你可以更改选项或首选项的设置。

要在Internet Explorer中禁用Cookie，请按照以下步骤操作：

- 1. **选择“工具”→“Internet选项”。**

“Internet选项”对话框随即打开。

- 2. **在IE 5.5中单击“安全”选项卡，或在IE 6中单击“隐私”选项卡。**

- 3. **单击“Internet”图标将其高亮显示。**

- 4. **单击“自定义级别”按钮。**

“安全设置”对话框随即出现。

- 5. **向下滚动到“Cookie”区域，并为每个Cookie设置选择“禁用”。**

- 6. **单击“确定”。**

要在Netscape Navigator中禁用Cookie，请按照以下步骤操作：

- 1. **选择“编辑”→“首选项”。**

- 2. **突出显示“高级”。**

- 3. **勾选“禁用Cookie”。**

- 4. **单击“确定”。**

如果在浏览器中关闭Cookie后，sessionTest2的输出显示`$session_var`为空值，这很可能是因为`trans-sid`未启用。你可以在`php.ini`文件中启用`trans-sid`。找到以下行：

```
session.use_trans_sid = 0
```

将0改为1即可启用`trans-sid`。如果你无法解决此问题，你仍然可以使用会话，但必须在编程语句中传递会话ID号，因为当Cookie被关闭时PHP不会自动传递它。有关在未启用`trans-sid`时如何使用会话的详细信息，请参阅下一节。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_293_0.png)

对于PHP 4.1.2或更早版本，除非在编译PHP时使用了`--enable-trans-sid`选项启用它，否则`trans-sid`不可用。

## 不使用Cookie的会话

许多用户会在浏览器中关闭Cookie。PHP会检查用户的浏览器是否允许Cookie，并据此采取相应行为。如果用户的浏览器允许Cookie，PHP将执行以下操作：

- ✓ 设置变量`$PHPSESSID`等于会话ID号

- ✓ 使用Cookie将`$PHPSESSID`从一页传递到下一页

如果用户的浏览器设置为拒绝Cookie，PHP将执行以下操作：

- ✓ 设置一个名为`SID`的常量。该常量包含一个看起来像`PHPSESSID=一长串数字`的变量=值对。

- ✓ 根据`trans-sid`是否启用，可能会或可能不会将会话ID号从一页传递到下一页。如果已启用，PHP会传递会话ID号；如果未启用，PHP不会传递会话ID号。

启用`trans-sid`有利也有弊。优点是，即使关闭了Cookie，会话也能无缝工作。而且启用`trans-sid`后，会话编程要容易得多。缺点是，会话ID号经常在URL中传递。在某些情况下，会话ID号不应显示在浏览器地址栏中。此外，当会话ID号在URL中时，用户可能会将其添加为书签。然后，如果用户使用包含会话ID号的书签返回你的网站，当前访问的新会话ID号可能会与上次访问的旧会话ID号混淆，并可能引发问题。

## 启用trans-sid时的会话

启用`trans-sid`且用户关闭了Cookie时，PHP会自动在URL中或作为隐藏表单字段发送会话ID号。如果用户通过链接、`header`函数或使用`get`方法的表单进入下一页，会话ID号会被添加到URL中。如果用户通过使用`post`方法的表单进入下一页，会话ID会在隐藏字段中传递。PHP将`$PHPSESSID`识别为会话ID号，无需你做任何特殊编程即可处理会话。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_294_0.png)
