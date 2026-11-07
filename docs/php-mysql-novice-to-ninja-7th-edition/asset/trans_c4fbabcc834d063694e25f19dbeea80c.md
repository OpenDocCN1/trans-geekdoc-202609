
# 用于笑话管理的 PHP 通用函数

```
<?php
include __DIR__ . '/../includes/DatabaseConnection.php';
include __DIR__ . '/../includes/DatabaseFunctions.php';

try {
        if (isset($_POST['joketext'])) {
                update($pdo, 'joke', 'id', [
                        'id' => $_POST['jokeid'],
                        'joketext' => $_POST['joketext'],
                        'authorId' => 1
                     ]
                );

                header('location: jokes.php');
        } else {
                $joke = find($pdo, 'joke', 'id', $_GET['id'])[0];

                $title = 'Edit joke';

                ob_start();

                include  __DIR__ . '/../templates/editjoke.html.php';

                $output = ob_get_clean();
        }
}
// …
```

以下是更新后的 `deletejoke.php`：

```
<?php
try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../includes/DatabaseFunctions.php';

    delete($pdo, 'joke', 'id', $_POST['id']);

    // …
```

下一部分是笑话列表。目前，它使用 `allJokes()` 函数，该函数还会检索每个笑话的作者信息。没有简单的方法可以编写一个从两个表中检索信息的通用函数。它必须知道用于连接表的字段以及正在连接的表。可以用一个参数很多的函数来实现，但该函数会难以使用且过于复杂。

相反，我们可以结合使用通用的 `findAll` 和 `find` 函数来实现这一点：

```
$result = findAll($pdo, 'joke');

$jokes = [];
foreach ($result as $joke) {

    $author = find($pdo, 'author', 'id', $joke['authorId'])[0];

    $jokes[] = [
        'id' => $joke['id'],
        'joketext' => $joke['joketext'],
        'name' => $author['name'],
        'email' => $author['email']
    ];
}
```

完整的 `jokes.php` 如下所示。

**示例：[结构2-通用函数](https://github.com/spbooks/phpmysql7/tree/Structure2-GenericFunctions)**

```
<?php

try {
        include __DIR__ . '/../includes/DatabaseConnection.php';
        include __DIR__ . '/../includes/DatabaseFunctions.php';

        $result = findAll($pdo, 'joke');

        $jokes = [];
        foreach ($result as $joke) {
                $author = find($pdo, 'author', 'id', $joke['authorId'])[0];

                $jokes[] = [
                        'id' => $joke['id'],
                        'joketext' => $joke['joketext'],
                        'jokedate' => $joke['jokedate'],
                        'name' => $author['name'],
                        'email' => $author['email']
                ];
        }

        $title = 'Joke list';

        $totalJokes = total($pdo, 'joke');

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

这通过获取笑话列表（不含作者信息），然后遍历每个笑话并通过其 `id` 找到对应的作者，然后将来自两个表的信息完整的笑话写入 `$jokes` 数组来实现。这本质上就是 MySQL 中 `INNER JOIN` 的作用。

每个笑话现在都由 `$author` 变量的值组成，该变量是来自 `author` 表的记录，以及来自 `joke` 表的值。

你可能已经意识到这种方法会更慢，因为会向数据库发送更多查询。这类通用函数的常见问题，被称为 **N+1 问题**。有几种方法可以减少这种性能问题，但对于小型站点而言，我们处理的是数百或数千条记录而不是数百万条记录，因此不太可能造成任何实际问题。差异可能在毫秒级别。

### N+1 问题

有关 N+1 问题的更多信息，请参阅 Microsoft 文章“[选择 N+1 问题 – 如何降低您的 ORM 性能](https://dzone.com/articles/select-n1-problem-%E2%80%93-how)”，其中详细解释了它。

要了解如何完全避免 N+1 问题，请参阅“[N+1 问题的（银色）子弹](https://www.sitepoint.com/silver-bullet-n1-problem/)”。

## 重复代码是敌人

无论何时编写软件，都需要警惕重复代码。只要发现自己有两份或更多份相同或非常相似的代码，总是值得退一步看看是否有办法将其合并为一个可重用的块。

通过创建通用的函数 `insert`、`update`、`delete`、`findAll` 和 `find`，我们现在可以非常快速和轻松地创建一个处理任何数据库操作的网站。可以使用这些函数非常简单地与我们可能需要的任何数据库表进行交互。

但仍有改进空间。文件 `addjoke.php` 和 `editjoke.php` 执行非常相似的工作：它们显示一个表单，并在表单提交时将提交的数据发送到数据库。

同样，模板文件 `addjoke.html.php` 和 `editjoke.html.php` 几乎相同。两者之间几乎没有区别。唯一的真正区别是编辑页面显示预填的表单，而添加页面则显示空表单。

重复代码的问题在于，如果需要更改，就必须在多个位置进行相同的更改。如果我们想为笑话添加一个类别，以便用户在添加或编辑笑话时可以选择 *敲门笑话*、*编程笑话*、*双关语*、*一句话笑话* 等，该怎么办？

我们可以通过在添加笑话页面添加一个 `<select>` 框来实现，但也需要在编辑笑话页面做同样的更改。每次对 `addjoke.php` 进行更改时，都需要在 `editjoke.php` 中做相应的更改。

如果你发现自己处于这种情况，必须在多个文件中进行类似的更改，这是一个很好的迹象，表明你应该将两组代码合并为一个。当然，新代码需要处理两种情况。

`addjoke.php` 和 `editjoke.php` 之间有几个区别：

*   `addjoke.php` 发出 `INSERT` 查询，而 `editjoke.php` 发出 `UPDATE` 查询。
*   `editjoke.php` 的模板文件有一个隐藏输入，用于存储正在编辑的笑话的 ID。
*   当编辑笑话表单显示时，正在编辑的笑话的信息会在显示之前加载到表单中。

但其他一切几乎都相同。

让我们将两段代码合并在一起，以便 `editjoke.php` 可以同时处理编辑现有笑话和添加新笑话。脚本将能够根据 URI 中是否提供 ID 来判断我们是添加还是编辑。

访问 `editjoke.php?id=12` 将从数据库加载 ID 为 12 的笑话并允许我们编辑它。当表单提交时，它将发出相关的 `UPDATE` 查询，而仅访问 `editjoke.php`——未指定 ID——将显示空表单，并在提交时执行 `INSERT` 查询。

### 创建添加和编辑页面

首先处理表单——它要么将笑话加载到字段中，要么显示空白表单。目前，`editjoke.php` 假定已设置 `id` URL 变量，并在加载模板文件之前相应地加载笑话：

```
else {
    $joke = find($pdo, 'joke', 'id', $_GET['id'])[0];

    $title = 'Edit joke';

    ob_start();

    include  __DIR__ . '/../templates/editjoke.html.php';

    $output = ob_get_clean();
}
```

这可以用一个 `if` 语句替换，仅在实际提供了 `id` 时才从数据库加载笑话：
