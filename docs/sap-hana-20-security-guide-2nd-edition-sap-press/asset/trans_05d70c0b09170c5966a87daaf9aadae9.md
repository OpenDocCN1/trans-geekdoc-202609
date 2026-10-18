

在 Windows 操作系统上配置 ODBC 数据源名称（`DSN`）时，你会发现有用于配置基于 SSL 的连接的选项。就像在 SAP HANA Studio 中一样，你可以选择绕过 SSL 证书的验证。

例如，在安装了 SAP HANA 客户端的 Windows 操作系统上，你可以使用 ODBC 数据源管理器来配置 SAP HANA ODBC DNS。在 Windows 开始菜单中搜索 ODBC 管理器。打开 ODBC 管理器后，选择“系统 DSN”选项卡。单击“添加”以设置新的 DSN。在弹出窗口中，浏览系统上安装的数据源驱动程序列表。查找名为 `HDBODBC32` 或 `HDBODBC` 的驱动程序（取决于你正在配置的 DSN 版本）。选择驱动程序并单击“完成”。将出现一个新窗口，允许你定义数据源名称以及 SAP HANA 服务器和端口。要配置 SSL，请单击右下角的“设置”按钮。SAP HDB 高级设置窗口将出现，如 [图 13.13](#13_002.html#f13.13) 所示。

[![为 SSL 通信配置 Windows ODBC DNS](bilderklein/klein13_013.png)](img-f13.13.html)

**图 13.13** 为 SSL 通信配置 Windows ODBC DNS

要启用 SSL 通信，请选择“使用 SSL 连接”复选框。如果你使用的 SSL 证书不会被自动信任，请保持“验证 SSL 证书”复选框未选中状态。如果你需要覆盖 SSL 证书中列出的主机的通用名称，请在“证书中覆盖主机名”字段中输入备用主机名。单击“确定”保存高级设置，然后再次单击“确定”保存 DSN。

大多数 JDBC 连接字符串将提供类似的选项。JDBC 驱动程序不能在 Windows ODBC 管理器中使用。大多数基于 Java 的应用程序将提供其自己的 SAP HANA JDBC 连接配置界面。鉴于其专有性质，我们不会为 JDBC 驱动程序提供逐步配置示例，但请注意，ODBC 驱动程序可用的相同 SSL 选项也适用于 JDBC 驱动程序。应用程序供应商拥有可用的 API，即使他们选择不将 SSL 选项纳入其配置 GUI 中。例如，[清单 13.2](#13_002.html#l13.2) 中显示的代码取自基于 Java 的 SAP HANA Studio 跟踪文件。在连接字符串中，你会看到 `encrypt=true` 和 `validateCertificate=false` 选项在跟踪文件结果中列出。

```
new Connection 'jdbc:sap://w3-hanan01.e-corp.internal.root:30015; 
10.54.240.31:30015'
locale=en_US
user=SYSTEM
password=***
reconnect=true
timeout=0
encrypt=true
validateCertificate=false
```

**清单 13.2** SAP HANA Studio 跟踪文件显示与 SAP HANA 的安全 JDBC 连接

为 JDBC 或 ODBC 连接层启用 SSL 通信是一种良好的做法，可确保与客户端和服务器交换的信息受到良好保护，免受未经授权的访问。但是，除非 SAP HANA 系统本身要求 SSL 连接，否则配置此设置是可选的。幸运的是，SAP HANA 提供了一个选项，用于强制客户端使用 SSL 安全连接，该选项位于“配置”选项卡下的路径 `global.ini • communication • sslenforce` 中。[图 13.14](#13_002.html#f13.14) 显示了 SAP HANA 驾驶舱 INI 配置界面中此选项的概览。

此选项默认为 False，意味着客户端可以选择如何配置连接。当选项设置为 True 时，客户端必须启用“使用 SSL 连接”选项。除了使用 SAP HANA 驾驶舱的 INI 文件编辑器外，你还可以发出以下 SQL 语句来启用该选项：

```
ALTER SYSTEM ALTER CONFIGURATION 
('global.ini','SYSTEM')
SET ('communication','sslenforce') ='true' WITH RECONFIGURE;
```

[![为 global.ini 强制 SSL 客户端连接的通信设置](bilderklein/klein13_014.png)](img-f13.14.html)

**图 13.14** 为 global.ini 强制 SSL 客户端连接的通信设置

要禁用该选项，请发出以下 SQL 语句：

```
ALTER SYSTEM ALTER CONFIGURATION 
('global.ini','SYSTEM')
SET ('communication','sslenforce') ='false' WITH RECONFIGURE;
```

### 13.2.4 SAP HANA 驾驶舱

在 SAP HANA 驾驶舱中注册系统时，你也可以选择加密通信。在注册系统时，在“连接”部分建立了使用加密连接的选项。在“通过导入的受信任证书使用加密 (TLS/SSL)”消息下，有一系列复选框可供使用。让我们逐一查看每个复选框，如下所示：

*   `Encrypt SAP Control connection`

    此选项强制 SAP HANA 驾驶舱通过 SSL 与 SAP 控制子系统通信。选择此复选框是良好的做法，因为通过此通道传递的凭据是操作系统上用户的凭据。

*   `Encrypt the database connection`

    此选项强制 SAP HANA 驾驶舱通过 SSL 与数据库通信。同样，数据库级凭据通过此通道传递，加密该通信有助于避免中间人攻击。

*   `Validate the certificate`

    如果你使用的是默认安装证书或自签名 SSL 证书，请取消选择此复选框。仅当安装的证书来自 SAP HANA 扩展应用程序服务、高级模型引擎（XSA 引擎）已配置为信任的受信任证书颁发机构时，才选择此选项。否则，连接将失败。

*   `Override hostname in certificate`

    当使用受信任证书且证书通用名称与连接定义中使用的完全限定的 SAP HANA 服务器主机名不同时，请选择此复选框。当使用 DNS 别名来支持 SAP HANA 数据库连接时，有时会出现这种不匹配。将证书的通用名称放入文本框中，因为 SAP HANA 驾驶舱将假设该主机名已在连接中定义。

SAP HANA 提供了多种用于管理证书和加密客户端与 SAP HANA 服务器之间通信的选项。在下一节中，我们将回顾如何使用加密来保护 SAP HANA 持久存储层。

## 13.3 加密数据

加密与 SAP HANA 的通信至关重要。但是，加密也可用于保护存储在 SAP HANA 服务器持久层上的数据。虽然 SAP HANA 是内存数据库，但其数据并非完全存储在内存中。SAP HANA 会定期创建保存点，将内存数据镜像到磁盘。保存点过程将数据保存到每个 SAP HANA 服务器节点上托管的 `/hana/data/<SID>` 卷中。

除了这些数据保存点外，每个已提交的事务同时写入每个 SAP HANA 服务器节点上的 `/hana/log/<SID>` 卷和内存中。在发生断电的情况下，SAP HANA 系统将使用存储在 `/data` 卷中的持久数据快照和每个 SAP HANA 服务器节点上的 `/log` 卷中的事务重做日志的组合来重新创建内存数据。因为这些存储区域包含 SAP HANA 中托管数据的二进制版本，所以你应该加密这些数据。

如果你将数据库备份到 NFS 位置的磁盘上，情况也是如此。除了数据和日志加密外，SAP HANA 还支持备份媒体加密。启用后，备份文件将使用与加密数据和日志分区相同的根密钥进行加密。启用后，除非该数据库具有完全相同的根密钥，否则加密的备份文件无法在 SAP HANA 数据库中恢复或访问。

