   

# Table of Contents

1.  [Introduction](#index.html)
2.  [入门级](#README.html) 
    1.  [为什么学PHP](#why_php.html)
    2.  [语义化HTML](#html.html)
    3.  [搭建开发环境服务器](#dev_server.html)
    4.  [PHP让内容动起来](#php_provide_dynamic_content.html)
    5.  [表现与业务逻辑分离](#separate_view_and_logic.html)
    6.  [PDO MySQL](#pdo_mysql.html)
    7.  [目录规划意识的觉醒](#project_directory_structure_starter.html)
    8.  [SQL注入攻击](./0/sql_injection.html)
    9.  [XSS攻击](./0/xss.html)
    10.  [注册与登录](./0/register_and_login.html)
    11.  [CSS：让网页漂亮起来](./0/css.html)
    12.  [细节：404、robots和favicon](./0/robots_and_favicon.html)
    13.  [商业模式](./0/business_model.html)
    14.  [搭建生产环境服务器](./0/prod_server.html)
    15.  [手动上线](./0/release.html)
    16.  [学会了本章，你的收入应达到](#show_me_the_money.html)
3.  [初级](./1/README.html) 
    1.  [不只是网页，还有txt](./1/txt.html)
    2.  [new一个对象](./1/object.html)
    3.  [书写规范](./1/phpcs.html)
    4.  [单元测试](./1/phpunit.html)
    5.  [git版本管理](./1/git.html)
    6.  [脚本上线](./1/release.html)
    7.  [异常](./2/exception.html)
    8.  [学会了本章，你的收入应达到](./1/show_me_the_money.html)
4.  [中级](./2/README.html) 
    1.  [命名空间](./2/namespace.html)
    2.  [REST](./2/rest.html)
    3.  [多台服务器负载均衡](./2/load_balancing.html)
    4.  [网页如何支持手机和平板](./2/phone_and_pad.html)
    5.  [如何支持手机APP](./2/app.html)
    6.  [学会了本章，你的收入应达到](./2/show_me_the_money.html)

# Introduction

# PHP 5.5 Web零基础教程：开发一个在线阅读网站

从零开始，教你HTML、PHP、MySQL、CSS、JavaScript，开发一个在线阅读网站（可以当短篇小说网站、新闻网站），并且赚钱。

基于兴趣，想做什么就动手做，边做边学，理论后来再总结，自然醍醐灌顶。

本书是开源书籍，采用markdown语法，书放在[github.com](http://github.com)。代码也是开源的，也在github上。图片放在免费的七牛云存储[qiniu.com](https://portal.qiniu.com/signup?code=3lafkpsz7yes1)上。例子中的文章来自简书的[Ryekee](http://jianshu.io/users/30f22635968e/latest_articles)、[游苏赋](http://jianshu.io/users/9fc68a490b8a/latest_articles)，在此先说声“谢谢”:)

如果发现错别字或者有意见建议，欢迎反馈，可以在简书里直接评论，或者在github Issues里面提，电子书修改更新还是很方便的。

GitBook在线阅读与下载：[https://www.gitbook.io/book/sinkcup/php-web-tutorial-create-online-reader](https://www.gitbook.io/book/sinkcup/php-web-tutorial-create-online-reader)

简书在线阅读：[http://jianshu.io/notebooks/104779/latest](http://jianshu.io/notebooks/104779/latest)

书的github：[https://github.com/sinkcup/php-web-tutorial-create-online-reader](https://github.com/sinkcup/php-web-tutorial-create-online-reader)

代码的github：[https://github.com/sinkcup/php-ebook-online-reader](https://github.com/sinkcup/php-ebook-online-reader)

[知识共享署名-非商业性使用-相同方式共享 4.0 国际许可协议](http://creativecommons.org/licenses/by-nc-sa/4.0/)进行许可。

# 入门级

# 入门级

本章教你做一个能运行的网站，并且带来收入，学完以后编程就入门了，但离高手还很远。

# 为什么学PHP

# 为什么学PHP

如果是想做网站，那看这本书就对了。

## 哪些国际公司使用PHP

todo

## 哪些国内公司使用PHP

todo

# 语义化HTML

# 语义化HTML

打开浏览器，访问一个网站，看到了漂亮的网页。比如豆瓣（[douban.com](http://douban.com)）是这样的：

右键“查看页面源代码”，看到了一行行的文本。是这样的：

把这些代码复制下来，保存成index.html文件，用浏览器打开，看到了和访问douban.com一样的内容。如图：

这就是HTML，写的时候是一行行的文本，用浏览器打开，就会渲染成图形化的界面。

下面开始开发一个“在线阅读网站”，可以用来当小说网站、博客、新闻网站等等。

先来规划一下产品要做哪些功能？

*   首页：显示文章列表，列表里显示每篇文章的标题、摘要。
    
*   详情页：显示整篇文章。
    
*   发表页：给出文本框，录入保存文章。
    

首页的HTML代码如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="zh-Hans" lang="zh-Hans">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title>在线阅读</title>
    </head>
    <body>
        <h1>在线阅读</h1>
        <div><a href="./add_article.html">写文章</a></div>
        <ul>
            <li><a href="./get_article.html?id=1">论不同的科学上网的方式对数据造
成的影响</a>
                <p>摘要：通过对不同的科学上网的方式的体验和说明，试图探寻其造成>这种现象的背后的原因。并为其他研究者提供理论依据。 1) GoAgent  口感偏硬，数据刚>朗，不经任何的加工和修饰，尤其是在 Windows 下使用，一口咬下去让人头皮发麻。即便>最新的产品通过 rc4 稍稍润饰，但仍旧无法洗去那钻……</p>
            </li>
            <li><a href="http://tech.163.com/11/0401/15/70IJH2KI000915BF.html" target="_blank">奇虎360上市 员工平均身价580万</a>
                <p>“360员工全部进入北京二环以内。”现场一位北京记者的一句戏言，引发现场爆发出欢呼。奇虎总裁齐向东对本报表示，360此举，确实创造了中国互联网的员工>致富神话。据了解，入职9个月以上的员工一般就能拿到股份，一般员工持股4000股左右，>按照每股34美元减去相关费用计算，获利约70多万元人民币……</p>
            </li>
            <li><a href="http://www.douban.com/note/214971831/" target="_blank">你想在一个暮气沉沉的大公司里写一天用不上的代码然后回家撸撸就睡？</a>
                <p>在我们这里，你可以得到什么？
                1.跟对一个老大，参与一个伟大的公司的创业；
                2.在它伟大之前，就得以在一个甚至能输出价值观的牛逼公司里骄傲地工
作；
                3.虽然我们相信你不会舍得早早从这样的公司退休，但还是为你准备了一
份上市时就足以让你退休、足以让你彻底沦为一个废物的股份/期权；
                4.每人一把Herman Miller的Embody，或okamura的contessa。

                 来吧，小伙子们，这多半是你们一生一次的机会，把个人简历投到这里吧：
                 laoluomobile@gmail.com

                  罗永浩
                  </p>
            </li>
        </ul>
    </body>
</html>
```

在浏览器中打开是这样的：

能看懂这些代码吗？如果看不懂，自学一下HTML语法就行了，很简单，预计需要1至2天时间。教程在这里：《梦之都HTML教程》[www.dreamdu.com](http://www.dreamdu.com/xhtml/)。

自学：2天。

注意：截图的Firefox右上角有个“0错误/0警告”，这是Firefox扩展HTML Validator，能保证你写出100%标准的HTML，特别方便，推荐安装。下载页面：[http://users.skynet.be/mgueury/mozilla/](http://users.skynet.be/mgueury/mozilla/)。

学完HTML，知道语义化是什么意思了，会写最简洁的HTML了，那咱们继续。

刚才的代码是首页，其他还有详情页、发表页，在这里：

代码下载：[https://github.com/sinkcup/php-ebook-online-reader/tree/0.1.0](https://github.com/sinkcup/php-ebook-online-reader/tree/0.1.0)

下载以后，你就可以看到截图里的精彩内容，知道如何“在北京买房”、“9个月挣到70w”、“30岁退休”，当然了，为了吸引青年男女，特意放了几篇XXOO相关的文章，其中有一篇是老罗写的，很精彩又不低俗，人格担保，你懂的。

## 总结一下

### 我的技术水平

| HTML |
| --- |
| 语义化：最简HTML |
| --- |

### 已解决的问题

*   零基础如何学习HTML
    
    自学[《梦之都HTML教程》](http://www.dreamdu.com/xhtml/)。
    
*   如何写出100%标准的HTML
    
    使用Firefox扩展[HTML Validator](http://users.skynet.be/mgueury/mozilla/)即可。
    
*   【人在北京，30 岁了，实在买不起房，对生活感到悲观，怎么办？】
    
    胖狗同学：事实上，我是为这个被折叠的答案来写一篇回复的，我只想说，楼主在精神上没准备好买房（虽然我很不爱这么定义一个人），即使他的收入增长50%，到了30万，他还会抱怨买不起房…… [http://zhi.hu/WAJ1](http://zhi.hu/WAJ1)（分享自知乎）
    

### 待解决的问题

*   这些HTML代码都在电脑上存着，本地能打开，但别的电脑、手机如何访问呢？
    
    且听下回分解。
    

# 搭建开发环境服务器

# 搭建开发环境服务器

这些HTML代码都在电脑上存着，本地能打开，但别的电脑、手机如何访问呢？

安装HTTP server即可，常见的有nginx、apache。本书以流行的nginx为例。

看过《计算机互联网导论》的童鞋可能知道，计算机有很多种：电脑、服务器、手机、平板、路由器等等，其中电脑是面向个人桌面的，分为两种：PC和Mac，PC上面主要安装Windows系统、Linux系统，Mac上面主要是OS X。引用那本书的两个数据表格：

## 电脑操作系统市场占有率

| 硬件 || OS || 市场占有率 |
| --- | --- | --- |
| x86 PC || Windows（个人使用￥400起，公司商业使用￥1988起） || 90% |
| --- | --- | --- |
| x86 PC || Linux（￥0） || 1% |
| x86 Mac || OS X（￥0） || 8% |

## 各大公司使用的服务器操作系统

| 硬件 || OS || 谁在用 |
| --- | --- | --- |
| x86-64 server（arm-64正在起步） || Linux server || Google、Facebook、腾讯、阿里、百度、小米、锤子、360等绝大部分互联网公司 |
| --- | --- | --- |
| x86-64 server || Windows server || 微软、事业单位、传统行业等非技术公司 |

很明显，服务器大部分都是Linux的，因为系统免费又开源，可以自行修改定制；硬件可自由选择，便宜；命令行界面适合脚本编程实现自动化。

不过大陆高校与技术前沿脱节比较严重，编程教科书、机房都是Windows的，没有Linux，也没有Mac。如果你热爱编程，经过几年的实践，自然就去接触到Linux服务器自动化部署、代码自动化测试发布，这就是自动化，不再喜欢在界面上点来点去了。而且这时候你所在的公司也不一样了，到了前沿技术公司，没有Windows，只有Linux和OS X，和服务器环境一致或接近，比如Google、豆瓣、小米、饿了么，甚至二三线公司比如安居客。

举个例子，大家也许就明白了：“学校机房需要给1000台电脑安装盗版Office、QQ等几十个软件，你会怎么做？跑到每台电脑上点下一步？1天之内能完成吗？这时候就知道自动化的意义了。”。

有的童鞋看到这个问题乐了，休息一下，请看这里：[zhi.hu/31MG](http://zhi.hu/31MG)

回到正题，现在假设你是一个编程菜鸟，热爱图形界面，痛恨命令行。没关系，本章就是面向菜鸟的，大家都是从这个阶段过来的，在大陆的Windows教育下，菜鸟热爱图形界面是正常的，不丢人。那你很可能用的是Windows，如果用的是Linux或OS X，那说明你爱钻研，领先同龄人好几年。

入门时，如何快速搭建开发环境？

Windows：下载wnmp（[getwnmp.org](http://www.getwnmp.org/)），图形界面的，点下一步安装，右键使用管理员权限启动即可。

Ubuntu（Linux有很多版本，本书以流行的Ubuntu为例）：一个命令即可

```
sudo apt-get install nginx php5-fpm php5-mysqlnd
```

Mac：

```
brew install nginx
```

安装过程不再截图，不再详述，因为“DIY、装系统、装软件、Android刷机”对于计算机爱好者来说，是小意思。如果你刚刚大一，对这些不熟，没关系，多装几次就熟了，有问题“Google一下，你就知道的太多了”。如果装过几次，你发现自己对“CPU、内存、显卡、固态硬盘、系统、软件、网站”不感兴趣，嫌麻烦不爱折腾，那说明你真的不爱好计算机，千万不要学编程，立即停止阅读本书，转专业还来得及，钻研感兴趣的方向，否则工作几年差距越来越大，别人感兴趣，自然爱折腾爱钻研，进入BAT一线公司（[应届一本本科生起薪12w](http://zhi.hu/3yYh)），逐渐成为高级工程师、架构师、技术专家，或者去创业9个月挣70w，而你在一个不感兴趣的行业里，一直是入门级工程师打杂，只能在二线公司（新浪、网易、搜狐，应届本科生月薪几千），甚至在三流四流公司，一直工资低，碌碌无为。

装好以后，用浏览器访问[http://localhost/](http://localhost/)，看到一个简单的网页，是这样的：

这个网页在哪呢？找到以后，把上次下载的网站代码放进去，换掉它，就行了吧？

对。

Windows：在C:\\Wnmp\\html\\，把index.php删除，然后把index.html等等放进去。

Linux：在/usr/share/nginx/html/，修改权限，然后把index.html等等放进去。

```
sudo chmod -R 777 /usr/share/nginx/html
```

这时候用浏览器访问[http://localhost/](http://localhost/)，就看到网站了。不过localhost代表本机，别人还是访问不了。所以别人要通过IP访问，比如我的电脑IP是192.168.1.107，那访问[http://192.168.1.107/](http://192.168.1.107/)即可。如图：

注意：这是内网IP，在同一个内网里可以访问，比如学校等大局域网环境。如果想对外提供网站服务，需要一个公网IP。那时候就需要购买云服务器了，那是另一个话题“搭建生产环境服务器”，以后再说。

IP都是数字太难记了，现在网站都是用域名啊。如何使用域名访问本网站呢？

很简单，域名是由域名注册商出售的，在google中搜索domain即可，各家价格都差不多，.com后缀约$8/年，还有很多有意思的后缀，比如[douban.fm](http://douban.fm)、[zhi.hu](http://zhi.hu)、[github.io](http://github.io)、[jianshu.io](http://jianshu.io)。但国内域名注册商大部分都不正规，你购买了域名，会发现实际管理员邮箱是商家的，最重要的资产是域名转移码，都不在你手里，这就很危险，你买的东西却不属于你，仍然属于商家。而在国外购买域名就很正规，管理员邮箱、转移码都是你的。

常见的国外域名注册商支持支付宝的有：[godaddy.com](http://www.godaddy.com/China)、[resellerclub.com](http://www.resellerclub.com)，支持VISA的就很多了，比如register.com、name.com。

网站正式运营的时候，需要购买顶级域名。现在只是学习开发，那申请一个免费的二级域名即可。提供免费二级域名的商家很多，比如在花生壳[oray.com](http://oray.com/)，注册登录后，进入我的控制台——域名管理——壳域名——添加域名即可。比如我申请了一个sinkcup.wicp.net，指向192.168.1.107，如图：

现在一个网站就诞生啦！点“写文章”，然后“发表”，观察发生了什么。

## 总结一下

### 我的技术水平

| HTML || 服务器部署 |
| --- | --- |
| 语义化：最简HTML || 管理员权限GUI或CLI安装包 |
| --- | --- |

### 已解决的问题

*   如何提供网站服务
    
    安装HTTP server即可。
    
*   通过IP访问网站，很难记怎么办
    
    购买顶级域名，或者申请免费的二级域名。
    
*   奇虎360上市 员工平均身价580万
    
    “360员工全部进入北京二环以内。”现场一位北京记者的一句戏言，引发现场爆发出欢呼。奇虎总裁齐向东对本报表示，360此举，确实创造了中国互联网的员工致富神话。据了解，入职9个月以上的员工一般就能拿到股份，一般员工持股4000股左右，按照每股34美元减去相关费用计算，获利约70多万元人民币。网易新闻，与你分享。[http://163.fm/WqOc6mR](http://163.fm/WqOc6mR)
    

### 待解决的问题

*   哪里能找到《计算机互联网导论》这本书？
    
    找不到……我正在写的，还没写完……有一本讲互联网的书《浪潮之巅》，很精彩，推荐阅读，但不是面向大一新生互联网入门的，所以我才想到写一本导论。如果大家喜欢现在情况，而不是“第一台计算机是什么时候诞生的”这种导论……欢迎联系我，参加试读。
    
*   发表的文章怎么不见了？
    
    且听下回分解。
    

# PHP让内容动起来

# PHP让内容动起来

发表的文章怎么不见了？

因为那是静态HTML网页，不能处理数据。这时候就需要PHP了。

首先要配置一下nginx服务器，当发现请求了PHP文件时，就传递给PHP程序进行处理。

Windows：无需配置。wnmp已经默认配置好了，启动PHP和nginx即可。

Linux：按照下面的图片进行修改。

```
sudo vi /etc/nginx/sites-enabled/default
```

修改完毕，重启nginx。

```
sudo /etc/init.d/nginx reload
```

然后开始写代码。修改“发表页”add\_article.html的表单，提交到PHP。代码如下：

```
<h1>写文章</h1>
<form action="add_article_submit.php" method="post">
```

add\_article\_submit.php收到数据，保存到哪里呢？最简单的方法：本地文件。代码如下：

```
<?php
$input = $_POST;
$file = './articles.json';
$data = array();
if (file_exists($file)) {
    $tmp = file_get_contents($file); //读取文件，变成字符串
    if(!empty($tmp)) {
        $data = json_decode($tmp, true); //json解码成array
    }
}
$data[] = $input;
file_put_contents($file, json_encode($data)); //把字符串保存到文件
echo '保存成功';
```

能看懂这些代码吗？如果看不懂，学一下PHP语法，很简单。看这里：《PHP官方手册：第一个 PHP 页面》[http://www.php.net/manual/zh/tutorial.firstpage.php](http://www.php.net/manual/zh/tutorial.firstpage.php)

自学：0.5天。

然后把这些代码下载下来：[https://github.com/sinkcup/php-ebook-online-reader/tree/0.2.0](https://github.com/sinkcup/php-ebook-online-reader/tree/0.2.0)

在浏览器里访问，尝试录入一篇文章。如图：

然后回到首页，刷新，看到文章列表，可以点进去阅读，如图：

## 总结一下

### 我的技术水平

| HTML || PHP || 数据存储 || HTTP协议 |
| --- | --- | --- | --- |
| 语义化：最简HTML || 让内容动起来 || 文件存数据 || GET、POST |
| --- | --- | --- | --- |

### 已解决的问题

*   提交的内容跑哪里去了？
    
    可以存到本地文件里
    
*   GET和POST有什么区别？该用哪个？
    
    简单的说：GET表示读，POST表示写。
    
*   【阿里 IPO 后员工套现 410 亿美元，对杭州这个城市会有怎样的影响？】
    
    匿名用户：现身说法，房子有了，目前的代步车是mini，套现后换辆路虎揽胜，还有让妻子去香港生孩子，这就是我的计划。[http://zhi.hu/4OKR](http://zhi.hu/4OKR)（分享自知乎）
    

### 待解决的问题

*   PHP和HTML混写，很乱啊，怎么解决？
    
    且听下回分解。
    
*   保存之后，在Firefox中页面怎么乱码了？
    
    且听下回分解。
    

# 表现与业务逻辑分离

# 表现与业务逻辑分离

## PHP和HTML混写，很乱啊，怎么解决？

一个页面分成两个文件即可，一个PHP做逻辑，一个HTML做模板。

比如“首页”`index.php`分成：`index.php`和`index.html`。`index.php`代码如下：

```
<?php
$articles = array();
$file = './articles.json';
if (file_exists($file)) {
    $tmp = file_get_contents($file);
    if (!empty($tmp)) {
        $articles = json_decode($tmp, true);
    }
}

$d = array(); //d 是 data的意思，后续会用到
$d['articles'] = $articles;
require_once __DIR__ . '/index.html';
```

`index.html`代码如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="zh-Hans" lang="zh-Hans">
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
                    echo '<p>' . mb_substr($v['content'], 0, 100, 'UTF-8') . '……</p></li>';
                }
                echo '</ul>';
            }
        ?>
    </body>
</html>
```

## 保存之后，在Firefox中页面怎么乱码了？

打开`add_article_submit.php`的源代码看一下，只输出了“保存成功”，那这不是一个网页。一个正常的网页需要包含DOCTYPE html、head、body等内容，其中head里的charset声明了编码，这样浏览器才能正常显示。所以添加一个`notice.html`模板即可。代码如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="zh-Hans" lang="zh-Hans">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
        <title>提示：<?=$d['notice']['msg']?></title>
    </head>
    <body>
        <h1>提示：<?=$d['notice']['msg']?></h1>
        <p><a href="/">回到首页</a></p>
    </body>
</html>
```

截图如下：

代码下载：[https://github.com/sinkcup/php-ebook-online-reader/tree/0.3.0](https://github.com/sinkcup/php-ebook-online-reader/tree/0.3.0)

## 总结一下

### 我的技术水平

| HTML || PHP || 数据存储 || HTTP协议 || 程序员的自我修养 || 装备 || 等级 |
| --- | --- | --- | --- | --- | --- | --- |
| 语义化 || 让内容动起来 || 单机文件 || GET、POST ||  || PC + Windows || 0.2 |
| --- | --- | --- | --- | --- | --- | --- |
|  || 表现与业务分离 ||  || charset || Unicode ||  || 0.3 |

### 已解决的问题

*   PHP和HTML混写，很乱啊，怎么解决？
    
    把HTML单独保存，PHP中require即可，这样就实现了表现与业务逻辑分离。
    
*   保存之后，在Firefox中页面怎么乱码了？
    
    HTML中需要声明charset，浏览器才知道用什么编码解析。
    
*   ANSI与ASCII的区别，UTF-8与Unicode的区别，GB2312、CP936、GBK、GB18030的区别，为什么技术公司的程序（Android、iOS、Linux、OS X、Windows）都使用Unicode？
    
    请自行学习。
    
*   【百万年薪的人都是怎么过日子的？】
    
    匿名用户：感谢大家的关注。很多朋友对选对行业……[http://zhi.hu/3Rv9](http://zhi.hu/3Rv9)（分享自知乎）
    

### 待解决的问题

*   查看`get_article.php`的代码，读一篇文章，却把所有文章取了出来，再取其中一篇，这样浪费性能啊，如果文章有成千上万篇，那怎么办？
    
    且听下回分解。
    

# PDO MySQL

# PDO MySQL

## 如果文章有成千上万篇，该怎样保存？

数据保存有多种方式，比如单机文件（JSON、txt）、单机数据库（SQLite、Access）、网络数据库（MySQL/MariaDB、Oracle、SQL Server）等等，根据项目需要进行选型。做Web一般采用开源并且免费的MySQL/MariaDB，本书也以MySQL为例。

学校里应该学过SQL，如果没学过，请先自学《SQL 教程》[http://www.w3school.com.cn/sql/](http://www.w3school.com.cn/sql/)。

自学：1天。

假设这个在线阅读项目叫做“reader”，需要一个“文章”表“articles”。建库建表代码如下：

```
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

然后修改`add_article_submit.php`，把文章保存到数据库中即可。代码如下：

```
<?php
$input = $_POST;
$dsn = 'mysql:host=127.0.0.1;port=3306;dbname=reader;charset=utf8';
$user = 'root';
$password = '1';
$db = new PDO($dsn, $user, $password); //连接数据库

$sql = 'INSERT INTO `articles` (`author`, `title`, `content`) VALUES (' . '\'' . $input['author'] . '\',\'' . $input['title'] . '\',\'' . $input['content'] . '\');';

$stmt = $db->query($sql); //执行SQL
$id = $db->lastInsertId(); //获得自增id

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

然后首页`index.php`把这些文章查出来即可，代码如下：

```
<?php
$dsn = 'mysql:host=127.0.0.1;port=3306;dbname=reader;charset=utf8';
$user = 'root';
$password = '1';
$db = new PDO($dsn, $user, $password);

$sql = 'SELECT `id`, `author`, `title`, `content` FROM `articles` LIMIT 10';

$stmt = $db->query($sql);
$stmt->setFetchMode(PDO::FETCH_ASSOC);
$articles = $stmt->fetchAll();

$d = array();
$d['articles'] = $articles;
require_once __DIR__ . '/index.html';
```

然后单篇阅读页`get_article.php`，根据id，查出一篇即可，这样比查出来所有文章合理多了。代码如下：

```
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

代码下载：[https://github.com/sinkcup/php-ebook-online-reader/tree/0.4.1](https://github.com/sinkcup/php-ebook-online-reader/tree/0.4.1)

现在可以发表、查看首页、单篇阅读，功能都实现了。

## 总结一下

### 我的技术水平

| HTML || PHP || 数据存储 || HTTP协议 || 程序员的自我修养 || 装备 || 等级 |
| --- | --- | --- | --- | --- | --- | --- |
| 语义化 || 让内容动起来 || 单机文件 || GET、POST ||  || PC + Windows || 0.2 |
| --- | --- | --- | --- | --- | --- | --- |
|  || 表现与业务分离 ||  || charset || Unicode ||  || 0.3 |
|  || PDO || MySQL ||  ||  ||  || 0.4 |

### 已解决的问题

*   如何用PHP操作MySQL数据库？
    
    使用PDO即可。
    
*   PDO、php\_mysqli和php\_mysql的区别是什么？
    
    请自学了解。注意：php\_mysql已废弃。
    
*   【没钱，对现在的年轻人意味着什么？】
    
    luckystar神探：来，讲个故事。 从前有个骚年叫小明。不是姚小明，不是黄小明，也不是郭小明。就是一个普普通通的、扎人堆里找不出来的小明。 男，二十多岁，家境普通。口头禅是「还不是因为老子穷」。 高中时，和…… [http://zhi.hu/1P8D](http://zhi.hu/1P8D)（分享自知乎）
    

### 待解决的问题

*   访问index.php是正常网页，但访问index.html看到了什么？
    
    请进行实验。且听下回分解。
    
*   `index.php`、`get_article.php`等多个文件里都连了数据库，如果密码变了，每个地方都要改，怎么办？
    
    且听下回分解。
    

# 目录规划意识的觉醒

# 目录规划意识的觉醒

## 访问index.php是正常网页，但访问index.html看到了什么？

如上图所示，访问`index.html`会看到代码片段，而不是正常的网页，这会给用户带来困惑。所以应该只允许访问`index.php`、`add_article.html`、`get_article.php`等文件，其他文件一律禁止访问，比如`index.html`这种模板文件。

如何禁止访问呢？

把允许访问的文件放在一个目录，修改HTTP Server的根目录指向这里即可。

本来项目里没有目录，所有文件都放在一起，是这样的：

```
add_article_submit.php
get_article.html
get_article.php
index.html
index.php
```

改成下面的目录结构：

```
htdocs/
    add_article_submit.php
    get_article.php
    index.php
res/
    /layout/
        get_article.html
        index.html
```

然后找到nginx的配置文件，在这里：

*   Windows：`C:\Wnmp\Conf\nginx.conf`
    
*   Linux： `/etc/nginx/sites-enabled/default`
    

修改其中的server->root，重启nginx即可。如图所示：

目录变了，包含就变了，记得`index.php`等php文件中的代码要改。以前是：

```
require_once __DIR__ . '/index.html';
```

要改成：

```
require_once __DIR__ . '/../res/layout/index.html';
```

然后访问`index.html`会出现404错误，即“不存在”。而访问`index.php`是可以的，如图所示：

## 多个文件里都连了数据库，如果密码变了，每个地方都要改，怎么办？

同一件事情，重复做很多次，浪费了时间，是编程的大忌，违反了DRY原则（don't repeat yourself）。使用配置文件即可解决此问题。

配置文件用什么格式？打开PHP安装后的目录，会发现lib/php.ini文件，这是PHP的配置文件，由此可知PHP原生支持ini格式。本书也采用ini格式。配置文件当然也不应该让用户访问，所以单独建一个conf目录，现在项目目录结构如下：

```
conf/
    db.ini
htdocs/
    add_article.html
    get_article.php
    index.php
res/
    /layout/
        get_article.html
        index.html
```

db.ini的内容如下：

```
host="127.0.0.1"
port="3306"
dbname="reader"
charset="utf8"
username="root"
password="1"
```

然后每个php页面解析配置文件，连接数据库，执行SQL。代码如下：

```
$conf = parse_ini_file(__DIR__ . '/../conf/db.ini');
$dsn = 'mysql:host=' . $conf['host'] . ';port=' . $conf['port'] . ';dbname=' . $conf['dbname'] . ';charset=' . $conf['charset'];
$db = new PDO($dsn, $conf['username'], $conf['password']);
```

如图所示：

可以看到，如果数据库地址、用户名、密码改了，只用改db.ini即可，很方便。

代码下载：[https://github.com/sinkcup/php-ebook-online-reader/tree/0.5.0](https://github.com/sinkcup/php-ebook-online-reader/tree/0.5.0)

## 总结一下

### 我的技术水平

| HTML || PHP || 数据存储 || HTTP协议 || 程序员的自我修养 || 装备 || 等级 |
| --- | --- | --- | --- | --- | --- | --- |
| 语义化 || 让内容动起来 || 单机文件 || GET、POST ||  || PC + Windows || 0.2 |
| --- | --- | --- | --- | --- | --- | --- |
|  || 表现与业务分离 ||  || charset || Unicode ||  || 0.3 |
|  || PDO || MySQL ||  ||  ||  || 0.4 |
|  || 目录规划 ||  ||  || DRY ||  || 0.5 |

### 已解决的问题

*   访问index.php是正常网页，但访问index.html看到了什么？
    
    用户看到了代码片段，这是不对的，目录规划隔离即可。
    
*   多个文件里都连了数据库，如果密码变了，每个地方都要改，怎么办？
    
    谨记DRY，使用ini配置文件。当然还可以使用PHP array、PHP object、JSON，请自行了解。
    
*   【锤子手机 Smartisan T1 正式发售版的实际使用体验如何？】
    
    喻梦萱：谢邀。。。 11日早上收到的，优先码来源是自己购买的发布会门票。总体感觉是…美哭了…非常非常精致。… [http://zhi.hu/5h2M](http://zhi.hu/5h2M)（分享自知乎）
    

### 待解决的问题

*   单引号能保存吗？会导致什么后果？
    
    请按照截图进行实验。且听下回分解。
    

# 学会了本章，你的收入应达到

# 学会了本章，你的收入应达到

学会了本章，你的月薪应达到