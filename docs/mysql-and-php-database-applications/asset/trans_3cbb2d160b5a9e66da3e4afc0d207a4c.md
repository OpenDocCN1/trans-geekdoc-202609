

## 第四部分：不简单的应用

此查询收集了所有阶段并对 `content_users` 表进行了外连接（outer join）。如果用户已被授予访问某个阶段的权限，该阶段名称将出现在返回结果集的 `matchvalue` 字段中。如果没有，该字段将返回一个破折号（-）。当循环运行 `checkbox_field()` 函数时，第三个参数要么是破折号，要么与 `stage` 字段的值相同。此查询的结果如下：

| matchvalue | stage_id | stage | stage_dsc |
|---|---|---|--|
| Writing | 1 | Writing | 正在编写。 |
| Editing | 2 | Editing | 准备好审核。 |
| | 3 | Proofreading | 拼写检查等。 |
| Live | 4 | Live | 故事已发布。 |
| Killed | 5 | Killed | 已删除。 |

这些知识将能够让你阅读此脚本的剩余部分。当然，光盘中的应用程序中还包含了进一步的注释。

## edit_story.php

这个脚本最多有 500 行，虽然很长，但并不特别复杂。考虑到我们之前讨论的数据结构，它需要创建新故事并在它们经过编辑阶段后更新故事。在此过程中，脚本需要检查用户是否有权对故事进行操作，并清理用户输入到中的。

该文件应该可以通过查看页面内容来读取，这些内容是由随附的 CD 光盘提供的。为了让此页面正确运行，需要做出许多决策，这增加了长度。但在字段内做出的决策非常直接。此外，还有几条 `insert`（插入）和 `update`（更新）语句。如果你在阅读代码时紧跟书本内容，那么读完它不会太困难。

本章花费了大量的空间来讨论如何使用 MySQL 的 `grant` 语句为用户分配权限。希望到这里，你已经了解这些权限是如何分配的。接下来的简短脚本将根据表中的权限，测试当前用户是否有权对某个故事进行操作。

它首先根据 `stage_id` 获取阶段名称，然后通过附加一个包含你刚刚创建的表名的 `select` 语句来创建表名字符串。如果该查询不被允许，查询将失败并返回 `false`。在查询内部，我们还涉及了 `user_stage_map` 表。该表提供了我们的安全保障，如果用户必须在 `user_stage_map` 表中拥有当前阶段的权限。如果用户在该表中没有定义权限，查询将不返回任何行。如果查询失败或返回为空，则将打印错误并退出脚本。

```php
$result = safe_query("select stage from content_stages")
where stage_id = \$stage_id;

$stage = mysql_result($result, 0);
if (!empty($stage)) {

    $stage_table = strtolower(trim($stage))."stories";
    $result = mysql_query("select a.story_id
    from $stage_table_a, content_users u, user_stage_map m
    where a.story_id = \$story_id
    and u.username = '$this_username'
    and u.user_id = \$user_id
    and m.stage_id = \$stage_id");

    if ($result === false || mysql_num_rows($result) == 0) {
        print subtitle("您没有权限在 \$stage 阶段编辑故事。");
        print paragraph(anchor_tag("index.php","主页"));
        exit;
    }
}
```

另一个特别感兴趣的项是此脚本中大量的文本处理。如果你的用户在使用某种处理工具（HTML 编辑器、文字处理器），这就是你可能需要进行的此类处理的示例。每个工具都有自己的小癖，你需要考虑这些。要确切知道你需要什么种类型的清理，唯一的方法是检查工作环境中文本编辑器生成的代码。

例如，在文章正文中不会有 `<body>` 标签。

```php
$body = eregi_replace(".*<body[^]*>.*", "", $body);
$body = eregi_replace("</body>.*.*", "", $body);
```

当然，如果你允许有限的标签集并删除所有其他标签，PHP 的 `strip_tags` 函数可以为你工作。

对于由表单上传并在 HTML 页面上重新显示的文本，运行 `stripsslashes` 函数是非常重要的。极有可能，你的 `magic_quotes_get` 设置（见附录 B）会自动用反斜杠转义上传文本中的引号或连字符。如果你将其发送浏览器，用户将在屏幕上看到反斜杠。此外，如果再次上传该文本，将再添加一组反斜杠。

```php
$body = stripsslashes($body);
$headline = stripsslashes($headline);
$subtitle = stripsslashes($subtitle);
$summary = stripsslashes($summary);
```

从 `edit_story.php` 文件的第300 行开始，有一段很代码可以执行几件巧妙的事情。如果用户在没有使用 `<p>` 标签的情况下输入文本，脚本将在合适的地方添加，假设用户通过换行（硬回车）指示了段落。如果用户确实使用了 `<p>` 标签，脚本将检查文本，确保没有奇怪的空格或格式错误的标签。我们建议你查看 CD 光盘上提供的代码和注释，以便对如何进行复杂的文本处理有一个良好的理解。

## 总结

在本章中，你看到了了创建内容管理系统时可以包含的一些奇妙功能。当然，像这样的应用程序可以比这复杂得多、远得多（**far, far more complex**）。但这是一个很好的开始，并提供了一种组织代码和数据库表的合理方法。

我们在创建此应用程序时还使用了 MySQL 的 `grant` 语句。正如我们在整个应用程序中所说的，我们在这里使用的授权方案可能并不完美（**may not be terribly**）。但它提供了一个很好的示例，说明了如何建立一个一个用户名和密码对于整个应用程序是不够的系统。

## 第12 章

## 线程讨论

### 本章内容

- 为你的 Web 网站添加社区
- 使用高级技术编写函数
- 在设计数据库时要考虑的其他标准

如果你创建了一个 Web 网站或正准备创建一个，可能可以假设你希望人们频繁访问你的页面。但正如 Web 行业中每个人所知，忠诚度是转瞬即逝的，人们总在寻找更好、更有吸引力或更符合自己兴趣的东西。毕竟，总有别人拥有更好的布兰妮·斯宾斯照片。如果你希望你的访问者为你的网站做出贡献，他或她可能对你展示的主题有意见。如果我的多年观察结论是正确的，人们喜欢分享他们的意见。使用本章中的线程讨论应用程序，你可以创建一个允许用户分享意见并与你以及彼此互动的 Web 网站。

