
然而，并非所有的入侵都涉及技术漏洞。事实上，最成功的入侵中很多是完全非技术性的。[Social engineering](#glossary.xhtml#gloss77) 是一种通过利用人性而非技术手段来突破系统安全的技术，这正是著名黑客凯文·米特尼克最常使用的路径。Social engineering 使用标准的诱骗技术，诱使用户提供获取目标系统访问权限所需的信息。该方法的运作方式相对简单：攻击者首先获取目标组织的初步信息，然后利用这些信息从系统用户那里获取更多信息。

下面是一个社交工程的实际例子。如果你掌握了系统管理员的姓名，你可以给企业会计部的某个人打电话，并冒充公司技术支持人员。提及系统管理员的姓名可以帮助验证你的主张，从而让你能够提问以获取更多关于系统规格的细节。一个有经验的入侵者甚至可能让会计人员说出用户名和密码。正如你所见，该方法的成功在于是否能够操纵他人，而实际上与计算机技能关系不大。

无线网络的日益普及催生了新型的攻击方式。其中一种活动是[war-driving](#glossary.xhtml#gloss91)。这种攻击是[war-dialing](#glossary.xhtml#gloss90) 的一个分支。在 war-dialing 中，黑客会设置电脑自动拨打电话号码序列，直到另一台电脑应答，然后尝试入侵其系统。而 war-driving 则是将这一概念应用于寻找弱点的无线网络。在这种情况下，黑客只需驾车在周围寻找弱点的无线网络。很多人忘记了，他们的无线网络信号往往能覆盖多达 100 英尺（因此，信号会穿透墙体）。在 2004 年黑客 DEF CON 会议上，曾举办过 war-driving 竞赛，参赛者驾车在城市中寻找尽可能多的弱点无线网络。这类竞赛如今已在各类黑客会议中常见。（DEF CON 是全球规模最大、历史最悠久的黑客会议。）

近年来，技术创新催生了 war-driving/dialing 的新变种——war flying。攻击者使用装有 Wi‑Fi 默 sniffing 和 cracking 软件的小型私人无人机在目标区域飞行，并尝试入侵无线网络。

当然，Wi‑Fi 黑客只是一种泄漏的形式。密码破解工具现在已普遍可在 Internet 上下载。我们稍后会在本书中探讨其中一些。此外，还有利用软件漏洞的攻击，使得对手能够访问目标计算机。

### DoS 攻击

在 DoS 攻击中，攻击者并不直接访问系统，而是简单地阻止合法用户的访问。一种常见的做法是向目标系统发送大量伪造的连接请求，导致系统无法响应合法请求。DoS 攻击之所以如此普遍，是因为它操作简单。

近年来，Internet 上出现了大量 DoS 工具。其中最常见的工具之一是 Low Orbit Ion Cannon（LOIC）。由于这些工具可以免费从 Internet 下载，任何人都可以执行 DoS 攻击，甚至不具备技术背景。

还有变体，如 DDoS 攻击。DDoS 攻击利用多台机器同时攻击目标。鉴于许多现代网站托管在网络集群或云端，单台攻击机很难产生足够的流量将服务器宕机。但几百甚至几千台电脑组成的网络却可以轻松完成。我们将在 [第 4 章](#ch04.xhtml#ch04) “[Denial of Service Attacks](#ch04.xhtml#ch04)” 中更详细探讨 DoS 和 DDoS 攻击。

### Web 攻击

由于服务器本质上必须允许通信，网站通常会让用户与之交互。任何允许用户交互的网站部分，都可能成为 Web 攻击的潜在目标。SQL 注入是一种通过在登录表单（用户名和密码文本框）中输入 SQL（结构化查询语言）命令，诱使服务器执行这些命令的技术。其最常见的目的之一是强制服务器在没有合法用户名和密码的情况下登录。虽然 SQL 注入只是一种 Web 攻击类型，但它是最为常见的。

#### SQL 注入

SQL 注入至今仍相当常见，尽管该技术已知多年。遗憾的是，仍有不少 Web 开发者未采取适当措施来修复使此类攻击成为可能的漏洞。鉴于此类攻击的普遍性，本文将对其进行更详细的描述。

考虑最简单的 SQL 注入形式——用于绕过登录界面的技巧。网站可能使用 PHP、ASP.NET 等编程语言开发，数据库通常是像 Oracle、SQL Server、MySQL 或 PostgreSQL 这样的关系型数据库，用于与数据库通信，需要在编写的 Web 页面中嵌入 SQL 语句，从而查询数据库以验证用户名和密码的有效性。

SQL 语言相对易懂，其语法类似于英语。常见命令包括 `SELECT`（获取数据）、`INSERT`（写入数据）和 `UPDATE`（修改数据）。要登录网站，Web 页面必须查询数据库表以确认用户名和密码是否正确。SQL 的基本结构如下：

[Click here to view code image](Images/ch01_images.xhtml#p11pro01)

```
select column1, column2 from tablename
```

或：

[Click here to view code image](Images/ch01_images.xhtml#p11pro02)

```
select * from tablename;
Conditions:
select columns from tablename where condition;
```

例如：

[Click here to view code image](Images/ch01_images.xhtml#p11pro03)

```
SELECT * FROM tblUsers WHERE USERNAME = 'jsmith'
```

该语句从名为 `tblUsers` 的表中检索所有列，条件是用户名为 `jsmith`。

当我们尝试在 Web 页面中嵌入 SQL 语句时，问题会出现。Web 页面的代码是用 PHP 或 ASP.NET 等语言编写的，如果直接把 SQL 语句放进去，会产生错误。SQL 语句必须使用引号将其与程序代码区分。典型的 SQL 语句可能如下：

[Click here to view code image](Images/ch01_images.xhtml#p11pro04)

```
"SELECT * FROM tblUsers WHERE USERNAME = '" + txtUsername.Text +' AND PASSWORD = '" +
txtPassword.Text +"'" .
```

如果输入用户名 `'jdoe'`、密码 `'password'`，上述代码会生成如下 SQL 命令：

[Click here to view code image](Images/ch01_images.xhtml#p11pro05)

```
SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'password'
```

这对非程序员也很易理解，并且有效。如果数据库中存在匹配记录，则用户名和密码匹配；若返回空结果，则登录无效。

最基础的 SQL 注入方式是构造一个永远为真（True）的语句。例如，攻击者在用户名和密码框中输入 `'` 或 `'1' = '1`，这将导致程序生成如下查询：

[Click here to view code image](Images/ch01_images.xhtml#p12pro01)
