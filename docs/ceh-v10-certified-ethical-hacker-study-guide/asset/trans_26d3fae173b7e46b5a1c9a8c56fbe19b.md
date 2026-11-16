

用于创建该哈希的明文。所有耗时的工作都在你需要破解密码之前很久就完成了。当然，这里存在权衡。预计算哈希意味着你需要将它们存储在某个地方。

彩虹表是存储的预计算哈希。彩虹表并不像哈希与密码之间简单映射那样直截了当。彩虹表以链的形式存储，以限制存储的明文密码数量。在某些情况下，如果明文没有直接存储，仍可以推断出来。有许多工具可以用来从这些表中查找密码，但首先我们需要这些表。Rainbow Crack 项目有一个用于查找密码的工具，还有一个用于创建彩虹表的工具。这个创建工具不用于从字典生成哈希。相反，它将根据提供的约束从所有可能的密码值生成一个哈希。在以下代码中，你将看到使用 rtgen 生成彩虹表的示例。

### 使用 rtgen 生成彩虹表

```
root@quiche:~# rtgen md5 loweralpha-numeric 5 8 0 3800 33554432 0
rainbow table md5_loweralpha-numeric#5-8_0_3800x33554432_0.rt parameters
hash algorithm: md5
hash length: 16
charset name: loweralpha-numeric
charset data: abcdefghijklmnopqrstuvwxyz0123456789
charset data in hex: 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 70 71 72 73
74 75 76 77 78 79 7a 30 31 32 33 34 35 36 37 38 39
charset length: 36
plaintext length range: 5 - 8
reduce offset: 0x00000000
plaintext total: 2901711320064
```

```
sequential starting point begin from 0 (0x0000000000000000)
generating...
131072 of 33554432 rainbow chains generated (0 m 28.5 s)
262144 of 33554432 rainbow chains generated (0 m 28.5 s)
393216 of 33554432 rainbow chains generated (0 m 28.5 s)
524288 of 33554432 rainbow chains generated (0 m 28.5 s)
655360 of 33554432 rainbow chains generated (0 m 28.5 s)
786432 of 33554432 rainbow chains generated (0 m 28.5 s)
917504 of 33554432 rainbow chains generated (0 m 28.5 s)
1048576 of 33554432 rainbow chains generated (0 m 28.5 s)
1179648 of 33554432 rainbow chains generated (0 m 28.5 s)
1310720 of 33554432 rainbow chains generated (0 m 28.5 s)
1441792 of 33554432 rainbow chains generated (0 m 28.5 s)
1572864 of 33554432 rainbow chains generated (0 m 28.6 s)
```

你会注意到传递给 rtgen 的参数。第一个是使用的哈希算法。在此示例中，它是消息摘要算法 5（MD5），一种常用的哈希算法。彩虹表中使用的哈希算法必须与密码文件中使用的算法匹配。如果它们不匹配，你将找不到哈希或密码。下一个参数是用于生成密码的字符集。我们使用小写字母以及数字。这样每个位置就有 36 个可能的字符。这会产生 36^n 个值，其中 n 是位置数。如果我们试图生成四字符密码，则会有 36*36*36*36 个可能的密码，即 1,679,616——近 200 万个四字符密码。

我们需要告诉 rtgen 我们希望密码的长度。命令行上的接下来两个值是最小密码长度和最大密码长度。出于我们的目的，我们生成的密码长度在五到八个字符之间。这意味着总共需要 36^5 + 36^6 + 36^7 + 36^8 个密码。这使得密码数量为 2.8 * 10^12。很显然，我们考虑的密码长度越多，就需要生成的密码越多，输出也就越大。

下一个值选择一个内部于 rtgen 的函数，用于将哈希映射到明文。这被称为缩减函数。接下来两个值与彩虹链有关。第一个是生成的链的数量。生成的链越多，存储在磁盘上的数据就越多，因为这意味着存储了更多的明文。之后的值是要生成的链的数量。彩虹表是一组链的集合，每个链为 16 字节。最后，最后一个值与将大型彩虹表存储在多个文件中的能力相关。要做到这一点，保持所有其他参数相同，并更改此值。

一旦我们有了彩虹表，就可以将我们拥有的密码文件与之核对。你可以在下一个代码清单中看到 rcrack 程序的运行示例。此次运行没有结果，因为使用的彩虹表非常有限。要拥有足够的彩虹表来真正破解密码，我们至少需要千兆字节，甚至太兆字节或更多。这里有两个参数。第一个是彩虹表的位置，此处为点（.），表示本地目录。第二个告诉 rcrack 所提供的文件是一组 LAN Man 哈希。

### 使用彩虹表运行 rcrack

```
root@quiche:~# rcrack . -lm passwords.txt
1 rainbow tables found

no hash found

result
```

关于彩虹表位置需要注意的一点是，它们实际上并不存储在运行 rcrack 的目录中。相反，彩虹表存储在运行此操作的 Kali 系统上的 /usr/share/rainbowcrack 目录中。当你运行 rtgen 时，表会存储在该目录，因为二进制文件位于那里。在此示例中，当前目录是 rcrack 所在的目录，而不是用户所在的目录。

## 客户端漏洞

当然，监听服务并不是获得系统访问权限的唯一方式。事实上，它们不一定是最佳方式。这在一定程度上取决于作为攻击者你在寻找什么。攻击者可能在寻找计算和网络资源。结果可能是任何系统都可以。这意味着系统越多越好，而且通常桌面系统比服务器更多。用户也通常是进入系统的更容易途径。这可能需要客户端漏洞，即存在于桌面上且在没有客户端交互的情况下不会暴露给外部世界的漏洞。例如，邮件客户端中可能存在一个漏洞。攻击者可以触发该漏洞，不是通过探测桌面系统的外部，而是通过向受害者发送电子邮件。客户端系统上的受害者打开电子邮件，漏洞被触发，攻击者获得对系统的访问权限。

Web 浏览器是便捷的攻击载体，原因有多种。其一是它们是最常用的应用程序之一。并非每个人都还在使用 Outlook 或 Thunderbird 等电子邮件客户端，尽管电子邮件客户端曾经非常常用。许多人使用 Web 浏览器来访问他们的电子邮件。浏览器被用于如此多的其他常见功能，以至于对某些人来说，它可能是他们唯一使用的应用程序。可以考虑 Chrome OS 及其运行的 Chromebook 作为示例。Chrome OS 将浏览器用作用户界面。由于 Chrome OS 最初是作为瘦 Web 客户端诞生的，因此你在 Chrome OS 上运行的大多数应用程序都在浏览器上下文中运行。

使浏览器成为绝佳目标的另一个因素是，使用的浏览器种类并不多。来自几个不同来源的数据显示，Chrome 是全球使用最广泛的浏览器，遥遥领先。远远落后于其后的是 Internet Explorer、Firefox、Safari 和 Edge 等浏览器。因此，如果你能找到影响 Windows 上 Chrome 的漏洞，你就能大赚一笔。问题是，Google 在查找和修复漏洞方面往往非常勤勉。Metasploit 中没有针对 Chrome 的漏洞。但是，其他浏览器确实有相关的模块。一个示例是 MacOS 上 Firefox 中的一个漏洞。你可以在此处看到在 msfconsole 中加载此模块。

### msfconsole 中的 Firefox 漏洞利用模块

```
msf > use exploit/osx/browser/mozilla_mchannel
msf exploit(osx/browser/mozilla_mchannel) > show options
```

模块选项 (exploit/osx/browser/mozilla_mchannel)：

| 名称 | 当前设置 | 必需 | 描述 |
| :--- | :--- | :--- | :--- |
| SRVHOST | 0.0.0.0 | 是 | 要监听的本地主机。这必须是本地计算机上的地址或 0.0.0.0 |
| SRVPORT | 8080 | 是 | 要监听的本地端口。 |
| SSL | false | 否 | 为传入连接协商 SSL |

