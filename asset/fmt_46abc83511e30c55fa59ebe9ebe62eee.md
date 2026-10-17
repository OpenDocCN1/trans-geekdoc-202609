
```php
echo '<optgroup label="' . $value . '">\n';

userOptionList($key);

echo '</optgroup>\n';

}
?>
</select>
```

注意，你是通过调用 `userOptionList()` 函数来创建用户列表的。该函数位于 `functions.php`，每个访问级别会被调用一次。它会输出一个 `<option>` 标签列表，包含相应的用户信息。

```php
function userOptionList($level) {
  $sql = 'SELECT id, name, access_lvl FROM forum_users WHERE access_lvl=' . $level . '" ORDER BY name;';
  $result = mysql_query($sql) or die(mysql_error());
  while ($row = mysql_fetch_array($result)) {
    echo "<option value='" . $row['id'] . "'>" . htmlspecialchars($row['name']) . "</option>";
  }
}
```

其实就这些了。当选择了合适的用户时，其 ID 会传递给 `transact-admin.php` 事务页面，在那里管理员用户将被重定向到该用户的 `useraccount.php` 页面。

接下来让我们来看论坛管理页面。

# 论坛管理

这部分非常直观。我们在 `forum` 表中查找所有论坛，然后列出它们及其描述，以及一个编辑链接和一个删除链接。选择 `delete-affirm.php`，它会在删除论坛之前提示用户进行确认。这是在删除论坛之前的一种安全措施，因为删除论坛将同时删除该论坛内的所有帖子。我们留给你自己去探索 `transact-affirm.php`。这是一个非常自显易懂的页面，到目前你应该没有问题能弄清楚它是如何工作的了。

# BBcode 管理

现在我们进入了真正有趣的部分。这部分涉及正则表达式的大量讨论。我们认为它应该拥有自己的标题。

# 正则表达式

如果你不熟悉正则表达式，看到一个正则表达式可能会让你思考你所认为的什么是“规则”。然而，就像任何语言一样，只要学习了语法含义，正则表达式并没有那么困难。通过正确的命令组合，正则表达式可以非常强大。

正则表达式（通常缩为 "regex" 或 "regexp"）是一种用于匹配的符号和字母模式。一旦找到匹配，就可以将其显示、删除或替换为其他内容。如果你使用过 `*.php` 来列出目录中所有的 PHP 文件，那么你就使用过正则表达式。

那么，正则表达式如何应用于这样的应用程序呢？很好的问题。假设这个网站面向儿童（事实上它确实如此，因为很多孩子都是漫画粉丝？），你可能希望防止网站上出现性词汇，使其成为一个父母欣赏并允许孩子访问的友好场所。通过正则表达式，你可以在帖子显示在屏幕之前对其进行扫描，并将任何粗俗替换为更洁的文字。

正则表达式的主题足以写满一本书。事实上，在本章中你将在很多地方学习正则表达式。你可以通过访问 `www.php.net/pcre` 开始学习 PHP 手册。

# 两种正则表达式函数

在 PHP 中，有两种基本类型的正则表达式函数：POSIX 和 PCRE。

POSIX 代表可移植操作系统接口（不要问关于 X；我们认为极客只是随心所欲地使用 X）。POSIX 是基于 UNIX 操作系统的标准标准操作接口集。POSIX 术语实际上并不是指正则表达式本身，而是描述了正则语法的来源。更恰当的称呼是 POSIX 风格的正则表达式。POSIX 风格的正则表达式在 PHP 中通过 `ere()` 函数实现，例如 `ere_match()`、`preg_replace()`（注：此处原文可能有误，应为 `ere_replace`）和 `ere_replace()`。

PCRE 代表 Perl 兼容正则表达式。它们通常比 POSIX 风格的正则表达式更快，由于某些原因以及 PCRE 正则表达式通常更强大，大多数开发者选择 PCRE。例如 `preg_match()` 和 `preg_replace()`。

第 7 章简要向你介绍了 POSIX 风格的正则表达式。在这里我们展示 PCRE。最终选择哪种取决于你。为了彻底理解两种样式，请务必阅读手册。

# 如何编写 PCRE 正则

那么，正则表达式看起来像这样吗？我们将使用 `preg_replace()` 函数演示不同的模式。该函数接受三个参数：针、替换模式和要搜索的文本。正则模式包含在 :needle: 中

```php
$result = preg_replace($needle, $replacement, $haystack);
```

创建模式时，必须使用分隔符来定义边界。最简单的是斜杠（`/`）。模式内部有多种方式指定字符，以下是合法的：

| 模式 | 描述 |
| :--- | :--- |
| `.` | 匹配换行符外的任意字符 |
| `^` | 匹配字符串的开头 |
| `$` | 匹配字符串的结尾 |
| `*` | 匹配前面的元素零次或多次 |
| `+` | 匹配前面的元素一次或多次 |
| `?` | 匹配前面的元素 0 次或 1 次 |
| `{x}` | 恰好匹配 x 次前面的元素 |
| `{x,y}` | 匹配 x 到 y 次元素 |
| `{x,}` | 匹配 x 次或更多 |
| `[]` | 匹配括号内的任意字符 |
| `[^ ]` | 匹配括号外的任意字符 |
| `\|` | 作为“或” (altern) 使用 |
| `()` | 将多个标记组合在一起 |
| ` \ ` | 转义特殊字符 |

除了模式匹配，还有一些修符可以改变模式的“规则”。这些修符位于分隔符的右侧。目前，这里是部分列表：

- `i` | 忽略大小写：模式匹配任何大写和小写
- `s` | (.) 匹配所有字符，包括换行符
- `e` | 非常强大！模式匹配后，将结果作为 PHP 执行

# 第15章

```php
function bbcode($data) {
  $sql = 'SELECT * FROM forum_table';
  $result = mysql_query($sql);
  if (mysql_num_rows($result) > 0) {
    while($row = mysql_fetch_array($result)) {
      $bbcode['tpl'][] = '*' . html_entity_decode($row['template'], ENT_QUOTES) . ' *';
      $bbcode['rep'][] = html_entity_decode($row['replacement'], ENT_QUOTES);
    }
  }
  $data = preg_replace($bbcode['tpl'], $bbcode['rep'], $data);
  $count = 1;
  while ($data != $data && ($count < 4)) {
    $data = $data;
    $count++;
  }
  $data = preg_replace($bbcode['tpl'], $bbcode['rep'], $data);
  return $data;
}
```

由于正则表达式在模式中使用了许多字符，在将数据存储到我们的 MySQL 表格之前，它是可以安全存储的。因此，在检索数据时，我们必须执行 `html_entity_decode()`。注意使用 `$` 字符作为分隔符，因为它在正则表达式模式中没有被使用，是一个完美的分符。要使用该字符，请确保你的数字键已启用，按住 Alt 键并输入 067。或者，你可以使用其他非字母数字字符作为分隔符。

还要注意在右侧修饰符之后使用 `/` 修饰符。这指定我们不在乎大小写。如果你想使用大小敏感匹配，可以从此修饰符中删除它。

如代码所示，`$row['template']` 包含正则表达式模式。数组变量 `$row['replacement']` 包含替换模式。现在，让我们来看你之前输入的一些模式/替换对：

| 模式 (Pattern) | 替换 (Replacement) | 说明 (Explanation) |
| :--- | :--- | :--- |
| very hard | cats and dogs | 这是一个非常简单的替换，使用了字面模式。它会将任何帖子或签名中的“very hard”替换为“cats and dogs”。你在你的一个帖子中看到了这一证据。 |
| \/url\| | <a> | 将正文中任何 [url] 实例替换为 <a> 标签。注意，如果你想字面量匹配它们，必须对开启和关闭方括号进行分隔。 |
| \[b\](.+)?\[/b\] | <b>$1</b> | 现在我们进入了一些有趣的内容了。此模式匹配 [b]some text here[/b] 并将其替换为 <b>some text here</b>。 |

# 创建公告板系统 (Bulletin Board System)

最后一个模式值得稍微解释一下，因为它引入了几个新概念。括号的存在是为了让我们使用我们所谓的“反向引用”（back references）。注意替换模式中的 `$1`。这告诉函数：“提取你在第一组括号中找到的任何内容并将其放在这里。” 如果我们有一个带有第二组括号的更复杂的模式，我们将使用 `$2` 来引用在那些括号内匹配的数据。

在这些括号中，我们正在匹配除左方括号以外的任何字符。`[^]` 告诉表达式从 1 到任意数量的字符。如果你想让表达式匹配 0 个或更多，请使用 `*` 代替 `-`。

`?` 可能会让人困惑，特别是对于那些不熟悉正则表达式的人来说。因为它紧接在一个量词（`+`）之后，它并不像通常那样表示 0 个字符或 1 个字符。在这种情况下，它是告诉正则表达式不要“贪婪地”（greedy）。

想象以下文本：

Hello, [b]George[/b], how are [b]you[/b] doing today?

如果我们对该文本运行正则 `%[b]\[.+\]\[/b]$/i`缺少 `?`），正则将是“贪婪的”并匹配它能找到的最大尺寸。结果是前面的文本看起来像这样：

Hello, <b>George[/b], how are [b]you</b></b> doing today?

这在特定情况下是不好的，因为我们正尝试对“George”和“you”进行加粗。我们在模式的 `+` 之后使用 `?` 是为了告诉正则表达式非贪婪模式，这样它就能找到最小匹配项。通过添加 `?`，结果将是：

Hello, <b>George</b>, how are <b>you</b> doing today?

这当然是预期的结果。

我们知道正则表达式可能有点困惑。但请花时间学习它们。如果你理解了它们，它们可以成为你最大的盟友。你会对用正则表达式可以匹配的各种模式感到惊讶的。

关于正则表达式的更多信息，请访问 PHP 手册中的以下页面：

- `http://www.php.net/manual/en/ref.pcre.php`
- `http://www.php.net/manual/en/pcre.pattern.modifiers.php`
- `http://www.php.net/manual/en/pcre.pattern.syntax.php`

# 搜索 (Searching)

如果你没有搜索旧帖的能力，那么公告板的功能将大打折扣。你可能熟悉的任何访客板，很可能在那里都有一个搜索功能。

搜索有许多类型。最简单是要求你在输入框中输入文本，当你点击搜索按钮时，它会查找你输入的任何文本。这就是我们为此应用程序创建的搜索。

搜索也可以变得非常复杂。你可能想按输入日期或作者进行搜索。你可能想找到一个日期范围。你甚至可能想指定结果的排序方式。这些功能目前 CBA 中尚可用，但如果你觉得心比云勃，尽管提升你的搜索。

实际机制非常简单。你有一个与你的表单匹配的单文本字段和一个搜索按钮。`search.php` 页面捕捉搜索词，并构建一个相对 SQL 语句，用于返回匹配的行。然后我们遍历这些行并将数据显示在屏幕上。这与在页面上显示帖子没有太大。唯一的区别在于 SQL 语句。

```php
if (isset($_GET['keywords'])) {
  $sql = 'SELECT *, MATCH(subject, body) AGAINST(' . $_GET['keywords'] . ') AS score
  FROM forum_posts
  WHERE MATCH(subject, body) AGAINST(' . $_GET['keywords'] . ')
  ORDER BY score DESC';
}
```

```php
$result = mysql_query($sql, $conn)
or die("Could not perform search: " . mysql_error());
```

大部分搜索发生在数据库中。可以说，我们的数据库越高效，我们检索的速度就越快。为了最大化效率，我们

## 第 15 章

了解你一次可以访问多少页。例如，如果你有 40 页数据要显示，你可能只想显示第 1 到第 10 页，或第 12 到第 21 页的链接，依此类推。

让我们来看看如何对帖子列表页进行分页。大部分代码可以位于 `functions.php` 中。

在 `viewtopic.php` 中，你可以看到我们创建了一个名为 `$limit` 的变量，它是从 `config.php` 中设置限制的 `$admin` 数组中获取的：

```
$limit = $admin['pageLimit']['value'];
```

现在我们来看下 `functions.php` 中的 `showTopic()`。我们将只列出与分页相关的行：

```
global $limit;
if (isset($_GET['page'])) {
    $page = $_GET['page'];
} else {
    $page = 1;
}
if ($limit == "") $limit = 25;
$start = ($page - 1) * $limit;
```

声明 `$limit` 会使得 `viewtopic.php` 中的变量对该函数可用。如果我们没有将 `$page` 传递到 页面，我们就假设我们处于第 1 页。否则，我们将 `$page` 设置为 URL 中传递给我们的值。通过知道页码和限制（每页帖子数），我们可以计算出 `$start`（它将用于 SQL 中的 `LIMIT` 语句以检索行）。例如，如果我们在第 3 页，且限制为每页 25 个帖子，那么第 3 页将显示第 51 到 75 行。

这里是返回帖子的 SQL 语句。它很长，但并不十分复杂。它是通过 `JOIN` 语句连接的四个表。请注意 SQL 语句的第一行和最后一行：

```
SELECT SQL_CALC_FOUND_ROWS *
    p.id, p.body, p.date_posted,
    p.date_updated, u.name as author_name, u.id as author_id, 
    u.signature as sig, c.postcount as postcount,
    f.forum_id as forum_id, f.forum_moderator as mod,
    p.update_id, u2.name as updated_by
FROM forum f
JOIN forum_posts p
    ON f.id = p.forum_id
JOIN forum_users u
    ON u.id = p.author_id
LEFT JOIN forum_users u2
    ON u2.id = p.update_id
LEFT JOIN forum_postcount c
    ON u.id = c.user_id
WHERE (p.topic_id = $topicid OR p.id = $topicid)
ORDER BY p.topic_id, p.date_posted
```

# 创建公告板系统

```
LIMIT $start,$limit;
$result = mysql_query($sql, $conn)
or die(mysql_error()) . "<br>" . $sql;
$pagelinks = paginate($limit);
```

此查询返回的行数最多为 `limit` 的数量。问题是，我们需要知道如果没有使用 `LIMIT`，会返回多少行。幸运的是，MySQL 提供了一种让我们发现结果的方法。

在第一行中，我们使用了 SQL `SQL_CALC_FOUND_ROWS`。它不会对查询产生任何直接影响。它会稍微减慢速度，但它允许我们运行以下 SQL 命令：

```
$sql = SELECT FOUND_ROWS();
```

该命令执行时，会返回 `SQL_CALC_FOUND_ROWS` 找到的行数。尽管 `SQL_CALC_FOUND_ROWS` 让查询花费时间长一点，但它仍然比使用 `COUNT(*)` 运行第二次查询要高效得多。好了，我们有了创建页码链接所需的数字。

```php
function paginate($limit=10) {
  global admin;
  $sql = SELECT FOUND_ROWS();
  $result = mysql_query($sql) or die(mysql_error());
  $row = mysql_fetch_array($result);
  $numrows = $row[0];
  $pagelinks = "<div class='pagelinks'>";
  if ($numrows > $limit) {
    if (isset($_GET['page'])) {
```

