

# SAP Logon Tickets

SAP logon tickets 充当数字凭据，用于对支持的外部系统中的 SAP 系统用户进行身份验证。在 SAP HANA 的情况下，logon tickets 可提供从 SAP 应用程序到 XS 引擎 Web 应用程序的单点登录 (SSO)。例如，用户可以登录到托管在 SAP NetWeaver 应用程序服务器 (SAP NetWeaver AS) 上的 Web 应用程序。该应用程序中包含指向基于 XS 引擎的 Web 应用程序的代理链接。基于 SAP NetWeaver 的应用程序配置为生成 logon ticket，并将此票据作为临时会话 HTTP cookie 存储在用户的浏览器中。XS 引擎应用程序配置为支持 logon tickets。单击代理链接时，SAP HANA 系统会在浏览器中找到 cookie，并使用它对 XS 引擎应用程序进行身份验证。

在 SAP HANA 系统信任 logon ticket 之前，必须将外部 SAP 应用程序服务器证书导入 SAP HANA 信任存储。建立此信任后，必须为每个 SAP HANA 用户配置支持此身份验证机制。假设 cookie 中找到的用户 ID 将与 SAP HANA 系统中配置的用户 ID 匹配。与 Kerberos 和 SAML 不同，logon ticket 身份验证启用时，没有可用于显式定义用户外部身份的选项。

## 其他配置信息

有关其他配置详细信息，请参阅 SAP HANA Administration Guide 中的“Configure SSO with SAP Logon Tickets for SAP HANA XS Applications”部分，网址为 [http://s-prs.co/v498213](http://s-prs.co/v498213)。

SAP HANA Security Guide 也提供了有关配置过程的几个其他详细信息。请查找“Single Sign-On Using SAP Logon and Assertion Tickets”部分：[http://s-prs.co/v498214](http://s-prs.co/v498214)。

每个 SAP HANA 用户帐户都必须配置为支持 logon tickets。您可以在 SAP HANA cockpit 的用户管理选项中为用户启用支持，也可以使用 SQL 命令。

要在 SAP HANA cockpit 中为用户启用 logon tickets，请打开用户管理窗口。在用户管理窗口中，选择位于 Kerberos 配置区域下方的 SAP Logon Ticket 复选框，如 [图 12.11](#12_003.html#f12.11) 所示。

[![在 SAP HANA Cockpit 中启用 Logon Ticket](bilderklein/klein12_011.png)](img-f12.11.html)

**图 12.11** 在 SAP HANA Cockpit 中启用 Logon Ticket

要使用 SQL 执行相同操作，请在 SQL 控制台中执行以下命令，将 `<USER_NAME>` 变量替换为 SAP HANA 用户：

```
ALTER USER <USER_NAME> ENABLE SAP LOGON TICKET;
```

# 12.3.5 SAP Assertion Tickets

SAP assertion tickets 的工作方式与 logon tickets 类似，但有一些例外。主要区别在于，assertion tickets 是从一个应用程序服务器通过 HTTP 标头传输到下一个服务器的。在 SAP HANA 的情况下，SAP 凭据是从 HTTP 标头中获取的，而不是从会话 cookie 中获取的。这些票据配置为仅与一个特定目标系统配合使用，并且固定生存期为 2 分钟。使用一次后，assertion ticket 将被删除。大多数专家会认为，由于这些因素，assertion tickets 比 logon tickets 更安全一些。除此之外，assertion ticket 过程与 logon ticket 过程类似。

必须为 SAP HANA 用户帐户配置支持 assertion tickets。您可以在 SAP HANA cockpit 的用户管理选项中为用户启用支持，也可以使用 SQL 命令。

要在 SAP HANA cockpit 中为用户启用 assertion tickets，请打开用户管理窗口。在用户管理窗口中，选择 SAP Assertion Ticket 复选框，如 [图 12.12](#12_003.html#f12.12) 所示。

[![在 SAP HANA Cockpit 中启用 Assertion Ticket](bilderklein/klein12_012.png)](img-f12.12.html)

**图 12.12** 在 SAP HANA Cockpit 中启用 Assertion Ticket

要使用 SQL 执行相同操作，请在 SQL 控制台中执行以下命令，将 `<USER_NAME>` 变量替换为 SAP HANA 用户：

```
ALTER USER <USER_NAME> ENABLE SAP ASSERTION TICKET;
```

# 12.3.6 JWT Identity Providers

JSON Web Token (JWT)，有时发音为“jot”，是一种开放标准 (RFC 7519)，它概述了使用 JavaScript Object Notation (JSON) 对象在两方之间传递安全信息的一种方式。SAP HANA 使用此标准用于第三方 SSO 和两个 SAP HANA 系统之间 SAP HANA 智能数据访问功能的身份验证。与 SAML 类似，您必须导入一个共享证书，该证书在配置为用于 JWT 身份验证的 PSE 中。

在配置 SAP HANA 智能数据访问源时，SAP HANA 系统会在 SAP HANA cockpit 中或通过 SQL 命令注册为 JWT 提供程序。对于 JWT 提供程序，您将使用 JWT claims 设置来配置如何识别用户。在大多数情况下，您将使用传输的 JSON 文件中的 'user' 值。证书在两个 SAP HANA 数据库之间共享，以保护和信任凭据的交换。

## 关于配置 JWT 进行身份验证和 SSO 的其他信息

由于此设置仅支持特定用例，本章不会进一步介绍详细信息。请查看 SAP HANA Platform 的 SAP HANA Administration Guide，尤其是可在 [http://s-prs.co/v498215](http://s-prs.co/v498215) 上找到的“Managing Single-Sign On (SSO) with JSON Web Tokens”部分。

# 12.4 案例研究：添加 SAML 身份用户帐户

在最初实施 SAP HANA 时，E-Corporation 在决定实施 SAML 身份验证之前创建了几百个用户帐户。现在，公司需要一个脚本来更新现有用户帐户并添加相应的 SAML 身份。在 [第 4 章](#04_001.html#h4) 中，我们讨论了 E-Corporation 如何从文件导入用户数据并使用存储过程来配置用户。该过程可以创建新用户并添加其 SAML 身份，但无法对现有用户帐户执行相同操作。为了解决此问题，E-Corporation 决定创建一个新的存储过程，该过程将向现有帐户添加 SAML 身份。该过程仅会为列在 `Security.Tables::adusers` 表中且尚未拥有 SAML 身份的用户添加 SAML 身份。

公司对存储过程和以编程方式更新用户帐户所需的流程有以下其他要求：

* 仅当用户帐户在表 `Security.Tables::adusers` 中有记录时，才会用 SAML 身份对其进行更新。该表包含从外部系统获取的用户属性。
* 用户帐户的内部基本身份验证密码不会更改；用户可以继续使用内部基本身份验证和 SAML 身份验证进行 SSO。
* 用户帐户的内部基本身份验证密码生存期将符合 E-Corporation 配置的密码策略。

要在 SAP HANA Web-Based Development Workbench 编辑器中创建基于存储库的存储过程，请右键单击 `Security.Provisioning` 包并选择 New • HDB Procedure。

将出现 New Stored Procedure 窗口。在 File Name\* 字段中，输入“ADD\_SAML\_TO\_EXISTING\_USERS”，使用大写字母。在 schema 字段中，输入或选择 `Security_tables`。单击 Create 保存文件并打开 `ADD_SAML_TO_EXISTING_USERS.hdbtable` 配置文件进行编辑。将出现一个空白模板，可在定义过程时将其用作指南。

要在 SQL 中定义基于存储库的 `ADD_SAML_TO_EXISTING_USERS` 存储过程，请使用 [清单 12.4](#12_004.html#l12.4) 中所示的语法。按 (Ctrl)+(S) 激活设计时脚本。

