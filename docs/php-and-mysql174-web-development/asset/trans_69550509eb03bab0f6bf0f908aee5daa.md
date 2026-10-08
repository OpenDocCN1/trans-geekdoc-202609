

# 实现书签的存储与检索

你开始此脚本时，首先执行常规验证。当你确定用户选择了一些书签进行删除时，你可以通过以下循环进行删除操作：

```php
foreach($del_me as $url) {
    if (delete_bm($valid, $url)) {
        echo 'Deleted ' . htmlspecialchars($url) . '<br>';
    } else {
        echo 'Could not delete ' . htmlspecialchars($url) . '<br>';
    }
}
```

如你所示，`delete_bm()` 函数负责从数据库中删除书签的实际工作。该函数位于列表 27.25 中。

+ 列表 27.25 url_fns.php 中的 delete_bm() 函数——此函数从用户的列表中删除单个书签

```php
function delete_bm($user
```

如你所见，`delete_bm()` 也是一个非常简单的函数。它尝试从数据库中删除特定用户的书签。请注意，在这种情况下，你想移除的是一个特定的用户名-书签对。其他用户可能仍然标记了该 URL。

运行删除脚本的某些输出结果如图 27.10 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_625_0.png)

图 27.10 删除脚本通知已删除的书签，然后显示剩余的书签

在 `add_bms.php` 脚本中，对数据库进行更改后，你使用 `get_user_urls()` 和 `display_user_urls()` 显示新的书签列表。

## 实现推荐功能

最后，你准备好编写链接推荐脚本 `recommend.php`。你有许多不同的方法来实现推荐。你应该执行我们所谓的“喜好”推荐。即：寻找其他至少与你的给定用户拥有相同书签的用户。这些用户的其他书签可能会吸引你的给定用户的兴趣。

实现此点的最简单方法是在 SQL 查询中使用子查询。第一个子查询看起来如下：

```sql
select distinct (b2.username)
from bookmark b1, bookmark b2
where b1.username='$valid_user.'
and b1.username != b2.username
and b1.bm_URL = b2.bm_URL
```

# 实现推荐功能

此查询使用别名来连接数据库表 `bookmark`——这是一个奇特但有时很有用的概念。想象你实际上有两个书签表，一个称为 `b1`，另一个称为 `b2`。在 `b1` 中，你查看当前用户及其书签。在另一个表中，你查看所有其他用户的书签。你正在寻找其他用户 (`b2.username`)，他们拥有与当前用户相同的 URL (`b1.bm_URL = b2.bm_URL`) 且不是当前用户 (`b1.username != b2.username`)。

该查询为你的当前用户提供了一个志同道合的人员列表。有了这个列表，你可以通过以下查询搜索他们的其他书签：

```sql
select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1, bookmark b2
    where b1.username='$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
```

你添加了第二个查询来过滤掉用户的已有书签；如果用户已经有了书签，那么就没有必要推荐它。最后，你还使用 `$popularity` 变量进行过滤。你不想推荐任何过于私人的 URL，因此你只建议那些在志同道合的用户列表中被一定数量的其他用户收藏的 URL。最终的查询看起来如下：

```sql
select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1
    where b1.username='$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
and bm_URL not in
    (select bm_URL
    from bookmark
    where username='$valid_user.')
group by bm_url
having count(bm_url) >$popularity;
```

如果你预见到会有许多用户使用你的系统，可以调高 `$popularity` 值，以便仅建议被大量用户收藏的 URL。许多人收藏的 URL 质量可能更高，且比普通网页具有更广泛吸引力。

制作推荐的完整脚本位于列表 27.26 和 27.27 中。制作推荐的主脚本称为 `recommend.php`（见列表 27.26）。它调用了 `url_fns.php` 中的推荐函数 `recommend_urls()`（见列表 27.27）。

# 第 27 章 构建用户身份验证与个性化

列表 27.26 recommend.php——此脚本建议了一些用户可能喜欢的书签

```php
<?php
require_once('bookmark_fns.php');
session_start();
do_html_header('Recommended URLs');
try {
    check_valid_user();
    $urls = recommend_urls($_SESSION['valid_user']);
    display_recommended_urls($urls);
} catch(Exception $e) {
    echo $e->getMessage();
}
display_user_menu();
do_html_footer();
?>
```

列表 27.27 url_fns.php 中的 recommend_urls() 函数——此函数实现了具体的推荐

```php
function recommend_urls($valid_user, $popularity = 1) {
// 我们将向人们提供半智能的推荐
// 如果他们与其他用户有共同的 URL，他们可能喜欢
// 这些人喜欢的其他 URL
    $conn = db_connect();

// 寻找其他匹配的用户
    // 拥有和你相同的 URL
    // 作为排除用户私有页面的简单方法，
    // 并增加推荐吸引 URL 的概率，我们
    // 指定了最小流行度水平
    if ($popularity = 1, 则在在我们推荐之前，必须有超过一个人推荐它
$query = "select bm_URL
from bookmark
where username in
    (select distinct(b2.username)
    from bookmark b1, bookmark b2
    where b1.username='$valid_user.'
    and b1.username != b2.username
    and b1.bm_URL = b2.bm_URL)
    and bm_URL not in
    (select bm_URL
    from bookmark
    where username='$valid_user.')

```php
group by bm_url
having count(bm_url) >$popularity;

if (!($result = $conn->query($query))) {
    throw new Exception('未能找到任何推荐的书签');
}

if ($result->num_rows==0) {
    throw new Exception('未能找到任何推荐的书签');
}

$urls = array();
// 构建相关 URL 的数组
for ($count=0; $row = $result->fetch_object(); $count++) {
    $urls[$count] = $row->bm_url;
}

return $urls;
```

运行推荐脚本的某些输出结果如图 27.11 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_628_0.png)

图 27.11 推荐脚本建议了用户可能喜欢的 espn.com。数据库中至少有两个喜欢 espn.com 的用户收藏了该网站

## 实现扩展

在前面的章节中，我们描述了书签应用的基本功能。你有许多不同的扩展方法。你可能考虑：

- 按主题对书签分组
- “添加到我的书签”推荐链接
- 基于数据库或特定主题的热门 推荐
- 设置用户和主题的管理界面
- 让推荐更智能或更快的方法

实验！这是学习的最佳方法。

## 安装 Apache、PHP 和 MySQL

Apache、PHP 和 MySQL 适用于许多操作系统和 Web 服务器的组合。在本录中，我们解释了如何在 UNIX 平台上从零开始设置 Apache、PHP 和 MySQL，并为 Windows 和 Mac OS X 的安装提供了建议。

本录的关键主题包括

- 以 CGI 解释器或模块运行 PHP
- 在 UNIX 下安装 Apache、PHP 和 MySQL
- 使用一体化安装包安装 Apache、PHP 和 MySQL
- 安装 PEAR
- 考虑其他 Web 服务器配置

