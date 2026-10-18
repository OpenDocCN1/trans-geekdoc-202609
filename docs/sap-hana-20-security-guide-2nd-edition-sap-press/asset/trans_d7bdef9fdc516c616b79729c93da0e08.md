

请注意，您可以使用 `SQL` 语句将此功能应用于视图，或在使用 `SAP Web IDE for SAP HANA` 开发计算视图时应用。目前您无法使用 `SAP HANA cockpit` 创建这些视图。

您现在应该已基本了解如何访问 `Anonymization Report` 磁贴以及在管理 `SAP HANA` 安全模型时它提供的选项。在下一节中，我们将探讨 `Auditing` 磁贴及其链接。

### 1.2.6 Auditing

`Auditing` 磁贴及其链接可用于访问审计设置并在 `SAP HANA` 数据库中配置审计策略。审计策略（如 [第 15 章](#15_001.html#h15) 中进一步讨论）用于跟踪 `SAP HANA` 数据库中的特定操作。此磁贴中的所有链接均可点击，包括 `Auditing` 标题，它将导航至 `Auditing` 配置界面，如 [图 1.15](#01_002.html#f1.15) 所示。

[![Auditing Tile and Links in SAP HANA Cockpit](bilderklein/klein01_015.png)](img-f1.15.html)

**图 1.15** SAP HANA Cockpit 中的 Auditing 磁贴和链接

`Status` 链接；`Audit Trail Target` 链接；`Enabled Audit Policies` 链接（包含已启用策略的摘要）；以及 `Disabled Audit Policies` 链接（同样包含摘要）均可点击，以直接跳转至 `Auditing` 配置界面中的相应设置。磁贴底部是 `Turn on Auditing` 链接，它将启用审计机制。

您现在应该已基本了解如何使用 `Auditing` 磁贴及其提供的链接选项访问 `Auditing` 配置界面。我们已对 `SAP HANA cockpit` 提供的用于管理安全性的磁贴和链接进行了高级概述。后续章节将提供有关如何使用每个磁贴及其链接来管理 `SAP HANA` 安全模式的更多信息。

在下一节中，我们将探讨 `SAP HANA database explorer` 和 `SQL console`，这两者都是 `SAP HANA cockpit` 中的重要工具集。您将发现，需要使用这些工具来探索数据库并执行 `SQL` 语句，所有这些都是管理 `SAP HANA` 安全模型所必需的。

## 1.3 SAP HANA Database Explorer 和 SQL Console

`SAP HANA cockpit` 提供 `SAP HANA database explorer`，以便您可以连接到 `SAP HANA` 数据库并在运行时处理目录对象。从 `SAP HANA cockpit` 主页，单击 `Browse Database Objects` 磁贴以访问 `SAP HANA database explorer`，如 [图 1.16](#01_003.html#f1.16) 所示。您也可以通过单击此页面上的 `Execute SQL` 磁贴直接访问 `SQL console`。

[![Browse Database Objects and Execute SQL Tiles](bilderklein/klein01_016.png)](img-f1.16.html)

**图 1.16** Browse Database Objects 和 Execute SQL 磁贴

或者，您可以在连接到已注册的 `SAP HANA` 数据库时访问 `SQL console`。在 `System Overview` 页面上，如 [图 1.17](#01_003.html#f1.17) 所示，您将在右上角看到两个链接：`Open SQL Console` 和 `Manage Databases`。

[![Open SQL Console Link Used to Access the SQL Console from the SAP HANA Cockpit System Overview Page](bilderklein/klein01_017.png)](img-f1.17.html)

**图 1.17** 用于从 SAP HANA Cockpit 系统概览页面访问 SQL Console 的 Open SQL Console 链接

单击 `Open SQL Console` 链接可直接导航至 `SAP HANA database explorer`，连接到已注册系统，并在单个步骤中启动 `SQL console`。从技术上讲，此链接除了打开 `SQL console` 之外，还会带您进入 `SAP HANA database explorer`。

在 `SAP HANA database explorer` 界面中，您可以单击 `SAP HANA Database Explorer` 标题下方窗格中的加号图标（`+`）来添加连接。您有多种 `Database Types` 可供选择：`SAP HANA database`、`SAP HANA database (Multitenant)` 或 `Cockpit Resource`。选择 `Cockpit Resource` 选项可使用 `SAP HANA cockpit` 注册信息连接到 `SAP HANA` 数据库。要连接到经典 `SAP HANA` 数据库对象，请选择 `SAP HANA database` 或 `SAP HANA database (Multitenant)` 选项，并输入所需数据库的连接信息。

对于每个连接，您将获得各种目录对象类型的图形列表，如 [图 1.18](#01_003.html#f1.18) 所示。例如，如果您正在搜索表，请单击 `Catalog` 下的表选项，然后使用下方窗格中的架构选择栏和搜索栏在所选架构中按名称查找表。一旦在列表中找到对象，双击该对象即可显示其元数据，或右键单击该对象以打开包含与所选对象交互选项的弹出窗口。

当您进一步查看已连接数据库中 `Catalog` 文件夹下方时，您将看到一个 `Host Diagnostic Files` 文件夹。展开此节点下的子文件夹，直到找到以每个 `SAP HANA` 数据库服务命名的文件夹。例如，将出现 `Name Server` 和 `Index Server` 文件夹。在每个文件夹中，您将找到特定于服务文件夹的各种 `.trc` 文件（跟踪文件）。双击文件以打开并在 `SAP HANA database explorer` 界面右侧的选项卡中查看其内容。安全管理员在排查安全配置问题或用户无法访问内容时，通常需要查看这些文件。

[![SAP HANA Database Explorer Found in the SAP HANA Cockpit](bilderklein/klein01_018.png)](img-f1.18.html)

**图 1.18** SAP HANA Cockpit 中的 SAP HANA Database Explorer

您现在应该已基本了解 `SAP HANA cockpit` 中的 `SAP HANA database explorer`。

###### 关于 SAP HANA Database Explorer 的更多信息

有关 `SAP HANA database explorer` 的更多信息，请参阅 `SAP HANA Database Explorer Guide`，可在 [http://s-prs.co/v498201](http://s-prs.co/v498201) 上查阅。

一旦您与数据库建立连接，即可访问 `SQL console`，在其中执行 `SQL` 语句。要启动 `SQL console`，请从 `SAP HANA database explorer` 中找到的列表中选择现有数据库连接。单击数据列表右上角带有单词 `SQL` 的图标，如 [图 1.19](#01_003.html#f1.19) 所示。右侧将出现带有 `SQL console` 标签（可能带有数字）的新选项卡。

在此选项卡中是 `SQL console`。输入所需的 `SQL`，然后单击运行图标（绿色播放按钮）。您也可以按 (`F8`) 按钮来运行 `SQL` 命令。`SQL` 语句的结果将出现在输入的语句下方，如 [图 1.19](#01_003.html#f1.19) 所示。

[![Accessing and Using the SQL Console within the SAP HANA Cockpit](bilderklein/klein01_019.png)](img-f1.19.html)

**图 1.19** 在 SAP HANA Cockpit 中访问和使用 SQL Console

您现在应该已基本了解访问 `SAP HANA database explorer` 和 `SQL console` 所需的步骤。作为安全管理员，您将使用 `SQL console` 执行特定于安全性的语句。当您需要在数据库中定位目录对象并查看其元数据时，`SAP HANA database explorer` 非常有用。您还将使用 `SAP HANA database explorer` 访问可能包含特定于安全性的跟踪信息的 `.trc` 文件。

## 1.4 摘要

本章向您介绍了 `SAP HANA cockpit`。我们还提供了您管理对 `SAP HANA cockpit` 的访问以及各种应用程序、磁贴和链接所需的基本信息，这些应用程序、磁贴和链接允许您管理 `SAP HANA` 数据库的安全模型。在后续章节中，我们将提供有关如何使用 `SAP HANA cockpit` 管理 `SAP HANA` 安全模型特定方面的更多信息和示例。

# 2 SAP HANA 权限简介

