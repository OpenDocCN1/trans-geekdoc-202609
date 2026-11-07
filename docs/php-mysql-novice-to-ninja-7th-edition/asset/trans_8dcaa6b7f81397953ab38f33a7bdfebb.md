
```
<form action="name.php" method="post">
  <label for="firstname">First name:</label>
  <input type="text" name="firstname" id="firstname">

  <label for="lastname">Last name:</label>
  <input type="text" name="lastname" id="lastname">

  <input type="submit" value="GO">
</form>
```

这个 method 属性的新值指示浏览器将表单变量作为页面请求的一部分不可见地发送，而不是将它们嵌入到 URL 的查询字符串中。

由于我们不再将变量作为查询字符串的一部分发送，它们将不再出现在 PHP 的 `$_GET` 数组中。相反，它们被放置在专门为“已发布”表单变量保留的另一个数组中：`$_POST`。因此我们必须修改 `name.php` 以从这个新数组中检索值。

**示例: [PHP-POST-Form](https://github.com/spbooks/phpmysql7/tree/PHP-POST-Form)**

```
<?php
$firstname = $_POST['firstname'];
$lastname = $_POST['lastname'];
echo 'Welcome to our website, ' .
  htmlspecialchars($firstname, ENT_QUOTES, 'UTF-8') . ' ' .
  htmlspecialchars($lastname, ENT_QUOTES, 'UTF-8') . '!';
?>
```

下图显示了提交此新表单后结果页面的外观。

![表单提交后页面的结果](Images/post-result.png)

该表单在功能上与之前的表单相同。唯一的区别是，当用户点击 **GO** 按钮时加载的页面的 URL 将不带查询字符串。一方面，这让你可以在表单提交的数据中包含大值（或敏感值，如密码和信用卡号码），而不会让它们出现在查询字符串中。另一方面，如果用户将表单提交后生成的页面加入书签，该书签将毫无用处，因为它缺少提交的值。顺便说一下，这正是搜索引擎使用查询字符串提交搜索词的主要原因。如果你将 Google 上的搜索结果页面加入书签，你可以稍后使用该书签再次执行相同的搜索，因为搜索词包含在 URL 中。

## GET 或 POST？

作为经验法则，只有在表单提交时服务器上的内容 *不会* 发生变化时才应使用 `GET` 表单——例如在请求搜索结果列表时。因为搜索词在 URL 中，用户可以对搜索结果页面进行书签保存，并在无需再次输入搜索词的情况下返回该页面。但如果在提交表单后文件被删除、数据库被更新或记录被插入，则应使用 `POST`。这样做的主要原因是，如果用户将页面加入书签（或在浏览器中按返回按钮），它不会再次触发表单提交，从而可能创建重复记录。

`POST` 也更安全。通过 `GET` 发送的任何内容都会出现在 URL 中，并存储在用户的历史记录和书签中——这些对于密码和信用卡详细信息等敏感数据来说是非常不安全的位置。

这涵盖了使用表单与 PHP 产生基本用户交互的基础知识。我们将在后面的示例中查看更高级的问题和技术。

## 隐藏缝隙

你现在已经掌握了 PHP 编程语言基本语法的实用知识。你明白可以取任意 HTML 网页，将其重命名为 `.php` 文件扩展名，并向其中注入 PHP 代码以即时生成页面内容。不错的一天工作量！

不过，在继续之前，我想停下来对迄今为止讨论的示例进行批判性审视。假设你的目标是创建符合专业标准的数据库驱动网站，我们需要清理一些难看的瑕疵。

本章剩余部分中的技术将帮助你将编程技能提升到初学者水平之上，使其具有一定的专业水准。我将在本书其余部分中依赖这些技术，以确保无论示例多么简单，你都能对交付产品的质量充满信心。

### PHP 模板

在迄今为止看到的简单示例中，直接将 PHP 代码插入 HTML 页面是一种合理的方法。然而，随着生成平均页面所涉及的 PHP 代码量增加，维护这种 HTML 和 PHP 代码的混合体可能会变得难以管理。

特别是如果你在一个不特别精通 PHP 的网页设计师团队中工作，在 HTML 中混杂大量晦涩的 PHP 代码是灾难的根源。设计师很容易意外修改 PHP 代码，从而导致他们无法修复的错误。

一种更稳健的方法是将大部分 PHP 代码分离出来，使其驻留在自己的文件中，从而使 HTML 基本不受 PHP 代码污染。

实现这一点的关键是 PHP `include` 语句。有了 `include` 语句，你可以在语句所在的位置将另一个文件的内容插入到你的 PHP 代码中。为了向你展示其工作原理，让我们重建之前看到的“数到十” `for` 循环示例。

首先在你的 `public` 目录中创建一个新文件 `count.php`。打开文件进行编辑并输入以下代码：

```
<?php
$output = '';
for ($count = 1; $count <= 10; $count++) {
    $output .= $count . ' ';
}

include 'count.html.php';
```

是的，这就是该文件的 *完整* 代码。它完全不包含 HTML 代码。`for` 循环现在应该对你来说很熟悉了，但让我指出这段代码中有趣的部分：

*   而不是使用 `echo` 输出 1 到 10 的数字，此脚本会将这些数字添加到名为 `$output` 的变量中。因此，在此脚本开始时，我们将该变量设为空字符串。
*   行 `$output .= $count . ' '` 将每个数字（后跟一个空格）添加到 `$output` 变量的末尾。你在这里看到的 `.=` 运算符是将赋值和字符串连接运算符组合成一个的简写方式，用于向现有字符串变量末尾添加值。该行的长写法是 `$output = $output . $count . ' '`，但 `.=` 运算符可以节省你的输入。
*   `include` 语句指示 PHP 在此位置执行 `count.html.php` 文件的内容。你可以将 `include` 语句视为一种 *复制粘贴*。你可以通过打开 `count.html.php`，复制其内容并将其粘贴到 `count.php` 中，覆盖 `include` 行来获得相同的结果。
*   最后，你可能注意到该文件没有以 `?>` 结束以匹配开头的 `<?php`。如果你真的想加也可以，但不是必要的。如果 PHP 文件以 PHP 代码结束，就无需指示代码结束的位置；文件的末尾会为你完成。PHP 领域的聪明人通常更喜欢在仅包含 PHP 代码的此类文件末尾省略它。

#### Include 中的括号

在本书之外，你有时会看到 `include` 代码中文件名周围带有括号，就好像 `include` 是像 `date` 或 `htmlspecialchars` 这样的函数一样，事实远非如此。例如，除了 `include 'count.html.php';` 之外，你可能会看到 `include('count.html.php');`。这些括号在使用时只会使文件名表达式复杂化，因此在本书中避免使用。`echo` 也是如此，它是另一个流行的单行代码。

由于我们的 `count.php` 文件的最后一行包含了 `count.html.php` 文件，你应该接下来创建该文件。

**示例: [PHP-Count-Template](https://github.com/spbooks/phpmysql7/tree/PHP-Count-Template)**

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Counting to Ten</title>
  </head>
  <body>
    <p>
      <?php echo $output; ?>
    </p>
  </body>
</html>
```

该文件几乎完全是纯 HTML，除了输出 `$output` 变量值的那一行之外。这就是由 `count.php` 文件创建的同一个 `$output` 变量。
