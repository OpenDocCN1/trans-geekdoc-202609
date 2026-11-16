
都在该邮件列表上。不过，此函数要求服务器支持增强 SMTP（ESMTP）。您可以通过检查服务器是否接受 EHLO 来测试其是否支持 ESMTP，EHLO 是 HELO 的 ESMTP 版本。

## 基于 Web 的枚举

就枚举而言，在 Web 服务器上可能有几个我们想要查看的事项。第一个是识别网站中可用的目录。做这件事有很多不同的方法，尤其是如果您可以访问 Web 应用程序测试工具。即使您没有或不熟悉使用它们，也有简单的检查方法。您只需要一个可以提供潜在目录名称的单词列表，以及一个可以根据这些单词向 Web 服务器发出请求的工具——将每个单词附加到基础统一资源定位符（URL）。在此，您可以看到 dirb 程序的使用，它包含自己的常见目录名称单词列表。这是针对我自己网络上的一个 Web 服务器运行的，该服务器已将 WordPress 发行版解压到基础 Web 目录中。

## dirb 目录测试

```
root@quiche:~# dirb http://192.168.86.52/
--------------------------------------------------
DIRB v2.22
By The Dark Raver
--------------------------------------------------
START_TIME: Sun Aug 19 19:38:36 2018
URL_BASE: http://192.168.86.52/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt
--------------------------------------------------
GENERATED WORDS: 4612
---- Scanning URL: http://192.168.86.52/ ----
+ http://192.168.86.52/index.php (CODE:200|SIZE:418)
==> DIRECTORY: http://192.168.86.52/wp-admin/
==> DIRECTORY: http://192.168.86.52/wp-content/
==> DIRECTORY: http://192.168.86.52/wp-includes/
+ http://192.168.86.52/xmlrpc.php (CODE:200|SIZE:3065)
---- Entering directory: http://192.168.86.52/wp-admin/ ----
+ http://192.168.86.52/wp-admin/admin.php (CODE:200|SIZE:10531)
==> DIRECTORY: http://192.168.86.52/wp-admin/css/
==> DIRECTORY: http://192.168.86.52/wp-admin/images/
==> DIRECTORY: http://192.168.86.52/wp-admin/includes/
+ http://192.168.86.52/wp-admin/index.php (CODE:200|SIZE:7265)
==> DIRECTORY: http://192.168.86.52/wp-admin/js/
==> DIRECTORY: http://192.168.86.52/wp-admin/maint/
==> DIRECTORY: http://192.168.86.52/wp-admin/network/
==> DIRECTORY: http://192.168.86.52/wp-admin/user/
```

迄今为止，我们所做的是检查 Web 服务器上的已知或预期目录。使用单词列表并不能保证您能识别服务器上所有可用的目录。如果目录不在单词列表中，则不会被识别。我们可以转而使用另一个工具来帮助对目录名称进行模糊测试，即根据一组规则动态生成名称。到此为止，您可能会以为我们会转向 Metasploit，因为它非常有用。您是正确的。我们可以使用 brute_dirs 模块。使用此模块，您可以设置目录名称可能或应该呈现的格式。使用该模块将遍历所有与格式匹配的可能名称。在此，您可以看到模块可用的选项，随后是一组格式设置。我们将针对所有小写字符且长度在一到八个字符之间的单词进行测试。

## brute_dirs Metasploit 模块

```
msf > use auxiliary/scanner/http/brute_dirs
msf auxiliary(scanner/http/brute_dirs) > info
```

- 名称：HTTP 目录暴力扫描器
- 模块：auxiliary/scanner/http/brute_dirs
- 许可证：BSD 许可证
- 等级：普通

提供者：
et <et@metasploit.com>

基本选项：

| 名称 | 当前设置 | 必需 | 描述 |
| --- | --- | --- | --- |
| FORMAT | a,aa,aaa | 是 | 预期的目录格式（a 表示字母，d 表示数字，A 表示大写字母） |
| PATH | / | 是 | 用于识别目录的路径 |
| Proxies | | 否 | 格式为 type:host:port[,type:host:port][...] 的代理链 |
| RHOSTS | 192.168.86.52 | 是 | 目标地址范围或 CIDR |
| identifier | | | |
| RPORT | 80 | 是 | 目标端口（TCP） |
| SSL | false | 否 | 为外出连接协商 SSL/TLS |
| THREADS | 1 | 是 | 并发线程数 |
| VHOST | | 否 | HTTP 服务器虚拟主机 |

描述：
此模块通过在给定目录路径中暴力破解名称，来识别有趣目录的存在。

```
msf auxiliary(scanner/http/brute_dirs) > set FORMAT a,aa,aaa,aaaa,aaaaa,aaaaaa,aaaaaaa,aaaaaaaa
FORMAT => a,aa,aaa,aaaa,aaaaa,aaaaaa,aaaaaaa,aaaaaaaa
msf auxiliary(scanner/http/brute_dirs) > run
```

> [*] 使用代码 '404' 表示未找到。

和往常一样，Metasploit 拥有大量可用于基于 Web 的枚举的模块，而不仅仅是识别 Web 服务器上的目录。当您开始使用网站，尤其是 Web 应用程序时，您会遇到许多开源应用程序，因为它们使用非常广泛而广为人知。例如，您可能会发现一个 WordPress 安装。再次使用 Metasploit，我们可以枚举 WordPress 安装中的用户。wordpress_login_enum 模块可以接受用户文件或密码文件，或者您可以提供单个用户名配合密码文件，或单个密码配合用户名文件。模块中还有许多其他可设置的选项，提供了大量功能。在此，您可以看到针对本地 WordPress 安装运行该模块。

## 在 WordPress 中枚举用户名

```
msf auxiliary(scanner/http/wordpress_login_enum) > set BLANK_PASSWORDS true
BLANK_PASSWORDS => true
msf auxiliary(scanner/http/wordpress_login_enum) > set RHOSTS 192.168.86.52
RHOSTS => 192.168.86.52
msf auxiliary(scanner/http/wordpress_login_enum) > run
```

```
[*] / - WordPress Version 4.9.8 detected
[*] 192.168.86.52:80 - / - WordPress User-Enumeration - Running User Enumeration
[+] / - Found user 'kilroy' with id 1
[+] / - Usernames stored in:
/root/.msf4/loot/20180819205530_default_192.168.86.52_wordpress.users_790698.txt
[*] 192.168.86.52:80 - / - WordPress User-Validation - Running User Validation
[*] 192.168.86.52:80 - [1/0] - / - WordPress Brute Force - Running Bruteforce
[*] / - Brute-forcing previously found accounts...
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

您会注意到它提到将用户名存储在 root 用户主目录下的一个文件中，root 用户是 msfconsole 运行所在的用户。Metasploit 也会存储此信息。每当您想要查看已获取的诸如凭据等信息时，可以在 msfconsole 中运行 loot 命令。您可以在此处看到此命令的结果。

## 在 msfconsole 中列出战利品

```
msf auxiliary(scanner/http/wordpress_login_enum) > loot
```

| 主机 | 服务 | 类型 | 名称 | 内容 | 信息 | 路径 |
| ---- | ------- | ---- | ---- | ------- | ---- | ---- |
| 192.168.86.52 | | wordpress.users | 192.168.86.52_wordpress_users.txt | text/plain | | /root/.msf4/loot/20180819205530_default_192.168.86.52_wordpress_users_790698.txt |

说到 WordPress，我们不必依赖 Metasploit。同样，我们可以依赖 Kali Linux，因为它免费且易于使用，更不用说有数百种可用工具这一事实了。Kali 自带 wpscan 程序，可用于枚举不仅用户，还包括主题和插件。说到像 WordPress 这样的 Web 应用程序，了解插件也很有用，因为它们也可能引入漏洞。毕竟，它们确实包含额外代码。在下面的清单中，您可以看到 wpscan 的一次运行，其中我们枚举插件。您还会注意到，在运行过程中，它检测到了配置的用户。

## 在 WordPress 中枚举插件

```
root@quiche:~# wpscan --url http://192.168.86.52 --enumerate p
------------------------------------------------------------
|
| __ /
| / \__ \ / \__ \ |
| \ \ / / | | | | | |
| \ V / | |__| | | | | | | |
| \_/ |____/|____/|_| |_| |_|
```
