
现在我们有了数组及其中所有必需的数据；现在可以编写一个递归调用的函数，以正确的缩进显示评论：

```php
function displayComment(array $comments, int $n) {
    if (isset($comments[$n])) {
        $str = "<ul>";
        foreach ($comments[$n] as $comment) {
            $str .= "<li><div class='comment'><span class='pic'>{$comment->username}</span>";
            $str .= "<span class='datetime'>{$comment->datetime}</span>";
            $str .= "<span class='commenttext'>{$comment->comment}</span></div>";
            $str .= displayComment($comments, $comment->id);
            $str .= "</li>";
        }
        $str .= "</ul>";
        return $str;
    }
    return "";
}

echo displayComment($comments, 0);
```

由于我们在 PHP 代码中添加了一些 HTML 元素，因此需要一些基础 CSS 使其生效。以下是我们编写的 CSS 代码，旨在实现简洁的设计。没有花哨的效果，纯 CSS 用于创建层叠效果以及评论各部分的基础样式：

```css
ul {
    list-style: none;
    clear: both;
}

li ul {
    margin: 0 0 0 50px;
}

.pic {
    display: block;
    width: 50px;
    height: 50px;
    float: left;
    color: #000;
    background: #ADDFEE;
    padding: 15px 10px;
    text-align: center;
    margin-right: 20px;
}

.comment {
    float: left;
    clear: both;
    margin: 20px;
    width: 500px;
}

.datetime {
    clear: right;
    width: 400px;
    margin-bottom: 10px;
    float: left;
}
```

如前所述，我们这里不追求复杂，只求响应式、设备友好等。我们假设你可以毫无问题地将该逻辑集成到应用程序的不同部分中。

以下是数据和前述代码生成的输出：

![](Image00040.jpg)

从前述两个示例可以看出，创建嵌套内容非常容易，无需多次查询，也无连接语句嵌套层数的限制。甚至不需要自连接即可生成嵌套数据。

# 使用递归查找文件和目录

我们经常需要查找目录内的所有文件。这包括其内部的所有子目录，以及这些子目录内的目录。因此，我们需要一个递归解决方案来获取给定目录下的文件列表。以下示例将展示一个简单的递归函数，用于列出目录中的所有文件：

```php
function showFiles(string $dirName, array &$allFiles = []) {
    $files = scandir($dirName);

    foreach ($files as $key => $value) {
        $path = realpath($dirName . DIRECTORY_SEPARATOR . $value);
        if (!is_dir($path)) {
            $allFiles[] = $path;
        } elseif ($value != "." && $value != "..") {
            showFiles($path, $allFiles);
            $allFiles[] = $path;
        }
    }
    return;
}

$files = [];
showFiles(".", $files);
```

`showFiles` 函数接收一个目录，首先扫描该目录以列出其下的所有文件和目录。然后通过 `foreach` 循环遍历每个文件和目录。如果是目录，则再次调用 `showFiles()` 函数列出其下的文件和目录。此过程持续直到遍历完所有文件和目录。现在，所有文件都在 `$files` 数组中。现在，让我们用 `foreach` 循环顺序显示这些文件：

```php
foreach ($files as $file) {
    echo $file . "\n";
}
```

这将在命令行产生如下输出：

```
/home/mizan/packtbook/chapter_1_1.php
/home/mizan/packtbook/chapter_1_2.php
/home/mizan/packtbook/chapter_2_1.php
/home/mizan/packtbook/chapter_2_2.php
/home/mizan/packtbook/chapter_3_.php
/home/mizan/packtbook/chapter_3_1.php
/home/mizan/packtbook/chapter_3_2.php
/home/mizan/packtbook/chapter_3_4.php
/home/mizan/packtbook/chapter_4_1.php
/home/mizan/packtbook/chapter_4_10.php
/home/mizan/packtbook/chapter_4_11.php
/home/mizan/packtbook/chapter_4_2.php
/home/mizan/packtbook/chapter_4_3.php
/home/mizan/packtbook/chapter_4_4.php
/home/mizan/packtbook/chapter_4_5.php
/home/mizan/packtbook/chapter_4_6.php
/home/mizan/packtbook/chapter_4_7.php
/home/mizan/packtbook/chapter_4_8.php
/home/mizan/packtbook/chapter_4_9.php
/home/mizan/packtbook/chapter_5_1.php
/home/mizan/packtbook/chapter_5_2.php
/home/mizan/packtbook/chapter_5_3.php
/home/mizan/packtbook/chapter_5_4.php
/home/mizan/packtbook/chapter_5_5.php
/home/mizan/packtbook/chapter_5_6.php
/home/mizan/packtbook/chapter_5_7.php
/home/mizan/packtbook/chapter_5_8.php
/home/mizan/packtbook/chapter_5_9.php
```

这些是我们在开发中面临的一些常见挑战的解决方案。然而，还有其他地方会大量使用递归，例如二分查找、树、分治算法等。我们将在后续章节中讨论它们。

# 分析递归算法

递归算法的分析取决于我们使用的递归类型。如果是线性递归，复杂度会不同；如果是二叉递归，复杂度又会不同。因此，递归算法没有通用的复杂度。我们必须逐个案例分析。这里我们将分析阶乘序列。首先，让我们关注阶乘部分。如果回顾本节内容，我们对于阶乘递归有如下代码：

```php
function factorial(int $n): int {
    if ($n == 0)
        return 1;
    return $n * factorial($n - 1);
}
```

假设计算阶乘（`$n`）需要 `T(n)`。我们将重点关注如何用大 O 表示法表示此 `T(n)`。每次调用 `factorial` 函数都涉及特定步骤：

1. 每次都检查基本情况。
2. 每次循环调用 `factorial($n-1)`。
3. 每次循环与 `$n` 相乘。
4. 返回结果。

现在，如果用 `T(n)` 表示，则可表述为：

* `T(n) = a` 当 `n = 0` 时
* `T(n) = T(n-1) + b` 当 `n > 0` 时

此处 `a` 和 `b` 均为常数。现在，让我们建立 `a`、`b` 与 `n` 的关系。可以轻松写出如下方程：

* `T(0) = a`
* `T(1) = T(0) + b = a + b`
* `T(2) = T(1) + b = a + b + b = a + 2b`
* `T(3) = T(2) + b = a + 2b + b = a + 3b`
* `T(4) = T(3) + b = a + 3b + b = a + 4b`

可以看到此处出现了一个模式。因此可以确定：

* `T(n) = a + n * b`

或者简单地说 `T(n) = O(n)`。

因此，阶乘递归具有 `O(n)` 的线性复杂度。

递归实现的斐波那契数列复杂度约为 `O(2^n)`。计算过程非常详尽，因为我们必须同时考虑大 O 表示法的下界和上界。在后续章节中，我们还将分析二分查找和归并排序等二叉递归。我们将在这些章节中更多地关注递归分析。

# PHP 中的最大递归深度

既然递归是函数调用自身的过程，我们脑海中可能会出现一个合理的问题：“我们能递归多深？”。让我们做一个小程序测试一下：

```php
function maxDepth() {
    static $i = 0;
    print ++$i . "\n";
    maxDepth();
}

maxDepth();
```

我们能猜到最大深度吗？在耗尽内存限制前，深度达到了 917,056 层。如果启用了 `XDebug`，则限制将比这低得多。这也取决于你的内存、操作系统以及 PHP 设置，如 `memory_limit` 和 `max_execution_time`。
