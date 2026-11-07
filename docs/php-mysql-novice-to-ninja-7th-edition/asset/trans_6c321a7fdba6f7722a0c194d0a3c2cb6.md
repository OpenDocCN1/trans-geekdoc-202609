
```
function totalJokes($pdo) {
  $stmt = $pdo->prepare('SELECT COUNT(*) FROM `joke`');
  $stmt->execute();

  $row = $stmt->fetch();

  return $row[0];
}
```

然后，当调用该函数时，你传入在 `DatabaseConnection.php` 中创建的 `$pdo` 对象：

```
include_once __DIR__ . '/../includes/DatabaseConnection.php';
echo totalJokes($pdo);
```

这通过将其作为参数传入，使得 `$pdo` 变量在 `totalJokes` 函数中可用。值得花一点时间来准确理解这里发生了什么。`$pdo` 变量是在 `DatabaseConnection.php` 中创建的，这使得它在上面的代码块中可用。然后它被传入 `totalJokes` 函数。存储在全局 `$pdo` 变量中的对象随后被复制到函数内部名为 `$pdo` 的局部变量中。数据库连接需要作为参数传入，因为函数只能访问它们被赋予的数据；它们无法访问除所给变量之外的变量（或者，如前所述，确实有办法做到这一点，但它们几乎总是坏主意）。

通过将 `$pdo` 作为参数传入，如果函数中出现错误并且 `$pdo` 变量在函数内部被字符串覆盖，它只会在函数内部成为字符串，而不会影响脚本其余部分。

这意味着实际上存在两个不同的名为 `$pdo` 的变量。我们可以将函数内部的 `$pdo` 变量重命名为 `$database`，脚本仍然可以正常工作：

```
function totalJokes($database) {
  $stmt = $database->prepare('SELECT COUNT(*) FROM `joke`');
  $stmt->execute();

  $row = $stmt->fetch();

  return $row[0];
}
```

在这里，`$database` 变量存储的与全局作用域中 `$pdo` 变量存储的 `PDO` 连接相同。即使函数仍然使用 `totalJokes($pdo)` 调用，函数外部 `$pdo` 变量的内容与函数内部 `$database` 变量包含相同的数据库连接。尽管名称不同，两者都引用同一个连接。

如果你想深入技术细节，这个过程称为 **依赖注入**，但你需要知道的是，从实际角度来看，它是一种使单个变量在多个位置可用的方法。

## 将函数移至单独文件

将函数移至单独的文件是个好主意。将 `totalJokes` 函数放在 `includes` 目录下的名为 `DatabaseFunctions.php` 的文件中，然后你就可以按如下方式使用该函数。

**示例：[结构-总笑话数](https://github.com/spbooks/phpmysql7/tree/Structure-TotalJokes)**

```
// Include the file that creates the $pdo variable and connects to the database
include_once __DIR__ . '/../includes/DatabaseConnection.php';

// Include the file that provides the `totalJokes` function
include_once __DIR__ . '/../includes/DatabaseFunctions.php';

// Call the function
echo totalJokes($pdo);
```

将其保存为 `public` 目录下的 `showtotaljokes.php`，并在浏览器中导航到它。你应该会看到一个页面，页面大部分为空，但会显示数据库中笑话的总数。

你可能已经意识到，如果程序像这样被拆分为函数，你就需要将 `$pdo` 变量传入每个想要使用的函数。正如你可能怀疑的那样，这并不是实现此目标最高效的方式，我们稍后在学习对象和类时会看到这一点。

## 在网站中使用该函数

让我们在网站内部使用我们的新函数。在笑话列表顶部我们可以打印“[number] 条笑话已提交到互联网笑话数据库”。

打开 `jokes.php` 并将其更改为以下内容：

```
<?php

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../includes/DatabaseFunctions.php';

    $sql = 'SELECT `joke`.`id`, `joketext`, `name`, `email`
    FROM `joke` INNER JOIN `author`
      ON `authorid` = `author`.`id`';

    $jokes = $pdo->query($sql);

    $title = 'Joke list';

    $totalJokes = totalJokes($pdo);

    ob_start();

    include  __DIR__ . '/../templates/jokes.html.php';

    $output = ob_get_clean();
} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

这创建了一个可在 `jokes.html.php` 中使用的 `$totalJokes` 变量。

**示例：[结构-总笑话列表](https://github.com/spbooks/phpmysql7/tree/Structure-TotalJokesList)**

```
<p><?=$totalJokes?> jokes have been submitted to the Internet Joke Database.</p>

<?php foreach ($jokes as $joke): ?>
<blockquote>
  <p>
  <?=htmlspecialchars($joke['joketext'], ENT_QUOTES, 'UTF-8')?>

  (by <a href="mailto:<?php
    echo htmlspecialchars(
    $joke['email'],
    ENT_QUOTES,
      'UTF-8'
); ?>"><?php
    echo htmlspecialchars(
          $joke['name'],
          ENT_QUOTES,
      'UTF-8'
      ); ?></a>)

  <form action="deletejoke.php" method="post">
    <input type="hidden" name="id" value="<?=$joke['id']?>">
    <input type="submit" value="Delete">
  </form>
  </p>
</blockquote>
<?php endforeach; ?>
```

你可能会想知道如果 `totalJokes` 函数内部的查询包含错误会发生什么。我们可以在函数内部放置一个 `try … catch` 语句，但由于该函数已在现有的 `try … catch` 语句内部被调用，因此我们不需要这样做。

异常会 *冒泡*。从实际角度来看，这意味着即使在函数内部抛出异常，它仍然会被周围的 `try … catch` 语句捕获。

最好避免在函数内部处理错误。想象一下我们在函数内部有一个 `try … catch` 语句，如下所示：

```
function totalJokes($database) {
  try {
    $stmt = $database->prepare('SELECT COUNT(*) FROM `joke`');
    $stmt->execute();

    $row = $stmt->fetch();

    return $row[0];
  }
  catch {
    $title = 'An error has occurred';

      $output = 'Database error: ' . $e->getMessage() . ' in ' .
      $e->getFile() . ':' . $e->getLine();

    include  __DIR__ . '/../templates/layout.html.php';
    die();
  }
}
```

不仅我们有重复的代码，而且现在，无论 `totalJokes` 函数从何处被调用，错误都将以相同的方式处理。通过将其排除在函数之外，可以在 `totalJokes` 函数使用的不同位置使用不同的错误处理。例如，我们可能希望使用网站生成笑话列表作为 PDF 或 Excel 文件，而不是 HTML 文档。如果是这种情况，我们当然不希望错误信息以 HTML 形式显示。

通过让错误自然发生，我们可以在不同情况下以不同方式处理错误。

## 将代码拆分为可重用函数

现在你已经熟悉声明自己的函数，可以开始编写函数来执行每个任务。例如，与每次想要从数据库读取特定笑话时都写出 `SELECT` 查询相比，你可以编写一个可重用的函数来为你完成此操作：

```
function getJoke($pdo, $id) {
  $stmt = $pdo->prepare('SELECT * FROM `joke` WHERE `id` = :id');

  $values = [
      'id' => $id
  ];
  $stmt->execute($values);

  return $stmt->fetch();
}
```

这与之前的 `totalJokes` 函数的工作方式相同。唯一的区别是有一个第二个参数 `$id`，它将存储要查找的笑话的 ID。

这使我们能够通过 ID 快速查找笑话：

```
include __DIR__ . '/../includes/DatabaseConnection.php';

//Equivalent of SELECT * FROM `joke` WHERE id = 1
$joke1 = getJoke($pdo, 1);

echo $joke1['joketext'];

//Equivalent of SELECT * FROM `joke` WHERE id = 2
$joke2 = getJoke($pdo, 2);

echo $joke2['joketext'];
```
