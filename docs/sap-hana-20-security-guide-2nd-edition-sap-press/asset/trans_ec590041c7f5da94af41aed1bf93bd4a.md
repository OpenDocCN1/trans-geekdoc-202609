

为确保安全访问，以下示例可帮助您构建正确的 URL：

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`

*   `https://sap-hana.myhost.com:4300/sap/hana/ide/security`

一旦您获得 SAP HANA Web-Based Development Workbench 安全管理器的访问权限，请展开右侧的 Security 节点。展开 Roles 以查看系统中定义的标准角色列表。双击某个角色以打开该角色的管理界面。在选定的角色管理窗口打开后，您可以开始授予和撤销权限。

###### Note

若要对单个用户帐户执行相同操作，请展开 Users 节点并双击所需的用户帐户。

如前所述，我们建议您使用基于仓库的角色来支持 SAP HANA 安全模型。但是，在本节中，我们将简单介绍如果您选择使用标准角色或直接在单个用户帐户上管理安全性时的基本工作流。

在为特定授予对象打开 GUI 管理界面后，您可以按以下方式添加分析权限。单击 Analytic Privileges 选项卡。单击加号 (`+`) 按钮，这将打开 Find Analytic Privileges 窗口，您可以在其中搜索特定的分析权限。选择所需的分析权限并单击 OK 将其添加到列表中。

要保存更改，请按 (`Ctrl`)+(`S`)，或单击左上角的磁盘图标以保存并激活权限。要撤销分析权限，请在列表中选择它并单击红色 X。再次保存更改，使其在数据库系统中生效。

如果出现任何激活问题，警告消息将出现在用户管理窗口底部的状态框中。状态框具有深色背景。错误消息将以红色文本显示。错误仅在尝试激活或保存更改时生成。

### 10.8.4 使用仓库角色授予分析权限

SAP HANA 初始发布时，将分析权限分配给标准角色是当时最佳可用选项。创建了多个 GUI 和 SQL 语句来帮助组织管理向标准角色授予和撤销权限。随着 SAP HANA 的发展，引入了仓库角色以辅助应用程序开发。由于其诸多优势，我们强烈建议使用仓库角色来生成安全模型。现在，让我们回顾向基于仓库的角色授予分析权限以及从基于仓库的角色撤销分析权限的过程。

#### 基于脚本的仓库角色

在 [第 6 章](#06_001.html#h6) 中，我们向您介绍了仓库角色，并概述了创建和管理仓库角色所需的工作流。在本节中，我们将再次回顾将分析权限分配给设计时基于仓库的角色脚本所需的语法。如果您需要了解此过程的更多信息，请参见 [第 6 章](#06_001.html#h6)。

在设计时基于仓库的角色脚本中定义分析权限时，必须以 `analytic privilege:` 开头每一行。冒号后，您可以提供逗号分隔的分析权限列表。在列表末尾，包含分号以结束该行。如果您不想包含逗号分隔的列表，可以在每一行上明确列出每个权限，每行均以 `analytic privilege:` 开头。

以下示例授予存储在 `e-corp.sales.security` 包中的 `ap_sales_reporting_region` 分析权限。请记住，仓库包和对象名称区分大小写：

```
analytic privilege:     
  e-corp.security:ap_sales_reporting_region.analyticprivilege;
```

在最后一个示例中，我们将授予 `_SYS_BI_CP_ALL` 系统分析权限。这种特殊的目录分析权限，一旦授予，将允许完全访问仓库中定义的所有信息视图：

```
catalog analytic privilege : "_SYS_BI_CP_ALL";
```

#### SAP HANA Web-Based Development Workbench 编辑器

SAP HANA Web-Based Development Workbench 编辑器托管在 XS 引擎中，提供了一个您可以用来构建和测试开发工件的界面。从安全角度来看，您可以使用此界面来创建和管理基于仓库的角色。此界面提供了基于仓库角色的所有优势，而无需使用脚本和 SAP HANA 特定领域语言来创建这些角色。但是，您可以使用此同一界面通过 GUI 编辑角色，或在文本编辑器中打开角色文件。

您可以通过受支持的 Internet 浏览器访问 SAP HANA Web-Based Development Workbench 编辑器。以下 URL 可根据您环境的详细信息进行自定义：

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/editor`

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/editor`

将 `<sap_hana_host>` 替换为您环境中 SAP HANA 系统的主机名。将 `<instance_number>` 替换为对应于您 SAP HANA 系统的两位数实例。

为确保安全访问，以下示例可帮助您构建正确的 URL：

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/editor`

*   `https://sap-hana.myhost.com:4300/sap/hana/ide/editor`

要使用 SAP HANA Web-Based Development Workbench 并定义仓库角色，用户帐户首先需要获得 [表 10.4](#10_008.html#t10.4) 中列出的角色之一。用户只需要两个角色中的一个即可使用 SAP HANA Web-Based Development Workbench。

| Role Name || Summary |

| --- | --- |

| `sap.hana.ide.roles::EditorDeveloper` || 在 SAP HANA Web-Based Development Workbench 中，用户只能访问编辑器。在编辑器中，用户可以查看、编辑、创建、删除或激活开发包或开发仓库中找到的基于仓库的角色或其他基于仓库的开发工件。用户除拥有此角色外，还必须拥有包权限才能正确访问和激活基于仓库的角色或其他开发工件。 |

| --- | --- |

| `sap.hana.ide.roles::Developer` || 此角色授予需要完全访问 SAP HANA Web-Based Development Workbench 的用户更高级别的权限。此角色授予对编辑器、目录和安全界面的访问权限，并被视为 `sap.hana.ide.roles::EditorDeveloper` 角色的父角色。 |

**Table 10.4** 使用 SAP HANA Web-Based Development Workbench 编辑器所需的角色

###### 使用 SAP HANA Web-Based Development Workbench 编辑器所需的包权限

除了 [表 10.4](#10_008.html#t10.4) 中列出的角色外，用户还需要为其计划编辑、创建或激活仓库角色的包拥有相应的包权限。此要求也适用于基于脚本的仓库角色。例如，用户需要以下包权限才能使用 SAP HANA Web-Based Development Workbench 编辑器界面创建仓库角色：

*   `REPO.READ`

*   `REPO.EDIT_NATIVE_OBJECTS`

*   `REPO.ACTIVATE_NATIVE_OBJECTS`

SAP HANA Web-Based Development Workbench 编辑器界面（如 [图 10.17](#10_008.html#f10.17) 所示）类似于 SAP HANA Studio 的 Repositories 选项卡中的开发区域。界面左侧是 Content 文件夹，其下是包层次结构。

[![SAP HANA Web-Based Development Workbench Editor](bilderklein/klein10_017.png)](img-f10.17.html) 

**Figure 10.17** SAP HANA Web-Based Development Workbench Editor

