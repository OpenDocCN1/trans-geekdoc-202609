
# 使用可选数据的编辑笑话表单

```
else {
    if (isset($_GET['id'])) {
        $joke = find($pdo, 'joke', 'id', $_GET['id']);
    }
    else {
      $joke = null;
    }

    $title = 'Edit joke';

    ob_start();

    include  __DIR__ . '/../templates/editjoke.html.php';

    $output = ob_get_clean();
}
```

如果你尝试上面的代码并访问 `editjoke.php` 而不作为 `GET` 变量提供 ID，它不会完全按预期工作。你实际上会在 `<textarea>` 内看到一些奇怪的错误出现。这是因为，当 `editjoke.html.php` 被加载时，它引用了一个名为 `$joke` 的变量，而由于新的 `if` 语句，该变量只有在提供 ID 时才会被创建。

一个解决方案是如果未设置 ID 则加载 `addjoke.html.php` 文件，如果设置了则加载 `editjoke.html.php`。不幸的是，这并不能解决初始问题：使用这种方法向表单添加新字段时，我们仍然需要编辑两个文件。

相反，让我们修改 `editjoke.html.php`，使其仅在笑话变量被设置时才尝试将现有数据打印到 textarea 和隐藏输入中：

```
<form action="" method="post">
    <input type="hidden" name="jokeid" value="<?php if (isset($joke)): ?>
                        <?=$joke['id']?>
                <?php endif; ?>">
        <label for="joketext">Type your joke here:</label>
        <textarea id="joketext" name="joketext" rows="3" cols="40"><?php if (isset($joke)): ?>
                <?=$joke['joketext']?>
        <?php endif; ?></textarea>
        <input type="submit" name="submit" value="Save">
</form>
```

现在 `joketext` 和 `id` 只有在 `$joke` 变量被设置时才会被写入页面，而它仅在我们编辑现有记录时才会被设置。

在继续之前，让我们稍微整理一下代码。之前，要将笑话的 ID 打印到隐藏输入中，需要更简单的代码：

```
<input type="hidden" name="jokeid" value="<?=$joke[id]?>">
```

现在我们使用 `if` 语句，需要完整的 `<?php` 开头和几行代码。

## 使用空合并运算符

PHP 7 中引入的一个不错的功能是 `??` 运算符，它充当简写的 `if-isset`，可用于以下代码的简写：

```
if (isset($something)) {
    echo $something;
}
else {
    echo 'variable not set';
}
```

这可以使用 `??` 运算符像这样表达：

```
echo $something ?? 'variable not set';
```

`??` 运算符左侧是要检查的变量，右侧是如果未设置时使用的输出。在上面的例子中，如果 `$something` 变量已设置，它将打印变量的内容。如果变量未设置，它将打印 `variable not set`，更棒的是，它也适用于数组。

在授课时，我总是尝试让学生猜测这个运算符的名字。就像我的学生一样，在猜到它的名字之前，你会花很长时间。它被称为 `Null coalescing operator`，这听起来比实际复杂得多。

让我们在模板中使用它，而不是为每个字段写出完整的 `if` 语句：

```
<form action="" method="post">
    <input type="hidden" name="jokeid" value="<?=$joke['id'] ?? ''?>">
        <label for="joketext">Type your joke here:</label>
        <textarea id="joketext" name="joketext" rows="3" cols="40"><?=$joke['joketext'] ?? ''?></textarea>
        <input type="submit" name="submit" value="Save">
</form>
```

在这种情况下，右侧部分是一个空字符串。加载的笑话的文本将显示在文本框中，或者如果 `$joke` 变量未设置，它将在框中显示一个空字符串 `''`。

我们需要再次使用 `??` 运算符来解决另一个问题。在上面的代码中，如果 `$_GET['id']` 设置为数据库中不存在的 ID 会怎样？以下代码将运行并尝试从具有指定 ID 的笑话列表中读取第一个笑话。如果列表中没有笑话，它将打印错误！为了避免这种情况，我们可以再次使用 `?? null`，以便如果没有指定 ID 的笑话，则 `$joke` 被设置为 `null`：

```
else {
    if (isset($_GET['id'])) {
        $joke = find($pdo, 'joke', 'id', $_GET['id'])[0] ?? null;
    }
    else {
      $joke = null;
    }
}
```

## 保存记录

要完成此页面，我们需要更改表单提交时发生的情况。需要运行 `update` 或 `insert` 查询。

最简单的方法是查看是否提供了 `ID` 字段：

```
if (isset($_POST['id']) && $_POST['id'] != '') {
    update(...);
}
else ;
    insert(...)
}
```

虽然这会起作用，但再次有机会使其更通用。*如果设置了 ID，则更新，否则插入* 的这种逻辑对于任何表单都是一样的。

如果我们有一个表单用于 *authors*，同样的逻辑也很有用：*如果没有 ID，则执行插入；如果有，则执行更新*。事实上，这适用于任何用于添加或编辑的表单。上面的代码需要为我们以这种方式实现的任何表单重复。

这种方法的另一个问题是，如果主键是表单上的普通字段，例如书籍的 ISBN，则它将无法工作。无论需要 `UPDATE` 还是 `INSERT` 查询，ISBN 都会被提供。

相反，我们可以尝试插入一条记录，如果不成功，则使用 `try … catch` 语句改为更新：

```
try {
    insert(…);

}
catch(PDOException $e) {
    update(…);
}
```

现在将向数据库发送一个 `INSERT`，但它 *可能* 会导致错误——“Duplicate key”——当已存在提供 ID 的记录时。如果确实发生错误，则会改为发出 `UPDATE` 查询以更新现有记录。

为了避免为每个表单重复此逻辑，我们可以再创建一个名为 `save` 的函数，该函数使用上面的 `try … catch` 执行插入或更新：

```
function save($pdo, $table, $primaryKey, $record) {
    try {
        if (empty($record[$primaryKey])) {
          unset($record[$primaryKey]);
        }
        insert($pdo, $table, $record);
    }
    catch (PDOException $e) {
        update($pdo, $table, $primaryKey, $record);
    }
}
```

这适用于任何表中的任何记录。如果尝试插入时出现错误，它将改为发出相应的更新查询。

这里的 `save` 函数需要 `insert` 和 `update` 函数调用它们所需的所有参数。无需重复这些函数的任何逻辑；它们可以只从相对简短的 `save` 函数内部调用。

请注意，如果主键为空，我已取消设置记录的主键。这是因为 `save` 函数可能会从表单中获取完整的记录。主键（通常是 `id`）可能具有空字符串 (`''`) 的值。由于我们不想尝试将空字符串插入 `id` 列，因此在插入记录之前需要将其删除。

### 性能开销

这种方法依赖于向数据库发送两个查询。当发生更新时，这会产生少量性能开销。然而，其他方法——例如使用 `SELECT` 查询来确定记录是否已存在——100% 的时间都会增加性能开销。

另外，MySQL/MariaDB 支持 `REPLACE INTO` 和 `INSERT INTO .. ON DUPLICATE KEY UPDATE`，它们执行相同的任务（根据是否存在指定 ID 的记录进行更新或插入）。它们本身可能很慢，并且是 MySQL 特定的；如果使用不同的数据库引擎代替 MySQL，则它们将无法工作。上面的代码无论使用哪个数据库都有效。

现在 `editjoke.php` 可以修改为使用新的 `save` 函数：
