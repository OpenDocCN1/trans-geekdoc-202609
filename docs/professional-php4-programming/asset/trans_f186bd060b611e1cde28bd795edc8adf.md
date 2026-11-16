

既然我们已经了解了日志的一般格式，就需要以编程方式从中提取信息。这可以通过先删除任何不需要的格式字符，然后对字符串进行标记化来实现。幸运的是，PHP 提供了一些函数，让我们可以轻松地完成此操作。以下函数接收一行日志，提取信息并以关联数组的形式返回。

函数的第一行会从传递给函数的行中删除任何不需要的格式字符，例如 ]、[ 和 "。这样可以在函数中更轻松地对其进行标记化和处理，因为我们不再需要关心不包含任何信息的字符：

```
function tokenizeLine($line)
{
    $line = preg_replace("/[\[\]\"\\\\]/", "", $line);
}
```

然后，我们使用 PHP 函数 strtok 对数组进行标记化，以返回直到下一个空格之前的所有字符。这是使用 while 循环来检查是否还有需要检索的标记：

```
$token = strtok($line, " ");
while ($token) {
    $token_array[] = $token;
    $token = strtok(" ");
}
$return_array['IP'] = $token_array[0];
```

上面的代码行用于检查用户是否提供了用户名。如果提供了，下一行会将此用户名分配给返回数组；否则，则不设置：

```
if ((!strstr($token_array[2], "-")) and (strlen($token_array[2]) > 1)) {
    $return_array['UserName'] = $token_array[2];
}
```

最好能够将日期和时间分开，因为目前它们都保存在 $token_array[3] 变量中。下面的正则表达式可以实现这一点。它会匹配直到第一个 ":" 之前的所有内容（即日期），然后匹配直到下一个空格之前的所有内容（即时间）。这些内容分别存储在 $date_array[1] 和 $date_array[2] 中。然后，我们将它们分配到 $return_array 变量中的正确位置：

```
preg_match("/([^:]+):([0-9:]+)/", $token_array[3], $date_array);
$return_array['Date'] = $date_array[1];
$return_array['Time'] = $date_array[2];
```

下面的代码行将所有剩余数据放入返回数组，然后从函数中返回 $return_array 的内容：

```
$return_array['TimeZone'] = $token_array[4];
$return_array['RequestMethod'] = $token_array[5];
$return_array['Resource'] = $token_array[6];
$return_array['HTTPVersion'] = $token_array[7];
$return_array['StatusCode'] = $token_array[8];
$return_array['BytesSent'] = $token_array[9];
return $return_array;
}
```

## 日志分析器脚本

我们现在需要编写脚本的其余部分。我们的示例将简单地记录每种状态码的数量，并将其发送给管理员。如果你使用此脚本，可能还希望包含其他统计信息：

```
<?php
set_time_limit(0); // Force this script to run without a time limit

/* -- Variables used in the script -- */
$logfile = "./access.log";
$admin_email = "admin@localhost";

function tokenizeLine($line)
{
    $line = preg_replace("/[\[\]\"\\\\]/", "", $line);
    $token = strtok($line, " ");
    while ($token) {
        $token_array[] = $token;
        $token = strtok(" ");
    }
    $return_array['IP'] = $token_array[0];

    if ((!strstr($token_array[2], "-")) and (strlen($token_array[2]) > 1)) {
        $return_array['UserName'] = $token_array[2];
    }

    preg_match("/([^:]+):([0-9:]+)/", $token_array[3], $date_array);
    $return_array['Date'] = $date_array[1];
    $return_array['Time'] = $date_array[2];
    $return_array['TimeZone'] = $token_array[4];
    $return_array['RequestMethod'] = $token_array[5];
    $return_array['Resource'] = $token_array[6];
    $return_array['HTTPVersion'] = $token_array[7];
    $return_array['StatusCode'] = $token_array[8];
    $return_array['BytesSent'] = $token_array[9];
    return $return_array;
}
```

脚本将日志文件的每一行读入名为 $file_contents 的数组中：

```
$file_contents = file($logfile);
```

然后它会遍历该数组，将每一行传递给 tokenizeLine() 函数，并为每个状态码递增计数器：

```
foreach ($file_contents as $line) {
    $info_array = tokenizeLine($line);
    $status_code[$info_array['StatusCode']]++;
}
```

随后脚本会创建电子邮件的文本，并最终将其发送给管理员：

```
$email = "Summary of codes for todays logs\n\nCode\tCount\n";
foreach ($status_code as $code => $count) {
    $email .= "$code:\t$count\n";
}

mail($admin_email, "Summary of weblogs", $email);
```

为了方便使用，我们希望自动化运行此脚本，使其每天午夜运行。在 Linux 下，我们使用 cron；在 Windows NT/2000 下，我们使用 AT 命令。我将先介绍 cron。

### cron

cron 是在 Linux/UNIX 下自动执行任务的一种方式。cron 守护进程每分钟会检查每个用户的 crontab 文件，看是否需要执行任何操作。系统管理员（或任何用户）都可以使用它来自动执行任务，例如运行上述脚本。

一个 crontab 条目有六个字段。前五个字段用于指定操作应执行的时间；最后一个字段指定 cron 守护进程应运行的命令。每个时间字段都指定了一个值，必须与当前系统时间匹配，命令才会运行。它们还可以包含通配符 *，以便在所有其他字段匹配时的任何时间运行命令。

第一个字段指定命令应在每小时多少分运行（0-59）。第二个字段指定命令应在一天中的哪个小时运行（0-23），第三个字段指定一个月中的哪一天（1-31），第四个字段指定一年中的哪个月（1-12），第五个字段指定一周中的哪一天（0-6，其中 0 表示星期日）。你可以在 http://hoth.stsci.edu/man/man1/crontab.html 上找到关于 crontab 命令的更详细信息。

我们需要脚本每天午夜运行。如果脚本名为 mail_stats.php 并位于目录 /home/jmoore/ 中，则以下 crontab 条目可以实现此目的。如果你需要编辑 crontab 文件，可以在终端中输入 crontab：

```
0 0 * * * /usr/local/bin/php -q /home/jmoore/mail_stats.php
```

这告诉 cron 守护进程，当任何月份的任何一天的小时和分钟都等于 0 时，应运行命令 /usr/local/bin/php -q mail_stats.php。

> 在 Linux/UNIX shell 下，你可以通过为脚本设置正确的权限来使脚本本身可执行（通常通过运行命令 chmod a+x mail_stats.php 来实现，但如果你不确定如何操作，请查看系统文档）。然后，你可以将 shell 应该用来执行脚本的命令作为脚本的第一行添加进去。例如 #!/usr/local/bin/php -q。这告诉 shell 使用 /usr/local/bin/php 处于的可执行文件和 -q 标志来执行脚本。

### AT

AT 命令是 Windows NT 上 Linux cron 的等效命令。它允许你在 Windows 2000、XP 和 NT 下自动执行命令。为此，你需要在 AT 列表中创建一个条目。这是在命令行中完成的，命令的形式如下：

```
at [\\computername] time [/interactive] [/every:date[,...] | /next:date[,...]]
command
```

我们希望每天午夜运行命令 php -q c:\\mail_stats.php（假设 mail_stats.php 脚本位于 C: 驱动器的根目录下）。可以使用以下命令实现：

```
AT 00:00 /every:M,T,W,Th,F,S,Su php -q c:\\mail_stats.php
```

这将在每个星期一、星期二、星期三、星期四、星期五、星期六和星期日的午夜执行命令 php -q c:\\mail_stats.php。

### Windows 计划任务管理器

Windows 95/98/ME 没有 crontab/AT 机制。相反，我们有计划任务管理器。可以通过“开始 | 程序 | 附件 | 系统工具 | 计划任务”访问向导。

首先，你需要创建一个名为（例如）C:\\CHECKLOG.BAT 的批处理文件。我们将使用此批处理文件来执行脚本。它只需要一行内容，假设你已设置好路径变量，请向其中添加以下行：

```
php -q c:\\mail_stats.php
```

保存批处理文件后，进入计划任务管理器，通过双击“添加计划任务”图标来添加新任务。在向导中单击“下一步”按钮，然后通过单击“浏览”按钮并浏览到我们刚刚创建的批处理文件来指定它。你可以为任务指定一个名称（例如 CheckLogTask）并指定其运行的时间和频率。但是，使用计划任务管理器有一个相当重大的限制。每个任务只能有一个时间设置。要解决此问题，你可以创建多个任务来访问同一个快捷方式，并为它们指定不同的名称（CheckLogTask1、CheckLogTask2、CheckLogTask3，依此类推）。

### 接受命令行参数

上述脚本工作良好，但如果你有许多不同虚拟主机的访问日志，并且每个日志都需要发送给不同的管理员，会发生什么呢？一种方法是为每个日志准备一份脚本副本，并更改每个不同日志和管理员的变量。一种更高效的方法是接受命令行参数，这样你就可以使用 mail_stats.php <logfile> <administrators_email> 调用脚本。

PHP 允许你像这样将命令行参数传递给脚本。执行此操作时，PHP 会设置两个变量：$argc 包含传递给脚本的命令行参数的数量，$argv[] 是传递给脚本的实际参数的数组。

