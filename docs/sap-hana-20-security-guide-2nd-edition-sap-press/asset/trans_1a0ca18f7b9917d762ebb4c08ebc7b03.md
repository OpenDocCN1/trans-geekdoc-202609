

SAP HANA Web-Based Development Workbench 安全管理器托管在 XS 引擎中，提供了一个可用于创建用户、创建角色或管理标准角色安全性的界面。此界面提供了 SAP HANA Studio 的 Web 替代方案，也可作为使用 SQL 执行 `GRANT` 和 `REVOKE` 语句的替代方案。

您可以通过受支持的 Internet 浏览器访问 SAP HANA Web-Based Development Workbench。以下 URL 可根据您的环境详细信息进行自定义：

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/security`

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`

在最后一个示例中，将 `<sap_hana_host>` 替换为您环境中 SAP HANA 系统的主机名，并将 `<instance_number>` 替换为与您的 SAP HANA 系统对应的两位数实例号。

为实现安全访问，以下示例应能帮助您构建正确的 URL：

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`

*   `https://sap-hana.myhost.com:4300/sap/hana/ide/security`

一旦您访问了 SAP HANA Web-Based Development Workbench 安全管理器，请在右侧展开 Security 节点。展开 Roles 以查看系统中定义的标准角色列表。双击角色以打开给定角色的管理界面。在选定的角色管理窗口打开后，您可以开始授予和撤销权限。

###### Note

要对单个用户帐户执行相同操作，请展开 Users 节点并双击所需的用户帐户。

请记住，我们建议您使用基于存储库的角色来支持 SAP HANA 安全模型。但是，在本节中，我们将简单介绍如果您选择使用标准角色或直接在单个用户帐户上管理安全性时的基本工作流程。

在为给定接收者打开 GUI 管理界面后，您可以按如下方式添加应用程序权限。单击 Application Privileges 选项卡。单击加号（`+`）按钮以添加并搜索所需的分析权限。将出现 Find Application Privileges 窗口，允许您搜索特定的应用程序权限。选择所需的应用程序权限并单击 OK 将其添加到列表中。

要保存更改，请按 (`Ctrl`)+(`S`) 或单击左上角的磁盘图标以保存并激活权限。要撤销应用程序权限，请在列表中选择它并单击红色 X。再次保存更改以使其在数据库系统中生效。

如果出现任何激活问题，警告消息将出现在用户管理窗口底部的状态窗格中。状态窗格具有深色背景。错误消息将以红色文本显示。仅在尝试激活或保存更改时才会生成错误。

### 11.3.4 在存储库角色中授予应用程序权限

如前所述，将安全模型基于基于存储库的角色是最佳选择。由于其优势，我们将回顾在基于存储库的角色中授予应用程序权限的过程。要将应用程序权限分配给基于存储库的角色，您可以在设计时脚本中修改或开发存储库角色，也可以使用 SAP HANA Web-Based Development Workbench 编辑器来创建和修改基于存储库的角色。

#### 设计时脚本中的 SQL 语法

在 [第 6 章](#06_001.html#h6) 中，我们向您介绍了存储库角色，并概述了创建和管理存储库角色所需的工作流程。在本节中，我们将再次回顾将应用程序权限分配给设计时基于存储库的角色脚本所需的语法。如果您需要更多关于此过程的信息，请参阅 [第 6 章](#06_001.html#h6)。

在基于存储库的角色脚本中定义应用程序权限时，必须以 `application privilege` 开头。在此术语后，包含冒号，然后包含应用程序权限的名称。应用程序权限名称必须包含包层次结构名称、两个冒号和应用程序权限的名称。为区分大小写，名称必须用双引号括起来。在语句末尾，包含分号以结束该行。

以下示例显示用于在基于存储库的角色中授予应用程序权限的单行：

```
application privilege: "sap.hana.security.base::DataService";
```

#### 使用 SAP HANA Web-Based Development Workbench 授予和撤销

SAP HANA Web-Based Development Workbench 编辑器托管在 XS 引擎中，提供了一个可用于构建和测试开发工件的界面。从安全角度来看，您可以使用此界面来创建和管理基于存储库的角色。此界面提供了基于存储库的角色的所有优势，而无需使用脚本和 SAP HANA 特定领域语言来定义存储库角色。但是，您可以使用此同一界面通过 GUI 编辑角色，或在文本编辑器中打开角色文件。

您可以通过受支持的 Internet 浏览器访问 SAP HANA Web-Based Development Workbench。以下 URL 可根据您的环境详细信息进行自定义：

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/editor`

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/editor`

在最后一个示例中，将 `<sap_hana_host>` 替换为您环境中 SAP HANA 系统的主机名，并将 `<instance_number>` 替换为与您的 SAP HANA 系统对应的两位数实例号。

为实现安全访问，以下示例应能帮助您构建正确的 URL：

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/editor`

*   `https://sap-hana.myhost.com:4300/sap/hana/ide/editor`

要使用编辑器，用户帐户首先需要被授予 [表 11.1](#11_003.html#t11.1) 中列出的角色之一。用户只需要两个角色之一即可访问 SAP HANA Web-Based Development Workbench 编辑器。

| Role Name || Summary |

| --- | --- |

| `sap.hana.ide.roles::EditorDeveloper` || 在 SAP HANA Web-Based Development Workbench 中，用户只能访问编辑器。编辑器提供用于创建各种存储库对象的界面，包括基于存储库的角色。 |

| --- | --- |

| `sap.hana.ide.roles::Developer` || 此角色授予需要完全访问 SAP HANA Web-Based Development Workbench 的用户更高级别的权限。此角色授予对编辑器、目录和安全界面的访问权限，并被视为 `sap.hana.ide.roles::EditorDeveloper` 角色的父角色。 |

**表 11.1** 使用 SAP HANA Web-Based Development Workbench 编辑器所需的角色

###### 使用编辑器所需的其他权限

请注意，[表 11.1](#11_003.html#t11.1) 中列出的角色仅允许被授予用户访问界面。用户还需要访问存储库角色所在的包。要将存储库角色授予其他用户和角色，用户需要对名为 "`_SYS_REPO`"."`GRANT_ACTIVATED_ROLE`" 的系统存储过程拥有 EXECUTE 访问权限。要撤销存储库角色，他们需要对 "`_SYS_REPO`"."`REVOKE_ACTIVATED_ROLE`" 存储过程拥有 EXECUTE 访问权限。

一旦您访问了 SAP HANA Web-Based Development Workbench 编辑器，请在右侧展开 Content 节点，然后展开 Packages 以查看系统中定义的包列表。如前所述，存储库角色必须存储在仅安全管理员可以访问的包中。您通常会创建一个名为 Security 的顶级包来托管此类对象。

要创建新的存储库角色，请右键单击要存储角色的包，然后选择 New • Role，如 [图 11.2](#11_003.html#f11.2) 所示。

[![Navigating the SAP HANA Web-Based Development Workbench and a Creating Repository Role](bilderklein/klein11_002.png)](img-f11.2.html)

