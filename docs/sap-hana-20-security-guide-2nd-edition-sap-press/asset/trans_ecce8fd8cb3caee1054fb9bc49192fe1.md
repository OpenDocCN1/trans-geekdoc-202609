

具有 SAP HANA OS 访问权限的用户可能会访问托管在数据或日志卷中的未加密数据。大多数组织会严格限制对本地 SAP HANA 实现的 OS 的访问，但使用托管或基于云的 SAP HANA 实现的组织可能对具有 OS 级访问权限或对存储驱动器物理访问权限的用户控制有限。当无法正确验证对 OS 的访问时，我们强烈建议使用备份、数据和日志卷加密。当对磁盘驱动器具有物理访问权限的个人未得到妥善管理时，情况亦是如此。

现在，让我们回顾一下 SAP HANA 如何管理用于加密的根密钥。

### 13.3.1 服务器端数据加密

SAP HANA 内置了加密服务，可帮助您管理托管在数据和日志卷中的数据的加密。该服务使用文件系统中的安全存储 (SSFS) 来保护加密根密钥。加密根密钥是 SAP HANA 系统内用于加密数据或通信的所有公钥或私钥的基础。SAP HANA 有两个 SSFS。第一个 SSFS 是 SAP HANA 实例 SSFS，它保护用于加密存储在数据和日志卷中的信息的根密钥。第二个 SSFS 是系统 PKI SSFS，它保护用于保护内部通信的根证书。

实例 SSFS 密钥默认存储在 OS 的以下位置：

`/usr/sap/<SID>/SYS/global/hdb/security/ssfs`

将示例中的 `<SID>` 变量替换为您的 SAP HANA 系统的 SID。在文件夹位置中，您将找到两个文件：`SSFS_<SID>.DAT` 和 `SSFS_<SID>.KEY`。

系统 PKI SSFS 密钥默认存储在 OS 的以下位置：

`/usr/sap/<SID>/SYS/global/security/rsecssfs/data`

将示例中的 `<SID>` 变量替换为您的 SAP HANA 系统的 SID。在文件夹位置中，您将找到两个文件：`SSFS_<SID>.DAT` 和 `SSFS_<SID>.KEY`。

鉴于其重要性，这些密钥应备份并存储在根密钥备份文件中。在恢复新 SAP HANA 主机或在备份文件创建日期之后生成新密钥的主机的恢复场景中，管理员必须能够访问此备份文件及其位置。启用数据或日志卷加密时，SSFS 需要在数据库恢复之前从备份中恢复。但是，如果您将备份恢复到用于生成备份文件的同一 SAP HANA 数据库，并且备份后未更改 SSFS 密钥，则不需要 SSFS 密钥恢复。备份介质可以恢复，因为目标上的 SSFS 与备份期间活动的 SSFS 密钥匹配。

接下来，我们将提供有关用于备份和恢复 SSFS 密钥的过程的更多详细信息。您的组织必须在每次更改 SSFS 密钥以及在启用备份、数据或日志卷加密之前维护 SSFS 密钥的备份。如果您丢失了 SSFS 密钥和 SAP HANA 系统，则无法将数据库恢复到另一个 SAP HANA 实例。

### 13.3.2 在 SSFS 中管理根密钥

在每个 SAP HANA 实例的标准安装或升级期间，会生成一个唯一的根密钥。标准安装是指遵循已记录的 SAP HANA 安装方法的安装。但是，由于 SAP HANA 通常作为设备交付，设备供应商可能在其每个设备构建中使用了相同的加密根密钥的副本。例如，供应商可能会部署 SAP HANA 设备文件系统的复制映像。使用映像可实现 SAP HANA 软件的快速且一致的部署，但每个默认实例最终都会使用相同的根密钥和 SSFS。组织还必须在安装期间考虑 SSFS 及其密钥的安全性。SAP HANA 目前必须由认证供应商或认证个人部署。该个人可能会复制根密钥并将其不安全地存储在组织控制之外。因此，无法保证加密根密钥的副本不存在于组织之外。因此，供应商完成安装后应更改这些密钥。

因此，组织通常需要在 SAP HANA 系统初始部署后生成新的加密根密钥。从 SAP HANA 2.0 开始，生成新根密钥时应备份 SSFS。组织可以执行一系列 SQL 语句来生成新密钥。要备份 SSFS，需要操作系统的命令行访问权限。在 SAP HANA 2.0 中生成新根密钥的过程如下：

1. 使用 SQL 命令生成新根密钥。
2. 备份新密钥并将其存储在安全的文件位置。
3. 使用 SQL 命令激活新密钥。

要正确执行这些活动，被授予者将需要 `<sid>adm` 操作系统凭据来执行命令行实用程序 `hdbnsutil`。被授予者需要 ENCRYPTION ROOT KEY ADMIN 系统权限。您还需要为根密钥备份文件建立密码。要建立此密码，请执行以下 SQL 语句：

```
ALTER SYSTEM SET ENCRYPTION ROOT KEYS BACKUP PASSWORD "<Password>";
```

要为 SAP HANA 数据卷生成新根密钥，请执行以下 SQL 命令：

```
ALTER SYSTEM PERSISTENCE ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

要为 SAP HANA 日志卷生成新根密钥，请执行以下 SQL 命令：

```
ALTER SYSTEM LOG ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

要为 SAP HANA 的内部应用程序加密生成新根密钥，请执行以下 SQL 命令：

```
ALTER SYSTEM APPLICATION ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

对于所有三个 SQL 语句，请注意指定了 `WITHOUT ACTIVATE` 选项。此选项允许生成新密钥而不使其在系统中处于活动状态。您必须在激活根密钥之前但在其创建之后立即备份根密钥。为此，您可以使用 `hdbnsutil` 命令行实用程序。要使用此实用程序，请使用 `<sid>adm` 凭据登录到 SAP HANA 操作系统。或者，您可以执行一个返回包含加密文本消息的 CLOB 字段的 SQL 语句。您可以将文本消息复制到文件并将其保存为 `.rkb` 扩展名。

要使用 `hdbnsutil` 命令行实用程序，请使用您选择的安全外壳 (SSH) 服务登录到 SAP HANA 系统。使用 `<sid>adm` 凭据登录到 shell。此实用程序存储在 `/usr/sap/<sid>/HDB<instance_number>/exe`。执行以下命令以备份根密钥：

```
./hdbnsutil -backupRootKeys <file path and name>.rkb --dbid=<dbid> --type='ALL'
```

如果 SAP HANA 是单容器系统，则可以省略命令中的 `–dbid=<dbid>` 部分。变量 `<dbid>` 应替换为租户数据库 ID。

如果您无法访问操作系统 shell，也可以执行一个 SQL 语句来返回包含 RKB 文件内容的 CLOB 字段。将 CLOB 字段的内容复制并保存到带有 `.rkb` 扩展名的文件中。要返回 CLOB 字段，请执行以下 SQL：

```
SELECT ENCRYPTION_ROOT_KEYS_EXTRACT_KEYS 
('PERSISTENCE, APPLICATION, LOG') FROM DUMMY
```

在激活新根密钥之前，您必须验证您拥有恢复根密钥所需的正确密码。为此，请从 SAP HANA OS shell 执行以下命令：

```
./hdbnsutil -validateRootKeysBackup <path to filename> --password="<password>"
```

