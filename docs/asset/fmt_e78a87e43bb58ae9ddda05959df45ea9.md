
然而，你今天使用的大多数 Web 应用程序都需要在浏览器请求之间存储数据。例如，购物车需要记住你向其中添加了哪些，而论坛应用程序需要在你在论坛中发布消息时记住你的身份。

换句话说，需要将用户与应用程序交互的当前状态从一次操作保留到下一次操作。

你已经在上一个章节看过了存储数据的简单示例，当时你使用隐藏表单字段（`hidden form fields`）在三阶段注册表单的每个步骤存储之前输入的数据。虽然填写注册涉及三个独立的浏览器请求——因此是 PHP 脚本的三次运行——但脚本能够通过将状态存储在字段中来“记住”注册过程的状态。

尽管这种方法在简单情况下运行良好，但它也有一些缺点。例如，存储大量数据非常慢，因为所有数据在每次请求期间都必须在浏览器和服务器之间来回。此外，它非常不利，因为对于坏心的用户来说，更改表单中存储的数据几乎是轻而易举的。此外，如果在请求之间存储大量变量，以及数组和对象等复杂变量，隐藏表单字段方法可能会变得非常繁琐。

# 第三部分：PHP 练习

在本章中，你将查看保存状态的其他方法。你将学习如何使用：

- 查询字符串（`Query strings`）在 URL 中存储少量数据
- Cookies 在浏览器本身中存储更多数据
- Sessions 存储更多量的数据，并以更安全的方式存储

通过使用这三种方法中的任何一种（或它们的组合），你可以创建持久的 Web 应用程序，将数据从一个页面携带到下一个页面。

## 使用查询字符串保存状态

查询字符串是在浏览器请求之间传递少量数据的一种快速、方便的方法。查询字符串的常见用途包括：在使用搜索功能时记住用户输入的关键词、识别在向用户显示论坛中的哪个主题，以及指定在博客中显示哪篇帖子。

查询字符串对用户来说非常简单，因为在浏览器的地址栏中是可见且可编辑的。因此，查询字符串应仅用于发送错误数据不会危及安全的情况（除非你的脚本额外验证了用户确实是他们所称的人）。

> 你还需要确保不要依赖查询字符串来验证用户身份，因为人们会在电子邮件或即时消息应用程序中将 URL 发给朋友。如果你的 URL 包含了验证用户所需的所有数据，而该用户与朋友一起该 URL，那么朋友就可以冒充他们！你会发现 sessions——在本章稍后会讨论——是验证身份好得的方法。

如果你已经学习了第 9 章，你对查询字符串的概念已经比较熟悉。你会记得可以通过将表单的 `method` 属性设置为 `get` 在 URL 中发送表单数据。当表单数据发送到服务器时，它将如下所示附加到 URL 的末尾：

```
http://localhost/myscript.php?firstName=Fred&lastName=Bishop&
```

换句话说，浏览器在 URL 末尾添加一个查询 (`?`) 字符，然后以 "`name=value`" 的形式跟随每个表单字段，每对之间用连符号 (`&`) 隔开。查询字符串就是 URL 中 (`?`) 字符之后的字符串。

### 构建查询字符串

查询字符串的伟大之处在于它们不仅限于表单数据。由于查询字符串仅仅是存储在 URL 中的字符字符串，你可以在 PHP 脚本中手动创建查询字符串，然后将 URL 作为链接包含在显示的页面或电子邮件中，例如。PHP 甚至有内置函数来让这个过程变得更容易。

这里是一个简单的示例，它创建了两个变量 `$firstName` 和 `$age`，然后在显示的页面中创建一个包含查询字符串的链接，以存储变量值：

### 第 10 章：使用查询字符串保留状态

```php
<?php
$firstName = "John";
$age = 25;
$queryString = "firstName=" . $firstName . "&age=" . $age;
echo '<a href="moreinfo.php?' . $queryString . '">Click here for info</a>';
?>
```

此代码生成了以下标记：

```html
<a href="moreinfo.php?firstName=John&age=25">Click here for info</a>
```

如果用户点击此链接，将运行 `moreinfo.php`：

```php
<?php
$firstName = $_GET['firstName'];
$age = $_GET['age'];
echo "First name: " . htmlspecialchars($firstName) . ", Age: " . htmlspecialchars($age);
?>
```

输出为：

First name: John, Age: 25

### 数字平方

显示数字 10 到 19 的平方数

| n | n^2 |
|---|---|
| 10 | 100 |
| 11 | 121 |
| 12 | 144 |
| 13 | 169 |
| 14 | 196 |
| 15 | 225 |
| 16 | 256 |
| 17 | 289 |
| 18 | 324 |
| 19 | 361 |

<上一页 | 下一页 >>

完成

### 工作原理

脚本从标准的 `XHTML_PAGE` 头部开始，为页面中的表格添加一些 CSS 样式。下一个脚本定义了一个常量 `PAGE_SIZE`，它存储了每页要显示的平方数数量（在本例中）。

脚本脚本创建了一个变量 `$start`，用于存储页面内显示的第一个整数。它的默认值为零。然而，如果在查询字符串中向脚本传递了 `start` 字段——且该字段的值在接受范围内，则会使用此值。注意，脚本出于安全考虑，将 `$_GET["start"]` 的值强制转换为整数；过滤和/或验证任何用户输入以确保其格式正确总是良好的习惯：

### 第 10 章：使用查询字符串保持状态

```php
$start = 0;

if ( isset($_GET["start"] ) && $_GET["start"] >= 0 && $_GET["start"] <= 1000000) {
  $start = (int) $_GET["start"];
}
```

接下来，脚本计算出当前页显示的最后一个整数，并将其存储在另一个变量中：

```php
$end = $start + PAGE_SIZE - 1;
```

现在只需显示十个整数的标题及其平方数即可。使用 PHP 的 `pow()` 函数来计算每个整数的平方：

```php
<h2>数字平方</h2>

<p>正在显示从 <?php echo $start ?> 到 <?php echo $end ?> 的数字的平方数：</p>
<table cellspacing="0" border="0" style="width:20em; border:1px solid #666;">
<tr>
<th>n</th>
<th>n²</th>
</tr>

<?php
for ($i=$start; $i <= $end; $i++) {
<tr<?php if ($i % 2 != 0 ) echo ' class="alt"' ?>><td><?php echo $i; ?></td>
<td><?php echo pow($i, 2); ?></td>
</tr>
}
?>
</table>
```

最后，显示“下一页”和（在合适的情况下）“上一页”链接。注意脚本是如何内部构建查询字符串的：

```php
if ($start > 0 ) {
<a href="number_squaring.php?start=<?php echo $start - PAGE_SIZE ?>">&lt; 上一页</a> |
<?php }

<a href="number_squaring.php?start=<?php echo $start + PAGE_SIZE ?>">下一页&gt;</a>
```

# 第三部分：在实战中使用 PHP

因为你知道 `start` 只会包含数字，在这种情况下不需要对值进行编码。然而，如果你的值可能包含保留字符，你应该像本章稍些讨论的那样使用 `urlencode()` 或 `http_build_query()`。

## 使用 Cookie

现在你已经学习了查询字符串，在上一章中也学习了隐藏表单字段作为在请求之间保持应用程序状态的方法。虽然这些技术对于少量临时数据完全足够，但当你需要长期存储大量数据时，这些技术就会变得笨拙。例如，你可能允许每个用户为网站的文本选择字体大小。这实现起来将困难。

Cookie 是解决此问题的一种较为复杂的方法。Cookie 允许你在浏览器本身存储少量数据——不超过 4KB。然后，每当浏览器请求你网站上的页面时，Cookie 都会在请求中自动发送到服务器。

尽管 Cookie 比查询字符串稍微安全一些——例如，浏览器（默认情况下）只向创建它的 网站发送 Cookie——但它们仍然很容易被攻击者篡改。你不应该依赖 Cookie 来识别或验证你的用户。此外，在浏览器中关闭 Cookie 支持非常容易，许多人都会这样做。这意味着你的网站不应该依赖 Cookie 实现核心功能——或者，如果依赖，它应该在必要时提示你为该网站启用 Cookie。

然而，如果你需要持续存储非关键数据（如偏好设置），Cookie 是一个非常有用的工具。

> 这是一个提示：大多数浏览器都允许你查看以及删除浏览器存储的任何 Cookie。例如，在 Firefox 中选择“编辑”->“偏好设置”（Mac 上），然后选择“隐私”并点击“Cookies”按钮。

### Cookie 组件

Cookie 作为 HTTP 头部的一部分从服务器发送到浏览器。这里有一个用于创建 Cookie 的 HTTP 头部示例：

```
Set-Cookie: fontSize=3; expires=Tuesday, 6-Jan-2009 17:53:08 GMT; path=/; domain=.example.com; HttpOnly
```

如你所见，Cookie 包含若干信息，汇总如下表：

| Cookie 字段 | 描述 |
| --- | --- |
| name（例如） |  |

尽管你可以使用 `domain` 字段让浏览器向同一域内的其他机器发送 Cookie，但你无法利用此技巧设置发送其他域的 Cookie。例如，如果你的 `www.example.com` 尝试设置一个值为 `www.google.com` 的 Cookie，该 Cookie 将被浏览器拒绝。

# 第三部分：在实战中使用 PHP

### 在 PHP 中设置 Cookie

如何通过 PHP 脚本在浏览器设置 Cookie？虽然你可以直接用 `Set-Cookie`: HTTP 头部设置 Cookie（使用 PHP 的 `header()` 函数），但有更简单的方法。PHP 提供了一个内置函数 `setcookie()`，它可以发送相应的 HTTP 头部在浏览器中创建 Cookie。它按照上表所示顺序接收每个 Cookie 字段的参数。只有 `name` 参数是必须的，为了避免任何歧义，至少提供 name、value、expires 和 path 是良好的习惯。

`expires` 参数应该是 Unix 时间戳格式。Unix 时间戳表示从 1970 年 1 月 1 日午夜（UTC 时区）到要表示的时间的秒数。不用担心——你不需要自己计算。PHP 提供了许多时间函数来计算此值，正如此处所示。

有关 PHP 时间和日期函数的更多信息，请参见第 16 章。

确保在向浏览器发送任何输出之前调用 `setcookie()`。这是因为 `setcookie()` 需要发送 `Set-Cookie`: HTTP 头部。如果你在调用 `setcookie()` 之前输出任何内容，PHP 会自动发送头部，导致 Cookie 太晚，无法发送 Set-Cookie 头部。

这是一个示例，我们如何使用 `setcookie()` 使用用户的字体偏好（在本例中）创建一个 Cookie：

```php
setcookie("fontSize", time() + 60 * 24 * 365, "/.example.com", false, true);
```

### 第 10 章：使用查询字符串保留状态

### 在脚本中访问 Cookie

在 PHP 中访问 Cookie 非常简单：你只需要从 `$_COOKIE` 全局数组中读取值即可。如你想象的那样，这个关联数组包含了浏览器在当前请求中设置的所有 Cookie 值列表，并以 Cookie 名称作为键。

因此，要显示上一个示例中设置的 `pageViews` Cookie，你可以使用：

```php
echo $_COOKIE["pageViews"]; // 显示 "8"
```

在使用 `$_GET` 和 `$_POST` 时，在实际情况下，你不应该在不对 `$_COOKIE` 数组进行过滤或验证的情况下直接输出其中的数据。攻击者很容易向发送到服务器的 Cookie 中注入恶意数据。

重要的一点是：新创建的 Cookie 在下一次浏览器请求之前，你的脚本无法通过 `$_COOKIE` 访问它。这是脚本第一次运行时，它仅仅是将 Cookie 发送给浏览器。浏览器在下一次向服务器请求该 URL 之前不会返回该 Cookie。例如：

```php
setcookie("pageViews", 7, 0, "", false, true );
echo isset($_COOKIE["pageViews"]);
```

这段代码没有显示任何内容（第一次运行时为 false，`$_COOKIE["pageViews"]` 不存在）。然而，如果用户再次刷新页面脚本，脚本将显示 1 (true)，因为浏览器已将 `pageViews` Cookie 发回了服务器，因此它在 `$_COOKIE` 数组中可用。

同样，如果你更新了 Cookie，在脚本执行期间，`$_COOKIE` 数组仍然包含旧值。只有当用户通过刷新页面再次运行脚本时，`$_COOKIE` 数组才会更新为新值。

### 删除 Cookie

如果你不再需要存储在用户浏览器上的 Cookie，可以指示浏览器删除它。要删除 Cookie，你需要调用 `setcookie()` 并传入 Cookie 名称和任何值（空字符串），同时传递一个处于过去的 `expires`（过期时间）参数。这会立即让浏览器上的 Cookie 过期。你应该传递与初次创建 Cookie 时完全相同的路径、域和其他其它字段，以确保删除的是正确的 Cookie：

```php
setcookie("pageViews", "", time() - 3600, "/", "example.com", false, true);
```

此示例将 Cookie 的过期时间设置为过去一小时前，从而有效地从浏览器中删除了它。与创建和更新 Cookie 不同，通过 `setcookie()` 删除 Cookie 不会在脚本运行期间从 `$_COOKIE` 数组中删除它。然而，当浏览器下次访问该页面时，它将不再向服务器发送该 Cookie，相应的 `$_COOKIE` 数组元素也不会被创建。

# 第三部分：使用练习

在这个示例中，你创建了一个脚本，它可以在 Cookie 中存储访问者的名字和位置，从 Cookie 中检索信息，并在请求时删除 Cookie。将以下脚本保存为根目录下的 `remember_me.php`，然后在浏览器中运行该脚本。你会看到一个询问姓名和位置的表单。输入信息并点击 Info。你会看到一个类似于图 10-2 的页面。尝试在浏览器中刷新页面，或在新浏览器中重新打开 URL。注意，即使你向服务器发送了新的请求，脚本仍然记得你的信息。你甚至可以重启浏览器并返回该页面，脚本仍然记得你的详情。点击“About me”链接来删除 Cookie。

```php
<?php
if (isset($_POST["sendInfo"])) {
  storeInfo();
} else if (isset($_GET["action"]) && $_GET["action"] == "forget") {
  forgetInfo();
} else {
  displayPage();
}

function storeInfo() {
  if (isset($_POST["firstName"])) {
    setcookie("firstName", $_POST["firstName"], time() + 60 * 24 * 365, "", false, true);
  }

  if (isset($_POST["location"])) {
    setcookie("location", $_POST["location"], time() + 60 * 24 * 365, "", false, true);
  }

  header("Location: remember_me.php");
}

function forgetInfo() {
  setcookie("firstName", "", time() - 3600, "", false, true);
  setcookie("location", "", time() - 3600, "", false, true);
  header("Location: remember_me.php");
}

function displayPage() {
  $firstName = (isset($_COOKIE["firstName"])) ? $_COOKIE["firstName"] : "";
  $location = (isset($_COOKIE["location"])) ? $_COOKIE["location"] : "";
}
?>
```
