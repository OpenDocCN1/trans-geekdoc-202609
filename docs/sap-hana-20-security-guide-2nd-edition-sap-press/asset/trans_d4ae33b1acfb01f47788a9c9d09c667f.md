

我们强烈建议使用此方法，因为只有安全角色创建者才能访问这些对象。如果标准开发人员意外获得此包的编辑访问权限，开发人员可以更新设计时仓库角色，激活更改，并提升其自身权限。因此，将此包放在根级别风险较小，因为可以防止意外继承包权限。理想情况下，此包将包含用于在 SAP HANA 系统中建立角色和权限的基础仓库角色。现在，让我们来看看创建仓库角色的过程。

### 6.2.2 在包中创建仓库角色

如前所述，包用于存储仓库角色。要在 `Security.Roles` 包中创建新的仓库角色（如 [图 6.1](#06_002.html#f6.1) 所示），右键单击 `Roles` 包并选择 New • File。将文件命名为 `ExampleRole.hdbrole`，如 [图 6.2](#06_002.html#f6.2) 所示。扩展名 `.hdbrole` 是强制性的，您应使用与预期分配给角色的名称相同的名称来命名角色文件。

[![Naming Your .hdbrole File](bilderklein/klein06_002.png)](img-f6.2.html)

**Figure 6.2 Naming Your .hdbrole File**

默认情况下，新选项卡将出现在右侧。SAP HANA Web-Based Development Workbench 会将对象默认设置为仓库角色 GUI 编辑器界面。但是，为了说明，我们想要查看角色文件脚本的文本。要查看文本，您需要保存文件，关闭选项卡，然后使用文本编辑器重新打开文件。保存文件后，右键单击 `ExampleRole.hdbrole` 文件并选择 Open With • Text Editor。[图 6.3](#06_002.html#f6.3) 显示了用于用文本编辑器打开 `Examplerole.hdbrole` 文件的右键菜单。

[![Opening the ExampleRole.hdbrole File with the Text Editor](bilderklein/klein06_003.png)](img-f6.3.html)

**Figure 6.3 Opening the ExampleRole.hdbrole File with the Text Editor**

### 6.2.3 定义角色名称标记

因为我们使用 SAP HANA Web-Based Development Workbench 编辑器创建了角色，所以语法的这部分在创建过程中已完成。但是，仓库角色的语法以单词 `role` 开头，后跟完全限定的仓库名称。完全限定的角色名称以完整的包层次结构名称开头，后跟两个冒号和角色名称。此脚本中的角色名称必须与 `.hdbrole` 文件名前缀完全相同。以下脚本表示仓库角色的基本语法。将尖括号 (`<>`) 中的项目替换为您环境中特有的对象：

```
role <package.subpackage>::<repository role name> {    
}
```

例如，假设您需要创建一个名为 `ExampleRole` 的角色，该角色将存储在 `Security.Roles` 包中。以下脚本将是定义该仓库角色的起点：

```
role Security.Roles::ExampleRole {    
}
```

### 6.2.4 扩展角色

在角色名称和第一个左括号之间，您可以选择添加将扩展新仓库角色的现有角色。因此，引用角色中的权限将授予您的新仓库角色，此外还包括您在括号之后明确定义的任何权限。[清单 6.1](#06_002.html#l6.1) 向您展示了如何通过添加 `extends role`，后跟现有的完全限定的仓库角色名称的逗号分隔列表来包含现有角色。

```
role Security.Roles::ExampleRole extends role     
sap.hana.xs.formLogin.profile::ProfileOwner,
sap.hana.xs.selfService.user.roles::USSExecutor {
}
```

**Listing 6.1 Repository Role Script with Multiple Extended Roles**

### 6.2.5 分配权限

每个权限都使用特殊语法授予或分配给角色。权限将在左花括号和右花括号 (`{}`) 内指定。[清单 6.2](#06_002.html#l6.2) 所示的脚本将为 `StagingMart` 和 `SalesMart` 架构授予架构权限，此外还授予 `CATALOG READ` 系统权限、分析权限和包权限。

```
role Security.Roles::ExampleRole extends role   
 sap.hana.xs.formLogin.profile::ProfileOwner,
 sap.hana.xs.selfService.user.roles::USSExecutor {

  -- Begin Schema Privileges  
  catalog schema "StagingMart": SELECT, EXECUTE;
  catalog schema "SalesMart": SELECT, EXECUTE;

  -- Begin System Privileges
  system privilege: CATALOG READ;

  -- Begin Analytic Privileges
  catalog analytic privilege : "_SYS_BI_CP_ALL";

  // Begin Package Privileges
  package .REPO_PACKAGE_ROOT: REPO.READ; 
}
```

**Listing 6.2 Repository Role Script Granting Different Privilege Types**

每个权限行必须以分号结尾。要在脚本中放置注释，请以两个连续的破折号或斜杠 (`--` 或 `//`) 开头注释行。注释是可选的，但应包含注释以传达有关脚本整体或每个脚本行的重要信息。同样，各个权限必须限定在左花括号和右花括号内。如 [清单 6.2](#06_002.html#l6.2) 所示，您可以在同一脚本中定义不同类型的权限。在大多数情况下，每种权限类型都需要略有不同的语法。

### 6.2.6 保存和激活

脚本完成后，您需要保存并激活脚本。要保存脚本，请单击保存图标（软盘）或按 `(Ctrl)+(S)`。保存还会在 SAP HANA Web-Based Development Workbench 编辑器中激活文件。但是，如果保存文件时出现任何错误，请查看文本编辑器下方的状态窗格。状态区域默认具有深色背景。如果有任何错误，请查找红色文本。白色文本的消息通常表示保存操作成功。

### 6.2.7 运行时仓库角色

激活仓库角色后，将在 SAP HANA 目录中创建该角色的运行时版本。运行时角色的名称将使用包层次结构和仓库角色名称的组合构建。每个元素将由两个冒号分隔，如以下示例所示：

*   `<package.subpackage>::<repository role name>`
*   `Security.Roles::ExampleRole`

该角色将在 SAP HANA Web-Based Development Workbench 编辑器的安全管理器中找到的标准角色列表中可见。现在，让我们花点时间来看看如何为每个对象和权限类型定义权限。

## 6.3 在设计时脚本中授予和撤销权限

使用设计时脚本开发仓库角色时，您会发现语法因对象类型或权限类型而异。[图 6.4](#06_003.html#f6.4) 显示了 SAP HANA Web-Based Development Workbench 的文本编辑器选项卡中完整仓库角色脚本的示例。为了演示目的，此角色向各种设计时和运行时对象类型授予了各种权限。

[![Example Repository Role Script](bilderklein/klein06_004.png)](img-f6.4.html)

**Figure 6.4 Example Repository Role Script**

使用基于仓库的脚本时，请注意 `_SYS_REPO` 系统用户必须拥有目录对象，或者必须使用 `WITH ADMIN OPTION` 或 `WITH GRANT OPTION` 被授予相同的权限。如果 `_SYS_REPO` 不满足这些要求，仓库角色将无法激活。在本节中，我们将探讨使用设计时仓库角色脚本授予权限的语法。

### 6.3.1 系统权限

