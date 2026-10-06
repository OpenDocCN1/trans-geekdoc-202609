

# 表 19.1：IIS 8 的 OS 角色服务（与服务器管理器向导中的顺序一致）（续）

| 服务名称 (GUI) | POWERSHELL 功能名称 | 描述 | 默认 |
| :--- | :--- | :--- | :--- |
| HTTP 错误 | Web-Http-Errors | 自定义错误消息 | 是 |
| 静态内容 | Web-Static-Content | 发布静态 Web 文件格式 | 是 |
| HTTP 重定向 | Web-Http-Redirect | 将一个 URL 重定向到另一个 URL | 否 |
| WebDAV 发布 | Web-DAV-Publishing | 通过 HTTP 向/从 Web 服务器发布文件 | 否 |
| HTTP 日志 | Web-Http-Logging | 提供网站活动的日志记录 | 是 |
| 自定义日志 | Web-Custom-Logging | 创建自定义日志模块 | 否 |
| 日志工具 | Web-Log-Libraries | 提供 Web 服务器日志管理和基础设施辅助 | 否 |
| ODBC 日志 | Web-ODBC-Logging |为 Web 服务器活动提供到符合 ODBC 标准的数据库的基础，并检索其用于 Web 显示 | 否 |
| 请求监控 | Web-Request-Monitor | 提供捕获 IIS 工作进程信息（包括 HTTP 请求详情）的基础设施 | 否 |
| 跟踪 | Web-Http-Tracing | 提供捕获定义事件的基础设施 | 否 |
| 静态内容压缩 | Web-Stat-Compression | 提供用于缓存的内容压缩的基础设施 | 是 |
| 动态内容压缩 | Web-Dyn-Compression | 提供压缩动态内容的基础设施 | 否 |
| 请求过滤 | Web-Filtering | 根据管理员定义的规则过滤传入的请求 | 是 |
| 基本身份验证 | Web-Basic-Auth | 支持基本身份验证 | 否 |
| 集中 SSL 证书支持 | Web-CertProvider | 支持集中式 SSL 证书 | 否 |
| 客户端证书映射验证 | Web-Client-Auth | 支持使用 Active Directory 进行客户端证书验证（跨多个 Web 服务器的一对一映射） | 否 |
| 摘要身份验证 | Web-Digest-Auth | 支持密码哈希身份验证 | 否 |
| IIS 客户端证书映射验证 | Web-Cert-Auth | 支持使用 IIS 进行客户端证书验证（一对一或多一映射） | 否 |
| IP 和域限制 | Web-IP-Security | 通过请求的 IP 地址或域名传递内容 | 否 |
| URL 授权 | Web-Url-Auth | 支持与用户、组或 HTTP 请求头谓词相关的基于规则的内容限制 | 否 |
| Windows 身份验证 | Web-Windows-Auth | 支持 Windows 账户身份验证 | 否 |
| .NET 扩展 3.5 | Web-Net-Ext | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| .NET 扩展 4.5 | Web-Net-Ext45 | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| 应用程序初始化 | Web-AppInit | 在提供 Web 页面之前执行昂贵的 Web 初始化任务 | 否 |
| ASP | Web-ASP | 提供 Active Server Page 服务器端脚本（包括 VScript 和 JScript） | 否 |
| ASP.NET 3.5 | Web-Asp-Net | 为基于 .NET Framework 的托管应用程序提供服务器端对象模型 | 否 |
| ASP.NET 4.5 | Web-Asp-Net45 | 为基于 .NET 4.5 Framework 的托管应用程序提供服务器端对象模型 | 否 |
| CGI | Web-CGI | 为外部程序的 CGI 脚本提供 CGI 支持 | 否 |
| ISAPI 扩展 | Web-ISAPI-Ext | 支持通过请求时启用的 ISAPI 扩展提供动态 Web 内容 | 否 |
| ISAPI 过滤器 | Web-ISAPI-Filter | 支持过滤 Web 服务器请求的文件，以扩展或更改特定功能 | 否 |
| 服务器端包含 (SSI) | Web-Includes | 提供动态 HTML 页面的脚本生成 | 否 |
| WebSocket 协议 | Web-WebSockets | 支持通过 WebSocket 协议通信的应用 | 否 |
| FTP 服务器 | Web-Ftp-Server | 提供构建使用 FTP 上传和下载 FTP 站点的基础设施 | 否 |
| FTP 服务 | Web-Ftp-Service | Enable FTP 发布 | 否 |
| FTP 扩展性 | Web-Ftp-Ext | 支持作为自定义提供程序、ASP.NET 用户或 IIS 管理器的 FTP 扩展性 | 否 |
| IIS 主机 Web Core | Web-WHC | 允许 IIS 之外的应用程序使用自己的 .config 文件提供服务 | 否 |
| IIS 管理控制台 | Web-Mgmt-Console | 提供 IIS 7.5 服务的 GUI 管理（不包括 FTP 或 SMTP） | 是 |
| IIS 6 管理兼容性 | Web-Mgmt-Compat | 为现有的 IIS 6.0 管理服务提供 ASP 和 ADSI 支持 | 否 |
| IIS 6 元数据库兼容性 | Web-Metabase | 为 ASP 和 ADSI 提供 IIS 6.0 元数据库和配置支持 | 否 |
| IIS 6 管理控制台 | Web-Mgmt-Console | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IIS 6 脚本工具 | Web-Scripting | 提供在 IIS 7.5（包括 AD 和 WAS）上运行 IIS 脚本的基础设施 | 否 |
| IIS 6 WMI 兼容性 | Web-WMI | 提供在 IIS 7.5 上运行 IIS 脚本的基础设施 | 否 |
| IIS 脚本台 | Web-Mgmt | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IP 和域限制 | Web-IP | 通过请求的 IP 地址或域名传递内容 | 否 |
| URL 授权 | Web-Url-Auth | 支持与用户、组或 HTTP 请求头谓词相关的基于规则的内容限制 | 否 |
| Windows 身份验证 | Web-Windows-Auth | 支持 Windows 账户身份验证 | 否 |
| .NET 扩展 3.5 | Web-Net-Ext | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| .NET 扩展 4.5 | Web-Net-Ext45 | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| 应用程序初始化 | Web-AppInit | 在提供 Web 页面之前执行昂贵的 Web 初始化任务 | 否 |
| ASP | Web-ASP | 提供 Active Server Page 服务器端脚本（包括 VScript 和 JScript） | 否 |
| ASP.NET 3.5 | Web-Asp-Net | 为基于 .NET Framework 的托管应用程序提供服务器端对象模型 | 否 |
| ASP.NET 4.5 | Web-Asp-Net45 | 为基于 .NET 4.5 Framework 的托管应用程序提供服务器端对象模型 | 否 |
| CGI | Web-CGI | 为外部程序的 CGI 脚本提供 CGI 支持 | 否 |
| ISAPI 扩展 | Web-ISAPI-Ext | 支持通过请求时启用的 ISAPI 扩展提供动态 Web 内容 | 否 |
| ISAPI 过滤器 | Web-ISAPI-Filter | 支持过滤 Web 服务器请求的文件，以扩展或更改特定功能 | 否 |
| 服务器端包含 (SSI) | Web-Includes | 提供动态 HTML 页面的脚本生成 | 否 |
| WebSocket 协议 | Web-WebSockets | 支持通过 WebSocket 协议通信的应用 | 否 |
| FTP 服务器 | Web-Ftp-Server | 提供构建使用 FTP 上传和下载 FTP 站点的基础设施 | 否 |
| FTP 服务 | Web-Ftp-Service | Enable FTP 发布 | 否 |
| FTP 扩展性 | Web-Ftp-Ext | 支持作为自定义提供程序、ASP.NET 用户或 IIS 管理器的 FTP 扩展性 | 否 |
| IIS 主机 Web Core | Web-WHC | 允许 IIS 之外的应用程序使用自己的 .config 文件提供服务 | 否 |
| IIS 管理控制台 | Web-Mgmt-Console | 提供 IIS 7.5 服务的 GUI 管理（不包括 FTP 或 SMTP） | 是 |
| IIS 6 管理兼容性 | Web-Mgmt-Compat | 为现有的 IIS 6.0 管理服务提供 ASP 和 ADSI 支持 | 否 |
| IIS 6 元数据库兼容性 | Web-Metabase | 为 ASP 和 ADSI 提供 IIS 6.0 元数据库和配置支持 | 否 |
| IIS 6 管理控制台 | Web-Mgmt-Console | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IIS 6 脚本工具 | Web-Scripting | 提供在 IIS 7.5（包括 AD 和 WAS）上运行 IIS 脚本的基础设施 | 否 |
| IIS 6 WMI 兼容性 | Web-WMI | 提供在 IIS 7.5 上运行 IIS 脚本的基础设施 | 否 |
| IIS 脚本台 | Web-Mgmt | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IP 和域限制 | Web-IP | 通过请求的 IP 地址或域名传递内容 | 否 |
| URL 授权 | Web-Url-Auth | 支持与用户、组或 HTTP 请求头谓词相关的基于规则的内容限制 | 否 |
| Windows 身份验证 | Web-Windows-Auth | 支持 Windows 账户身份验证 | 否 |
| .NET 扩展 3.5 | Web-Net-Ext | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| .NET 扩展 4.5 | Web-Net-Ext45 | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| 应用程序初始化 | Web-AppInit | 在提供 Web 页面之前执行昂贵的 Web 初始化任务 | 否 |
| ASP | Web-ASP | 提供 Active Server Page 服务器端脚本（包括 VScript 和 JScript） | 否 |
| ASP.NET 3.5 | Web-Asp-Net | 为基于 .NET Framework 的托管应用程序提供服务器端对象模型 | 否 |
| ASP.NET 4.5 | Web-Asp-Net45 | 为基于 .NET 4.5 Framework 的托管应用程序提供服务器端对象模型 | 否 |
| CGI | Web-CGI | 为外部程序的 CGI 脚本提供 CGI 支持 | 否 |
| ISAPI 扩展 | Web-ISAPI-Ext | 支持通过请求时启用的 ISAPI 扩展提供动态 Web 内容 | 否 |
| ISAPI 过滤器 | Web-ISAPI-Filter | 支持过滤 Web 服务器请求的文件，以扩展或更改特定功能 | 否 |
| 服务器端包含 (SSI) | Web-Includes | 提供动态 HTML 页面的脚本生成 | 否 |
| WebSocket 协议 | Web-WebSockets | 支持通过 WebSocket 协议通信的应用 | 否 |
| FTP 服务器 | Web-Ftp-Server | 提供构建使用 FTP 上传和下载 FTP 站点的基础设施 | 否 |
| FTP 服务 | Web-Ftp-Service | Enable FTP 发布 | 否 |
| FTP 扩展性 | Web-Ftp-Ext | 支持作为自定义提供程序、ASP.NET 用户或 IIS 管理器的 FTP 扩展性 | 否 |
| IIS 主机 Web Core | Web-WHC | 允许 IIS 之外的应用程序使用自己的 .config 文件提供服务 | 否 |
| IIS 管理控制台 | Web-Mgmt-Console | 提供 IIS 7.5 服务的 GUI 管理（不包括 FTP 或 SMTP） | 是 |
| IIS 6 管理兼容性 | Web-Mgmt-Compat | 为现有的 IIS 6.0 管理服务提供 ASP 和 ADSI 支持 | 否 |
| IIS 6 元数据库兼容性 | Web-Metabase | 为 ASP 和 ADSI 提供 IIS 6.0 元数据库和配置支持 | 否 |
| IIS 6 管理控制台 | Web-Mgmt-Console | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IIS 6 脚本工具 | Web-Scripting | 提供在 IIS 7.5（包括 AD 和 WAS）上运行 IIS 脚本的基础设施 | 否 |
| IIS 6 WMI 兼容性 | Web-WMI | 提供在 IIS 7.5 上运行 IIS 脚本的基础设施 | 否 |
[/content]

由于提供的文本中出现了大量的重复内容（表格内容完全重复多次），以下是基于你提供的原始文本内容的翻译译文：

[content]

# 表 19.1：IIS 8 的 OS 角色服务（与服务器管理器向导中的顺序一致）（续）

| 服务名称 (GUI) | POWERSHELL 功能名称 | 描述 | 默认 |
| :--- | :--- | :--- | :--- |
| HTTP 错误 | Web-Http-Errors | 自定义错误消息 | 是 |
| 静态内容 | Web-Static-Content | 发布静态 Web 文件格式 | 是 |
| HTTP 重定向 | Web-Http-Redirect | 将一个 URL 重定向到另一个 URL | 否 |
| WebDAV 发布 | Web-DAV-Publishing | 通过 HTTP 向/从 Web 服务器发布文件 | 否 |
| HTTP 日志 | Web-Http-Logging | 提供网站活动的日志记录 | 是 |
| 自定义日志 | Web-Custom-Logging | 创建自定义日志模块 | 否 |
| 日志工具 | Web-Log-Libraries | 提供 Web 服务器日志管理和基础设施辅助 | 否 |
| ODBC 日志 | Web-ODBC-Logging |为 Web 服务器活动提供到符合 ODBC 标准的数据库的基础，并检索其用于 Web 显示 | 否 |
| 请求监控 | Web-Request-Monitor | 提供捕获 IIS 工作进程信息（包括 HTTP 请求详情）的基础设施 | 否 |
| 跟踪 | Web-Http-Tracing | 提供捕获定义事件的基础设施 | 否 |
| 静态内容压缩 | Web-Stat-Compression | 提供用于缓存的内容压缩的基础设施 | 是 |
| 动态内容压缩 | Web-Dyn-Compression | 提供压缩动态内容的基础设施 | 否 |
| 请求过滤 | Web-Filtering | 根据管理员定义的规则过滤传入的请求 | 是 |
| 基本身份验证 | Web-Basic-Auth | 支持基本身份验证 | 否 |
| 集中 SSL 证书支持 | Web-CertProvider | 支持集中式 SSL 证书 | 否 |
| 客户端证书映射验证 | Web-Client-Auth | 支持使用 Active Directory 进行客户端证书验证（跨多个 Web 服务器的一对一映射） | 否 |
| 摘要身份验证 | Web-Digest-Auth | 支持密码哈希身份验证 | 否 |
| IIS 客户端证书映射验证 | Web-Cert-Auth | 支持使用 IIS 进行客户端证书验证（一对一或多一映射） | 否 |
| IP 和域限制 | Web-IP-Security | 通过请求的 IP 地址或域名传递内容 | 否 |
| URL 授权 | Web-Url-Auth | 支持与用户、组或 HTTP 请求头谓词相关的基于规则的内容限制 | 否 |
| Windows 身份验证 | Web-Windows-Auth | 支持 Windows 账户身份验证 | 否 |
| .NET 扩展 3.5 | Web-Net-Ext | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| .NET 扩展 4.5 | Web-Net-Ext45 | 在请求或 UI 中扩展 Web 服务器功能 | 否 |
| 应用程序初始化 | Web-AppInit | 在提供 Web 页面之前执行昂贵的 Web 初始化任务 | 否 |
| ASP | Web-ASP | 提供 Active Server Page 服务器端脚本（包括 VScript 和 JScript） | 否 |
| ASP.NET 3.5 | Web-Asp-Net | 为基于 .NET Framework 的托管应用程序提供服务器端对象模型 | 否 |
| ASP.NET 4.5 | Web-Asp-Net45 | 为基于 .NET 4.5 Framework 的托管应用程序提供服务器端对象模型 | 否 |
| CGI | Web-CGI | 为外部程序的 CGI 脚本提供 CGI 支持 | 否 |
| ISAPI 扩展 | Web-ISAPI-Ext | 支持通过请求时启用的 ISAPI 扩展提供动态 Web 内容 | 否 |
| ISAPI 过滤器 | Web-ISAPI-Filter | 支持过滤 Web 服务器请求的文件，以扩展或更改特定功能 | 否 |
| 服务器端包含 (SSI) | Web-Includes | 提供动态 HTML 页面的脚本生成 | 否 |
| WebSocket 协议 | Web-WebSockets | 支持通过 WebSocket 协议通信的应用 | 否 |
| FTP 服务器 | Web-Ftp-Server | 提供构建使用 FTP 上传和下载 FTP 站点的基础设施 | 否 |
| FTP 服务 | Web-Ftp-Service | Enable FTP 发布 | 否 |
| FTP 扩展性 | Web-Ftp-Ext | 支持作为自定义提供程序、ASP.NET 用户或 IIS 管理器的 FTP 扩展性 | 否 |
| IIS 主机 Web Core | Web-WHC | 允许 IIS 之外的应用程序使用自己的 .config 文件提供服务 | 否 |
| IIS 管理控制台 | Web-Mgmt-Console | 提供 IIS 7.5 服务的 GUI 管理（不包括 FTP 或 SMTP） | 是 |
| IIS 6 管理兼容性 | Web-Mgmt-Compat | 为现有的 IIS 6.0 管理服务提供 ASP 和 ADSI 支持 | 否 |
| IIS 6 元数据库兼容性 | Web-Metabase | 为 ASP 和 ADSI 提供 IIS 6.0 元数据库和配置支持 | 否 |
| IIS 6 管理控制台 | Web-Mgmt-Console | 提供远程 IIS 服务器管理以及 FTP 和 SMTP 管理的基础设施 | 否 |
| IIS 6 脚本工具 | Web-Scripting | 提供在 IIS 7.5（包括 AD 和 WAS）上运行 IIS 脚本的基础设施 | 否 |
| IIS 6 WMI 兼容性 | Web-WMI | 提供在 IIS 7.5 上运行 IIS 脚本的基础设施 | 否 |

