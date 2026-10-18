

# SAP HANA Cockpit：系统配置 GUI

不再使用 SQL 命令来更新安全策略设置，而是可以使用 SAP HANA Cockpit（位于数据库管理下）中的管理系统配置选项。单击管理系统配置以启动系统配置 GUI。

系统配置 GUI 列出了 SAP HANA 的任何默认或自定义配置设置。在参数选项卡下方，您将看到一个搜索栏和一系列下拉列表，如 [图 12.1](#12_001.html#f12.1) 所示供参考。请注意，您需要 `INIFILE ADMIN` 系统权限才能查看或修改这些设置。

[![SAP HANA Cockpit 系统配置 GUI](bilderklein/klein12_001.png)](img-f12.1.html)

**图 12.1** SAP HANA Cockpit 系统配置 GUI

您可以使用搜索栏搜索特定参数名称。此外，您可以使用配置文件下拉列表将列表筛选到特定配置文件。各个参数被组织为相关参数的节。您可以使用节下拉列表筛选到特定节。如果 SAP HANA 系统有多个服务器（横向扩展），您可以使用主机节将列表筛选到给定服务器节点或主机。最后，您可以使用数据库下拉列表将列表筛选到特定租户数据库的设置。

找到参数后，您可以使用位于参数最右侧的覆盖值链接来更改当前值，或者在某些情况下更改默认值。[图 12.2](#12_001.html#f12.2) 显示了 GUI 的示例，其中我们搜索了术语“password”并在配置文件下拉列表中选择了 indexserver.ini 选项。结果显示了节 `[]password_policy` 和可更改的参数列表。要更改单个参数配置值，请单击最右侧的覆盖值选项，这将为关联参数启动一个配置窗口。

[![使用 SAP HANA Cockpit GUI 查看 indexserver.ini 配置文件的密码策略设置](bilderklein/klein12_002.png)](img-f12.2.html)

**图 12.2** 使用 SAP HANA Cockpit GUI 查看 indexserver.ini 配置文件的密码策略设置

[图 12.3](#12_001.html#f12.3) 显示了 `last_used_passwords` 参数配置窗口的示例，以及如何为系统值覆盖参数，即在选择数据库下拉列表下为所有租户数据库或单个租户数据库值覆盖参数。

[![更改 last_used_passwords 的密码策略设置](bilderklein/klein12_003.png)](img-f12.3.html)

**图 12.3** 更改 last_used_passwords 的密码策略设置

配置窗口将列出设置的默认值和活动值。此外，您可以单击恢复默认值按钮以快速恢复设置的默认值。要更改配置设置，请在提供的字段中输入所需值并单击确定按钮。要在保存前取消更改，请单击取消按钮。密码策略设置在 SAP HANA 系统中立即生效；无需重启即可生效。

## SAP HANA Cockpit：身份验证密码策略 GUI

SAP HANA Cockpit 还提供了一个专用 GUI 来管理密码策略。您可以通过单击 SAP HANA Cockpit 系统概览页面身份验证部分中的密码策略链接来访问该 GUI。[图 12.4](#12_001.html#f12.4) 显示了 SAP HANA Cockpit 中密码策略管理 GUI 的概览。请注意，前一节中列出的相同配置设置也在此 GUI 中可用。

要修改密码策略，请单击窗口右上角的编辑按钮。对于每个设置，将出现可编辑字段或单选按钮选项。单击底部的保存按钮以保存更改。单击取消以丢弃任何未保存的更改。

[![SAP HANA Cockpit 中的密码策略配置 GUI](bilderklein/klein12_004.png)](img-f12.4.html)

**图 12.4** SAP HANA Cockpit 中的密码策略配置 GUI

GUI 还在顶部提供了一个额外的密码黑名单选项卡，位于密码策略选项卡旁边，如 [图 12.4](#12_001.html#f12.4) 所示。此界面（如 [图 12.5](#12_001.html#f12.5) 所示）允许管理员定义一组特定单词、短语或密码组合，系统不会为给定用户接受这些组合。

[![密码黑名单配置 GUI](bilderklein/klein12_005.png)](img-f12.5.html)

**图 12.5** 密码黑名单配置 GUI

要添加黑名单项，请单击密码黑名单选项卡右上角的编辑按钮。在提供的列中，单击添加条目按钮以向列表中插入新短语。如果您希望系统在提供的密码中查找该单词，请选择包含在密码中选项旁边的复选框。例如，如果黑名单单词是“welcome”，则密码“welcome1234”不会被接受，因为它包含目标单词。如果未选择包含在密码中选项，系统将仅阻止第一个单元格中列出的确切单词。使用相同示例，密码“welcome1234”是可接受的，因为它不是“welcome”的精确匹配。如果应使用输入文本的精确大小写来评估该单词，请选择区分大小写复选框。例如，如果选择区分大小写选项，则如果提供的黑名单单词是“welcome”，将接受“Welcome”。

您还可以执行以下 SQL 语句以查看系统中定义的配置黑名单密码单词列表：

```
SELECT * FROM "_SYS_SECURITY"."_SYS_PASSWORD_BLACKLIST"
```

## SAP HANA Cockpit：用户组特定密码策略

从 SAP HANA 2.0 开始，您还可以定义用户组。用户组是组织单元，可帮助您将用户分组到容器中，用于委派管理目的和密码策略目的。用户组当前不用于授权目的。使用用户组，您可以向特定管理员授予对选定用户组的访问权限。您还可以为每个组定义唯一的密码策略。

在 SAP HANA Cockpit 中，您可以从用于创建和编辑组的相同磁贴和链接访问此密码策略。找到用户和角色管理磁贴并单击管理用户组链接，这将启动用户组管理窗口。在管理窗口中，您将看到先前定义的用户组列表。单击列表中的组以打开该组的管理选项。在组管理窗口打开时，单击密码策略选项卡。您将看到该组的配置密码策略选项列表。单击编辑按钮以修改该组的密码策略。

请注意，如果未为用户组显式配置单个密码策略，则该值将默认为系统或租户数据库中配置的值。您还可以随时发出以下 SQL 语句以查看给定用户的密码策略，以查看其有效密码策略：

```
SELECT * FROM "SYS"."M_EFFECTIVE_PASSWORD_POLICY" WHERE USER_NAME = '<USER_NAME>';
```

## SAP HANA Web-Based Development Workbench 安全管理器

SAP HANA Web-Based Development Workbench 安全管理器托管在 XS 引擎中，提供了一个用于管理安全设置（包括密码策略）的界面。

您可以通过更新以下两个 URL 以匹配您环境的详细信息来访问 SAP HANA Web-Based Development Workbench 安全管理器：

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`
*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`

