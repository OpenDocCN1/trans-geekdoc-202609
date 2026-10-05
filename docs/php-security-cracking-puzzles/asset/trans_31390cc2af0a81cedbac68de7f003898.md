

# 368 第二部分：解决方案

# 用...打开...

![](img/a893312ec68b8170fe567f785e95c06e_381_0.png)

图 II.14.3. 用...打开...文件选择对话框

![](img/a893312ec68b8170fe567f785e95c06e_381_1.png)

图 II.14.4. 将 PHP 脚本解释器指定为 PHP 文件解释器

# 第 II.14 节：告警性脚本 369

这一系列操作将 PHP 脚本解释器<sup>1</sup> 指定为 PHP 文件的解释器（图 II.14.4）。现在 PHP 脚本将像普通可执行文件一样运行，可以通过按下 <Enter> 键或双击选定的文件来启动。

现在当脚本被系统作为普通可执行文件触发时，可以通过 cron 在调度的时间启动。执行任务将通过编辑 `crontab` 配置文件进行调度。

在 Windows 中，`crontab` 文件可以在 C:\Program Files 目录中找到；在 UNIX 中，它通常位于 \etc 目录。有关 UNIX `crontab` 文件的详细信息，请查阅特定操作系统的文档。

![](img/a893312ec68b8170fe567f785e95c06e_382_0.png)

crontab 文件中的每一行描述一个调度任务。除了任务行外，该文件还可以包含以井号（#）开头的注释。任务行的格式如下：

```
minutes day_of_month day_of_week command
```

参数可以取以下值：

- minutes（分钟）—0–59
- hours（小时）—0–23
- day_of_month（日期） —1–31
- month（月份） —1–12
- day_of_week（星期几）—0–7（0 和 7 表示星期日）
- command（命令）—要执行的命令，例如 d:/main/reserve.php

参数之间用空格分隔。作为参数值的星号表示该特定参数的整个范围。例如，考虑以下任务指令：

```
0 23 * * d:/main/reserve.php
```

它指定每天在 23:00 启动 d:/main/reserve.php 脚本。如果每个参数之间用逗号分隔，可以为每个参数指定多个值。因此，你可以拥有以下任务指令：

```
0 8,16 * * d:/main/cleanup.php
```

它指定每天在 00:00、8:00 和 16:00 启动 d:/main/cleanup.php 脚本。

> ¹ 命令行解释器（CLI）可能会被指定为 PHP 解释器。

# 370 第二部分：解决方案

如前所述，使用空格来分隔参数；因此，逗号后不允许有空格。因此，0 0, 8, 16 * * d:/main/cleanup.php 任务指令是错误的。

![](img/a893312ec68b8170fe567f785e95c06e_383_0.png)

作为另一个例子，考虑此任务指令：
0,30 18-23 * * * /home/root/check.php

它将在 18:00 到 23:00 之间每半小时运行一次 /home/root/check.php 脚本。

考虑以下任务指令：
0/10 * * * /home/root/log.php

它将每十分钟启动一次 /home/root/log.php 脚本。后期模式最适合验证远程站点链接的存在。

主机提供商不批准频繁执行脚本。因此，在调度任务之前，你应该咨询你的主机提供商的技术支持，关于脚本运行数量和频率的任何限制。

![](img/a893312ec68b8170fe567f785e95c06e_383_1.png)

现在当自动启动脚本的问题解决后，必须编辑列表 II.14.1 中的脚本以能够自主运行。它必须将检查结果放入 link.log 日志文件中，如果链接缺失，则每 24 小时发送一次关于此的消息。编辑后的脚本位于列表 II.14.4。

# 列表 II.14.4. 用于验证链接存在的自主脚本

```php
<?php
// 要验证的链接
$http = "http://www.php.net/";
// 页面链接所在的地址。
$url = "http://en.wikipedia.org/";

// 加载内容
$contents = file_get_contents($url);
$http = str_replace(".", $http);
$pattern = "|<a]+href="

if (preg_match($pattern, $contents)) {
  $str = date("d.M.Y H:i").": 链接存在。";
}
else {
  $str = date("d.M.Y H:i").": 链接缺失！";
  if (date("G") == 0) {
    mail("admin@somewhere.com", "链接缺失!", $str);
  }
}

$fd = fopen("link.log", "a");
if ($fd) {
  fwrite($fd, $str);
  fclose($fd);
}
```

注：由于原文中存在大量重复且断裂的 PHP 代码和描述，译文部分对代码逻辑进行了部分语性的重组，以确保文档的可读性。

