

SAP HANA Web-Based Development Workbench 编辑器托管在 XS 引擎中，提供了一个可用于构建和测试开发工件的界面。从安全角度来看，你可以使用此界面创建和管理基于存储库的角色。此界面提供了基于存储库的角色的所有优势，而无需使用脚本和 SAP HANA 领域特定语言来定义存储库角色。但是，你可以使用此界面通过 GUI 编辑角色，或在文本编辑器中打开角色文件。

你可以通过受支持的 Internet 浏览器访问 SAP HANA Web-Based Development Workbench 编辑器。以下 URL 可根据你的环境详细信息进行自定义：

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/editor`
*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/editor`

将 `<sap_hana_host>` 替换为你环境中 SAP HANA 系统的主机名。将 `<instance_number>` 替换为对应于你的 SAP HANA 系统的两位数实例。

为了安全访问，以下示例应能帮助你构建正确的 URL：

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/editor`
*   `https://sap-hana.myhost.com:4300/sap/hana/ide/editor`

要使用 SAP HANA Web-Based Development Workbench 并定义存储库角色，用户帐户首先需要被授予 [表 7.1](#07_003.html#t7.1) 中列出的角色之一。用户只需要两个角色中的一个即可使用 SAP HANA Web-Based Development Workbench。

| 角色名称 | 摘要 |
| --- | --- |
| `sap.hana.ide.roles::EditorDeveloper` | 在 SAP HANA Web-Based Development Workbench 中，用户只能访问编辑器。在编辑器中，用户可以查看、编辑、创建、删除或激活开发包或开发存储库中找到的基于存储库的角色或其他基于存储库的开发工件。用户除了拥有此角色外，还必须拥有包权限才能正确访问和激活存储库角色或其他开发工件。 |
| `sap.hana.ide.roles::Developer` | 此角色授予需要完全访问 SAP HANA Web-Based Development Workbench 的用户更高级别的权限。此角色授予对编辑器、目录和安全界面的访问权限，并被视为 `sap.hana.ide.roles::EditorDeveloper` 角色的父角色。 |

**表 7.1** 使用 SAP HANA Web-Based Development Workbench 编辑器所需的角色

###### 使用 SAP HANA Web-Based Development Workbench 编辑器所需的包权限

除了 [表 7.1](#07_003.html#t7.1) 中列出的角色外，用户还需要为其计划在其中编辑、创建或激活存储库角色的包分配适当的包权限。此要求也适用于基于脚本的存储库角色。例如，用户将需要以下包权限才能使用 SAP HANA Web-Based Development Workbench 编辑器界面创建存储库角色：

*   `REPO.READ`
*   `REPO.EDIT_NATIVE_OBJECTS`
*   `REPO.ACTIVATE_NATIVE_OBJECTS`

SAP HANA Web-Based Development Workbench 编辑器界面（如 [图 7.3](#07_003.html#f7.3) 所示）与 SAP HANA Studio 的 Repositories 选项卡下的开发区域非常相似。界面左侧是一个 Content 文件夹，其下是包层次结构。

[![SAP HANA Web-Based Development Workbench Editor](bilderklein/klein07_003.png)](img-f7.3.html)

**图 7.3** SAP HANA Web-Based Development Workbench Editor

当你展开包层次结构节点时，你将开始看到开发工件，具体取决于你的环境中可用的内容。要创建存储库角色，请右键单击要存储角色的包，然后选择 New • Role。将出现一个小窗口，要求输入角色名称。输入所需名称并单击 OK；右侧将出现一个新的基于选项卡的窗口，如 [图 7.3](#07_003.html#f7.3) 所示，其中选项卡名为 `SECURITY_ADMIN.hdbrole`。单击 System Privileges 选项卡以管理和列出系统权限。

在此选项卡下，要添加系统权限，请单击子选项卡标题上的大加号 (+) 按钮。将出现 Select System Privilege 弹出窗口，如 [图 7.4](#07_003.html#f7.4) 所示。

将在此窗口中出现一个搜索框；输入系统权限名称的一部分以缩小结果范围，或滚动浏览未过滤的列表以找到所需的系统权限。在列表中选择一个或多个权限，单击时按住 (Ctrl) 键以选择多个项目。所选项目将以浅蓝色高亮显示。单击窗口底部的 OK 按钮以最终确定选择。

所选权限将现在出现在 System Privileges 选项卡中。要删除已分配的系统权限，请从列表中选择该权限，然后单击列表上方的大减号 (–) 按钮。列表中的项目必须逐个删除。

[![Searching for System Privileges within the Select System Privileges Dialog Box](bilderklein/klein07_004.png)](img-f7.4.html)

**图 7.4** 在 Select System Privileges 对话框中搜索系统权限

配置好所需的系统权限列表后，单击左上角的保存所有图标（三个软盘）。

如果在保存和激活存储库角色时出现任何问题，消息将以红色文本显示在打开的存储库角色选项卡下方的控制台窗口中。控制台窗口具有深色背景，位于打开的选项卡底部。肯定消息将以白色文本显示，错误消息以红色文本显示。

要关闭打开的存储库角色选项卡，请单击选项卡右侧的小 X。

## 7.4 案例研究：安全管理员系统权限

E-Corporation 已联系其首席 SAP HANA 安全顾问，并请求帮助定义一系列存储库角色，以供其安全团队用于管理 SAP HANA 环境中的安全性。基于以往经验，顾问建议为安全团队定义四个存储库角色，以允许在系统内实现职责分离。这种分离有助于减少安全模型中的欺诈和疏忽。顾问建议根据以下组创建四个角色：

*   负责管理用户的管理员
*   负责创建角色的管理员
*   管理通信和数据加密的管理员
*   管理系统审计的管理员

为了帮助 E-Corporation 更好地理解顾问的推理，他为每项活动提供了理由，并说明了为什么需要将它们相互分离。此外，他还列出了每项广泛活动所需的功能和系统权限。在此案例研究中，我们将审查顾问的建议及其对每项活动的理由。

### 7.4.1 用户管理角色

安全顾问推荐的第一个存储库角色授予配置和管理用户帐户所需的权限。该角色的获得者将负责以下任务：

*   配置用户帐户
*   重置用户帐户密码
*   分配安全断言标记语言 (SAML) 和 Kerberos 身份

为了确保遵循最佳实践并正确实施职责分离，拥有此角色的获得者不应能够执行以下任务：

*   创建或更新现有角色
*   将标准角色授予用户
*   将存储库角色授予用户
*   将单个权限授予用户
*   管理系统审计

