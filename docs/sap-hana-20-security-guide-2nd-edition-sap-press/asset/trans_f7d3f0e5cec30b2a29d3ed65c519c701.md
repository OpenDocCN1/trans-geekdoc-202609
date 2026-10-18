

点击 `Step 2` 按钮以继续。在 `2. Cockpit Roles` 页面上，选择要授予用户的角色的复选框。点击 `Step 3` 按钮以继续。在 `3. Resource Groups` 部分页面，点击 `Add Groups` 按钮以打开 `Add User to Existing Group` 弹出窗口。在此弹出窗口中，选择要分配给用户的组的复选框。点击 `OK` 关闭弹出窗口，然后最后一次点击 `Create User` 以完成该过程。

[![在 SAP HANA Cockpit Manager 中创建用户](bilderklein/klein01_005.png)](img-f1.5.html)

**图 1.5** 在 SAP HANA Cockpit Manager 中创建用户

现在，让我们来看看可以授予用户的各种角色。请注意，角色不是累积的，这意味着一个角色不会建立在另一个角色之上。相反，每个角色都是明确的，每个角色只直接提供对一个区域的访问权限。用户需要获得所有授予的角色才能完全访问 SAP HANA cockpit 和 SAP HANA cockpit manager。

以下列表概述了每个角色，并提供了每个角色授予用户的权限的其他信息：

*   `Cockpit Administrator Role`

    此角色仅提供对 SAP HANA cockpit 设置的管理访问权限。此角色不是主角色，仅提供更改设置的访问权限；不包含其他访问权限。

*   `Cockpit Resource Administrator Role`

    此角色将授予用户注册 SAP HANA 数据库、创建资源组和管理资源组分配的权限。具有此角色的用户将可以访问所有已注册的资源，无论其分配的 SAP HANA cockpit 组如何。

*   `Cockpit User Administrator Role`

    此角色将授予用户在 SAP HANA cockpit manager 和底层 SAP HANA cockpit 数据库中创建和管理其他用户的能力。在数据库级别，此角色授予 `ROLE ADMIN` 和 `USER ADMIN` 系统权限。在 SAP HANA cockpit manager 应用程序级别，此角色授予类似的访问权限。

*   `Cockpit User Role`

    此标准角色是用户访问 SAP HANA cockpit 所必需的。用户必须具有此角色才能访问 SAP HANA cockpit 主页。此角色的两个其他选项将授予标准 SAP HANA cockpit 用户有限但额外的权限。让我们更详细地看看这些选项：

    *   `Register resources through the Cockpit Manager`

        此子角色选项授予用户有限的访问权限，以便在 SAP HANA cockpit manager 中创建和注册 SAP HANA 服务器资源。资源将不带组创建，访问权限仅限于 `Cockpit Resource Administrator` 角色的成员和其自身。

    *   `System configuration template administrator role`

        此子角色允许用户访问 SAP HANA cockpit 配置模板磁贴。配置模板包含 SAP HANA 数据库 `.ini` 文件设置，可以存储并应用于 SAP HANA 数据库。

*   `Cockpit Troubleshooting Role`

    此角色授予用户查看 SAP HANA cockpit manager 中 SAP HANA XSA 日志区域的访问权限。用户必须是 SAP HANA XSA 组织管理员才能使用此功能。您可以使用 SAP HANA XSA cockpit 图形用户界面 (`GUI`) 或使用 SAP HANA XSA 命令行运行以下命令来授予 SAP HANA cockpit 管理员此访问权限：`xs set-org-role COCKPIT_ADMIN HANACockpit OrgManager`。

在下一节中，我们将更详细地探讨 SAP HANA cockpit 组，并向您展示如何在 SAP HANA cockpit manager 中创建组。

### 创建 SAP HANA Cockpit 资源组

SAP HANA cockpit 使用资源组来组织和保护已注册的 SAP HANA 数据库。SAP HANA cockpit 用户可以分配到一个或多个组。对于标准 SAP HANA cockpit 用户，您可以使用组来限制他们在 SAP HANA cockpit 中看到的已注册系统。但是，如果用户被授予 `Administrators` 或 `Resource Administrators` 角色，他们将看到所有资源组，无论其分配的组如何。

资源组是使用 SAP HANA cockpit manager 创建的。从 SAP HANA cockpit manager 主页，单击 `Resource Groups` 菜单选项以访问资源组管理界面。该界面分为两个窗格。左侧是 `Resource Groups` 窗格中现有资源组的列表。右侧是 `Resource Group Details` 窗格，如 [图 1.6](#01_001.html#f1.6) 所示。当您单击左侧的资源组时，其已注册的资源或 SAP HANA 数据库将出现在右侧。

[![SAP HANA Cockpit Manager 资源组管理界面](bilderklein/klein01_006.png)](img-f1.6.html)

**图 1.6** SAP HANA Cockpit Manager 资源组管理界面

要创建组，请找到资源组列表底部的 `Create Group` 按钮。单击该按钮以启动三步 `Create Group` 向导。在第一步 `1. General information` 中，在提供的字段中输入资源 `Group name` 和 `Description`。单击 `Step 2` 按钮以继续。在第二步 `2. Resource` 中，将现有已注册的 SAP HANA 系统分配给组。单击 `Step 3` 按钮以继续。在第三步 `3. Cockpit Users` 中，将一个或多个用户分配给组。单击 `Create Group` 按钮以完成向导。

您可以通过在 SAP HANA cockpit manager 右侧选择一个组，在 `Resource Group Details` 窗格左侧列出的资源或用户上方的 `Resource` 和 `Cockpit Users` 选项卡之间切换，来修改现有组。您也可以使用此界面从资源组中删除或移除已注册的资源或用户。

分配给组的用户现在登录到 SAP HANA cockpit 时将看到相应的已注册资源。在下一节中，我们将探讨已注册资源的用途以及如何使用 SAP HANA cockpit manager 注册它们。

### 注册 SAP HANA 数据库和租户

在与 SAP HANA 系统交互之前，您必须先添加或配置与 SAP HANA 系统的连接，并将此连接存储在 SAP HANA cockpit 中。

要注册资源或 SAP HANA 数据库，请单击 SAP HANA cockpit manager 主页上方的 `Registered Resources` 按钮以访问已注册资源管理界面。此界面分为两个窗格。左侧是 `Registered Resources` 窗格中现有已注册资源或 SAP HANA 服务器的列表。右侧是 `Resource Details` 窗格，如 [图 1.7](#01_001.html#f1.7) 所示。当您单击左侧的资源组时，有关已注册资源或 SAP HANA 数据库的详细信息将出现在右侧。

[![SAP HANA Cockpit Manager 中的 SAP HANA 数据库或已注册资源](bilderklein/klein01_007.png)](img-f1.7.html)

**图 1.7** SAP HANA Cockpit Manager 中的 SAP HANA 数据库或已注册资源

