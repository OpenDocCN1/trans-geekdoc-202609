
`echo "Please enter your state: ";`

`$state = trim(fgets(STDIN));`

`echo "Please enter your zip code: ";`

`$zip = trim(fgets(STDIN));`

`echo "Please enter your phone number: ";`

`$phone = trim(fgets(STDIN));`

`echo "Please enter your email address: ";`

`$email = trim(fgets(STDIN));`

`echo "Please enter a name for this signature: ";`

`$sig = trim(fgets(STDIN));`

`$data = "$name\n$address\n$city\n$state\n$zip\n$phone\n$email\n$sig\n";`

`$signature = fopen($sig, "w") or die("Could not open file for writing\n");`

`fwrite($signature, $data) or die("Failed writing data\n");`

`fclose($signature);`

`echo "Your signature file is ready now.\n";`

`?>`

### 示例运行

```bash
$ ./signature_generator.php

Welcome to the signature file generator.

Please enter your full name: John Brown

Please enter your street address: 1234 Anystreet

Please enter your city: Anywhere

Please enter your state: CA

Please enter your zip code: 95123

Please enter your phone number: 415-123-4567

Please enter your email address: john@example.com

Please enter a name for this signature: normal

Your signature file is ready now.

$ cat name

--

John Brown

1234 Anystreet

Anywhere, CA 95123

415-123-4567

john@example.com

$
```

> UNIX `cat` 命令在终端窗口中显示文件内容——在本例中，即名为 `normal` 的签名文件。

## 调度 PHP 命令行脚本

由于命令行脚本不需要 Web 浏览器的请求即可开始运行，因此可以在每天或每周的预定时间进行调度。调度脚本有许多用途，包括：

- 备份数据
- 定期清理数据库表和日志文件
- 定期发送电子邮件，例如新闻通讯或发送给用户或管理员
- 获取已发布的数据，如 RSS 馈

### 在 Windows 上调度命令行 PHP 脚本

在 Windows 上调度命令行 PHP 脚本非常简单：

1. 在 PHP 脚本所在的文件夹中为你的脚本创建一个批处理文件，如之前在“运行命令行 PHP 脚本”中所描述的。
2. 点击开始菜单并选择“控制面板”。
3. 在控制面板窗口中，双击“任务计划”。
4. 双击“创建基本任务”。
5. 在向导中点击“下一步”，然后点击“浏览”。
6. 选择你在第1步中创建的批处理文件并点击“打开”。
7. 选择每天、每周、每月、仅一次、计算机启动时或登录时执行任务。点击“下一步”。
8. 如果选择每天、每周或每月，请选择任务的开始时间和频率。点击“下一步”。
9. 根据提示输入密码。点击“下一步”。
10. 任务已调度。点击“完成”关闭向导。

### 在类 Unix 操作系统中调度脚本

在类 Unix 操作系统（包括 Mac OS 和 Ubuntu）中调度脚本需要编辑一个名为 `crontab` 的文件。要执行此操作，请以运行调度任务的用户身份登录，然后输入：

```bash
crontab -e
```
