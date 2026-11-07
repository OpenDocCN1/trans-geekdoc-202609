
自 PHP 5.4 起（也就是你现实中会遇到的任何版本），简写 echo 无论 PHP 设置如何都能正常工作，因此你可以安全地使用它，而不必担心它在所有服务器上都无法工作。

## 提前思考

在我们刚才查看的示例中，我们创建了一个模板，`jokes.html.php`，其中包含显示页面所需的所有 HTML。然而，随着网站的增长，我们会添加更多页面。我们肯定需要一个页面让人们能够向网站添加笑话，还需要一个带有一些介绍性文字的首页、一个包含网站所有者联系方式的页面，以及随着网站的增长，或许还有一个人们可以 *log in* 到网站的页面。

我在这里有点跳得太快了，但始终值得考虑项目的增长方式。如果我们将刚才对 `jokes.html.php` 使用的方法应用到其他模板——`addjoke.html.php`、`home.html.php`、`contact.html.php`、`login.html.php` 和 so on——我们最终会得到大量重复的代码。

网站上的每个页面都需要一个模板，大致如下：

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>IJDB - Internet Joke Database</title>
  </head>
  <body>
  <?php if (isset($error)): ?>
  <p>
    <?=$error?>
  </p>
  <?php else: ?>
    : do whatever is required for this page: show text,
    : show a form, list records from the database, etc.
  <?php endif; ?>
  </body>
</html>
```

作为程序员，重复代码是最糟糕的事情之一。事实上，程序员经常提到 **DRY** 原则，其含义是“Don’t repeat yourself”。如果你发现自己在重复代码段，几乎肯定有更好的解决方案。

所有优秀的程序员都很懒，而重复代码意味着重复工作。使用这种复制/粘贴方法来处理模板会使网站变得难以维护。让我们想象一下，我们希望在每个页面上都出现页脚和导航部分。我们的模板现在会看起来像这样：

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>IJDB - Internet Joke Database</title>
  </head>
  <body>
  <nav>
    <ul>
      <li><a href="index.php">Home</a></li>
      <li><a href="jokes.php">Jokes List</a></li>
    </ul>
  </nav>

  <main>
  <?php if (isset($error)): ?>
  <p>
    <?=$error?>
  </p>
  <?php else: ?>
    : do whatever is required for this page: show text,
    : show a form, list jokes, etc.
  <?php endif; ?>
  </main>

  <footer>
  &copy; IJDB 2021
  </footer>
  </body>
</html>
```

我们会在 2022 年遇到问题！如果网站上所有页面的模板——例如，`jokes.html.php` `addjoke.html.php`、`home.html.php`、`contact.html.php` 和`login.html.php`——都包含上述结构中的代码，要将版权声明中的年份更新为“2022”，你就需要打开每个模板并更改日期。

我们可以聪明一点，让日期动态地从服务器时钟读取（`echo date('Y');` 如果你好奇的话！）以避免这个问题，但如果我们想在每个页面上都添加一个 `<script>` 标签呢？或者在菜单中添加一个新链接呢？我们仍然需要打开每个模板文件并进行更改！

更改五六个模板可能有点烦人，但不会造成太大问题。然而，如果网站增长到数十或数百个页面呢？每次你想在菜单中添加一个链接时，你就必须打开每个模板并进行更改。

这个问题 *could* 通过一系列 `include` 语句来解决。例如：

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>IJDB - Internet Joke Database</title>
  </head>
  <body>
  <nav>
    <?php include 'nav.html.php'; ?>
  </nav>

  <main>
  <?php if (isset($error)): ?>
  <p>
    <?=$error?>
  </p>
  <?php else: ?>
    : do whatever is required for this page: show text,
    : show a form, list jokes, etc.
  <?php endif; ?>

  </main>

  <footer>
  <?php include 'footer.html.php'; ?>
  </footer>
  </body>
</html>
```

但这种方法需要预知能力：我们需要准确预见到未来可能需要做哪些更改，并在我们预见到会发生变化的地方使用相关的 `include` 语句。

例如，在上面的示例中，通过将它们添加到 `nav.html.php` 很容易添加新的菜单项，但要在每个页面上添加一个 `<script>` 标签，甚至像给 `nav` 元素添加一个 CSS 类这样微不足道的事情，仍然意味着要打开每个模板来进行更改。

无法准确预测网站生命周期内可能需要的所有更改，因此我在本章开头向你展示的方法实际上更好：

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="jokes.css">
    <title><?=$title?></title>
  </head>
  <body>

  <header>
    <h1>Internet Joke Database</h1>
  </header>
  <nav>
    <ul>
      <li><a href="index.php">Home</a></li>
      <li><a href="jokes.php">Jokes List</a></li>
    </ul>
  </nav>

  <main>
  <?=$output?>
  </main>

  <footer>
  &copy; IJDB 2021
  </footer>
  </body>
</html>
```

如果我们始终包含这个模板，我们称之为 `layout.html.php`，就可以将 `$output` 变量设置为一些 *HTML code*，并让它与导航和页脚一起出现在页面上。这样做的好处是，要更改网站每个页面上的日期，我们只需在一个位置进行更改。

我还偷偷加入了一个 `$title` 变量，这样每个控制器都可以定义一个出现在 `<title>` 和 `</title>` 标签之间的值，以及一些 CSS（在示例代码中作为 `jokes.css` 提供）来让页面看起来更漂亮一些。

![IJDB——现在带有 CSS 样式](Images/jokes-css.png)

任何控制器现在都可以使用 `include __DIR__ . '/../templates/layout.html.php';` 并为 `$output` 和 `$title` 提供值。

使用 `layout.html.php` 的我们的 `jokes.php` 代码如下所示。

**示例：[MySQL-列出笑话-布局-1](https://github.com/spbooks/phpmysql7/tree/MySQL-ListJokes-Layout-1)**

```
<?php

try {
    $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

    $sql = 'SELECT `joketext` FROM `joke`';
    $result = $pdo->query($sql);

    while ($row = $result->fetch()) {
        $jokes[] = $row['joketext'];
    }

    $title = 'Joke list';

    $output = '';

    foreach ($jokes as $joke) {
        $output .= '<blockquote>';
        $output .= '<p>';
        $output .= $joke;
        $output .= '</p>';
        $output .= '</blockquote>';
    }
} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

但等等！`try` 块中 `$output` 到底发生了什么？`$output` 变量实际上包含了一些 HTML 代码：循环构建了一个包含笑话列表 HTML 代码的字符串。

原则上，这正是我们想要发生的事情：`$output` 变量包含将要插入到 `layout.html.php` 中导航和页脚之间的 HTML 代码，但我想你会同意这段代码非常丑陋。

我已经向你展示了如何通过 `include` 语句避免混合 HTML 和 PHP 代码。像我们之前做的那样，将显示笑话的 HTML 移到自己的文件中会很好——这次，只是将笑话列表页面独有的 HTML 代码移出。

`templates` 目录中的 `jokes.html.php` 应包含以下代码：

```
<?php foreach ($jokes as $joke): ?>
<blockquote>
  <p>
  <?=htmlspecialchars($joke, ENT_QUOTES, 'UTF-8')?>
  </p>
</blockquote>
<?php endforeach; ?>
```

重要的是，这只是用于显示笑话的代码。它不包含导航、页脚、`<head>` 标签或我们希望在每个页面上重复的任何内容；它只是笑话列表页面独有的 HTML 代码。

要使用此模板，你可以尝试以下操作：

