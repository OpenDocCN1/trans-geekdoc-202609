
与 OpenVAS 不同，Nessus 没有提供向发现结果添加注释的功能。但 Nessus 提供了你在 OpenVAS 中没有的审计日志。你可以通过插件 ID 和主机进行搜索，并获取运行该插件时的额外详细信息。例如，搜索关键的 macOS 过时发现的插件 ID 时，会显示 Nessus 无法识别操作系统的主机 IP 地址、Nessus 识别到操作系统但不是 macOS 的主机 IP 地址，以及操作系统正确但版本号错误的 IP 地址（即该插件运行后未产生任何发现）。

与 OpenVAS 类似，Nessus 使用 Network Attack Scripting Language（NASL） 脚本。这些脚本与 Nessus 安装一起存储。在 Windows 上，安装目录位于 Program Files 文件夹；在 Linux 上，文件存放在 `/opt/nessus`，插件则放在 `/opt/nessus/lib/plugins`。如果想详细了解插件的具体功能以验证发现，应查看脚本。可以通过插件 ID 定位对应的脚本文件。一旦熟悉这些脚本，它们会提供复制漏洞验证测试的详细步骤，这对于排除误报至关重要，且在确认真实漏洞时，需要向所在公司或组织提供相应的文档。

漏洞扫描仅是测试过程中的一个阶段，并非终点。漏洞必须始终进行验证。如果你的任务是尽可能发现更多漏洞，则需要进一步利用这些漏洞进行开发，以期发现更多问题。这可能需要使用 Metasploit 等 exploit 工具，或自定义开发工具，甚至需要构造形态特定的数据包。无论发现的结果如何，都必须在正式呈现前进行验证。

### 使用 Metasploit 查找漏洞

Metasploit 是一个功能多样的工具。当然，你可以使用它来开发应用漏洞，也可以进行之前的端口扫描。由于它是框架且包含大量模块，自然会有大量漏洞扫描模块。例如，有一个针对 Eternal Blue 漏洞的扫描模块。该漏洞是服务器消息块（SMB）协议实现中的缺陷，由国家安全局（NSA）发现并开发了 exploit，随后被名为 Shadow Brokers 的组织在未经 NSA 同意的情况下公开。下面是一个查找易受 Eternal Blue 影响系统的漏洞扫描示例。虽然该漏洞的修复已有多年，但仍有大量生产环境中的系统受其影响。

```
msf6 auxiliary(scanner/portscan/syn)> use auxiliary/scanner/smb/smb_ms17_010
msf6 auxiliary(scanner/smb/smb_ms17_010)> set RHOSTS 192.168.4.0/24
RHOSTS => 192.168.4.0/24
msf6 auxiliary(scanner/smb/smb_ms17_010)> run
 
[-] 192.168.4.10:445 - Host does NOT appear vulnerable.
[-] 192.168.4.15:445 - Host does NOT appear vulnerable.
[*] 192.168.4.0/24:445 - Scanned 26 of 256 hosts (10% complete)
```

Metasploit 中提供了大量扫描器，并非所有扫描器都直接关联到漏洞。在 Metasploit 中搜索关键字 *scanner* 返回了 619 条结果，其中部分与已知漏洞相关，部分则用于查找可能存在配置问题的应用实例。

```
   192  auxiliary/scanner/http/manageengine_deviceexpert_user_creds              2014-08-28       normal  No     ManageEngine DeviceExpert User Credentials
   193  auxiliary/scanner/http/manageengine_securitymanager_traversal            2012-10-19       normal  No     ManageEngine SecurityManager Plus 5.5 Directory Traversal
   194  auxiliary/scanner/http/mediawiki_svg_fileaccess                                           normal  No     MediaWiki SVG XML Entity Expansion Remote File Access
   195  auxiliary/scanner/http/meteocontrol_weblog_extractadmin                                   normal  No     Meteocontrol WEBlog Password Extractor
   196  auxiliary/scanner/http/mod_negotiation_brute                                              normal  No     Apache HTTPD mod_negotiation Filename Bruter
   197  auxiliary/scanner/http/mod_negotiation_scanner                                            normal  No     Apache HTTPD mod_negotiation Scanner
   198  auxiliary/scanner/http/ms09_020_webdav_unicode_bypass                                     normal  No     MS09-020 IIS6 WebDAV Unicode Authentication Bypass
   199  auxiliary/scanner/http/ms15_034_http_sys_memory_dump                                      normal  Yes    MS15-034 HTTP Protocol Stack Request Handling HTTP.SYS Memory Information Disclosure
```

虽然它不是最全面的漏洞扫描器，但如果你已经在 Metasploit 中进行其他工作，可以利用这些漏洞扫描模块有针对性地查找特定漏洞。若你能够检测到漏洞且熟悉 Ruby，则可以编写 Metasploit 模块来实现自定义漏洞检测。

### 数据包构造与操作

当你通过网络发送数据时，它遵循一条明确的路径直至从系统网络接口退出。我们在讨论 OSI（开放系统互连）模型时已经提及过这一点。假设你正在访问一个网页，输入 URL 后，浏览器会生成发送到服务器的 HTTP 请求报文头。为简化，我们跳过加密环节，仅说明完整数据包的组成过程。

应用程序向操作系统请求建立到服务器的连接，这会触发操作系统根据应用提供的信息（如主机名或 IP 地址、端口号）构建数据包。默认情况下，端口号为 80（HTTP）或 443（HTTPS）。这些信息使操作系统能够为 TCP 与 IP 层（第 4 与第 3 层）生成相应的报文头。

所有过程表明，应用程序是基于用户交互发起请求的，数据包的报文头信息结构清晰、可追溯至原始数据源。然而，有时你需要发送不遵循常规路径的数据，例如篡改包含非常规数据的报文头。每个报文头字段具有固定长度且为二进制格式，意味着不能在头部字段中传输字符而非数值。网络层以下的报文头绝不会经过 ASCII 解码转换为字符数据。

