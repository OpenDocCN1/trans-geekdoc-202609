

# 网站（继续）

- 开源项目, 11
- PEAR, 662
- PHP, 13
- PHPBuilder.com, 593
- phpMyAdmin, 109
- P2P 邮件列表, 5
- 正则表达式, 559
- 第三方主机, 660
- Webalzer, 579
- WebTrends, 580
- Wrox, 4, 593
- W3 Security FAQ, 55, 551
- Webalzer, 579
- WebTrends, 580–581, 582
- 欢迎消息，添加, 66–68
- WHERE 子句 (SELECT 命令, MySQL), 102–104
- while 命令 (PHP), 79–83
- Windows
- htaccess 安装, 319
- 安装 AMP, 带有 669–671
- 工作流应用及实现确认, 300
- Wrox 网站, 4, 593
- W3 Security FAQ 网站, 55, 551
- W3C 网站, 138

# Y

- year（长度）字段类型 (MySQL), 90

# Z

- Zend Technologies, Ltd., 13
- Zero Form, 245

# Wrox::Beginning PHP, MySQL Web Development

# 章节页面详情

# 打印日期

（整本书 $S-mail 是一个无效的变量名）在编辑过程中，$Smail 被更改为了 $S-mail，这是一个无效的变量名。该变量名在书中多次出现。读者需要在所有适用之处将 $S-mail 替换为 $Smail。

6/14/04

74 语法错误纠正
在第 74 页底部的“foreach Constructs”部分，代码第 6 行目前显示为：($flavor, as $currentvalue) 应修改为：($flavor as $currentvalue)

6/16/04

96 createmovie.php 代码中的致命错误
有些人在第 96 页的 createmovie.php 中遇到了错误，这是由于使用了已弃用的代码导致的。虽然这并不总是导致错误，但如果你遇到了致命错误，可以使用此修复：INSTEAD OF mysql_create_db(wiley); USE $query = mysql_query("CREATE DATABASE wiley") or die(mysql_errorn));

6/14/04

491 checkout3.php 代码第 77 行错误
代码第 77 行：行尾缺少一个逗号。请改为 "shipping",

6/16/04

493 checkout3.php 代码第 179 行错误
第 179 行的代码为 $message .ne $quan，应为 $message = $qty;

6/16/04

493 checkout3.php 代码第 189 行错误
第 189 行的代码为 $extprice = number_format($price * $quan, 2);，应为 $extprice = number_format($price * $quan, 2);

6/16/04

495 checkout3.php 代码第 288 行错误
第 288 行的代码为 echo $quan;，应为 echo $qty;

6/16/04

495 checkout3.php 代码第 298 行错误
第 298 行的代码为 $extprice = number_format($price * $quan, 2);，应为 $extprice = number_format($price * $quan, 2);

6/16/04

http://www.wrox.com/WileyCDA/WroxTitle/productCd-0764557440,descCd-view_errata.html?print... 7/23/2004
