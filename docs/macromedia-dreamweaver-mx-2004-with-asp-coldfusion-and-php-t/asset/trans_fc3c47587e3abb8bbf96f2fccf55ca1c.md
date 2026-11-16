

当您关闭对话框时，Dreamweaver 会在您的站点中创建一个名为 Connections 的新文件夹，文件夹内包含一个名为 conn_newland.asp 的新文件。您还应注意到，数据库面板现在显示了可展开的数据库及其资产列表。

![](img/43fd0127a958864ab2d93e28efe683e7_259_0.png)

- 9) 在文件面板中选择 Connections 文件夹，然后单击“上传”按钮将其上传到服务器。

您现在可以创建记录集并开始绑定数据库数据。跳转至任务：“检索记录集并显示数据库信息。”

## ColdFusion 用户（在本地运行 ColdFusion 或连接到远程服务器）

本节适用于所有 ColdFusion 用户，无论他们如何连接到服务器。

连接到远程服务器的 ColdFusion 用户必须让该服务器的管理员授予其 RDS 登录信息（该信息由密码组成）。如果没有 RDS 登录权限，您将无法完成本书的学习。

- 1) 打开 index.cfm。

在最初创建连接时，无关您的站点中哪个页面处于打开状态。Dreamweaver 会为整个站点创建连接。您打开了 index.cfm，因为您将在下一个任务中向该页面添加动态内容。

- 2) 打开“应用程序面板组”中的数据库面板。单击“为您的 ColdFusion 服务器指定 RDS 登录”链接，输入密码，然后单击“确定”。

RDS 登录授予开发人员访问 ColdFusion 服务器的权限，这是定义和使用数据源所必需的。

![](img/43fd0127a958864ab2d93e28efe683e7_259_1.png)

此步骤结束时，如果 ColdFusion 服务器上已存在许多数据源，它们都会在数据库面板中显示。

唯一的问题是，Newland 数据库不在其中。

- 3) 单击“创建 ColdFusion 数据源”链接（如果可用），或单击数据库面板右侧的“修改数据源”按钮。

无论您单击的是按钮还是链接，稍后 ColdFusion 管理员将在浏览器中打开“数据源”页面。您首先需要输入密码才能访问管理员。

![](img/43fd0127a958864ab2d93e28efe683e7_260_0.png)

- 4) 在“添加新数据源”框中，将 Data Source Name 输入为 newland。在“驱动程序”下拉菜单中，选择 Microsoft Access，然后单击“添加”。

DSN 包含一个名称、一个使应用程序能够与数据库通信的驱动程序，以及数据库的路径。在此步骤中，您已输入了这三项信息中的前两项。

![](img/43fd0127a958864ab2d93e28efe683e7_260_1.png)

- 5) 在出现的“Microsoft Access 数据源”框中，单击第一个“浏览服务器”按钮，然后浏览到站点上的 newland_tours.mdb 文件。单击“提交”。
对于 Windows XP 用户，请浏览到以下目录：C:\Documents and Settings\All Users\Documents\database\'。这是快捷方式“共享文档”所指向的目录。
对于以独立模式运行 ColdFusion 的 Windows 2000 用户，请浏览到以下目录：C:\CFusionMX\wwwroot\newland\database\。
对于与 IIS 一起运行 ColdFusion 的 Windows 2000 用户，请浏览到以下目录：C:\Inetpub\wwwroot\newland\database\。
此步骤为 ColdFusion 提供了连接到数据库所需的其余信息。

![](img/43fd0127a958864ab2d93e28efe683e7_261_0.png)

- 6) 关闭 ColdFusion 数据源网页以返回 Dreamweaver。在数据库面板中，单击您先前单击过的“修改数据源”旁边的“刷新”按钮。newland DSN 应该会显示出来。单击其旁边的 + 按钮将其展开并探索数据源。

![](img/43fd0127a958864ab2d93e28efe683e7_261_1.png)

既然您可以查看 newland_tours.mdb 数据库的内容，就知道 Dreamweaver 已成功建立连接。您现在可以创建记录集并开始绑定数据库数据。

跳转至标题为“检索记录集并显示数据库信息”的部分。

## PHP 用户（在本地运行 PHP/MySQL 或在远程服务器上运行）

由于 PHP 不使用 ODBC 或 DSN，您可以直接在 Dreamweaver 中指定访问 MySQL 数据库所需的所有信息。

- 1) 打开 index.php。
  无关打开哪个文件，因为 Dreamweaver 会使连接在整个站点中可用。但是，在创建到 MySQL 的连接之前，站点中必须至少打开一个文件。

- 2) 在“数据库”选项卡中，单击 + 按钮并选择 MySQL 连接以创建到 MySQL 的新连接。
  “MySQL 连接”对话框将打开。

- 3) 指定以下信息，以便 Dreamweaver 可以向您的站点提供 MySQL 数据源。
  连接名称：conn_newland
  MySQL 服务器：localhost（如果在本地开发）或您的服务器管理员告诉您的内容（如果在远程开发）
  用户名和密码：您用于访问 MySQL 的 MySQL 帐户的用户名和密码。
  数据库：newland_tours。

![](img/43fd0127a958864ab2d93e28efe683e7_262_0.png)

如果您在远程服务器上开发，只有您的服务器管理员才能告诉您如何从 Dreamweaver/PHP 访问 MySQL。如果您在本地开发，则只需使用首次安装 MySQL 时指定的信息即可。如果您是自己安装 MySQL 且不确定用户名和密码，请尝试将 root 作为用户名，并将密码留空。

**提示** 可选：单击“测试”按钮以确保 Dreamweaver 确实可以访问 MySQL。

- **4) 单击“确定”。** Dreamweaver 在您的站点中创建一个名为 Connections 的目录，目录内包含名为 conn_newland.php 的文件。该文件包含您的页面访问 MySQL 所需的信息。每当您从 PHP 调用数据库时，Dreamweaver 都会引用此文件。

- **5) 在数据库面板中展开 conn_newland，以便在 Dreamweaver 内部探索 newland_tours 数据库的结构。** Dreamweaver 实际上正在访问 MySQL 内部的数据库，并向您提供有关它的信息。尽管方式有限，您仍可通过 Dreamweaver 与 MySQL 进行交互。

![](img/43fd0127a958864ab2d93e28efe683e7_263_0.png)

- **6) 在文件面板中单击 Connections 文件夹，然后单击“上传”按钮将其上传到服务器。** 除非上传该文件夹，否则 PHP/MySQL 连接无法正常工作。

## 检索记录集并显示数据库信息

距您上次对实际站点进行任何改进似乎已过去很长时间。您已经完成了一些理论、一些探索和一些配置。但您尚未对任何页面进行任何操作。在本课的最后一个任务中，您将使“旅行者日志”从数据库动态加载。在浏览器中，主页看起来与之前相同，但在 Dreamweaver 中，差异将显而易见。

- 1) 在设计视图中打开 index.asp 时，选择底部的文本，从“Teens Discover...”一直到“...putting together”。不要选择 Teens 中 T 旁边的黄色图像图标（如果出现）。按 Delete 键。
  您将用动态文本替换此文本，因此此步骤只是腾出空间。

![](img/43fd0127a958864ab2d93e28efe683e7_264_0.png)

- 2) 单击“旅行者日志”图片将其选中。在标记选择器（文档窗口左下角）中，右键单击位于  标记左侧的 <h3> 标记，并从菜单中选择“删除标记”。
  数据库中的日志条目已使用 HTML 进行标记。您需要在此处删除 <h3> 标记，否则日志条目中的标记将非法地嵌套在 <h3> 标记内。

- 3) 在“绑定”面板中，单击“新建绑定 (+)”按钮，并从菜单中选择“记录集 (查询)”。

此时，您已将站点连接到数据源，这意味着您已使 Dreamweaver 能够为您编写从数据库检索数据的代码。但是，您尚未实际检索任何数据。在接下来的三个步骤中，您将创建一个记录集，正如您从本课开头所记得的那样，记录集是使用 SQL 从数据库中检索的、满足特定条件的数据集合。

![](img/43fd0127a958864ab2d93e28efe683e7_265_0.png)

您的目标是显示日志条目，但您不想显示所有日志条目，只想显示最新的一条。为了方便这一点，每个日志条目都已赋予一个唯一 ID（主键）。随着记录的添加，这些 ID 以增量方式编号。因此，journalID 最高的记录是最新的一条。您需要对数据进行排序，然后检索最新日志条目的内容以显示它。您将在下一步中开始执行此操作。

- 4) 在“记录集”对话框中，将 Name 输入为 rs_journal。从 Connection 下拉列表中选择 conn_newland（ColdFusion 用户为 newland）。从 Table 下拉列表中选择 tbl_journal。在 Columns 部分，选择 Selected 单选按钮，然后 Ctrl-选择 (Windows) 或 Command-选择 (Macintosh) journalID 和 journal_entry。

在此对话框中，您正在创建名为 rs_journal 的记录集。此记录集中的数据是使用在 SQL 中指定的条件检索的。您可能没有意识到，但您已经开始编写 SQL 语句。

具体来说，您已指定存储在 conn_newland 中的数据源中的数据（该连接指定 newland DSN）。在该数据源中，您指定数据位于名为 tbl_journal 的表中。进一步地说，您指定只想从该表中检索 journalID 和 journal_entry 字段。

