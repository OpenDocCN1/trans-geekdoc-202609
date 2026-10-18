

你也可以使用 SQL 语句来定义 SAP HANA 审计策略。使用 SQL 不太容易，但这种脚本选项可以帮助你在整个 SAP HANA 环境中应用一致的审计策略。SQL 脚本可以在 SAP HANA 大多数管理工具中找到的 SQL 控制台中执行。我们发现，基于 GUI 的工具在不一致的时间可用，并且不总是支持所有审计策略选项，但 SQL 选项支持所有可能的审计配置。

创建审计策略时，请使用 [清单 15.2](#15_003.html#l15.2) 中显示的通用 SQL 语法。

```
CREATE AUDIT POLICY <POLICY NAME> 
AUDITING <STATUS> <ACTIONS>
ON <CATALOG OBJECTS>
FOR | EXCEP FOR <USER LIST>
LEVEL <LEVEL> 
TRAIL TYPE <TRAIL>;
```

**清单 15.2** 定义审计策略的 SQL 模板

`<POLICY NAME>` 变量将替换为策略的名称。`<STATUS>` 变量应替换为 `SUCCESSFUL`、`UNSUCCESSFUL` 或 `ALL`。`<ACTIONS>` 变量应替换为特定于正在审计的操作的语法；例如，你可以指定一个或多个操作，如 `CREATE USER`、`ALTER USER` 或 `ALTER ROLE`。

###### 注意

所有可能操作的语法非常广泛，可以在 SAP HANA SQL 和系统视图参考指南中的“CREATE AUDIT POLICY 语句参考”部分找到。

你可以从 [http://s-prs.co/v498219](http://s-prs.co/v498219) 下载该指南。

`ON` 子句和 `<CATALOG OBJECTS>` 变量对于数据操作操作是必需的。`<CATALOG OBJECTS>` 变量应替换为目录对象的完全限定名称。

`<USER LIST>` 变量可以包含系统中用户账户的逗号分隔列表。`FOR` 和 `EXCEPT FOR` 语法对于大多数审计操作是可选的。`<LEVEL>` 变量可以替换为 `EMERGENCY`、`ALERT`、`CRITICAL`、`WARNING` 或 `INFO`。`<TRAIL>` 变量可以替换为 `TABLE`、`SYSLOG` 或 `CSV`。

为了更好地理解 SQL 语法，让我们回顾几个完整的 SQL 示例。要审计标准角色的管理，你可以使用以下代码创建名为 `MANAGE ROLE` 的审计策略：

```
CREATE AUDIT POLICY "MANAGE ROLE" 
AUDITING ALL CREATE ROLE, ALTER ROLE, DROP ROLE
LEVEL INFO;
```

要审计用户账户的管理，你可以使用以下代码创建名为 `MANAGE USER` 的审计策略：

```
CREATE AUDIT POLICY "MANAGE USER" 
AUDITING ALL CREATE USER, ALTER USER, DROP USER
LEVEL INFO;
```

要监控 `_SYS_REPO` 架构中存储过程的执行实例，你可以使用 [清单 15.3](#15_003.html#l15.3) 中显示的 SQL 代码创建审计策略：

```
CREATE AUDIT POLICY "GRANT OR REVOKE REPOSITORY OBJECTS" 
AUDITING ALL 
EXECUTE ON 
"_SYS_REPO"."*"
LEVEL INFO;
```

**清单 15.3** 创建名为 GRANT OR REVOKE REPOSITORY OBJECTS 的策略

要监控除系统账户用户外所有用户的所有不成功操作，你可以使用 [清单 15.4](#15_003.html#l15.4) 中显示的 SQL 代码创建策略：

```
CREATE AUDIT POLICY "ALL ACTIONS" 
AUDITING UNSUCCESSFUL ACTIONS 
EXCEPT FOR 
_SYS_DI, _SYS_AFL, _SYS_XB, _SYS_WORKLOAD_REPLAY, 
_SYS_TASK, _SYS_STATISTICS, _SYS_SQL_ANALYZER, 
_SYS_REPO, _SYS_ES, _SYS_EPM, _SYS_DI_TO, _SYS_DI_SU, 
_SYS_DI_SEARCH_CATALOG, _SYS_DI_CDS_CATALOG, _SYS_DI_CATALOG, 
_SYS_DI_BI_CATALOG 
LEVEL INFO;
```

**清单 15.4** 创建名为 ALL ACTIONS 的策略

使用 SQL 创建审计策略时，审计策略默认处于禁用状态。要激活策略，你需要发出 `ALTER AUDIT POLICY` SQL 语句。例如，你可以发出以下 SQL 语句来启用名为 `ALL ACTIONS` 的审计策略：

```
ALTER AUDIT POLICY "ALL ACTIONS" ENABLE;
```

要禁用审计策略，你可以发出以下 SQL 语句：

```
ALTER AUDIT POLICY "ALL ACTIONS" DISABLE;
```

要删除审计策略，你必须使用 `DROP AUDIT POLICY` SQL 语句。例如，你可以按如下方式删除 `ALL ACTIONS` 策略：

```
DROP AUDIT POLICY "ALL ACTIONS";
```

###### SAP HANA SQL 和系统视图参考指南

用于删除和修改审计策略的完整语法可以在 SAP HANA SQL 和系统视图参考指南中在线找到。查找“ALTER AUDIT POLICY 语句（访问控制）”和“DROP AUDIT POLICY 语句（访问控制）”部分。

用于创建审计策略的完整语法也可以在此指南中找到。查找“CREATE AUDIT POLICY 语句（访问控制）”部分。

使用 SQL 定义和管理审计策略有助于在整个 SAP HANA 环境中应用一致的审计策略。在下一节中，我们将简要回顾如何在 SAP HANA cockpit 中创建审计策略。

### 15.3.4 使用 SAP HANA Cockpit 创建策略

SAP HANA cockpit 提供了一个 GUI 界面，你可以在其中管理 SAP HANA 数据库中的审计。要访问安全管理器，请登录 SAP HANA cockpit 并连接到所需的数据库。单击“审计”磁贴。在此磁贴中，单击“审计”标题以访问审计界面。

在审计界面中，查找审计策略选项卡，如 [图 15.6](#15_003.html#f15.6) 所示。

要定义新的审计策略，请单击位于已定义审计策略列表上方的“创建审计策略”链接。将出现一个新界面，带有两步选项，最终将转变为四步过程。在第一步 `1. Name` 中，在提供的字段中输入审计策略的名称，将出现一个标记为 `Step 2` 的新按钮。单击 `Step 2` 按钮以进入下一步。

[![SAP HANA Cockpit 中的审计策略区域](bilderklein/klein15_006.png)](img-f15.6.html) 

**图 15.6** SAP HANA Cockpit 中的审计策略区域

下一步 `2. 审计操作和操作状态` 将出现，如 [图 15.7](#15_003.html#f15.7) 所示。在此页面上，你可以按类别为策略配置审计操作状态和特定的审计操作。请注意，你可以使用列出的审计事件上方的搜索框搜索类别或操作。选择操作后，`Step 3` 按钮将出现。单击此按钮以进入下一步。

[![在 SAP HANA Cockpit 中配置审计操作状态和审计策略操作](bilderklein/klein15_007.png)](img-f15.7.html) 

**图 15.7** 在 SAP HANA Cockpit 中配置审计操作状态和审计策略操作

下一步 `3. 审计用户` 将出现，如 [图 15.8](#15_003.html#f15.8) 所示。在“选择要由策略审计的用户”部分下选择一个选项。如果需要审计特定用户或多个用户，请在提供的列表中搜索用户，并为每个要审计的用户选择复选框。单击列表下方的 `Step 4` 按钮以继续。

[![在 SAP HANA Cockpit 中配置审计策略目标用户](bilderklein/klein15_008.png)](img-f15.8.html) 

**图 15.8** 在 SAP HANA Cockpit 中配置审计策略目标用户

下一步 `4. 审计跟踪` 将出现，如 [图 15.9](#15_003.html#f15.9) 所示。在此步骤中，你将为策略配置审计级别设置。

[![在 SAP HANA Cockpit 中配置审计策略审计跟踪](bilderklein/klein15_009.png)](img-f15.9.html) 

**图 15.9** 在 SAP HANA Cockpit 中配置审计策略审计跟踪

对于系统数据库，你可以配置一个或多个审计跟踪目标。对于租户数据库，你只能选择为数据库配置的默认跟踪目标。单击 `Step 5` 按钮以继续。

最后一步 `5. 策略状态` 允许你在保存时选择启用或禁用策略，如 [图 15.10](#15_003.html#f15.10) 所示。单击 `Review` 按钮进入摘要屏幕并查看每个单独设置，然后在准备好激活策略时单击底部的 `Save` 按钮。

