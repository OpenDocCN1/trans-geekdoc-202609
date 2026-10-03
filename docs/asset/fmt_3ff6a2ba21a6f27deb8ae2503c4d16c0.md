
# 第 47 章 转换静态 HTML 站点

```php
    } elseif (strpos($table_val, '<b>Top 5</b>') > 1) {
        $chunk['top5'] = $table_val;
    } elseif (strpos($table_val, '<b>By the same</b>') > 1) {
        $chunk['sameauthor'] = $table_val;
    } elseif (strpos($table_val, '<b>Movies</b>') > 1) {
        $chunk['movies'] = $table_val;
    } else {
        $chunk['movie'] = $table_val;
    }
}
// 现在我们获取电影信息
if (isset($chunk['movie'])) {
    // 获取“Movies:” 之后之后的内容
    $movie_str = strstr($chunk['movie'], 'Movies:');
    // 获取电影数据的实际字符串值
    $movie_data_str = strstr($movie_str, '<font SIZE=2FACE=Arial, GENEVA, SANS-SERIF>');
    $movie_data = substr($movie_data_str, 47);
    // 移除上面的字体 标签
    echo $movie_data;
    // 现在你可以提取此字符串并将其放入数据库
    // 或其他地方...
}
?>
```

你可以对此代码进行少量扩展以提取此页面上的所有数据——只需复制电影地图，并替换你想要选择的数组名称和子字符串即可。

现在假设你想从大量的 HTML 或文本文件中提取数据。将它们复制到空空目录中以尽量减少意外后果。然后，你将希望通过封装以下情况来遍历文件：

```php
$path = '/path/to/directory';
if ($dir_handle = opendir($path)) {
    while ($file = false; $file = readdir($dir_handle)) != false) {
        if ($file != "." && $file != "..") {
            // 上述 harvest.php 的代码
```

这段代码打开了一个目录（该目录必须对 Web 用户具有正确的读取和执行权限），遍历目录中的所有文件，并对任何非特殊目录文件的数据执行 `harvest.php` 代码。你几乎肯定会从命令行运行此类脚本，而不是浏览器，因为遍历大量文件几乎保证会导致超时。

## 模板化

现在到了繁琐的部分。这是你想要草拟一个数据库，并将其转换为可运行的 Web 页面的时刻。

有多种方法可以实现这一点，包括使用完整的模板扩展，如 Smarty 模板。然而，我们的风格是使用 `heredoc` 语法布局 HTML，并在同一个页面上定义变量。这是最快的方法之一，并且保持了逻辑与显示之间的分离。

列表 47-4 显示了一个完整的页面模板，在这种情况下用于书籍评论的。

列表 47-4：页面模板

```php
<?php
/****************
 * 书籍评论页面
 ***************/
// 现在，在 GET 中传递 id
$book_id = $_GET['book_id'];
if (!isset($book_id) || !numeric($book_id)) {
    echo "未传递有效的书籍 ID";
    exit;
}
// 获取数据
// --------------------------------
$db = mysql_connect('localhost', 'user', 'mg');
mysql_select_db('mg');
// 书籍数据
$query = "SELECT
B_id,
B_title,
B_year,
B_rating,
B_movie,
B_awards,
B_review,
B_similar
FROM book
WHERE B_id = $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) == 1) {
  $book_arr = mysql_array($result);
} else {
  echo mysql_error();
}
$title = stripslashes($book_arr['B_title']);
$year = stripslashes($book_arr['B_year']);
$rating = stripslashes($book_arr['B_rating']);
$movie = stripslashes($book_arr['B_movie']);
$awards = stripslashes($book_arr['B_awards']);
$review = stripslashes($book_arr['B_review']);
$review_words = explode(',', $review);
$chunk = array_slice($review_words, 0, 200);
$review = implode(',', $chunk);
$similar = stripslashes($book_arr['B_similar']);
// 作者数据
$query = "SELECT author.A_id, author.A_firstname,
author.A_lastname
FROM author JOIN book_author (A_id)
WHERE author.B_id = $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) == 1) {
  $author_arr = mysql_array($result);
  $author_id = $author_arr['A_id'];
  $a_firstname = stripslashes($author_arr['A_firstname']);
  $a_lastname = stripslashes($author_arr['A_lastname']);
  $author = "$a_firstname $a_lastname";
} else {
  echo mysql_error();
}
// 同一作者的其他书籍
$query = "SELECT book.B_title
FROM book JOIN book_author USING (B_id)
WHERE book_author.A_id = $author_id
AND book.B_id != $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) >= 1) {
    while ($titles_arr = mysql_array($result)) {
        $titles[] = stripslashes($titles_arr['B_title']);
    }
    $title_str = implode('<BR>\n', $titles);
} else {
    $title_str = 'None';
}
// 主角数据
$query = "SELECT protagonist.P_firstname, protagonist.P_lastname
FROM protagonist
LEFT JOIN book_protagonist USING (P_id)
WHERE book_protagonist.B_id = $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) == 1) {
    $protagonist_arr = mysql_array($result);
    $p_firstname = stripslashes($protagonist_arr['P_firstname']);
    $p_lastname = stripslashes($protagonist_arr['P_lastname']);
    $protagonist = $p_firstname . " " . $p_lastname;
} else {
    echo mysql_error($query);
}
// 多子类型
$query = "SELECT Sub_name
FROM subsubgenre LEFT JOIN book_subgenre USING (Sub_id)
WHERE book_subgenre.B_id = $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) >= 1) {
    while ($sub_arr = mysql_array($result)) {
        $sub_name[] = stripslashes($sub_arr['Sub_name']);
    }
    $subgenre = implode(', ', $sub_name);
} else {
    echo mysql_error($query);
}
// 多设置
$query = "SELECT Set_name
FROM setting LEFT JOIN book_setting USING (Setting_id)
WHERE book_setting.B_id = $book_id";
$result = mysql_query($query);
if (mysql_num_rows($result) >= 1) {
    while ($set_arr = mysql_array($result)) {
        $set_name[] = stripslashes($set_arr['Set_name']);
    }
    $setting = implode(', ', $set_name);
} else {
    echo mysql_error();
}
//
// 显示页面
//
$php_self = $_SERVER['PHP_SELF'];
// 全局数组无法工作于
$page_str = <<<
<HTML>
<HEAD>
<STYLE>
TD.textblock {
    padding-left: 20;
    padding-top: 20;
    padding-right: 20;
}
P.td {
    font-family: arial, sans-serif;
    font-size: 8pt;
}
P.td_med {
    font-family: arial, sans-serif;
    font-size: 10pt;
    line-height: 125%;
}
P.title {
    font-family: arial, sans-serif;
    font-size: 10pt;
    font-weight: bold;
}
P.tab_links {
    font-family: arial, sans-serif;
    font-size: 10pt;
    margin-top: 17;
}
a {
    color:#00640;
    text-decoration:none;
}
a:link {
    color:#00640;
}
a:visited {
    color:#800080;
}
</STYLE>
</HEAD>
```

列表 47-4（继续）

| 字段 | 值 |
| :--- | :--- |
| 浏览分类： | 类型、作者、标题、评分 |
| 作者 | `$author` |
| 主人角名字 | `$protagonist` |
| 出版年份 | `$year` |
| 子类型 | `$subgenre` |
| 设定 | `$setting` |
| 该作者的其他已评论作品 | `$title_str` |
| 前 5 个最相似标题 | `similar` |
| 电影版 | `movie` |
| 我们的评分 | `$rating` |
| 社区评分 | `$comm_rating` |
| 奖项 | `$award` |

- 新评论
- 读者评分
- **类型**
  - 偷盗冒险
  - 经典侦探推理
  - 轻松推理风
  - 间谍战
  - 法医推理
  - 硬派
  - 历史类
  - 军事类
  - 警匪故事
  - 政治类
  - 私家侦探
  - 连环杀手
  - 科幻谜
  - 特殊主题
  - 悬疑
  - 惊悚

`$review` ...阅读完整...

**你觉得这本书怎么样？**

读过这本书吗？

- 5 - 极好
- 4 - 非常好
- 3 - 好
- 2 - 平庸
- 1 - 糟糕

常见问题 | 团队 | 隐私 | 广告 | 联系我们

评论页面的结果如图 47-3 所示。如果你将此图与图 47-2 进行比较，一眼就能看出设计师看到的并非所有内容都能轻松实现。在这种情况下，我们发现，随着你向 HTML 的最终布局移动，如果不产生巨大的开销，微小的视觉元素将极其难以布局。你的设计师应该愿意在这一阶段与你合作进行微调。

![](img/70f9af3d71f908e4cb0592eb9a6800.png)

图 47-3：评论页的模板版本

## 性能与缓存

在此阶段，你应该进行一些性能测试和评估。你希望获得以下估计：

- **服务器延迟**：服务器生成代码所需的时间。
- **网络延迟**：代码通过链路传输所需的时间。
- **浏览器延迟**：浏览器完全渲染页面所需的时间。

你可以通过在每个页面的开始和结束处放置 `microtime()` 调用来测量服务器延迟：

```php
<?php
$begin_time = microtime();

// 在此处编写你的脚本

$end_time = microtime();
$duration = $end_time - $begin_time;
echo $duration;
?>
```

这个持续时间在每个页面上平均小于一秒。如果每个页面加载时间超过一秒，说明你的架构存在问题。亚秒级响应是通过比你大得多且更复杂的网站实现的。请确保在与生产环境类似的设置上进行测试——生产服务器可能比开发服务器快几倍，因此在开发环境中不可接受的时间在生产环境中可能会奇般地变得可以接受。

延迟之所以特别糟糕，原因是因为它还会增加你扩展站点的成本。因为你的代码占用循环周期、数据库连接和其他资源的时间比应有的长，你投入到硬件上的资金将比一个具有类似功能的更快的服务器更多。解决这类性能问题的方法是简化你的架构，特别是那些已知会增加服务器延迟的部分（模板、对象、消息目录等）。

网络延迟（在 Web 开发者能够影响的范围内）通常取决于你的页面有多大。要测试这一点，你需要保存一个 HTML 页面及其所有相关的图形文件（包括广告），并记录它们的总大小。除以每秒 40 千字节（56k 调制解调器速度的估计值），可以估算出数据等待的时间。

沉重的页面也会浪费你的钱，特别是如果你支付了内存费用。你的 Web 服务器在发送完当前页的所有数据之前无法处理另一个请求——耗时越长，可用的 Web 服务器就越少。你有时可以通过研究透明页面压缩来临时解决页面臃肿——例如，Apache 可以在提供服务之前对任何文件进行 `gzip` 处理，这对用户来说是完全透明的——但从长远来看，你应该让你的页面更轻量。

你可以安排此脚本每天通过 `cron` 任务在命令行运行一次。（你绝对无法使用 Web 版本的 PHP 来完成此任务。）或者你可以在每次向网站添加新页面时启动它。这还有另一个安全优势：你不需要在生产环境中维护扁平数据库，只需定期推送扁平文件（也许通过 `rsync` 等工具），并维护一个只包含你想要动态显示的字段的小型数据库。

## 总结

PHP 书籍通常假设你从零开始构建站点——但在现实世界中，另一个非常常见的场景是升级现有的静态站点。PHP 和数据库可以使站点变得更容易维护，因为它们是由 PHP 从数据库中的数据组装而成的。你不需要维护数百个 HTML 文件，只需要处理一个模板，并让 PHP 按需组装页面即可。

# 使用恩图进行数据可视化

在本章的案例研究中，我们将展示如何使用 PHP 将 MySQL 数据库与图形图像相结合。我们构建了一个包含数据库的完整系统，并使用 `gd` 库生成某种数据可视化结果。书中关于这部分的章节如下：

- *第二部分*：我们使用 PHP 查询 MySQL 数据库。
- *第 42 节（图形）*：我们的最终产品是使用 `gd` 库生成的图像。
- *第 27 节（数学）*：我们需要一些三角函数来创建图像。

## 比例恩图
