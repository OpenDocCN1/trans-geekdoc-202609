

# 11.4 用户权限

与应用程序权限无关，名为 `Privileges on Users` 的附加选项可用于授予 `ATTACH DEBUGGER` 权限，但在 SAP HANA 中具有有限的使用范围。`Privileges on Users` 允许用户将其自身会话的调试访问权限授予被授予者。此权限仅提供分配 `ATTACH DEBUGGER` 权限的功能，并且仅限于授予者的账户。

例如，用户账户 `SYSTEM` 可以登录到 SQL 控制台，并将 `ATTACH DEBUGGER` 权限授予用户账户 `ADMIN_MIKE`，但仅限于用户 `SYSTEM`。实际上，此功能的 GUI 界面只允许您在“用户”列下指定 `SYSTEM` 账户。此权限授予 `ADMIN_MIKE` 在 `SYSTEM` 账户会话中调试 SQLScript 代码的权限。`SYSTEM` 也是唯一可以将此权限授予 `ADMIN_MIKE` 的用户。

在以下部分中，我们将回顾使用 SAP HANA cockpit 和使用 SQL 语句授予用户权限的两个选项。

## 11.4.1 使用 SAP HANA cockpit 授予用户权限

让我们回顾使用 SAP HANA cockpit 授予和撤销用户权限所需的工作流程。作为使用 SQL 语句的替代方案，您可以使用名为 `Assign Privileges` 或 `Manage Roles` 的 SAP HANA cockpit GUI 操作。每个界面都允许您授予和撤销用户权限。大多数用户会发现使用 SAP HANA cockpit 比记忆和输入 SQL 语句更容易。

要访问 `Assign Privileges` 或 `Manage Roles` 区域，请从 SAP HANA cockpit 主屏幕开始，在资源目录中找到 SAP HANA 系统。连接到所需的租户数据库或 `SYSTEMDB`，这将带您进入系统概览窗口。使用按区域筛选下拉列表，选择安全选项。在用户和角色管理磁贴中找到 `Assign Privileges` 或 `Manage Roles`。

[Figure 11.5](#11_004.html#f11.5) 显示了 SAP HANA cockpit 中 `TEST_01` 用户账户的 `Assign Privileges` 界面内的 `Assign Privileges` 界面。在窗口中，您将看到几个选项卡，用于各种权限类别，从 `System Privileges`、`Object Privileges`、`Analytic Privileges`、`Application Privileges`、`Package Privileges` 和 `Privileges on Users` 选项卡开始。在使用角色时，您会发现类似的界面。但是，`Role Details` GUI 有一个名为 `Roles` 的附加链接，您可以在其中将现有角色授予所选角色。

`Assign Privileges` 窗口中的第六个选项卡名为 `Privileges on Users`。使用此选项卡配置用户权限。

如果已配置，界面将列出 `ATTACH DEBUGGER` 权限以及分配该权限的授予者。如果列表为空，则当前未配置任何内容。要授予附加调试器，请单击界面右侧搜索字段附近的 `Edit` 按钮。单击 `Edit` 按钮后，将出现标记为 `Save`、`Cancel`、`Add` 和 `Remove` 的新按钮。单击 `Add` 按钮将 `ATTACH DEBUGGER` 添加到被授予者。请注意，授予者始终是用于与 SAP HANA 系统进行身份验证的账户。`Attach Debugger` 分配现在应出现在列表中。请注意，此处无法配置其他内容。只能分配 `ATTACH DEBUGGER` 权限，授予者会自动确定为通过 SAP HANA cockpit 访问系统所使用的账户。配置此选项后，单击 `Save` 按钮以授予权限。

![Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit](bilderklein/klein11_005.png)

**Figure 11.5** Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit

要撤销 `ATTACH DEBUGGER` 权限，请先单击 `Edit` 按钮。突出显示 `Attach Debugger` 分配行，然后单击 `Remove` 按钮以撤销权限。移除项目后，单击 `Save` 按钮。移除的权限将被撤销，用户对象将被更新。

在添加或移除权限的过程中，您可以单击 `Cancel` 按钮以丢弃任何未保存的更改。单击 `Cancel` 按钮将停用 `Add`、`Cancel` 和 `Remove` 按钮，并将您返回到之前的只读状态。

## 11.4.2 使用 SQL 授予用户权限

除了使用 SAP HANA cockpit 之外，授予者可以执行以下 SQL 代码将 `ATTACH DEBUGGER` 权限授予另一个被授予者：

```
GRANT ATTACH DEBUGGER TO <GRANTEE>;
```

将 `<GRANTEE>` 变量替换为您环境中被授予者的名称。执行后，被授予者将获得调试授予者会话的访问权限。

# 11.5 摘要

应用程序权限定义了在 XS 引擎中开发的应用程序的自定义访问级别。激活后，这些权限可以授予 SAP HANA 系统中的用户或角色。SAP HANA GUI 界面中的 `Privileges on Users` 选项卡用于将 `ATTACH DEBUGGER` 权限授予另一个被授予者。您也可以使用 SQL 授予 `ATTACH DEBUGGER` 权限。

# 12 身份验证

身份验证是验证用户访问 SAP HANA 系统的关键。在本章中，我们将讨论 SAP HANA 如何支持外部身份验证提供程序，以及其基本内部身份验证机制。

