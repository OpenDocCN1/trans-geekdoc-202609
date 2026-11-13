

| 表 1 |
|---|
| 第 1 行 |
| 第 2 行 |

| 表 2 |
|---|
| 第 1 行 |
| 第 2 行 |

A standard join

| Table 1 | Table 2 |
|---|---|
| Row 1 | Row 1 |
| Row 1 | Row 2 |
| Row 2 | Row 1 |
| Row 2 | Row 2 |

MySQL 通过列出两个表中所有可能的行组合来执行标准连接。在简单情况下，两个各包含两行的表的标准连接将包含四行：表 1 的第 1 行与表 2 的第 1 行，表 1 的第 1 行与表 2 的第 2 行，表 1 的第 2 行与表 2 的第 1 行，以及表 1 的第 2 行与表 2 的第 2 行。计算出所有这些结果行后，MySQL 然后参考 WHERE 子句来指导哪些行实际应被保留（例如表 1 的 AID 列与表 2 的 ID 列匹配的那些行）。

上述做法之所以不适合我们的目的，是因为我们希望还包括表 1（即 Authors）中不匹配表 2（即 Jokes）中任何行的那些行。左连接正好满足我们的需求——它会强制为第一个（左侧）表中的每一行在结果中显示一行，即使在第二个（右侧）表中找不到匹配条目。此类 **强制行** 在右侧表的所有列中都被赋予 NULL 值。

在 MySQL 中执行两个表之间的左连接，请在 FROM 子句中用 LEFT JOIN 而不是逗号分隔两个表名。然后在第二个表名后跟上 ON 条件，其中条件指定匹配两个表中行的标准（即您通常会放在 WHERE 子句中的内容）。下面是我们修订后的查询，用于列出作者及其名下的笑话数量：

```
mysql> SELECT Authors.NAME, COUNT(*) AS NumJokes
-> FROM Authors LEFT JOIN Jokes ON AID = Authors.ID
-> GROUP BY AID;
```

| 姓名 | 笑话数 |
|---|---|
| Amy Mathieson | 1 |
| Kevin Yank | 3 |
| Joan Smith | 1 |

等等，等等……突然 Amy Mathieson 有一个笑话？那不可能吧！事实确实如此——但仅仅是因为查询写错了。COUNT(*) 统计为每位作者返回的行数。如果我们查看 LEFT JOIN 的未分组结果，就能看出发生了什么：

```
mysql> SELECT Authors.Name, Jokes.ID AS JokeID
-> FROM Authors LEFT JOIN Jokes ON AID = Authors.ID;
```

| 姓名 | 笑话 ID |
| :--- | :--- |
| Kevin Yank | 1 |
| Kevin Yank | 2 |
| Kevin Yank | 4 |
| Joan Smith | 3 |
| Amy Mathieson | NULL |

明白了吗？Amy Mathieson *确实* 有一行 —— 就是由于 LEFT JOIN 的右侧表（Jokes）中没有匹配行而产生的强制行。笑话 ID 值为 NULL 这一事实不影响 COUNT(*) —— 它仍然将其计为一行。如果不是使用 *，而是为 COUNT 函数指定一个实际的列名（例如 Jokes.ID）来查看，它将忽略该列中的 NULL 值，并给出我们想要的计数：

```
mysql> SELECT Authors.Name, COUNT(Jokes.ID) AS NumJokes
-> FROM Authors LEFT JOIN Jokes ON AID = Authors.ID
-> GROUP BY AID;
```

| 姓名 | 笑话数 |
| :--- | :--- |
| Amy Mathieson | 0 |
| Kevin Yank | 3 |
| Joan Smith | 1 |

### 使用 HAVING 限制结果

如果我们只想要列出那些名下没有笑话的作者，*仅限*这些作者，该怎么办？再次，让我们看看大多数用户会先尝试的查询：

```
mysql> SELECT Authors.Name, COUNT(Jokes.ID) AS NumJokes
-> FROM Authors LEFT JOIN Jokes ON AID = Authors.ID
-> WHERE NumJokes = 0
-> GROUP BY AID;
ERROR 1054: Unknown column 'NumJokes' in 'where clause'
```

到这时，您可能对它没有按预期工作并不感到意外。WHERE NumJokes = 0 没起作用的原因与 MySQL 处理结果集的方式有关。首先，MySQL 从 Authors 和 Jokes 表中生成作者和笑话的原始组合列表。接下来，它处理 WHERE 子句和 FROM 子句中的 ON 部分，以便只返回列表中相关的行（在此例中，是将作者与其笑话匹配的行）。最后，MySQL 处理 GROUP BY 子句，按 AID 分组结果，统计每组中 Jokes.ID 非空的条目数量，并将 NumJokes 列作为结果生成。

请注意，NumJokes 列实际上是在处理 GROUP BY 子句时才创建的，而这发生在 WHERE 子句完成其工作**之后**！如果您想从计数中排除包含单词 "chicken" 的笑话，可以毫无问题地使用 WHERE 子句，因为该排除不依赖于 GROUP BY 子句负责生成的值。但是，影响分组后结果的条件必须出现在特殊的 HAVING 子句中。下面是修正后的查询：

```
mysql> SELECT Authors.Name, COUNT(Jokes.ID) AS NumJokes
-> FROM Authors LEFT JOIN Jokes ON AID = Authors.ID
-> GROUP BY AID
-> HAVING NumJokes = 0;
```

| 姓名 | 笑话数 |
|---|---|
| Amy Mathieson | 0 |

有些条件在 HAVING 和 WHERE 子句中都有效。例如，如果我们想按名称排除某个特定作者，可以在 WHERE 或 HAVING 子句中使用 Authors.Name != "Author Name" 来实现，因为无论您是在分组前还是分组后过滤掉作者，返回的结果都相同。在这种情况下，最好始终使用 WHERE 子句，因为 MySQL 在内部优化此类查询方面更擅长，因此它们运行速度更快。

### 摘要

在本章中，我们完善了您对 MySQL 支持的结构化查询语言 (SQL) 的了解。我们主要关注 SELECT 的功能，这些功能允许您以前所未有的灵活性和强大功能查看数据库中存储的信息。通过明智地使用 SELECT 的高级功能，您可以让 MySQL 发挥其所长，并在过程中减轻 PHP 的负担。

我们仍未看到一些孤立的查询类型（主要涉及索引），MySQL 提供了一整套内置函数库，用于计算日期和格式化文本字符串等操作。要真正精通 MySQL，您还应牢固掌握 MySQL 提供的各种列类型。例如，TIMESTAMP 类型可以真正节省时间（无意双关）。所有这些内容在 MySQL 手册中都有完整文档，并在附录 C 中简要介绍。

在第 10 章中，我们将探讨一些我们尚未有机会介绍的有用 PHP 功能。从加强安全到发送电子邮件，从处理文件上传到减轻服务器负担，我保证这是一章不容错过的结尾！

## 10 高级 PHP

PHP 的优势在于其庞大的内置函数库，即使是新手用户也可以执行非常复杂的任务，而无需安装新库或担心底层细节，这在 Perl 等其他流行的服务器端语言中经常发生。由于本书的侧重点，我们将探索范围限定在与 MySQL 数据库直接相关的那些函数（事实上，我们甚至没看到 *那些* 中的所有函数）。在这个最后部分，我们将稍微开阔视野，探讨 PHP 为构建数据驱动网站的人提供的一些其他有用功能。

我们将先了解 PHP 的 include 函数，它允许我们在多个页面中使用同一段 PHP 代码，并使常见代码片段的使用更加实用。我们还将了解如何利用此功能为网站增加额外的安全级别。

PHP 虽然通常快速高效，但仍会增加运行服务器的机器的加载时间和工作负载。在高流量网站（例如 SitePoint.com）上，此负载可能会增长到不可接受的水平。但这并不意味着我们必须放弃网站的数据驱动特性。我们将了解如何在幕后使用 PHP 来创建半动态页面，这些页面不会给服务器带来太大压力。

SitePoint.com 和其他网站论坛中常见的问题是如何使用 `<input type="file">` 标签接受网站访问者的文件上传。我们将学习如何使用 PHP 实现此功能，并了解如何使其适应数据驱动的网站。

最后，PHP 的一项非常强大的功能是能够轻松发送带有动态生成内容的电子邮件。无论您是想使用 PHP 让访问者将网站内容的电子邮件版本发送给朋友，还是只想为用户提供一种找回忘记密码的方式，PHP 的电子邮件函数都能派上用场！

### 使用 PHP 的服务器端包含

如果您在互联网上工作了一段时间，可能已经听说过服务器端包含（SSI's）这个术语；如果没有，您可以阅读 Matt

