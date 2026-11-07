
# 使用 PDO 进行动态 INSERT

## 构建查询

这将生成查询的第一部分，并且 `$query` 将存储以下内容：

```
INSERT INTO `joke` (`authorId`, `:jokedate`, `joketext`) VALUES (
```

… when called with this array:

… 当使用以下数组调用时：

```
[
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true'
    'jokedate' = '2021-04-22'
]
```

查询的下一部分应该是值的占位符：

```
VALUES (:authorId, :joketext)
```

这些是以冒号 (`:`) 为前缀的键。再次，我们可以使用 `foreach` 循环遍历列名并在将查询发送到数据库之前添加占位符：

```
function insertJoke($pdo, $values) {
    $query = 'INSERT INTO `joke` (';

    foreach ($values as $key => $value) {
        $query .= '`' . $key . '`,';
    }

    $query = rtrim($query, ',');

    $query .= ') VALUES (';

    foreach ($values as $key => $value) {
        $query .= ':' . $key . ',';
    }

    $query = rtrim($query, ',');

    $query .= ')';

    $stmt = $pdo->prepare($query);

    $stmt->execute($values);

}
```

## 使用 insertJoke

`insertJoke` 函数现在可用于使用一个指定哪个值将被放置到哪个列中的数组来插入笑话：

```
insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true',
    'jokedate' = '2021-04-22'
    ]
);
```

当然，如果使用错误的列名，它将导致错误，但对查看此代码的任何人来说都很清楚哪些数据被放置到每列中。正如我们稍后会看到的，这也使得使用该函数与表单变得更容易。

现在，通过在 `DatabaseFunctions.php` 中替换现有函数，使你的网站使用这两个新函数。然后修改 `editjoke.php` 以使用新的 `updateJoke` 函数：

```
updateJoke($pdo, [
    'id' => $_POST['jokeid'],
    'joketext' => $_POST['joketext'],
    'authorId' => 1
]);
```

最后，修改 `addjoke.php` 以使用新函数。

[结构2-数组函数-错误](https://github.com/spbooks/phpmysql7/tree/Structure2-ArrayFunctions-Error)

```
insertJoke($pdo, [
                    'authorId' => 1, 
                    'joketext' => $_POST['joketext'],
                    'jokedate' => date('Y-m-d')
            ]
 );
```

## 处理日期

你可能想知道在向数据库插入日期时，如何设置特定日期而不是当前日期。

之前，我们使用了 `date()` 函数。使用新的 `insertJoke` 函数，你可能会尝试这样设置笑话：

```
insertJoke($pdo, ['authorId' => 1,
    'jokeText' => $_POST['joketext'],
    'jokedate' =>  date('Y-m-d')
]);
```

`date()` 函数在我们想要使用系统日期时简单易用，但如果我们想要轻松设置特定日期，我们可以使用不同的工具。PHP `DateTime` 类可用于在 PHP 中表示日期并以任何方式格式化它们。例如：

```
$date = new DateTime();

echo $date->format('d/m/Y H:i:s');
```

与更简单的 `date()` 函数类似，默认情况下，`DateTime` 的新实例（不提供参数）将表示今天的日期，并且 `format` 方法中的字符串与你已熟悉的 `date()` 函数中使用的格式相同。如果你于 2021 年 9 月 8 日大约晚上 7 点阅读本文，它会打印类似以下内容：

```
08/09/2021 19:12:34
```

`DateTime` 类相对于 `date()` 函数的最大优势在于，你可以给它一个代表任意日期的字符串，并让它将其转换为不同的日期格式。例如：

```
$date = new DateTime('5th March 2021');

echo $date->format('d/m/Y');
```

这里的字符串 `d/m/Y` 代表日/月/年，这将打印 `05/03/2021`。PHP `DateTime` 类非常强大，并且在处理 PHP 中的日期时非常有用。有关格式化日期的可用方法的完整列表可在 [在 PHP 手册中](http://php.net/manual/en/function.date.php) 找到。

`DateTime` 类可用于表示任何日期和时间。今天的日期可以以此格式表示，如下所示：

```
// Don't give it a date so it uses the current date/time
$date = new DateTime();

echo $date->format('Y-m-d H:i:s');
```

上面将打印类似以下内容：

```
2021-09-08 19:16:34
```

这是你在 MySQL 中向 `DATETIME` 字段插入数据时需要的格式。

`insertJoke` 函数已经可以处理此问题。我们只需将当前日期作为数组键之一传递给函数即可：

```
$date = new DateTime();

insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => 'Why did the chicken cross the road? To get to the other side',
    'jokedate' => $date->format('Y-m-d H:i:s')
    ]
);
```

这将正常工作。然而，这与仅使用 `date()` 函数并没有什么不同，并且每次我们想要使用该函数时，都需要记住 MySQL 使用的日期格式。这可能有点麻烦，因为每次需要插入日期时都需要重复格式化日期的代码（并记住字符串 `Y-m-d H:i:s`）。

相反，更好的方法是将函数格式化日期供我们使用，每次调用时节省一些工作：

```
function insertJoke($pdo, $values) {
    $query = 'INSERT INTO `joke` (';

    foreach ($values as $key => $value) {
        $query .= '`' . $key . '`,';
    }

    $query = rtrim($query, ',');

    $query .= ') VALUES (';

    foreach ($values as $key => $value) {
        $query .= ':' . $key . ',';
    }

    $query = rtrim($query, ',');

    $query .= ')';

    foreach ($values as $key => $value) {
        if ($value instanceof DateTime) {
            $values[$key] = $value->format('Y-m-d');
        }
    }

        $stmt = $pdo->prepare($query);

        $stmt->execute($values);
}
```

使用上述版本的函数，可以在不格式化的情况下将日期 `object` 传递给函数：

```
insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true',
    'jokedate' =>  new DateTime()
    ]
);
```

函数将查找它收到的任何日期对象并自动将其格式化为 MySQL 所需的格式。调用函数时，你无需记住 MySQL 所需的确切格式；它在函数内部为你完成。函数将自动将遇到的任何 `DateTime` 对象转换为 MySQL 可理解的字符串：

```
// Loop through the array of fields
foreach ($values as $key => $value) {
    // If any of the values are a DateTime object
    if ($value instanceof DateTime) {
        // Then replace the value in the array with the date in the format
        // Y-m-d H:i:s
        $values[$key] = $value->format('Y-m-d H:i:s');
    }
}
```

你尚未遇到过的一个运算符是 `instanceof` 运算符。这是一个像 `==` 或 `!=` 这样的比较运算符。然而，它不是检查两个值是否 *相同*，而是检查左侧的变量（`$value`）是否与右侧的对象（`DateTime`）是同一类型。一个重要的区别是 *值* 并未被检查，只有 *类型*。这就像说“它是一辆车吗？”而不是“它是一辆 E-Type 捷豹吗？”

无论在数组中何处找到 `DateTime` 对象，它都会被替换为 MySQL 所需格式的等效日期字符串。这使我们完全可以忘记 MySQL 实际需要的格式，只需向 `insertJoke` 函数提供 `DateTime` 对象即可。

有了这段代码，如果我们想要指定要设置在数据库中的日期，可以这样做：

```
insertJoke($pdo, [
        'authorId' => 4,
        'joketext' => '!false - it\'s funny because it\'s true',
        'jokedate' =>  new DateTime('5th September 2021')
        ]
);
```

`insertJoke` 函数将看到 `DateTime` 实例并自动将其转换为 MySQL 使用的格式。

让我们也将自动日期格式化添加到 `updateJoke` 函数中：
