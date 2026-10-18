

[![在 SAP HANA Cockpit 中配置审计策略状态](bilderklein/klein15_010.png)](img-f15.10.html)

**图 15.10** 在 SAP HANA Cockpit 中配置审计策略状态

保存后，您现在应该在 SAP HANA Cockpit 的审计界面中看到已列出的策略。要在创建后编辑策略，请单击列表中的策略名称以打开策略详情。单击概览屏幕右上角的“编辑”按钮。启用编辑模式后，您可以更改策略状态、审计操作状态和审计跟踪目标选项。在“审计操作”部分中，如 [图 15.11](#15_003.html#f15.11) 所示，您可以单击每个操作右侧圆圈内的 X 图标来删除操作。您可以单击位于右上角的“添加操作”按钮来添加其他操作。

[![在 SAP HANA Cockpit 中修改现有审计策略的界面](bilderklein/klein15_011.png)](img-f15.11.html)

**图 15.11** 在 SAP HANA Cockpit 中修改现有审计策略的界面

在修改“审计对象”和“策略中包含的用户”部分时，您将遵循类似的过程。完成更改后，单击窗口右下角的保存按钮。

您现在应该对构成审计策略的组件有深入的了解。此外，您还应该了解如何使用 SAP HANA Web-Based Development Workbench 安全控制台、SAP HANA Cockpit 和 SQL 语句来配置策略。在下一节中，我们将回顾包含审计特定数据的各种系统视图。

## 15.4 查询审计数据

您可以查询三个与审计数据和 SAP HANA 中审计配置相关的主要系统视图。这些视图可用于多种目的。这三个视图是 `AUDIT_ACTIONS`、`AUDIT_LOG` 和 `AUDIT_POLICIES`，它们都位于 `SYS` 架构中。

###### 注意

有关每个视图的更多信息，请参阅 SAP HANA SQL 和系统视图参考指南，可在 [http://s-prs.co/v498219](http://s-prs.co/v498219) 处查阅。

* `AUDIT_ACTIONS`

    审计操作视图提供对 SAP HANA 系统中所有可审计操作列表的访问。此视图提供审计操作列表和标志，以指示需要用户或目录对象引用的操作。当您需要查看支持的审计操作列表时，此视图很有用。要查询该视图，请发出以下 SQL 语句：

    ```
    SELECT * FROM SYS.AUDIT_ACTIONS;
    ```

* `AUDIT_LOG`

    审计日志视图提供对基于启用的审计策略的所有记录操作的访问。启用审计策略后，事件会写入隐藏的系统表 `_SYS_AUDIT.CS_AUDIT_LOG_`。审计日志视图引用此系统表。管理员可以创建引用此系统视图的各种审计相关查询，并且该视图包含多个列。要查询该视图，请发出以下 SQL 语句：

    ```
    SELECT * FROM SYS.AUDIT_LOG;
    ```

* `AUDIT_POLICIES`

    审计策略视图提供系统中定义的所有审计策略的完整列表。可以查询此视图以确定在 SAP HANA 系统中定义的审计策略的数量和范围。请注意，单个策略在视图中可能有多个记录；每个记录代表一个唯一的配置选项。例如，如果您在策略中引用多个用户，则每个用户的记录都将在此视图中表示。要查询该视图，请发出以下 SQL 语句：

    ```
    SELECT * FROM SYS.AUDIT_POLICIES;
    ```

本节中列出的视图在您的组织需要检查从审计中收集的数据以及审计机制本身的配置时很有用。在下一节中，我们将带您了解一个案例研究，概述 E-Corporation 在定义其审计策略时使用的决策过程。我们还将向您展示公司用于定义其审计策略的 SQL。

## 15.5 案例研究：定义审计策略

E-Corporation 最近在 SAP HANA 环境中启用了审计。其内部审计小组确定，出于法规合规性和最佳实践的目的，捕获审计事件是必要的。E-Corporation 联系了其 SAP HANA 安全顾问，并请求帮助审查和实施拟议的审计策略。因此，E-Corporation 列出了其要求，随后是其顾问的建议，我们将在以下部分中进行审查。顾问将使用 SQL 语句来定义确切的推荐策略。

E-Corporation 要求审计策略配置为便于主动事件监控、审计报告、身份验证操作、未经授权的访问、系统更改、安全管理和超级用户事件。让我们详细查看每个要求。

### 15.5.1 主动事件监控

#### 要求

E-Corporation 要求 SAP HANA 审计系统支持可以主动挖掘系统审计日志的外部工具。这些工具将需要 Open Database Connectivity (ODBC) 和 Java Database Connectivity (JDBC) 访问审计日志表。

#### 解决方案

审计策略应配置为支持可以主动监控的事件。这些事件包括但不限于失败的登录事件、未经授权的操作、对系统的过度查询访问以及其他活动。此外，事件需要记录到内部 SAP HANA 数据库表中，以允许这些事件通过 JDBC 或 ODBC 连接以及通过 SQL 查询使用。大多数监控工具支持这种类型的访问。

### 15.5.2 审计报告

#### 要求

E-Corporation 要求所有审计日志数据都可以使用 ODBC 和 JDBC 协议访问。

#### 解决方案

审计事件必须记录到内部 SAP HANA 数据库表中，这将允许这些事件通过 JDBC 或 ODBC 连接以及通过 SQL 查询使用。大多数报告工具支持这种类型的访问。

### 15.5.3 身份验证审计

#### 要求

E-Corporation 要求记录审计日志中的所有连接和断开连接尝试。但是，E-Corporation 不希望记录内部系统帐户进行的身份验证尝试。

#### 解决方案

安全顾问建议创建一个审计策略，将这些活动记录到 SAP HANA 中的表 `AUDIT_LOG`。将创建一个名为 `USER CONNECT AND DISCONNECT` 的审计策略，以监控标准用户执行的所有成功连接和随后的断开连接操作。不会在此策略中记录不成功的尝试，因为它们将在后续的审计策略中捕获。该策略不会记录系统生成帐户的事件。

该策略将使用 [清单 15.5](#15_005.html#l15.5) 中显示的 SQL 代码定义。

```
CREATE AUDIT POLICY "USER CONNECT AND DISCONNECT" 
AUDITING SUCCESSFUL CONNECT, DISCONNECT SESSION 
EXCEPT FOR 
     _SYS_AFL,
     _SYS_DI,
     _SYS_DI_BI_CATALOG,
     _SYS_DI_CATALOG,
     _SYS_DI_CDS_CATALOG,
     _SYS_DI_SEARCH_CATALOG,
     _SYS_DI_SU,
     _SYS_DI_TO,
     _SYS_EPM,
     _SYS_ES,
     _SYS_REPO,
     _SYS_SQL_ANALYZER,
     _SYS_STATISTICS,
     _SYS_TASK,
     _SYS_WORKLOAD_REPLAY,
     _SYS_XB,
     SYS_XS_SBSS 
LEVEL INFO;
```

**清单 15.5** 创建名为 `USER CONNECT AND DISCONNECT` 策略的 SQL 代码

要激活策略，必须执行以下 SQL 语句：

```
ALTER AUDIT POLICY "USER CONNECT AND DISCONNECT" ENABLE;
```

### 15.5.4 未经授权的操作审计

#### 要求

