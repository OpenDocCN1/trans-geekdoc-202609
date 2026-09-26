# PHP 5.5 Web 开发实战





# 介绍


从零开始，教你 HTML、PHP、MySQL、CSS、JavaScript，开发一个在线阅读网站（可以当短篇小说网站、新闻网站），并且赚钱。

基于兴趣，想做什么就动手做，边做边学，理论后来再总结，自然醐醐灌顶。

本书是开源书籍，采用 markdown 语法，书放在`github.com`。代码也是开源的，也在`github`。图片放在免费的七牛存储（`qiniu.com/code=lafkpsz1`）。如果发现错字或者意见，欢迎在 Issues 反馈，例子中的文章来自简书（`jianshu.io/users/30f226598e/latest`）、游苏赋（`jianshu.io/users/fc68a49ba/latest`），在此先说“谢谢”。

GitBook 在线阅读与下载：`www.gitbook.io/book/sinkcup/php-tutorial-create-reader`。简书在线阅读：`jianshu.io/notebooks/4779/latest`。书的 github：`github.com/sinkcup/php-tutorial-create-reader`。代码的 github：`github.com/sinkcup/php-ebook-reader`。知识共享署名-非商业性相同方式 4.0 许可（`creativecommons.org/licenses/by-nc-sa/4.0/`）。

本章教你做一个能运行的网站，并且带来收入，学会完以后就入门了，但离高手还远。

# 为什么学 PHP

如果是想做网站，那看这本书就对了。

## 哪些国际使用

## 哪些国内公司使用

# 语义化 HTML

# 语义化 HTML

打开浏览器，访问一个网站，比如豆瓣（`douban.com`）是这样的：右键“查看源代码”，看到了一行的文本。是这样的：把这些代码复制下来，保存成`index.html`，用浏览器打开，看到了和`douban.com`一样的内容。这就是 HTML，写的时候是一行的文本，用浏览器打开，就会渲染成界面。

下面开始开发一个“在线网站”，可以用来小说网站、博客、等等。先规划一下功能？

* 首页：显示列表，列表里显示每篇文章的标题、摘要。
* 详情页：显示整篇文章。
* 发表页：给出文本框，录入文章。

首页的 HTML 代码如下：

```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0//EN" "http://www.w3.org/TR/xhtml1/transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="Hans">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title>在线阅读</title>
    </head>
    <body>
        <h1>在线阅读</h1>
        <div><a href="./add_article.html">写文章</a></div>
        <ul>
            <li><a href="./get_article.html?id=1">不同的上网的方式的影响</a>
                <p>摘要：通过不同的上网的方式体验和说明，试图探寻这种现象背后的原因。并为其他读者提供理论依据。偏硬，数据良好，不经任何加工和修饰，尤其是在 Windows 下，一口下去让人头皮麻。最新的产品通过润饰，但旧无法洗去……</p>
            </li>
            <li><a href="http://tech.163.com/11/0401/15/" target="_blank">奇虎 360 上市员工平均身价 580 万</a>
...
</html>
```

在浏览器中打开是这样的：能懂这些代码吗？如果看不懂，自学一下语法了，预计需要时间。教程：《`在线阅读教程`。注意：截图右上角有个“错误”，这是`Firefox`扩展，能保证写出 100%标准的 HTML，特别方便。下载页面：`users.skynet.be/mgueury/mozilla/`。简书在线阅读：`jianshu.io/notebooks/4779/latest`。书的 github：`github.com/sinkcup/php-tutorial-create-reader`。代码的 github：`github.com/sinkcup/php-ebook-reader`（此处对应原文链接保持一致）。

在浏览器中打开是这样的：能懂这些代码吗？如果看不懂，自学一下语法了，预计需要时间。教程：《`在线阅读教程`。

### 总结

我的技术水平

### 

### 语义化：最简 HTML

### 总结

### 解决 |

### 解决的问题 |

### 总结

| HTML |

| 硬件 | OS | 市场占有率 |
| --- | --- | --- |
| x86 PC | Windows（个人使用￥400 起，公司使用￥1988 起） | 90% |
| --- | --- |
| x86 PC | Linux（￥0） | 1% |
| x86 Mac | OS X（￥0） | 8% |





这时候用浏览器访问[`localhost/`](http://localhost/)，就看到网站了。不过`localhost`代表本机，别人还是访问不了。所以别人要通过 IP 访问，比如我的电脑 IP 是`192.168.1.107`，那访问[`192.168.1.107/`](http://192.168.1.107/)即可。如图：

注意：这是内网 IP，在同一个内网里可以访问，比如学校等局域网环境。如果想对外提供网站服务，需要一个公网 IP。那时候就需要购买云服务器了，那是另一个话题“搭建生产环境服务器”，以后再说。

IP 都是数字太难记了，现在网站都是用域名啊。如何使用域名访问本网站呢？

很简单，域名是由域名注册商出售的，在 google 中搜索`domain`即可，各家价格都差不多，`.com`后缀约$8/年，还有很多有意思的后缀，比如[douban.fm](http://douban.fm)、[zhi.hu](http://zhi.hu)、[github.io](http://github.io)、[jianshu.io](http://jianshu.io)。但国内域名注册商大部分都不正规，你购买了域名，会发现实际管理员邮箱是商家的，最重要的资产是域名转移码，都不在你手里，这就很危险，你买的东西却不属于你，仍然属于商家。而在国外购买域名就很正规，管理员邮箱、转移码都是你的。

常见的国外域名注册商支持支付宝的有：[godaddy.com](http://www.godaddy.com/China)、[resellerclub.com](http://www.resellerclub.com)，支持 VISA 的就很多了，比如`register.com`、`name.com`。

网站正式运营的时候，需要购买顶级域名。现在只是学习开发，那申请一个免费的二级域名即可。提供免费二级域名的商家很多，比如花生壳[oray.com](http://oray.com/)，注册登录后，进入我的控制台——域名管理——壳域名——添加域名即可。比如我申请了一个`sinkcup.wicp.net`，指向`192.168.1.107`，如图：

现在一个网站就诞生啦！点“写文章”，然后“发表”，观察发生了什么。

## 总结一下

### 我的技术水平

| HTML | 服务器部署 |
| --- | --- |
| 语义化：最简 HTML | 管理员权限 GUI 或 CLI 安装包 |

### 已解决的问题

*   如何提供网站服务
    安装`HTTP server`即可。
*   通过 IP 访问网站，很难记怎么办
    购买顶级域名，或者申请免费的二级域名。
*   奇虎 360 上市 员工平均身价 580 万
    “360 员工全部进入北京二环以内。”现场一位北京记者的一句戏言，引发现场爆发出欢呼。奇虎总裁齐向东对本报表示，360 此举，确实创造了中国互联网的员工致富神话。据了解，入职 9 个月以上的员工一般就能拿到股份，一般员工持股 4000 股左右，按照每股 34 美元减去相关费用计算，获利约 70 多万元人民币。网易新闻，与你分享。[`163.fm/WqOcR`](http://163.fm/WqOcR)

### 待解决的问题

*   哪里能找到《计算机导论》？
    找不到……我正在写的，还没完……有一本讲互联网的《浪潮之巅》，精彩，推荐阅读，但不是面向新生入门的，所以我才想到一本导论。
*   发表的文章怎么了？
    且听下分解。

### PHP 让内容起来

### PHP 让内容起来

发表的文章怎么了？
因为那是静态网页，不能处理。这时候就需要 PHP 了。首先要配置`nginx`，发现请求了 PHP 文件时，传递给 PHP 程序处理。
Windows：无需配置好了，启动`nginx`。
Linux：按照图片进行修改。
```
sudo vi /nginx/sites-enabled/default
```
修改完毕，重启`nginx`。
```
sudo /etc/init.d/nginx reload
```
然后开始写代码。修改“发表页”`article.html`的表单，提交到 PHP。
```html
<h1>写文章</h1>
<form action="add_article.php" method="post">
```
`add_article.php`收到数据，保存到哪里？最简单的方法：本地文件。
```php
<?php
$input = $_POST;
$file = './articles.json';
$data = array();
if (file_exists($file)) {
    $tmp = file_get_contents($file); //读取文件，变成字符串
    if(!empty($tmp)) {
        $data = json_decode($tmp, true); //解码成 array
    }
}
$data[] = $input;
file_put_contents($file, json_encode($data)); //把字符串保存到文件
echo '保存成功';
```能懂这些代码？如果看不懂，学一下 PHP，很简单。看这里：《PHP 手册[`www.php.net/manual/zh/firstpage.php`](http://www.php.net/manual/zh/firstpage.php)。然后把这些代码：[`github.com/sinkcup/php-ebook-reader/tree/0.2`](https://github.com/sinkcup/php-ebook-reader/tree/0.2)。在浏览器里访问，尝试录入一篇文章。如图：回到首页，刷新，看到文章列表，可以进去，如图：

## 总结一下

### 我的技术水平

| HTML | PHP | 数据存储 | HTTP 协议 |
| --- | --- | --- | --- |
| 语义化：最简 HTML | 让内容起来 | 文件 | GET、POST |

### 已解决的问题

*   提交的内容跑哪里？
    可以存到本地文件
*   `GET`和`POST`有什么区别？用哪个？
    简单的说：`GET`表示读，`POST`表示写。
*   这个城市会有影响？
    匿名用户：说法，房子有了，目前的步是 mini，套现后换路，还有妻子去香港，这就是计划。

### 待解决的问题

*   PHP 和 HTML 混写，很乱，怎么解决？
    且听分解。
*   保存之后，在 Firefox 中页面码了？

### 表现与逻辑分离

### 表现与逻辑分离

### PHP 和 HTML 混写，很乱，怎么解决？

一个页面分成文件，一个 PHP 做逻辑，一个 HTML 做模板。比如“首页”`index.php`分成：`index.php`和`index.html`。`index.php`代码如下：

```php
<?php
$articles = array();
$file = './articles.json';
if (file_exists($file)) {
    $tmp = file_get_contents($file);
    if (!empty($tmp)) {
        $articles = json_decode($tmp, true);
    }
}

$d = array(); //d 是数据，后续用到
$d['articles'] = $articles;
require_once __DIR__ . '/index.html';
```

`index.html`代码如下：

```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="zh-Hans">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title>在线阅读</title>
    </head>
    <body>
        <h1>在线阅读</h1>
        <div><a href="./add_article.html">写文章</a></div>
        <?php
            if (!empty($d['articles'])) {
                echo '<ul>';
                foreach ($d['articles'] as $k=>$v) {
                    $id = $k + 1;
                    echo '<li><a href="./get_article.php?id=' . $id . '">' . $v['title'] . '</a>';
                    echo '<p>' . mb_substr($v['content'], 0, 100, 'UTF-8') . '</p></li>';
                }
                echo '</ul>';
            }
        ?>
    </body>
</html>
```

保存之后，在 Firefox 中页面码了？打开`add_article.php`的源代码看一下，输出了“保存成功”，这不是网页。一个正常的网页包含`DOCTYPE html`、`head`等内容，其中`head`里的`charset`声明了编码，浏览器才能正常显示。添加一个`notice.html`模板即可：

```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="zh-Hans">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title><?notice['msg']?></title>
    </head>
    <body>
        <h1><?=$notice['msg']?>?></h1>
        <p><a href="/">首页</a></p>
    </body>
</html>
```
截图如下：代码下载：[`github.com/sinkcup/php-ebook-reader/tree/0.3`](https://github.com/sinkcup/php-ebook-reader/tree/0.3)

## 总结一下

### 我的技术水平

| HTML | PHP | 数据存储 | HTTP 协议 | 程序员的修养 | 等级 |
| --- | --- | --- | --- | --- | --- |
| 语义化：最简 HTML | 让内容起来 | 单机文件 | GET、POST | | 0.2 |
| | | | | PC + Windows | |
| | | | | | |
| | 表现与 | | Unicode | | 0.3 |

### 已解决的问题

*   PHP 和 HTML 混写，很乱，怎么解决？
    把 HTML 单独保存，PHP 中`require`即可，这样实现了表现与逻辑分离。
*   保存之后，在 Firefox 中页面码了？
    HTML 中声明`charset`，浏览器才知道什么编码。
*   `ANSI`与`ASCII`的区别，`UTF-8`与`Unicode`的区别，`GB2312`、`CP936`、`GBK`、`GB1830`的区别，为什么程序（`Android`、`iOS`、`Linux`、`OS X`、`Windows`）都使用`Unicode`？
    自行学习。
*   百万薪的人怎么过日子的？
    匿名用户：感谢大家的关注。很多朋友对行业[zhi.hu/3Rv9](https://zhi.hu/3Rv9)分享知乎

### 待解决的问题

*   数据有多种方式，比如单机文件（`JSON`、`txt`）、单机数据库（`Access`）、网络数据库（`MySQL`/`MariaDB`、`Oracle`、`SQL Server`）等等，根据项目进行选型。做 Web 一般采用开源免费的`MySQL`/MariaDB`，本书以`MySQL`为例。学校里应该学过`SQL`，如果没学过，请先学《SQL 教程》。

### MySQL

```sql
CREATE DATABASE `reader` DEFAULT CHARACTER SET utf8;
USE `reader`;
CREATE TABLE `articles` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `author` varchar(20) DEFAULT NULL,
  `title` varchar(50) DEFAULT NULL,
  `content` text NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

然后修改`add_article_submit.php`，把文章保存到数据库中。代码如下：

```php
<?php
$input = $_POST;
$dsn = 'mysql:host=127.0.0.1;port=3306;dbname=reader;charset=utf8';
$user = 'root';
$password = '1';
$db = new PDO($dsn, $user, $password); //连接数据库

$sql = 'INSERT INTO `articles` (`author`, `title`, `content`) VALUES (' . '\'' . $input['author'] . '\',\'' . $input['title'] . '\',\'' . $input['content'] . '\');';

$stmt = $db->query($sql); //执行 SQL
$id = $db->lastInsertId(); //获得自增 id

if (!empty($id)) {
    $notice = '保存成功';
} else {
    $notice = '出错了';
}
$d = array();
$d['notice'] = array(
    'msg' => $notice,
);
require_once __DIR__ . '/notice.html';
```





然后单篇阅读页`get_article.php`，根据`id`，查出一篇即可，这样比查出来所有文章合理多了。代码如下：

```php
<?php
$input = $_GET;
$d = array();
if (!isset($input['id']) || empty($input['id'])) {
    $d['notice'] = array(
        'msg' => '出错了：缺少参数',
    );
    require __DIR__ . '/notice.html';
    exit;
}

$dsn = 'mysql:host=127.0.0.1;port=3306;dbname=reader;charset=utf8';
$user = 'root';
$password = '1';
$db = new PDO($dsn, $user, $password);

$sql = 'SELECT `author`, `title`, `content` FROM `articles` WHERE id=' . $input['id'] . ' LIMIT 1';

$stmt = $db->query($sql);
$stmt->setFetchMode(PDO::FETCH_ASSOC);
$r = $stmt->fetchAll();

if (empty($r)) {
    $d['notice'] = array(
        'msg' => '出错了：查无此文',
    );
    require __DIR__ . '/notice.html';
    exit;
}

$d = array();
$d['article'] = $r[0];
require_once __DIR__ . '/get_article.html';
```

代码下载：[`github.com/sinkcup/php-ebook-online-reader/tree/0.4.1`](https://github.com/sinkcup/php-ebook-online-reader/tree/0.4.1)

现在可以发表、查看首页、单篇阅读，功能都实现了。

## 总结一下

### 我的技术水平

| HTML | PHP | 数据存储 | HTTP 协议 | 程序员的自我修养 | 装备 | 等级 |
| --- | --- | --- | --- | --- | --- | --- |
| 语义化 | 让内容动起来 | 单机文件 | GET、POST |  | PC + Windows | 0.2 |
| --- | --- | --- | --- | --- | --- | --- |
|  | 表现与业务分离 |  | charset | Unicode |  | 0.3 |
|  | PDO | MySQL |  |  |  | 0.4 |

### 已解决的问题

* 如何用 PHP 操作 MySQL 数据库？
  使用`PDO`即可。
* `PDO`、`php_mysqli`和`php_mysql`的分别是什么？
  请自学了解。注意：`php_mysql`已废弃。
* 【没钱，对现在的年轻人意味着什么？】
  luckystar 神探：来，讲个故事。从前有个骚年叫小明。不是姚小明，不是黄小明，也不是郭小明。就是一个普普通通的、扎人堆里找不出来的小明。男，二十多岁，家境普通。口头禅是「还不是因为老子穷”。高中时，和…… [`zhi.hu/1P8D`](http://zhi.hu/1P8D)（分享自知乎）

### 待解决的问题

* 访问`index.php`是正常网页，但访问`index.html`看到了什么？
  访问`index.php`是正常网页，但访问`index.html`看到了什么？
* `index.php`、`get_article.php`等文件里都连了数据库，如果密码变了，每个地方都要改，怎么办？
  `index.php`、`get_article.php`等文件里都连了数据库，如果密码变了，每个地方都要改，怎么办？

# 目录规划的觉醒

### 目录规划

访问`index.php`是正常网页，但访问`index.html`看到了什么？
如上所示，访问`index.html`会看到代码片段而不是正常的网页，这会给用户困惑。所以应该只访问`index.php`、`add_article.html`、`get_article.php`等文件，其他文件一律禁止。

如何禁止呢？
项目里没有目录，所有文件都放在一起，是这样的：
```
add_article.php
get.html
index.php
```

改成下面的结构：
```
htdocs/
    add_article.php
    get.html
    index.php
res/
    layout/
        article.html
        index.html
```

### Nginx 配置

找到`nginx`的配置文件，在这里：
* Windows：`C:\Windows\Conf\nginx.conf`
* Linux：`/etc/nginx/sites-enabled/default`

修改其中的`root`，重启`nginx`即可。如图所示，目录变了，包含就变了。

以前是：
```
require_once __DIR__ . '/index.html';
```
改成：
```
require_once __DIR__ . '../res/layout/index.html';
```
