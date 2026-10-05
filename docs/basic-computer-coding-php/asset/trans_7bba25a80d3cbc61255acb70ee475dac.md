

## 基础计算机编程：PHP

```php
doc_root = [DIR]
```

如果你正在使用 Apache，你已经在 httpd.conf 中为此服务器或虚拟主机设置了文档根。如果你正在使用安全模式（safe mode），或者只想在网站的部分启用 PHP（例如，仅在 Web 根目录的一个子目录下），请在此处设置此值。

```php
file_uploads = [on/off]
```

如果你将使用 PHP 脚本上传文件，请开启此标志位。

```php
upload_tmp_dir = [DIR]
```

除非你理解 HTTP 上传的影响，否则不要取消此行的注释！

```php
session.save-handler = files
```

除非少数情况下，否则你不会希望更改此设置。所以请不要动它。

```php
ignore_user_abort = [On/Off]
```

此设置控制网站访问者点击浏览器“停止”按钮时会发生什么。默认值为 On，这意味着脚本将继续运行完成或超时。如果将设置改为 Off，脚本将仅在模块模式下工作，而不在 CGI 模式下。

```php
mysql.default_host = hostname
```

在未指定其他主机的情况下，连接数据库服务器时使用的默认服务器主机名。

```php
mysql.default_user = username
```

在未指定其他名称的情况下，连接数据库服务器时使用的默认用户名。

```php
mysql.default_password = password
```

在未指定其他密码的情况下，连接数据库服务器时使用的默认密码。

## 1.2.4 Windows IIS 配置

要在你的 Windows 机器上配置 IIS，可以参考随 IIS 一起提供的 IIS 参考手册。

## 基础计算机编程：PHP

## 榜样

## 拉斯马斯·莱德多夫 (Rasmus Lerdorf)

Rasmus Lerdorf（1968 年 11 月 22 日出生）是一位丹麦裔加拿大程序员。他创建了 PHP 脚本语言，编写了该语言的前两个版本，并参与了由 Jim Winstead（后创建了 blo.gs）、Stig Bakken、Shane Caraveo、Andi Gutmans 和 Zeev Suraski 等一组人员领导的后续版本开发。他继续为该项目做出贡献。

### 早年生活与教育

Lerdorf 出于格陵兰岛的迪斯科岛，于 1980 年移往丹麦，1983 年移往安大略省的金市。他于 1988 年毕业于金市中学，并于 1993 年毕业于滑铁卢大学，获得系统设计工程应用学士学位。他贡献了 Apache HTTP Server 并为 mSQL DBMS 添加了 LIMIT 子句。这种 LIMIT 子句变体已经在大型机关系型数据库管理系统（如运行在 VAX/VMS 上的 Oracle Rdb，来自数字设备公司）中存在了十年，但显然尚未被新兴的 PC 数据库选中。它后来被其他几个兼容 SQL 的 DBMS 采用。他于 1995 年发布了第一版本的 PHP。

### 职业生涯

2002 年 9 月至 2009 年 11 月，Lerdorf 在 Yahoo! Inc 担任基础设施架构工程师。2010 年，他加入 WePay 以开发他们的应用程序接口。在整个 2011 年，他担任多家初创公司的流动顾问。2012 年 2 月 22 日，他在 Twitter 上宣布他加入了 Etsy。2013 年 7 月，Rasmus 加入 Jelastic 担任高级顾问，帮助他们创建新技术。

### PHP 简介

Lerdorf 是全球范围内开源会议的频繁演讲者。在 OSCMS 2007 的主旨演讲中，他展示了当年会议上代表的每个项目中的安全漏洞。

Lerdorf 还参加了 2017 年的 WeAreDevelopers 会，发表了关于 PHP 历史和 2017 年新 PHP 7 的演讲。

### 奖项

2003 年，Lerdorf 被《麻省理工评论》TR100 评为世界 35 岁以下顶级 100 位创新者之一。

## 总结

- PHP 代表“超文本处理器”（Hypertext Preprocessor）（如果你能理解它的意思，这是一个递归缩写）。PHP 是一种嵌入 HTML 的 Web 脚本语言。这意味着 PHP 代码可以插入到 Web 页面的 HTML 中。

## PHP 语言基础

> ""PHP 是由无能的业余人员实施并创造的小恶，而 Perl 则是由技术高超但心态扭曲的专业人士实施的巨大且阴险的恶。",
—Jon·Ribbons

### 学习目标

学习本章后，你将能够：

- 讨论数据类型
- 描述 PHP 运算符
- 解释控制流语句

