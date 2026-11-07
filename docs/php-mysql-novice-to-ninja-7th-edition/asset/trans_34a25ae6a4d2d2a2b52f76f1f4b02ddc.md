
*   你需要一个新的控制器（`deletejoke.php`）。
*   将需要 SQL `DELETE` 命令，我在第 3 章中介绍过它。
*   要在你的控制器中删除特定的笑话，你需要唯一地识别它。`joke` 表中的 `id` 列就是为此目的而创建的。你必须将要删除的笑话的 ID 与删除笑话的请求一起传递。最简单的方法是使用隐藏的表单字段。

至少，花点时间思考一下你将如何处理这个问题。当你准备好查看解决方案时，请继续阅读！

首先，我们需要修改从数据库获取笑话列表的 `SELECT` 查询。除了 `joketext` 列之外，我们还必须获取 `id` 列，以便我们可以唯一地识别每个笑话：

```
try {
  $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

  $sql = 'SELECT `id`, `joketext` FROM `joke`';
  $result = $pdo->query($sql);
  // …
```

我们还必须修改将数据库结果存储到 `$jokes` 数组中的 `while` 循环。不是简单地将每个笑话的文本作为数组中的一项存储，我们存储每个笑话的 ID 和文本。一种方法是使 `$jokes` 数组中的每个项目本身就是一个数组：

```
while ($row = $result->fetch()) {
  $jokes[] = ['id' => $row['id'], 'joketext' => $row['joketext']];
}
```

### 改用 `foreach` 循环

如果你已经改用 `foreach` 循环来处理数据库结果行，那也完全可以：

```
foreach ($result as $row) {
  $jokes[] = array('id' => $row['id'], 'joketext' =>
    $row['joketext']);
}
```

一旦此循环运行完毕，我们将拥有 `$jokes` 数组，其中的每个项目都是一个关联数组，包含两个项目：笑话的 ID 和其文本。对于每个笑话（`$jokes[n]`），因此我们可以检索其 ID（`$jokes[n]['id']`）和其文本（`$jokes[n]['text']`）。

下一步是更新 `jokes.html.php` 模板以从此新数组结构中检索每个笑话的文本，并为每个笑话提供一个 **删除** 按钮：

```
<?php foreach ($jokes as $joke): ?>
<blockquote>
  <p>
  <?=htmlspecialchars($joke['joketext'], ENT_QUOTES, 'UTF-8')?>
  <form action="deletejoke.php" method="post">
    <input type="hidden" name="id" value="<?=$joke['id']?>">
    <input type="submit" value="Delete">
  </form>
  </p>
</blockquote>
<?php endforeach; ?>
```

以下是此更新代码的亮点：

*   每个笑话都将显示一个表单，如果提交，将删除该笑话。我们使用表单的 `action` 属性将其信号发送给新的控制器 `deletejoke.php`。
*   由于 `$jokes` 数组中的每个笑话现在都由一个包含两项的数组而不是简单的字符串表示，我们必须更新此行以检索笑话的文本。我们使用 `$joke['text']` 而不是仅使用 `$joke` 来实现这一点。
*   当我们提交表单以删除此笑话时，我们会发送要删除的笑话的 ID。为此，我们需要一个包含笑话 ID 的表单字段，但我们更希望将此字段对用户隐藏；这就是为什么我们使用隐藏表单字段（`input type="hidden"`）。此字段的名称为 `id`，其值为要删除的笑话的 ID（`$joke['id']`）。

与笑话的文本不同，ID 不是用户提交的值，因此无需担心使用 `htmlspecialchars` 使其对 HTML 安全。我们可以放心它将是一个数字，因为它是由 MySQL 在笑话添加到数据库时为 `id` 列自动生成的。
*   提交按钮（`input type="submit"`）在点击时提交表单。其 value 属性为其提供 **删除** 标签。
*   最后，我们关闭此笑话的表单。

### 为什么表单和输入标签不在 blockquote 外部？

如果你了解 HTML，你可能正在思考表单和输入标签应该位于 blockquote 元素之外，因为它们不是引用文本（笑话）的一部分。

严格来说，这是正确的：表单及其输入实际上应该在 blockquote 之前或之后。不幸的是，使该标签结构清晰地显示需要一些 CSS（层叠样式表）代码，这超出了本书的范围。

与其在 PHP 和 MySQL 书中教您 CSS 布局技术，我决定使用这种不完美的标记。如果您计划在现实世界中使用此代码，您应该花一些时间学习 CSS（或至少聘请 CSS 专家）。这样，您就可以完全控制 HTML 标记，而不必担心使其看起来美观所需的 CSS。如果您想了解有关 CSS 布局的更多信息，请查看 Tiffany Brown 所著的 *[CSS 精通，第三版](https://www.sitepoint.com/premium/books/css-master-3rd-edition)*。

将以下 CSS 添加到 `jokes.css` 中以使按钮出现在笑话右侧并在它们之间画一条线：

```
blockquote {display: table; margin-bottom: 1em; border-bottom: 1px solid #ccc; padding: 0.5em;}
blockquote p {display: table-cell; width: 90%; vertical-align: top;}
blockquote form {display: table-cell; width: 10%;}
```

下图显示了添加 **删除** 按钮后的笑话列表。

![每个按钮都可以删除其各自的笑话](Images/deletebutton.png)

但等等！在我们继续使 **删除** 按钮工作之前，让我们先退一步仔细看看这一行：

```
$jokes[] = ['id' => $row['id'], 'joketext' => $row['joketext']];
```

这里，我们正在循环遍历 `PDOStatement` 对象，它为我们提供了一个包含键 `id` 和 `joketext` 以及相应值的 `$row` 变量，我们使用它来构建另一个具有相同键和值的数组。

您可能已经意识到这是极其低效的。我们可以使用以下代码实现相同的效果：

```
while ($row = $result->fetch()) {
  $jokes[] = $row;
}
```

但正如我们所知，这也可以使用 `foreach` 循环实现：

```
foreach ($result as $row) {
 $jokes[] = $row;
}
```

在这种情况下，我们使用 `foreach` 来遍历数据库中的记录并构建一个数组。然后我们在模板中用另一个 `foreach` 循环遍历该数组。我们可以直接写：

```
$jokes = $result;
```

现在，当在模板中遍历 `$jokes` 时，它不是一个数组而是一个 `PDOStatement` 对象。然而，这对输出没有影响并节省了一些代码。事实上，我们可以完全省略 `$result` 变量，并直接将 `PDOStatement` 对象加载到 `$jokes` 变量中。完整的 `jokes.php` 控制器现在如下所示：

```
try {
  $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

  $sql = 'SELECT `joketext`, `id` FROM joke';

  $jokes = $pdo->query($sql);

  $title = 'Joke list';

  ob_start();

  include  __DIR__ . '/../templates/jokes.html.php';

  $output = ob_get_clean();
}
catch (PDOException $e) {
  $title = 'An error has occurred';

  $output = 'Database error: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

现在我们在控制器中甚至没有一个遍历记录的 `while` 循环，而是在模板中直接遍历记录，节省了一些代码并使页面执行速度略快，因为它现在只遍历记录一次。

回到我们新的 **删除** 按钮：要使此新功能工作所剩下的就是添加一个相关的 `deletejoke.php` 来向数据库发出 `DELETE` 查询：

