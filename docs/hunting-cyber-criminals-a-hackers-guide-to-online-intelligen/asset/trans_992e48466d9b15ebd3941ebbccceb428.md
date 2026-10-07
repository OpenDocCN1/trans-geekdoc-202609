

# 第7 章

# 目录扫描

在寻找网站信息的过程中，你不可避免地需要寻找隐藏的（即被遗忘的）宝藏。最好的方法是寻找随机目录。如果你还没有尝试过，你将对人们竟然遗忘了多少信息感到惊讶：webshells、phpMyAdmin 页面、具有目录浏览和/或完全读写权限的文件夹、私有文件等等。实现这一目标有几种方法：一种是对目标进行暴力破解以找到可目录，另一种是分析爬虫数据。本章将介绍这两种方法。

## Dirhunt

Dirhunt 是一种网络爬虫，旨在搜索和分析 Web 应用中的目录和文件夹。Dirhunt 并不是真正的爬虫，它不使用暴力破解来寻找文件夹。相反，Dirhunt 通过多个来源来寻找感兴趣的文件或文件夹，包括 Google 和 VirusTotal。Dirhunt 还设计用于检测虚假的 404 错误，以尽可能地减少结果中的假阳性数量。

> 注意 你可以在 https://github.com/Nekmo/dirhunt 下载 Dirhunt。

Dirhunt 的参数包括：

- -t, --threads INTEGER 使用的线程数
- -x, --exclude-flags TEXT 排除带有这些标志的结果
- -i, --include-flags TEXT 仅包含带有这些标志的结果
- -e, --interesting-extensions TEXT 寻找具有这些扩展的文件
- -f, --interesting-files TEXT 这些名称的文件是有趣的
- --stdout-flags TEXT 仅在 stdout 中返回这些 url
- --progress-enabled / --progress-disabled
- --timeout INTEGER 超时
- --max-depth INTEGER 最大跟踪链接数
- --not-follow-subdomains 将忽略子域名
- --exclude-sources TEXT 排除源引擎：robots, virustotal, google 设置一个或多个代理进行交替
- -p, --proxies TEXT 请求之间的延迟
- -d, --delay FLOAT --not-allow-redirects 不跟随重定向
- --limit INTEGER 处理的最大页面数

让我们在不带参数的情况下，通过佛罗里达酒精和药物滥用协会（FADAA）测试 Dirhunt 的能力：

```
root@INTEL:/opt/dirhunt$ dirhunt https://www.fadaa.org/
```

[301] https://www.fadaa.org/ (重定向)
重到: https://www.fadaa.org/
[403] http://www.fadaa.org/global_inc/ (通用)
找到索引文件: index.php
[301] http://www.fadaa.org/ (重定向)
重到: https://www.fadaa.org/
[301] http://www.fadaa.org/global_engine/Default.asp?
重到: https://www.fadaa.org/
[301] http://www.fadaa.org/global_inc/*a2s.jsp (重定向)
重到: https://www.fadaa.org/404.aspx?704=
http://www.fadaa.org:80/global_inc/*
[301] http://www.fadaa.org/global_inc/*a2s.jsp (重定向)
重到: https://www.fadaa.org/404.aspx?704=
http://www.fadaa.org:80/global_inc/*
[301] http://www.fadaa.org/ (重定向)
重到: https://www.fadaa.org/default.aspx
[403] http://www.fadaa.org/global_inc/ (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/ (通用)
[404] http://www.fadaa.org/404.aspx (未找到)
[200] http://www.fadaa.org/default.aspx (通用)
[302] http://www.fadaa.org/global_engine/Default.asp (重定向)

重到: https://www.fadaa.org/global_engine/Default.asp
[302] http://www.fadaa.org/global_engine/ (重定向)
重到: http://www.fadaa.org/global_engine/
[302] http://www.fadaa.org/global_engine/ (重定向)
重到: http://www.fadaa.org/global_engine/
[302] http://www.fadaa.org/page/SAMHSA_Treatment (重定向)
重到: http://treatment.samhsa.gov/
[200] http://www.fadaa.org/staff/ (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/news/ (通用)
找到索引文件: index.php
[404] http://www.fadaa.org/page/ (未找到)
找到索引文件: index.php
[200] http://www.fadaa.org/page/resource_links (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/networking/ (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/page/AO2017 (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/page/Membership (通用)
找到索引文件: index.php
[200] http://www.fadaa.org/search/ (通用)
[302] http://www.fadaa.org/general/ (重定向)
重到: http://www.fadaa.org/general/
[200] http://www.fadaa.org/login.aspx (通用)
[302] http://www.fadaa.org/general/register_start.asp (重定向)
[404] http://www.fadaa.org/general/register_start.asp
[404] http://www.fadaa.org/graphics/ (未找到)
找到索引文件: index.php
[403] http://www.fadaa.org/global_inc/ (通用)
[403] http://www.fadaa.org/global_inc/site_templates/js/ (通用)

由于现在的网站非常普遍使用内容管理系统 (CMS)，你极有可能会发现它们。Dirhunt 的参数可以调整，以关注（或不关注）特定的文件、文件类型等。使用 -e 寻找压缩文件（如 .zip, .rar 或 .gz）可以让你获得应该被删除的文件：

```
dirhunt http://domain.com -e php,zip,sh
```

你也有很大机会发现被遗忘的有趣文件，如配置文件、备份和日志文件。针对文件，使用 -f 切换，如下：

```
dirhunt http://domain.com -f access_log,error_log
```

在寻找文件时，你也可以指定从字典搜索的文件列表。指定字典文件使用：

```
dirhunt http://domain.com -f /var/files/dictfile.txt
```

## Wfuzz

Wfuzz 已经存在了，可能是最著名的 Web 应用测试工具之一。Wfuzz 本质上是一个暴力破解工具，是针对 Web 应用最好的工具之一。

Fuzzing 是使用自动化工具通过向应用程序发送格式错误的数据寻找软件漏洞的过程。在这种情况下，我们并没有发送 Wfuzz（网络模糊）格式错误的数据。我们是使用它向 Web 服务器发送合词汇和短语，以检查隐藏或私有文件和文件夹的存在。Wfuzz 可以在 https://github.com/xmendez/wfuzz 下载。

Wfuzz 的选项包括：

```
-h : 帮助
--help : 高帮助
--version : Wfuzz 版本详情
-e <type> : 编码器/负载/迭代器/打印器/脚本
```

- -C : 彩色输出
- -V : 详细信息
--interact : 允许你与程序交互
- -p addr : 使用格式为 ip:port:类型的代理。如果省略，可以是 SOCKS4、SOCKS5 或 HTTP
- -t N : 指定并发连接数（默认 10）
- -s N : 指定请求之间的延迟
- -R depth : 递归路径发现深度
- -L, --follow 跟随 HTTP 重定向
- -u : 指定请求的 URL
- -z payload : 指定负载类型、参数、编码器
- -w wordlist : 指定字典文件（-z file,wordlist 的别名）
- -V alltype : 所有参数暴力破解（vars 和 allpost）
- -X method : 指定请求的 HTTP 方法
- -b cookie : 为请求指定 cookie
- -d postdata : 使用 post 数据（例如 "id=FUZZ&catalogue=1"）
- -H header : 使用 header（例如 "Cookie:id=1312321&user=FUZZ"）格式为 "user:pass" 或 "FUZZ:FUZZ"
--basic/ntlm/digest auth : 或 "domain\FUZZ:FUZZ"

Wfuzz 包含无限数量的字符，你可以用来“模糊” Web。在寻找目标域名的 Web 目录时也可以这样做。

Wfuzz 的工作原理是获取你的目标 URL，并尝试在 URL 中指定 "fuzz" 的任何地方插入字典中的每个单词。

让我们从一个简单的示例开始，尝试使用字典暴力破解主域名路径。对于示例单词，我们将使用第 2 章讨论的 SecLists 仓库中的 big.txt 单词。我们还将使用 --hc 标签来隐藏所有的 404 响应：

```
root@OSINT:wfuzz -c -z file,/SecLists/Discovery/Web-Content/big.txt --hc 404 http://www.biz-up.at/FUZZ
```

