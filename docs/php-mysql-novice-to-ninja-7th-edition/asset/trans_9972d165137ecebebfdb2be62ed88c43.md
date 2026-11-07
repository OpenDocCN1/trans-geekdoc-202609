
# 结果集获取与模板渲染

`fetch` 返回的结果集的行表示为关联数组，其索引以结果集中表列的名称命名。如果 `$row` 是我们结果集中的一行，则 `$row['joketext']` 是该行 `joketext` 列中的值。

我们在此代码中的目标是保存所有笑话的文本，以便在 PHP 模板中显示它们。最好的做法是将每个笑话存储为数组 `$jokes` 中的一个新项：

```
while ($row = $result->fetch()) {
  $jokes[] = $row['joketext'];
}
```

从数据库中取出笑话后，我们现在可以将它们传递给 PHP 模板 `jokes.html.php`。

## 控制器代码

总结一下，到目前为止本示例控制器的代码如下：

```
<?php

try {
    $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

    $sql = 'SELECT `joketext` FROM `joke`';
    $result = $pdo->query($sql);

    while ($row = $result->fetch()) {
        $jokes[] = $row['joketext'];
    }
} catch (PDOException $e) {
    $error = 'Unable to connect to the database server: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/jokes.html.php';
```

`$jokes` 变量是一个存储笑话列表的数组。如果你在 PHP 中写出该数组的内容，它看起来会像这样：

```
$jokes = [];
$jokes[0] = 'A programmer was found dead in the shower. The instructions read: lather, rinse, repeat.';
$jokes[1] = '!false - it\'s funny because it\'s true';
$jokes[2] = 'A programmer\'s wife tells him to go to the store and "get a gallon of milk, and if they have eggs, get a dozen." He returns with 13 gallons of milk.';
```

然而，数据是从数据库中检索出来的，而不是在代码中手动输入的。

你会注意到，根据 `try` 块是否成功执行，会设置两个不同的变量——`$jokes` 和 `$error`。

## 模板渲染

在 `jokes.html.php` 模板中，我们需要显示 `$jokes` 数组的内容或 `$error` 变量中包含的错误消息。

为了检查变量是否已被赋予值，我们可以使用 `isset` 函数，该函数之前用于检查表单是否已提交。模板可以包含一个 `if` 语句来确定是显示错误还是笑话列表：

```
if (isset($error)) {
  ?>
  <p>
  <?php
  echo $error;
  ?>
  </p>
}
else {
  : display the jokes
}
```

这里没有新内容，但要显示笑话，我们需要显示 `$jokes` 数组的内容。与到目前为止我们使用过的其他变量不同，`$jokes` 数组包含的不仅仅是一个值。

在 PHP 中处理数组最常见的方法是使用循环。我们已经见过 `while` 循环和 `for` 循环。`foreach` 循环对于处理数组特别有帮助：

```
foreach (array as $item) {
  ⋮ process each $item
}
```

与条件不同，`foreach` 循环顶部的括号中包含一个数组，后跟关键字 `as`，然后是新变量的名称，该变量将依次用于存储数组中的每个项。然后循环体对数组中的每个项执行一次。每次该项都存储在指定的变量中，以便代码可以直接访问它。

在 PHP 模板中使用 `foreach` 循环依次显示数组中的每个项是很常见的。以下是它在我们 `$jokes` 数组中的可能外观：

```
<?php
foreach ($jokes as $joke) {
    ?>
  ⋮ HTML code to output each $joke
<?php
}
?>
```

由于 PHP 代码描述循环与 HTML 代码显示内容的混合，代码看起来相当杂乱。因此，在模板中使用时，通常会使用另一种编写 `foreach` 循环的方式：

```
foreach (array as $item):
  ⋮ process each $item
endforeach;
```

这两段代码在功能上是相同的，但后者在与 HTML 代码混合时看起来更友好。以下是这种形式的代码在模板中的外观：

```
<?php foreach ($jokes as $joke): ?>
  ⋮ HTML code to output each $joke
<?php endforeach; ?>
```

对 `if` 语句也可以做同样的处理，通过避免使用大括号，使其在 HTML 模板中看起来更美观：

```
<?php if (isset($error)): ?>
  <p>
  <?php echo $error; ?>
  </p>
<?php else: ?>
  : display the jokes
<?php endif; ?>
```

掌握了这些新工具后，我们就可以编写模板来显示笑话列表。

### 示例：MySQL-ListJokes

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>List of jokes</title>
  </head>
  <body>
  <?php if (isset($error)): ?>
  <p>
    <?php echo $error; ?>
  </p>
  <?php else: ?>
  <?php foreach ($jokes as $joke): ?>
  <blockquote>
    <p>
    <?php echo htmlspecialchars($joke, ENT_QUOTES, 'UTF-8') ?>
    </p>
  </blockquote>
  <?php endforeach; ?>
  <?php endif; ?>
  </body>
</html>
```

要么在页面上显示 `$error` 文本，要么每个笑话都显示在块引用 (`<blockquote>`) 内的段落 (`<p>`) 中，因为我们实际上是在本页中引用每个笑话的作者。

因为笑话可能包含会被解释为 HTML 代码的字符（例如 `<`、`>` 或 `&`），我们必须使用 `htmlspecialchars` 来确保它们被转换为 HTML 字符实体（即 `&lt;`、`&gt;` 和 `&amp;`），以便正确显示。

下图显示了在向数据库添加几个笑话后此页面的外观。

![数据库中的笑话列表](Images/jokelist.png)

### 使用 foreach 处理 PDOStatement

还记得我们在控制器中如何使用 `while` 循环一次从 `PDOStatement` 结果集中获取一行吗？

```
while ($row = $result->fetch()) {
  $jokes[] = $row['joketext'];
}
```

事实证明，`PDOStatement` 对象在传递给 `foreach` 循环时被设计为表现得就像数组一样。因此，你可以使用 `foreach` 循环代替 `while` 循环来稍微简化数据库处理代码：

```
foreach ($result as $row) {
  $jokes[] = $row['joketext'];
}
```

我将在本书的其余部分使用这种更整洁的 `foreach` 形式。

### 简写 Echo 语法

PHP 提供的另一个不错的工具是调用 `echo` 命令的简写形式——正如你已经看到的，我们需要频繁使用它。我们的 `echo` 语句看起来像这样：

```
<?php echo $variable; ?>
```

相反，我们可以使用这个：

```
<?=$variable?>
```

这完全一样。`<?=` 表示 `echo`，为你提供了一种稍短的打印变量的方式。不过这也有局限性：如果使用 `<?=`, 你只能打印。不能包含 `if` 语句、`for` 语句等，尽管可以使用连接，并且可以在其后跟随函数调用。

以下是使用简写 echo 的更新模板。

### 示例：MySQL-ListJokes-Shorthand

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>List of jokes</title>
  </head>
  <body>
  <?php if (isset($error)): ?>
  <p>
    <?=$error?>
  </p>
  <?php else: ?>
  <?php foreach ($jokes as $joke): ?>
  <blockquote>
    <p>
    <?=htmlspecialchars($joke, ENT_QUOTES, 'UTF-8')?>
    </p>
  </blockquote>
  <?php endforeach; ?>
  <?php endif; ?>
  </body>
</html>
```

从现在开始，我将在适用时使用简写表示法。

### 使用简写

在 PHP 5.4 之前的版本中，这种简写表示法需要启用一个相当不常见的 PHP 设置，因此出于兼容性原因而被不鼓励使用。使用简写表示法可能会导致你的代码在从启用了该设置的服务器迁移到未启用的服务器时停止工作。
