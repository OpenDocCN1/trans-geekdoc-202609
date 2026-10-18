

# 配置和管理证书

配置用于身份验证和安全通信的证书所需的流程和工作流似乎随着每个新版本的 SAP HANA 而发生变化。因此，您应始终查阅适用于您 SAP HANA 版本的文档。在大多数情况下，您会在 SAP HANA 2.0 SPS 04 Administration Guide 中找到配置步骤，该指南可在 [http://s-prs.co/v498216](http://s-prs.co/v498216) 处查阅。

SAP HANA 2.0 SPS 04 Security Guide 也提供了关于配置过程的几个额外细节，可在 [http://s-prs.co/v498217](http://s-prs.co/v498217) 处查阅。

使用 SAP Web Dispatcher 管理 GUI 将大大简化管理 PSE 文件及其证书的过程。您可能会认为，在适用时使用数据库内的 PSE 管理选项是最佳选择。但是，某些功能（例如 HTTP SSL 和内部服务器加密）仍必须在文件系统上找到的 PSE 文件中进行管理。在下一节中，我们将探讨为连接到 SAP HANA 的客户端启用加密的可用选项。

## 13.2 客户端加密设置

在本节中，我们将回顾为 SAP HANA Studio、XS 引擎应用程序以及 JDBC/ODBC 客户端启用 TLS 或 SSL 设置的过程。您的组织必须了解如何配置这些选项，以保护客户端与 SAP HANA 之间的数据通信或传输。

### 13.2.1 SAP HANA Studio

在 SAP HANA Studio 中配置系统连接时，有多个选项可用于启用基于 SSL 的通信。当使用不受信任或不受限制的网络访问 SAP HANA 时，启用基于 SSL 的通信加密非常重要。例如，如果您从家中的桌面电脑访问基于云的 SAP HANA 实例，那么您的桌面电脑与 SAP HANA 之间的通信通道可能会经过多个网络跳转。每个跳转都会引入有人或某个组织可能正在监控和捕获您的 TCP/IP 数据包的可能性。如果没有加密，这些数据包可能会被重建，其中的信息可能会暴露给未经授权的个人。同样的漏洞甚至可能存在于私有企业网络中。因此，组织应加密可能包含敏感数据的通信。

要为 SAP HANA Studio 中现有系统连接启用 SSL 加密，请右键单击 Systems 选项卡中列出的系统。将出现 Properties 窗口，右侧有三个属性选项卡。第一个选项卡 General（如 [Figure 13.9](#13_002.html#f13.9) 所示）包含 Connect Using SSL 复选框。要强制连接使用 SSL 加密，请选择此复选框。

[![Configuring SAP HANA Studio Connection for SSL Communication](bilderklein/klein13_009.png)](img-f13.9.html)

**Figure 13.9** Configuring SAP HANA Studio Connection for SSL Communication

如果您使用的是自签名证书或 SAP HANA Studio 密钥库中不受信任的证书，请选择 Additional Properties 选项卡以配置一些其他选项。在此选项卡上，取消选择 Validate the SSL Certificate 复选框以忽略证书问题，如 [Figure 13.10](#13_002.html#f13.10) 所示。

SAP HANA 系统部署时带有可用于 TLS 通信的自签名证书。但是，这些证书不会被 SAP HANA Studio 等客户端信任。不受信任或自签名的证书仍然可以提供加密通信。如果 SAP HANA Studio 无法验证证书，您的组织仍然可以依赖该证书来加密客户端与服务器之间的通信，并且 SAP HANA Studio 确实提供了一个选项来忽略此类证书的问题。

[![Configuring SAP HANA Studio Connection to Ignore Untrusted SSL Certificate Issues](bilderklein/klein13_010.png)](img-f13.10.html)

**Figure 13.10** Configuring SAP HANA Studio Connection to Ignore Untrusted SSL Certificate Issues

单击 OK 以启用新的 SSL 设置。Systems 选项卡中列出的系统现在应显示右侧带有闭合黄色挂锁的图标，指示客户端与服务器之间的连接已加密。

在下一节中，我们将回顾保护托管在 XS 引擎中的基于 Web 的应用程序通信所需的步骤。

### 13.2.2 XS Engine Web-Based Applications

默认情况下，基于 Web 的 SAP HANA XS 应用程序的 SSL 访问在安装期间使用自签名证书进行配置。您也可以选择从公共受信任的证书颁发机构部署新证书。基于 Web 的 SAP HANA XS 应用程序的默认 SSL 监听端口为 43XX，其中 XX 表示两位数的 SAP HANA 实例号。虽然默认可用，但 SSL 访问并非 SAP HANA XS 引擎应用程序的强制要求。

要正确保护 SAP HANA XS 引擎基于 Web 的应用程序，应强制使用 SSL。此强制执行是按包启用的。SAP HANA 中的存储库包与网站文件夹结构具有直接关系。因此，您可以按子网站或网站文件夹结构强制执行 SSL 访问。

要强制 SSL，您必须访问托管在每个 SAP HANA 实例的 SAP HANA XS 引擎中的基于 Web 的 SAP HANA XS 工件管理应用程序。要访问此管理门户，请使用包含您详细信息的以下 URL；第二个 URL 提供了完整示例：

* `http://<hana host>:80<instance number>/sap/hana/xs/admin`
* `http://w4-db-hana.e-corp.internal.net:8000/sap/hana/xs/admin/`

如 [Figure 13.11](#13_002.html#f13.11) 所示的登录页面，左侧将首先显示 Application Objects 窗格。右侧是每个选定应用程序对象的 Runtime Configuration Details。

[![SAP HANA XS Artifact Administration Landing Page](bilderklein/klein13_011.png)](img-f13.11.html)

**Figure 13.11** SAP HANA XS Artifact Administration Landing Page

要编辑包，请在 Application Objects 窗格中选择包层次结构级别。在右侧的 Runtime Configuration Details 窗格中，单击页面底部的大型 Edit 按钮以打开包配置选项。在 Security & Authentication 部分中，选择 Force SSL 复选框，如 [Figure 13.12](#13_002.html#f13.12) 所示。

[![Forcing SSL Access](bilderklein/klein13_012.png)](img-f13.12.html)

**Figure 13.12** Forcing SSL Access

选择此复选框将强制包或相应的网站树结构使用 SSL 加密。单击窗口底部的 Save 按钮以激活新的配置选项。启用此选项后，用户将别无选择，只能使用加密与基于 Web 的应用程序进行交互。

### 13.2.3 JDBC and ODBC Drivers

JDBC 和 ODBC 是软件应用程序用于与 SAP HANA 交互的行业标准应用程序编程接口 (API)。这些 API 包含在 SAP HANA 客户端应用程序中。SAP HANA 客户端是包含多个行业标准编程接口的应用程序代码，可用于访问 SAP HANA。例如，一些组织使用这些 API 来授予其软件应用程序对托管在 SAP HANA 中的数据的查询访问权限。由于客户端应用程序与 SAP HANA 之间的通信可能包含敏感数据，因此这些通信通道应进行加密。

