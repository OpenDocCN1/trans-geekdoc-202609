
# Web 服务器黑客工具箱

也许最通用的 Web 攻击工具是那虽然谦虚的浏览器——仅凭它就能做很多事情。你将希望像开发者一样使用 Web 浏览器，以识别内容显示方式不一致之处。现代浏览器还具有某种形式的“开发者模式”，可以用它来查看和更改文档源代码、查看发送的 HTTP 请求和响应、查看调试信息、检查内存使用等。

# 第 7 章：漏洞遍布的世界网

在本章中，我们将关注命令行工具，并尝试通过练习加深你对 Netcat 的理解。我们将使用这些工具帮助你理解 HTTP 和 Web 服务器技术。以下是你发现的对于攻击非常有用的工具类型和示例：

- Web 浏览器（Firefox 和 Chrome）
- 命令行 Web 工具（`curl` 和 `Wget`）
- 内容发现工具（`Dirb`）
- Web 漏洞和 CGI 扫描工具（`Nikto`）
- Web 扩展工具（用于与 WebDAV 交互的 `Cadaaver`）
- 服务器端脚本后门工具（`Weeely` 或 ASP.NET）
- 隧道程序（`Proxchains`）
- 通用工具（`Nmap`、`Netcat`、`Metasploit` 和 `Searchscript`）

## 扫描 Web 服务器

本章的练习，你应该使用书籍（`www.hackerhouse.com/hh-booklab-vi-i386.hybrid.iso`）。将书籍 ISO 插入到你的漏洞虚拟机（VM）中，替换你在上一章使用的邮件 ISO，并重启虚拟机。起初，你可能想进行一次基础扫描以获取结果，然后使用同一组扫描选项对你的邮件服务器进行更全面的扫描。全面扫描命令中增加了一个变化，即添加了 `-ox` 选项，它将你的扫描结果输出到 XML 文件。`Nmap` 命令看起来如下：

```
nmap -sT -p -vv -Pn -oN ebook.txt -X ebook.xml
192.168.5.110
```

没有必要等待此扫描完成。评估 Web 服务器的逻辑起点是 80 端口，因为它是 HTTP 的默认端口，且在执行初始基础扫描时理想情况下它是开启的。因此，将你的服务器指向 80 端口并开始探索。你可以通过简单在浏览器中输入 `http://<TargetIP>` 来实现（如果你省略了 `http://`，你的浏览器通常会自动选择此协议作为默认）。你还应该检查 443 端口（HTTPS 的默认端口），可以通过访问 `https://<TargetIP>` 来。这些位置是你预期面向客户端的 Web 应用程序所在地。仅通过 443 端口而非 80 端口提供 HTTP 服务变得越来越普遍，这可能将客户端（浏览器）限制在 443 端口。事实上，在 80 端口发现内容本身可能构成一种漏洞。这是因为通过该连接发送的任何数据（如用户名、密码或 Cookie）都不会被加密，处于合适位置的恶意黑客可以使用 `Wireshark` 或 `TCPdump`（`www.tcpdump.org`）等数据包分析器拦截并轻松读取。

你还可以检查并尝试对其他端口建立 HTTP 连接，通过附加数字并在 HTTP 和 HTTPS 之间切换协议，例如 `http://192.168.56.110:8080`。你的浏览器还允许你使用其他端口访问服务（例如文件传输协议 FTP），使用如下 URL：`ftp://192.168.56.110`。

一旦全面的 `Nmap` 扫描完成，你可以获取 XML 格式输出的结果，将其转换为 HTML 并在浏览器中查看这些内容。

```
OS CPE: cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3
OS details: Linux 2.6.32 -3.13
# Nmap done at Feb 13 21:37:40 2019 - 1 IP address (1 host up)
scanned in 109.89 seconds
```

在上一个输出中开放的 TCP 端口有 80、443、3128、8080 和 10000。现在我们将使用 `Netcat` 和 Web 浏览器等工具访问这些端口中的每一个，并在探索过程中理解这些结果的含义。

## 手动 HTTP 请求

请记住，你可以使用 `Netcat` (`nc`) 尝试连接到开放的端口并手动获取横幅（banners），还可以与在端口上运行的服务进行交互。你已经在上一章中对 25 端口进行过这种操作，并学习了基础的 SMTP 协议命令。尝试同样的方法连接到 80 端口，然后尝试发送一个 HTTP 请求。

```
nc <IP> 80
```

要手动发送 GET 请求，请输入以下两行，每行输后按回车键。你需要第三次按回车以发送一个空行并完成请求。如果你打字太慢，请求可能会超时。

```
GET / HTTP/1.1
host: foo
```

之前的几行告诉服务器：“使用 1.1 版本的超文本传输协议获取文件系统的根目录 (/)”。如果你指定了 HTTP/1.1 协议版本，则需要 `host: foo` 这一行；你也可以发送一个带有 GET / 之后的请求，然后按回车。在真实的 Web 服务器上尝试这种操作没有害，因为你所做的只是发送了一个针对 Web 内容的合法 GET 请求。完整的响应包含 HTML，我们现在对此并不感兴趣。这就是 HEAD 请求用用场，假设目标服务器支持它。你应该尝试向书本发送一个 HEAD 请求，如下：

```
HEAD / HTTP/1.1
host: foo
```

这里是头部，如果你成功发送了之前的 GET 或 HEAD 请求，你应该看到它们：

```
HTTP/1.1 200 OK
Date: Mon, 25 Feb 2019 11:51:15 GMT
Server: Apache/2.2.21 (Debian)
X-Powered-By: PHP/5.3.8-1+b1
Set-Cookie: 07bd4853668425bbd0fe1b304ee94-65c6aeae77f3be051bde61d4f71db26;expires=Mon, 11-Mar-2019 11:51:19 GMT; path=/
P3P: CP=DAO CSP CUR AMA DEVA OUR IND PHYZ UNC COM NAT DEN
PRE=
Set-Cookie: copperm_data=vTYoyTOzOI6IklIEIjtzoyMyIMtVhYJnZmMrYTk5MfwYN3Yn2AMQ2c0MbAJEnXSI7coYJoihbIs7At0X30D;expires=Wed, 27-Mar-2019 11:51:19 GMT; path=/
Vary: Accept-Encoding
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
```

注意，你可以看到此响应中运行的 Web 服务器（Apache）的类型和版本。你还可以看到 PHP 及其对应的版本号。你应该立即使用 `Searchplo` 等工具检查服务器名称和版本是否存在已知的漏洞。一种常见的策略是接下来发送 OPTIONS 请求来了解服务器支持的技术。再次记住要包含第三个空行，否则 Web 服务器将等待你发送更多输入，而不会将请求视为完成，如下所示：

```
OPTIONS / HTTP/1.1
host : foo
```

之前的代码片段会导致服务器返回如下响应：

```
HTTP/1.1 200 OK
Date: Mon, 25 Feb 2019 11:58:04 GMT
Server: Apache/2.2.1 (Debian)
DAV: 1,2
DAV: <http://apache.com/dav/propset/fs/1>
MS-Author: DAV
Allow: OPTIONS,GET,HEAD,POST,DELETE,TRACE,PROPFIND,PROPPATCH,COPY,MOVE,LOCK,UNLOCK
Content-Length: 0
Content-Type: http/unix-directory
```

这似乎允许许多 HTTP 方法，包括一个危险的方法 DELETE，我们可以从服务器上删除文件吗？服务器还返回了 `MS-Author: DAV` 头部。这与 `PROPFIND`、`PROPPATCH`、`COPY`、`MOVE`、`LOCK` 和 `UNLOCK` 方法一起表明了 WebDAV 的存在。注意此响应的 `Content-Length` 为零 (0)，因为只有头部而没有正文——我们没有向服务器请求任何资源，我们只是让它告诉根位置 (/) 支持哪些 OPTIONS。不同的位置支持不同的 OPTIONS，你可能想要调查比根位置 (/) 更多的资源。

> **提示** 你可以使用 `Netcat` 尝试向目前为止所示的请求发送更高级的 HTTP 请求。你可以尝试在请求中发送额外的头部并使用不同的方法，以查看服务器如何响应。你可能会看到它想要为每个请求设置 cookie（通过返回 `Set-Cookie` 头部）；你可以获取该 cookie 并在随后的请求中返回它。如果你能花一些时间以此方式进行实验，你无疑会对 HTTP 学到很多！

## 漏洞扫描

你可以继续使用 `Netcat` 手动探测弱点，也可以使用专门的工具来帮助你。手动探测漏洞将是一个枯燥且耗时的过程。已经开发了用于发现 Web 应用程序常见漏洞的工具，你应该结合手动技术使用这些工具。其中一个 Web 扫描器称为 `Nikto`，它包含在 Kali Linux 中。由 Chris David Lodge 编写，在今天具有实际用途。

> **提示** 养成检查以下命令的习惯：如果你习惯了这一点，而不是仅仅开始使用搜索引擎在网上寻找答案，那么依靠像 Stack Overflow（一个基于社区的问答论坛）这样的网站会更好，并且能够更有效地找到你问题的答案。这需要一些时间适应，但值得的！

```
+ Entry '/xmlrpc.php/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/admin/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-comment/reply/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-filter/tips/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-node/add/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-search/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-user/password/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-user/register/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-user/login/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

```
+ Entry '/q-user/logout/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
```

- `/robots.txt` contains 4 entries which should be manually viewed.
- OSVDB-637: Enumeration of users possible by requesting -username (responds with 'Forbidden for users', 'not found' for non-existent users).
- Apache/2.4.2 appears to be outdated (current is at least Apache/2.4.33). Apache 2.4.33 is < the latest for the 2.x branch.
- OSVDB-397: HTTP method "PUT" allows clients to save files on the web server.
- Retrieved header: A3Err0 (0x5562d125668)
- Retrieved-ms-author-via header: DAV
- Uncommon header: "ms-author-via" found, with contents: DAV
- Allowed HTTP Methods: OPTIONS, GET, HEAD, POST, DELETE, TRACE, PROPFIND, PROPPATCH, COPY, MOVE, UNLOCK
- OSVDB-5646: HTTP method 'Allow' (Header): 'DELETE' allows clients to remove files from the web server.
- OSVDB-5647: HTTP method "MOVE" allows clients to change file locations on the web server.
- WebDav enabled (PROPFIND COPY PROPPATCH LOCKED list as allowed)
- Uncommon header: "A3rr0-cve-2014-6278" found, with contents: true vulnerability (http://www.cmire.org/cgi-bin/cve.cgi?name=CVE-2014-6271).
- OSVDB-3268: Directory indexing found.
- OSVDB-3092: /web.config Apache config file is accessible.
- //: Appending / to directory indexing
- OSVDB-3268: Directory indexing found
- Apache on Red Hat Linux 9 reveals the root directory listing by default if there is no index page.
- OSVDB-5756: /k2e/: allows source code or directory listing, upgrade to v6.0 SP1 or higher: http://www.securityfocus.com/bid/2513.
- /phpinfo.php: Output from the phpinfo() function was found.
- /sqldump.php: Database SQL?
- OSVDB-3268: Directory indexing found.
- OSDB-12184: PHPBBSFAZ0-SC392-11d3-A9A4-C7B0C10000: PHP reveals potentially sensitive information via HTTP requests that contain specific QUERY strings.
