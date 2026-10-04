
你可以通过使用`SQLmap`等工具对漏洞应用程序来练习你的渗透测试技能。The Art of Hacking GitHub 仓库包含了一个漏洞服务器和应用程序的列表，你可以下载并使用它们在安全环境中练习你的技能；请参阅[`github.com/The-Art-of-Hacking/art-of-hacking/tree/master/vulnerable_servers`](https://github.com/The-Art-of-Hacking/art-of-hacking/tree/master/vulnerable_servers)。

### 注意

你可以在以下 GitHub 仓库获取`SQLmap`的源代码和额外文档：[`github.com/sqlmapproject/sqlmap`](https://github.com/sqlmapproject/sqlmap)。

不要只是对漏洞应用程序启动工具，要尝试阅读调试信息并理解工具正在做什么。例如，在示例 10-16 和示例 10-17 中，你可以看到发送到漏洞应用程序随后发送到 SQL 服务器的不同 SQL 语句。

### Nikto

`Nikto`是一个开源的 Web 漏洞扫描器，可以从[`github.com/sullo/nikto`](https://github.com/sullo/nikto)下载。Nikto 的官方文档可以通过[`cirt.net/nikto2-docs`](https://cirt.net/nikto2-docs)访问。示例 10-18 显示了 Nikto 手帮助页的前几行。

#### 示例 10-18 Nikto 的帮助页

点击此处查看代码图像

```
NAME
         nikto - Scan web server for known vulnerabilities
SYNOPSIS
       /usr/local/bin/nikto [options...]
DESCRIPTION
       Examine a web server to find potential problems and security
vulnerabilities, including:
    · Server and software misconfigurations
    · Default files and programs
    · Insecure files and programs
    · Outdated servers and programs
 Nikto is built on LibWhisker (by RFP) and can run on any platform
which has a Perl environment. It supports SSL, proxies, host
authentication, IDS evasion and more. It can be updated automatically
from the command-line, and supports the optional submission of updated
version data back to the maintainers.
```

示例 10-19 演示了如何使用 Nikto 扫描托管在 10.1.1.14 的 Web 应用程序。

#### 示例 10-19 使用 Nikto 扫描 Web 应用程序

点击此处查看代码图像

```
root@kali:~# nikto -host 10.1.1.14
Nikto v2.1.6
------------------------------------------------------
+ Target IP:          10.1.1.14
+ Target Hostname: 10.1.1.14
+ Target Port:       80
+ Start Time:        2018-06-23 22:43:36 (GMT)
------------------------------------------------------
+ Server: Apache/2.2.8
```

根据 OWASP 的介绍，`OWASP Zed Attack Proxy (ZAP)`“世界上最流行的免费安全工具之一，并由数百名国际志愿者积极维护。”全球许多攻击和防御安全工程师都使用 ZAP，它不仅提供 Web 漏洞扫描功能，还可以作为一个复杂的 Web 代理使用。ZAP 带有 API，并可以作为模糊测试器（fuzzer）使用。你可以从[`www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project`](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)下载并获取有关 OWASP ZAP 的更多信息。

图 10-16 显示了 IP 地址为 10.1.1.14 的 Web 服务器进行的活动扫描。

图 10-17 显示了扫描结果的几项。图 10-17 中突出显示的漏洞是路径遍历漏洞。ZAP 还发现了许多其他漏洞。ZAP Spider（爬虫）会自动发现正在测试网站上的 URL。它从一个待访问 URL 列表开始，这些 URL 被称为“种子”。然后 ZAP Spider 尝试访问这些 URL，识别页面中的所有超链接，并将超链接添加到访问 URL 列表中；只要发现新资源，该过程就会递归持续。在处理 URL 期间，ZAP Spider 发起请求访问资源并解析响应。

![图 10-16 使用 OWASP ZAP 扫描 Web 应用程序](img/10fig16.jpg)

**图 10-16** 使用 OWASP ZAP 扫描 Web

![图 10-17 OWASP ZAP 的漏洞扫描结果](img/10fig17.jpg)

**图 10-17** OWASP ZAP 的漏洞扫描结果

### w3af

另一个流行的开源 Web 漏洞扫描器是`w3af`。可以从[`w3af.org`](https://w3af.org)下载 w3af，并从[`w3af.org/howtos`](https://w3af.org/howtos)获取其文档。

示例 10-21 显示了 w3af 控制台的帮助菜单。

**示例 10-21** w3af 控制台的帮助菜单

点击此处查看代码图像

```
w3af>>> help
|-----------------------------------------------------------------------|
| start                | 开始扫描。
|
| plugins              | 启用并配置插件
|
| exploit              |  利用漏洞
|
| profiles             | 列出并使用扫描配置方案。
|
| cleanup              | 在开始新扫描之前清理。
|
|---------------------------------------------------------------------|
| help                  | 执行：help [command]，打印关于“command”的更|
|                       具体的帮助信息
|
| version               | 显示 w3af 版本信息。
|
| keys                  | 显示快捷键。
|
|---------------------------------------------------------------------|
| http-settings         | 配置框架的 HTTP 设置。
|
| misc-settings         | 配置 w3af 杂项设置。
|
| target                | 配置目标 URL。
|
|---------------------------------------------------------------------|
| back                  | 返回上一个菜单。
|
| exit                  | 退出 w3af。
|
|---------------------------------------------------------------------|
| kb                    | 浏览存储在知识库中的漏洞
|---------------------------------------------------------------------|
```

w3af 工具有一个插件菜单，允许你配置和启用 mangle（混淆）、crawl（爬虫）、bruteforce（暴力破解）、audit（审计）以及其他插件。示例 10-22 显示了 w3af 的插件帮助菜单。

**示例 10-22** w3af 插件帮助菜单

点击此处查看代码图像

```
w3af>>> plugins
w3af/plugins>>> help
|---------------------------------------------------------------------|
| list             | 列出可用插件。
|
|---------------------------------------------------------------------|
| back             | 返回上一个菜单。
|
| exit             | 退出 w3af。
|
|---------------------------------------------------------------------|
| mangle           | 查看、配置并启用混淆插件
| crawl            | 查看、配置并启用 爬虫插件
| bruteforce       | 查看、配置并启用 暴力破解插件
| audit            | 查看、配置并启用 审计插件
| output           | 查看、配置并启用 输出插件
| evasion          | 查看、配置并启用 逃逸插件
| infrastructure   | 查看、配置并启用 基础设施插件
| auth             | 查看、配置并启用 认证插件
| grep             | 查看、配置并启用 grep 插件|
|-------------------------------------------------------------------|
w3af/plugins>>>
```

当你处于插件模式（plugins-mode）时，你可以使用`list audit`命令列出所有可用的审计插件，如示例 10-23 所示。你也可以对任何其他插件类别执行此操作。

**示例 10-23** w3af 的`list audit`命令

点击此处查看代码图像

```
w3af/plugins>>> list audit
|---------------------------------------------------------------------|
| 插件名称 | 状态 | 配置 | 说明 |
|---------------------------------------------------------------------|
| blind_sqli     |       | Yes     | 识别盲 SQL 注入
漏洞。 |
|
| buffer_overflow |      |         | 查找缓冲区溢出
漏洞。 |
|
| cors_origin     |      |  Yes    | 检查应用程序是否检查
"Origin" HTTP 头部的值是否与发送传入 HTTP 请求的
发送者的远程 IP 地址/
主机（Host）值一致。 | |
| csrf             |      |         | 识别跨站请求伪造
漏洞。 |
| dav              |      |         | 验证 WebDAV 模块是否
配置正确。 |
|
| eval             |      |   Yes   | 查找不安全的 eval() 使用。 |
|
| file_upload     |      |   Yes   | 上传文件然后在所有已知
目录中搜索
该文件。 | |
| format_string   |      |         | 查找格式化字符串
漏洞。 |
|
| frontpage        |      |         | 尝试使用 frontpage
扩展名（author.dll）上传文件。 |
|
| generic          |      |    Yes  | 在不使用固定错误
数据库的情况下查找所有类型的漏洞。 |
|
| global_redirect |      |          | 查找将浏览器
重定向到任何站点的脚本。 | |
|
| htaccess_methods   |     |         | 查找 Apache 中
"<LIMIT>" 配置中的错误配置。 |
|
| ldapi              |     |          | 查找 LDAP 注入漏洞。 |
|
| lfi                |     |         | 查找本地文件包含
漏洞。 |
|
| memcachei          |     |          | 此插件没有可用的描述。 |
|
| mx_injection       |     |           | 查找 MX 注入
漏洞。 |
|
| os_commanding      |     |           | 查找操作系统命令执行
漏洞。 |
|
| phishing_vector    |     |           | 查找钓鱼攻击向量。 |
|
| preg_replace       |     |            | 查找 PHP preg_replace 的
不安全使用。 |
|
| redos              |     |             | 查找 ReDoS
漏洞。 |
|
| response_splitting |     |            | 查找响应拆分
漏洞。 |
|
| rfd                |     |             | 识别反射型文件下载
漏洞。 |
|
| rfi                |     |    Yes      | 查找远程文件
包含
漏洞。 |
|
| shell_shock        |     |             | 查找 shell shock
漏洞。 |
|
| sqli               |     |             | 查找 SQL 注入漏洞。 |
|
| ssi                |     |             | 查找服务器端
包含
漏洞。 |
|
| ssl_certificate    |     |    Yes       | 检查 SSL
证书的有效性（如果使用了 https）。 |
|
| un_ssl             |      |             | 检查是否也可以使用 http
获取
安全内容。 |
|
| websocket_        |      |             | 检测跨站
WebSocket 劫持漏洞。 |
|
| xpath             |      |             | 查找 XPATH 注入
漏洞。 |
|
| xss               |      |    Yes       | 识别跨站脚本
漏洞。 |
|
| xst               |      |              | 查找跨站追踪
漏洞。 |
|---------------------------------------------------------------------|
```

示例 10-24 显示了如何配置`w3af`工具，以对 IP 地址为`10.1.1.14`的 Web 服务器进行 SQL 注入审计。

**示例 10-24** 使用`w3af`启动 SQL 注入审计

点击此处查看代码图像

```
w3af/plugins>>> audit sqli
w3af/plugins>>> back
w3af>>> target set target 10.1.1.14
w3af/config:target>>> back
配置已保存。
w3af>>> start
```

**提示**

关于`w3af`的详细用法和自定义，请参考[`docs.w3af.org/en/latest`](https://docs.w3af.org/en/latest)。

#### DirBuster

DirBuster 是一种用于暴力破解目录名的工具。

**注意**

DirBuster 是一个 Java 应用程序，旨在暴力破解 Web/应用程序上的文件名。通常看似正常的服务器内部都有隐藏页面。DirBuster 会尝试寻找这些页面。DirBuster 目前是一个未活跃的项目，其功能已集成并增强到 OWASP ZAP 中。DirBuster 的两个替代方案是 gobuster（[`github.com/gobuster`](https://github.com/gobuster)）和 ffuf（[`https://github.com/ffuf`](https://github.com/ffuf)）。

#### 常用凭据攻击工具

以下是一些用于暴力破解、破解和破解用户凭据的常用工具：
