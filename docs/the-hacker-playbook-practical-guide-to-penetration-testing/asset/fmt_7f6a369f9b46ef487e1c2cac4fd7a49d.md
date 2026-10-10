
# 从扫描结果到漏洞利用：基线概述

本章概述如何将扫描器的发现转化为实际行动，这些示例将引导读者了解后续章节中如何利用系统漏洞。攻击和漏洞利用并非总能奏效，因此我强调学生不应依赖工具。更重要的是理解攻击**为何**奏效以及底层问题是什么，这样当工具失效时，你才有能力修改和修复漏洞利用代码。

对我学习计算机漏洞利用帮助最大的方法，是从 [Exploit-DB](http://www.exploit-db.com/remote/) 等网站获取漏洞利用代码，并用我选择的另一种高级脚本语言重写它们。开发此类脚本并针对自己的服务器进行测试，将极大地增强你的编程背景，并加深对漏洞原理的理解。如果你想深入钻研漏洞利用开发，强烈推荐阅读《The Shellcoder's Handbook》：[http://amzn.to/19ZlgfE](http://amzn.to/19ZlgfE)。

![](images/00060.jpeg)

此时，你已完成目标评估、制定攻击计划，现在是利用 Web 漏洞的时候了。本书这一部分将深入探讨如何将 Web 应用扫描和手工测试的发现转化为系统沦陷。

![](images/00061.jpeg)

Web 应用测试部分涵盖的主题包括：SQL 注入（SQLi）、跨站脚本（XSS）、跨站请求伪造（CSRF）、会话令牌熵、模糊测试/输入验证以及业务逻辑。虽然这些不是所有的测试类型，但它们通常能发现导致用户群、应用或系统沦陷的主要漏洞。这也将为学习其他类型的 Web 攻击打下良好基础。

对于更深入的、针对特定应用的测试框架（相较于网络风格测试），你应非常熟悉 OWASP 测试指南：[http://bit.ly/19GkG5R](http://bit.ly/19GkG5R) 以及《The Web Application Hacker's Handbook》：[http://amzn.to/1lxZaCv](http://amzn.to/1lxZaCv)。

![](images/00062.jpeg)

通过扫描结果或手工探测，你可能会发现一些 SQL 注入（SQLi）漏洞。这非常关键，因为 SQLi 可能导致数据库甚至整个系统完全沦陷。我发现两款开源工具在大多数情况下效果最好：`SQLmap` 和 `Sqlninja`。让我们从识别到利用完整走一遍流程。

如果你在之前的 Web 应用扫描部分通过 `Burp Suite` 发现 SQL 注入，在扫描器结果标签页中通常如下图所示（[图 30](#part0008.html#id_457)）。

![](images/00063.jpeg)

**图 30 - Burp SQL 注入发现**

使用 `Burp` 的一大优势是它提供发现结果的置信度评级，帮助判断是真实漏洞还是潜在误报。在该例（[图 30](#part0008.html#id_457)）中，`Burp` 的置信度为“Certain”，且易受攻击的参数为 `Password`、`Username` 和 `User-Agent` 字段。

## SQLmap ([http://sqlmap.org/](http://sqlmap.org/)) (Kali Linux)

`SQLmap` 是我最喜欢的工具之一，用于发现 SQL 注入、操纵数据库查询和导出数据库。它还具备通过注入获取交互式 Shell 的额外功能，甚至能反弹 `Meterpreter` 或 `VNC` 会话。

以下示例将展示 `SQLmap` 针对 `GET` 参数和 `POST` 参数的用法，因为它们是最常见的 SQLi 类型。之所以演示两种 HTTP 方法，是因为如果请求配置不当，攻击极大概率会失败。

以下是 `SQLmap` 的帮助信息，包含大量可用于 SQLi 攻击的开关：`sqlmap -h`

![](images/00064.jpeg)

**图 31 - SQLMap 帮助信息**

### GET 参数示例

以下示例假设 SQLi 漏洞位于 URL 的 GET 参数中。我们要测试每个参数，确保 SQLi 漏洞确属实。我见过扫描工具有不少误报，因此验证是确保发现有效的唯一途径。请注意，若未指定测试值，`SQLmap` 默认会测试所有参数。

**验证 SQL 注入是否有效（若有效将返回 Banner 信息）：**

```bash
sqlmap -u "http://site.com/info.php?user=test&pass=test" -b
```

**获取数据库用户名：**

```bash
sqlmap -u "http://site.com/info.php?user=test&pass=test" --current-user
```

**交互式 Shell：**

```bash
sqlmap -u "http://site.com/info.php?user=test&pass=test" --os-shell
```

**提示与技巧：**

*   可能需要指定数据库类型。若认为存在注入但 `SQLmap` 未发现，尝试设置 `--dbms=[database type]` 标志。
*   若需测试需认证的 SQL 注入，通过浏览器登录网站并获取 Cookie（可直接从 `Burp Suite` 获取），然后使用 `--cookie=[COOKIE]` 开关定义 Cookie。
*   卡住了？尝试命令：`sqlmap --wizard`

### POST 参数示例

POST 示例模仿 GET 注入，区别在于易受攻击参数的传递方式。POST 参数不在 URL 中，而是在数据段传递。这常见于用户名和密码，因为 Web 服务器通常记录 GET 参数，不应记录密码。此外，GET 方法有大小限制，因此大型应用常通过 POST 参数传递大量数据。

**验证 SQL 注入是否有效（若有效将返回 Banner 信息）：**

```bash
sqlmap -u "http://site.com/info.php" --data="user=test&pass=test" -b
```

**获取数据库用户名：**

```bash
sqlmap -u "http://site.com/info.php" --data="user=test&pass=test" --current-user
```

**交互式 Shell：**

```bash
sqlmap -u "http://site.com/info.php" --data="user=test&pass=test" --os-shell
```

若能获得 `os-shell` 访问权限，你将拥有数据库用户的完整命令行访问权。下例中，我发现一个 SQLi 漏洞，获取 `os-shell` 并执行了 `ipconfig` 命令。

![](images/00065.jpeg)

**图 32 - SQLMap 命令 Shell**

建议花时间熟悉运行不同 SQLi 命令并尝试帮助文件中列出的各种开关。若 `SQLmap` 失败，可能是配置问题，请务必尝试使用向导设置。

## Sqlninja ([http://sqlninja.sourceforge.net/](http://sqlninja.sourceforge.net/)) (Kali Linux)

`Sqlninja` 是另一款优秀的 SQL 注入工具，擅长上传 Shell 和规避网络 IDS 系统。你可能会问：既然已熟练掌握 `SQLmap`，为何还要用 `Sqlninja`？凭借多年经验，我见过大量测试仅能用两者之一检测出 SQLi。这可能源于盲注检测方式、二进制上传机制、IPS 签名仅识别某工具、或 Cookie 处理方式的差异。变量太多，明智做法是始终用多工具交叉验证。

使用 `-h` 开关查看帮助文件，可见 `Sqlninja` 的所有功能。

![](images/00066.jpeg)

**图 33 - Sqlninja 帮助页面**

`Sqlninja` 唯一的问题是配置文件设置较难，且我从未找到优秀易读的文档。因此我将给出与 `SQLmap` 类似的两个示例。
