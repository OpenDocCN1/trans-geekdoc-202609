
# 数据和日志卷加密备份恢复

当在启用数据和日志卷加密的情况下创建备份时，该备份只能恢复到具有相同 SSFS 和根密钥的系统。如果需要将备份恢复到具有不同根密钥的系统，必须先从 RKB 文件恢复根密钥。要恢复根密钥，请从操作系统 shell 执行以下命令；您必须以 `<sid>adm` 用户身份进行身份验证才能恢复根密钥：

```
./hdbnsutil -recoverRootKeys <path to filename>.rkb --dbid=<dbid> 
--password="<password>" --type=ALL
```

如果 SAP HANA 是单容器系统，可以省略命令中的 `--dbid=<dbid>` 部分。变量 `<dbid>` 应替换为租户数据库 ID。

备份文件生成并验证后，可以在系统中激活新密钥。要激活所有三个区域的密钥，请执行以下三条语句：

```
ALTER SYSTEM PERSISTENCE ENCRYPTION ACTIVATE NEW ROOT KEY;
ALTER SYSTEM LOG ENCRYPTION ACTIVATE NEW ROOT KEY;
ALTER SYSTEM APPLICATION ENCRYPTION ACTIVATE NEW ROOT KEY;
```

要查看系统中生成的根密钥的当前和历史状态，请查询 `ENCRYPTION_ROOT_KEYS` 系统视图。要查询此视图，请从 SQL 控制台执行以下 SQL 语句：

```
SELECT * FROM SYS.ENCRYPTION_ROOT_KEYS;
```

也可以使用 SAP HANA cockpit 管理 SSFS 密钥。连接到 SAP HANA cockpit 中的数据库后，从系统概览页面，单击“数据加密”磁贴以管理 SSFS 密钥。再次单击“数据加密”链接以访问数据加密配置管理界面。找到“静态数据加密”部分，如 [Figure 13.15](#13_003.html#f13.15) 所示，以查看数据卷加密和日志卷加密的当前状态。也可以使用此页面启用或禁用加密。

[![SAP HANA Cockpit Interface for Managing Data at Rest Encryption and SSFS Keys](bilderklein/klein13_015.png)](img-f13.15.html)

**Figure 13.15** SAP HANA Cockpit Interface for Managing Data at Rest Encryption and SSFS Keys

在数据卷加密部分的右侧，如 [Figure 13.16](#13_003.html#f13.16) 所示，您会注意到“管理密钥”链接。单击该链接以访问“管理密钥”界面。在此界面中，您可以更改根密钥备份密码、备份根密钥、生成根密钥，并查看根密钥的历史和状态。为数据卷加密根密钥、重做日志加密根密钥和备份加密根密钥维护了历史记录。单击“查看所有版本”链接以查看每个密钥的历史记录。

顾名思义，使用“更改根密钥备份密码”链接访问弹出窗口，您可以在其中更改密码。请记住此密码，因为在恢复加密备份之前恢复 SSFS 密钥需要它。

单击“备份加密根密钥”链接以下载根密钥的备份。当您需要备份文件但没有操作系统级访问权限时，此备份很有用。请记住保存密钥，以便在恢复任何加密备份介质之前可以恢复它们。如果目标系统中的 SSFS 密钥与创建备份介质时使用的密钥不匹配，则恢复到任何目标 SAP HANA 系统都将失败。

[![SAP HANA Cockpit Interface for Manage SSFS Keys](bilderklein/klein13_016.png)](img-f13.16.html)

**Figure 13.16** SAP HANA Cockpit Interface for Manage SSFS Keys

“更改根密钥备份密码”链接将启动一个三步向导，引导您更改或重新生成新的 SSFS 密钥。更改 SSFS 密钥后，请记住制作新的密钥备份。

在 SSFS 中生成新根密钥是所有组织在收到新 SAP HANA 设备后都应考虑的重要步骤。在下一节中，我们将探讨启用数据和日志卷加密所需的要求和命令。

# 13.3.3 加密数据卷

在 SAP HANA 2.0 中，有两种主要方法可以启用数据卷加密：通过专用 SQL 语句或通过 SAP HANA cockpit 中的“数据加密”链接。

## 使用 SQL

注意，在较旧版本的 SAP HANA 中，如果系统中已启用扩展存储，则无法启用数据卷加密；您需要先将扩展存储表移回内存存储并禁用扩展存储，然后才能成功执行命令。用户还需要 `ENCRYPTION ROOT KEY ADMIN` 系统权限才能在所有版本的 SAP HANA 中启用/禁用数据卷加密。要启用数据卷加密，请执行以下 SQL 命令：

```
ALTER SYSTEM PERSISTENCE ENCRYPTION ON;
```

要监控数据卷加密的状态，请执行以下 SQL 语句：

```
SELECT * FROM SYS.M_ENCRYPTION_OVERVIEW
```

## 使用 SAP HANA Cockpit

也可以使用 SAP HANA cockpit 管理数据卷加密。连接到 SAP HANA cockpit 中的数据库后，从系统概览页面，单击“数据加密”磁贴以管理 SSFS 密钥并启用或禁用加密。同一磁贴还包含一个部分，您可以使用开/关滑块快速启用或禁用数据卷加密。也可以单击“数据加密”链接访问此同一选项。找到“静态数据加密”部分以查看数据卷加密和日志卷加密的当前状态，或使用开/关滑块禁用或启用加密，如 [Figure 13.17](#13_003.html#f13.17) 所示。滑块下方还有元数据，将指示上次更改密钥的时间和用于加密的算法。

[![SAP HANA Cockpit Data Volume and Redo Log Volume Encryption Management Screen](bilderklein/klein13_017.png)](img-f13.17.html)

**Figure 13.17** SAP HANA Cockpit Data Volume and Redo Log Volume Encryption Management Screen

# 13.3.4 加密日志卷

加密日志卷是 SAP HANA 2.0 SPS 00 首先提供的功能。日志卷加密可以使用 SQL 和 SAP HANA cockpit 启用。

## 使用 SQL

可以从任何受支持的 SQL 控制台使用 SQL 来启用重做日志卷加密。要启用日志卷加密，请执行以下 SQL 命令：

```
ALTER SYSTEM LOG ENCRYPTION ON;
```

要监控日志卷加密的状态，请执行以下 SQL 语句：

```
SELECT * FROM SYS.M_ENCRYPTION_OVERVIEW
```

## 使用 SAP HANA Cockpit

也可以使用 SAP HANA cockpit 启用或禁用重做日志卷加密。从系统概览页面，单击“数据加密”磁贴以管理 SSFS 密钥并启用或禁用加密。同一磁贴还包含一个部分，您可以使用开/关滑块快速启用或禁用重做日志卷加密。也可以单击“数据加密”链接访问此同一选项。找到“静态数据加密”部分以查看日志卷加密的当前状态。使用开/关滑块禁用或启用重做日志卷加密。

# 13.3.5 加密备份介质

加密备份介质是 SAP HANA 2.0 SPS 01 首先提供的功能。备份加密可以使用 SQL 和 SAP HANA cockpit 启用。

## 使用 SQL

可以从任何受支持的 SQL 控制台使用 SQL 来启用备份加密。要启用备份加密，请执行以下 SQL 命令：

```
ALTER SYSTEM BACKUP ENCRYPTION ON;
```

要监控备份加密的状态，请执行以下 SQL 语句：

```
SELECT * FROM SYS.M_ENCRYPTION_OVERVIEW
```

## 使用 SAP HANA Cockpit
