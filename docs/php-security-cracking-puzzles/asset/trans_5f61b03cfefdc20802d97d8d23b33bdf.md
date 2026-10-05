

```
// 在 archive.tar 文件中
$fd = fopen("archive.tar", "w");
fwrite($fd, implode("", $arr));
close($fd);
```

列表 II15.6 使用 `gzfile()` 函数，该函数类似于 `file()` 函数。`gzfile()` 函数返回一个数组，其中每个元素包含解压后的 GZ 文件的一行。数组元素使用 `implode()` 函数连接成字符串，从而生成原始的 `archive.tar` 文件。

## II15.4. 数据缓冲

解决此问题的一种简单方法是使用缓冲。通过 `ob_start()` 函数的帮助对输出进行缓冲，该函数告诉 PHP 解释器不在浏览器窗口中显示输出，而是将其存储在内部缓冲区中。可以使用 `ob_get_contents()` 函数获取缓冲区的内容。使用 `ob_end_clean()` 函数清除缓冲区。当缓冲区成功清除时，该函数返回 `true`，否则返回 `false`。在随机数字序列中将所有数字 1 加粗的任务可以像列表 II15.7 所示解决。

列表 II15.7. 高亮所有数字 1

```php
<?php
// 将所有输出重定向到缓冲区
ob_start();
// 构建页面
for($i = 0; $i < 1000; $i++) echo rand().
```

384 第二部分：解决方案

执行列表 II.15.7 中的脚本得到的结果可能如图 II.15.2 所示。

![](img/a893312ec68b8170fe567f785e95c06e_397_0.png)

**图 II.15.2.** 在随机数字序列中将所有数字 1 加粗。

## CD 盘说明

此 CD 盘的内容如下：

- `Readme.txt` 文件包含 CD-ROM 的说明。
- `Installing Apache, PHP, MySQL.htm` 文件包含在本地主机上安装 Apache、PHP 和 MySQL 组合的简要说明。
- `SCRIPTS` 目录包含书中的所有示例，并附带了现用的解决方案。其文件夹结构如下：

| 文件夹 | 描述 | 章节 |
|---|---|---|
| 1 | 第 1 章答案 | 1 |
| 2 | 第 2 章答案 | 2 |
| 3 | 第 3 章答案 | 3 |
| 4 | 第 4 章答案 | 4 |
| 5 | 第 5 章答案 | 5 |
| 6 | 第 6 章答案 | 6 |
| 7 | 第 7 章答案 | 7 |
| 8 | 第 8 章答案 | 8 |
| 9 | 第 9 章答案 | 9 |
| 10 | 第 10 章答案 | 10 |
| 11 | 第 11 章答案 | 11 |
| 12 | 第 12 章答案 | 12 |
| 13 | 第 13 章答案 | 13 |
| 14 | 第 14 章答案 | 14 |
| 15 | 第 15 章答案 | 15 |

## 索引

$ _SERVER['HTTP_USER_AGENT'], 257

C

foreach 循环, 102

层叠样式表, 6

格式:

Rich Site Summary, 68

命令:

前向代码, 373

chmod, 366

FTP, 77

dir, 99

函数:

find, 359

exec(), 88

常量:

feof(), 323

FTP_FAILED, 317

fgetrs(), 295, 323

FTP_FINISHED, 317

file_get_contents(), 294

FTP_MOREDATA, 317

filetime(), 374

Cookies, 46, 64

fileinode(), 321

禁用, 48

fsockopen(), 321, 343

窃取, 365

ftp_cdup(), 317

Cron 服务, 365

ftp_chdir(), 316

跨站脚本, 246

ftp_chmod(), 320

CSS, 6

ftp_close(), 313

自定义会话, 46

ftp_connect(), 312

机制, 232

ftp_login(), 312

D

ftp_nb_continue(), 317

数据库转储, 43

ftp_nb_get(), 318

指令:

ftp_nlist(), 316

memory_limit, 295

ftp_pwd(), 316

下拉列表, 40

E

ftp_rawlist(), 314

电子邮件, 82

ftp_systype(), 314

relay, 83

get_code(), 371

欧洲中央银行, 75, 304

get_content(), 232

gethostbyaddr(), 350

F

gethostbyname(), 349

文件:

gzfile(), 383

php.ini, 295

gzopen(), 382

文件传输协议, 77

highlight_file(), 17

highlight_string(), 17

htmlspecialchars(), 248

implode(), 383

INET_ATON(), 339

INET_NOA(), 339

mail(), 331

.htaccess, 61

_once 后缀, 107

<

<br> 标签, 98

<tr>, 104

A

访问权限, 360, 366

对齐, 6

美国互联网数字注册局, 84

Apache, 77

APNIC, 348

存档:

tar.gz, 363

tar.gz(), 89

ARIN, 84

亚太网络中心, 348

认证, 57

AUTO_INCREMENT, 30

B

反引号, 97

数据缓冲, 93

索引 387

mysql_query() 函数, 44

ob_end_clean(), 383

ob_get_contents(), 383

ob_start(), 383

parse_url(), 373

passsthru(), 88

printf(), 101

scan_dir(), 374

serialize(), 111, 380

session_id(), 231

session_set_handler(), 46, 232

session_start(), 110, 236

setcookie(), 111, 240

stripslashes(), 111

str(), 324

system(), 88

unserialize(), 111

urlencode(), 329

whois(), 346

P

页面访问代码, 372

参数, 331

errno, 321

host, 312

message, 331

port, 312

subject, 331

username, 313

I

include_once, 107

Inode, 89

J

JavaScript, 239

K

关键字, 52

L

链接标识符, 312

Linux, 60

G

GET 方法, 108

Gzip 工具, 363

H

头部:

accept, 298

Cc, 337

charset, 337

Connection, 326

Content-Language, 327

Content-Length, 328

Content-Type, 328

Date, 327

Last-Modified, 327

Server, 327

Transfer-Encoding, 328

User-Agent, 298

M

群发, 336

防止, 338

主键, 30

MD5, 59

Modifier:

i, 298

s, 298

监控, 91

Q

引号, 6

R

引用服务器, 346

正则表达式, 12

require_once, 107

Réseaux 中心, 384

RFC 2616, 79

RSS, 68

S

搜索引擎, 52

搜索模式:

贪婪, 298

统计:

字符串函数, 5

切换变量, 92

SQL 注入, 65

SSL, 56

会话, 46

Sockets, 108

会话式协议, 56

Sessions, 45

User , 61

USER_AGENT, 52

User-Agent 头部, 258

V

验证链接, 91

W

Web 应用, 15, 36

Whois 服务, 84

Windows XP, 55, 98

X

XML 文件, 68

XSS, 246

## PHP 安全与破解

## 谜题

本书专注于破解和保护使用 PHP 编写的 Web 应用，还考虑了相关的 Web 编程技术（HTML、Cookies、JavaScript）、应用协议（HTTP、SMTP）、SQL 查询语言以及 Apache Web 服务器的破解。由于这些技术只能通过实践获得，因此书分为两个部分：一部分涵盖问题（谜题），另一部分致力于解决方案。许多保护应用程序不被黑客攻击的 Web 程序员的主要障碍是他们的思维与黑客不同，本书让读者进入黑客的角度并理解他们使用的技术。

Web 应用解决方案

![](img/a893312ec68b8170fe567f785e95c06e_403_0.png)

关于作者

Maxim Kulmikov 是物理学、数学和量子力学 42 本书的合作者。
Igor Simdyanov 是软件开发、光化学和分子量子力学 42 本书的合作者。

随附的 CD-ROM 包含了书中的所有示例并附带现用的解决方案。

类别：Web 编程
级别：中级到高级

ISBN 1-931769-57-5
U.S. $39.95 Canada $53.95

![](img/a893312ec68b8170fe567f785e95c06e_403_1.png)

A-LIST, LLC
http://www.alistpublishing.com
所有商标和和服务标记均为其所有者的财产。
美国制造。

