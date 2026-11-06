
命令行工具对于希望在特定时间安排任务或以其他方式自动化任务的管理员也很有用。通过脚本或批处理文件运行命令，或通过内部开发的其他应用程序调用它们，您可以自动化某些任务，使管理更轻松。以这种方式允许调用这些命令也有助于让用户执行他们不熟悉的管理任务。

## 图形化管理工具/MMCs

管理 Windows Server 2003 和 Active Directory 的主要管理工具是 Microsoft Management Console（`MMC`）。`MMC` 本身并不是管理工具，而是一个用于加载提供管理功能的插件的界面。插件提供特定的功能或相关的一组功能。由于 `MMC` 接口的设计，您可以将多个插件加载到一个控制台中，并创建用于处理特定任务的自定义工具。此外，由于这些插件在同一环境中运行，因此学习使用这些工具变得更容易，因为您不必为每个工具学习不同的界面。

`MMCs` 可以通过打开位于 Windows `Start menu` 中 `Administrative Tools` 文件夹下的预制控制台来启动。空的 `MMC` 可以通过在 Windows `Start menu` 中使用 `Run` 命令启动。通过在 Windows `Start menu` 的 `Run` 命令中输入 `MMC`，空的 `MMC` 将启动，如 [图 1.14](#B9781931836944500076.xhtml#f0075) 所示。

![图 1.14 Microsoft 管理控制台](images/B9781931836944500076/f01-14-9781931836944.jpg)

图 1.14 Microsoft 管理控制台

在 `MMC` 中出现的窗口是与单个插件或自定义控制台文件对应的界面。`MMC` 中的每个子窗口都有两个窗格。左窗格显示控制台树，即通过控制台可用的工具的层次结构显示。这些可以是已加载到 `MMC` 中并保存为自定义控制台的多个插件。右窗格称为详细信息窗格，提供与在控制台树中选择的内容相关的命令和信息。

您可以通过单击 `File` 菜单并选择 `Add/Remove Snap-in` 来为特定任务添加插件。执行此操作后，将出现一个带有两个选项卡的新对话框：`Standalone` 和 `Extensions`。

`Standalone` 选项卡用于独立插件，这些插件设计为无需任何额外要求即可运行。`Extensions` 选项卡用于加载一种特殊的插件，称为扩展插件。这些用于为已安装的独立插件添加附加功能。

`Standalone` 选项卡用于从控制台添加或删除插件。如 [图 1.15](#B9781931836944500076.xhtml#f0080) 所示，单击此选项卡上的 `Add` 按钮将显示可用独立插件的列表。选择要添加的插件后，单击此对话框上的 `Add` 按钮。单击 `Close` 将退出此屏幕并返回到上一个屏幕，此时将包含您选择的插件的列表以在此控制台中安装。单击 `OK` 确认选择并安装它们。

![图 1.15 添加/删除管理单元对话框](images/B9781931836944500076/f01-15-9781931836944.jpg)

图 1.15 添加/删除管理单元对话框

如 [图 1.15](#B9781931836944500076.xhtml#f0080) 所示，Active Directory 可用的插件有三个：

![Squareb](images/Squareb.png) `Active Directory Users and Computers`

![Squareb](images/Squareb.png) `Active Directory Domains and Trusts`

![Squareb](images/Squareb.png) `Active Directory Sites and Services`

虽然我们将在后面的章节中讨论这些插件，但重要的是要认识到这些并不是您可以在 Windows Server 2003 中使用的唯一插件。`MMC` 为 Active Directory 提供这三个插件，但还有其他插件可用于特定目的和管理任务。每个插件都有用于管理 Windows Server 2003 和 Active Directory 的单独功能或相关功能集。

![注意](images/note.jpg)注意

请注意，虽然这三个与 Active Directory 相关的插件可以添加到自定义 `MMC` 中，但每个插件已在 `Administrative Tools` 菜单中可用的单独预配置 `MMC` 中安装。

由于可以在 `MMC` 中添加和配置多个插件，因此您可以创建自定义控制台来执行特定任务。设置好控制台后，可以将其保存为具有 `.msc` 扩展名的文件。控制台可以保存为两种模式之一：`Authoring` 和 `User`。

`Authoring` 模式用于提供对 `MMC` 控制台功能的完全访问。当以此模式保存时，打开控制台的用户可以添加和删除插件，创建新的 Windows，创建收藏夹和任务板，查看控制台树中的所有内容，并保存控制台。

`User` 模式用于限制其他用户使用控制台某些功能的能力。

如果您为用户创建控制台以执行特定任务，但不希望他们访问其他功能，则 `User` 模式是理想选择。`User` 模式有三个访问级别：

![Squareb](images/Squareb.png) `Full Access` 与 Author 模式相同，只是不能添加或删除插件，不能更改控制台设置，并且用户不能创建收藏夹和任务板。

![Squareb](images/Squareb.png) `Limited Access, Multiple Windows` 允许用户查看保存控制台时可见的控制台树部分，并禁止用户关闭现有窗口。但是，用户可以创建新窗口。

![Squareb](images/Squareb.png) `Limited Access, Single Window` 也允许用户访问保存控制台时可见的控制台树部分，但禁止用户创建新窗口。

![考试提示](images/note.jpg)考试日提示

考试将测试您对 Active Directory 的了解以及如何使用随 Windows Server 2003 提供的工具。请记住，`MMC` 允许您加载插件以执行特定任务，也可用于创建提供有限功能的自定义控制台。

### Active Directory 用户和计算机

`Active Directory Users and Computers` 控制台是用于 Active Directory 的 `MMC` 插件之一。它允许您管理存储在 Active Directory 中的用户和计算机帐户、组、打印机、OU、联系人和其他对象。使用此工具，您可以创建、删除、修改、移动、组织并设置这些对象的权限。

如 [图 1.16](#B9781931836944500076.xhtml#f0085) 所示，加载此工具时，控制台树（左窗格）中会出现一个节点，显示域。展开此节点将显示默认创建的多个容器。虽然可以创建额外的容器，但在创建 DC 后此处出现的容器有：

![图 1.16 Active Directory 用户和计算机](images/B9781931836944500076/f01-16-9781931836944.jpg)

图 1.16 Active Directory 用户和计算机

![Squareb](images/Squareb.png) `Builtin`

![Squareb](images/Squareb.png) `Computers`

![Squareb](images/Squareb.png) `Domain Controllers`

![Squareb](images/Squareb.png) `Users`

这些容器存储可使用此工具管理的对象，并允许您查看和修改与这些不同对象相关的信息。

`Builtin` 容器保存由 Windows Server 2003 创建的组，可用于控制访问。您可以将用户添加到这些 `Builtin` 组，以赋予他们执行某些任务的能力。例如，而不是允许 IT 部门中的每个人使用相同的 Administrator 帐户，可以将用户添加到内置的 `Administrators` 组。这赋予他们管理 Windows Server 2003 的能力，但允许您跟踪具有此安全级别的人员执行了某些任务。

