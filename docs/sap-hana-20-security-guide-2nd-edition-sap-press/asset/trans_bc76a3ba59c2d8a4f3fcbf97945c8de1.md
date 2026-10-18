

SAP HANA 2.0 支持通信加密、备份加密、数据卷加密和日志卷加密。SAP HANA 1.0 仅支持通信加密和数据卷加密。加密通信协议可保护数据在客户端应用程序与 SAP HANA 服务器之间传输时的信息。备份、数据和日志卷加密可保护数据免受拥有 SAP HANA 文件系统物理访问权限的个人访问。启用数据和日志卷加密后，数据只能通过 SAP HANA 支持的身份验证和内部授权机制访问。

当信息在不受信任且不安全的网络上传输时，应随时使用通信加密，这可能包括您组织的内部网络，但肯定包括通过公共网络的访问。例如，如果您的 SAP HANA 系统由云服务提供商托管，则应使用传输层安全协议 (TLS) 对通信协议进行加密，并要求客户端使用 TLS 连接。

如果对 SAP HANA 服务器或存储的物理访问控制存在疑问，则应使用备份、数据和日志卷加密。例如，如果服务器的数据中心由多个组织共享或由云服务提供商托管，则强烈建议使用数据和日志卷加密。

## 17.3 识别具有提升权限的用户

在实施安全模型时，您的组织应维护一份已被授予 SAP HANA 系统高级别访问权限的用户列表。高级别访问一词大致描述了用户拥有的本质上具有风险的权限。SAP HANA 中的许多系统权限本质上具有风险，不应授予其他用户，但其他类型的权限也可能具有风险。

使用 SAP HANA 的组织无法完全避免将这些权限授予部分用户。但是，应对系统进行审查并频繁审计，以确保用户根据其既定职能和组织定义的职责分工拥有适当的权限。

在本节中，我们将识别本质上具有风险的系统、包和分析权限，并列出本质上具有风险的默认角色。此外，我们将帮助您使用 SQL 语句识别具有这些权限的用户帐户。

### 17.3.1 系统权限

除少数例外外，大多数系统权限本质上具有风险，因为它们允许用户对系统进行更改。但是，在我们看来，`DATA ADMIN`、`USER ADMIN`、`ROLE ADMIN`、`AUDIT OPERATOR` 和 `INIFILE ADMIN` 系统权限是可授予的最危险的权限之一。应限制拥有这些系统权限的用户，并应定期审计其操作。让我们更详细地了解每个系统权限。

#### 数据管理员

拥有 `DATA ADMIN` 系统权限的被授予者可以查询所有系统视图。这些用户还可以针对任何架构中的任何表执行数据定义语言 (DDL) SQL 命令。DDL 命令包括 `ALTER`、`DROP` 和 `CREATE` 等项。仅在必要时才应授予此权限。要识别拥有此权限的被授予者，请执行 [清单 17.1](#17_003.html#l17.1) 中显示的 SQL 代码。

```
SELECT * 
FROM SYS.EFFECTIVE_PRIVILEGE_GRANTEES 
WHERE OBJECT_TYPE = 'SYSTEMPRIVILEGE' 
AND PRIVILEGE = 'DATA ADMIN' 
AND GRANTEE NOT IN ('SYSTEM','_SYS_REPO');
```

**清单 17.1** 识别拥有 DATA ADMIN 系统权限的被授予者的 SQL 代码

请注意，[清单 17.1](#17_003.html#l17.1) 中显示的代码从结果中排除了 `SYSTEM` 和 `_SYS_REPO` 默认帐户。

#### 用户管理员

`USER ADMIN` 系统权限允许被授予者在系统中 `CREATE`、`ALTER` 或 `DROP` 任何用户，并包括密码重置、第三方身份管理和删除用户等操作。在大多数情况下，此权限仅应授予负责用户帐户管理的用户。

要识别拥有此权限的被授予者，请执行 [清单 17.2](#17_003.html#l17.2) 中显示的 SQL 代码。

```
SELECT * 
FROM SYS.EFFECTIVE_PRIVILEGE_GRANTEES 
WHERE OBJECT_TYPE = 'SYSTEMPRIVILEGE' 
AND PRIVILEGE = 'USER ADMIN' 
AND GRANTEE NOT IN ('SYSTEM','_SYS_REPO');
```

**清单 17.2** 识别拥有 USER ADMIN 系统权限的被授予者的 SQL 代码

请注意，[清单 17.2](#17_003.html#l17.2) 中显示的代码从结果中排除了 `SYSTEM` 和 `_SYS_REPO` 默认帐户。

#### 角色管理员

`ROLE ADMIN` 系统权限允许被授予者 `CREATE` 和 `DROP` 标准角色。此权限还允许被授予者将现有标准角色授予另一个被授予者，即使 `ROLE ADMIN` 权限持有者未明确分配 `WITH ADMIN` 选项。因此，如果用户拥有 `ROLE ADMIN` 系统权限，组织无法限制可以授予哪些角色。此外，您的组织应限制标准角色的使用，而改用基于存储库的角色。考虑到这些风险，仅在必要时才应授予此权限。

要识别拥有此权限的被授予者，请执行 [清单 17.3](#17_003.html#l17.3) 中显示的 SQL 代码。

```
SELECT * 
FROM SYS.EFFECTIVE_PRIVILEGE_GRANTEES 
WHERE OBJECT_TYPE = 'SYSTEMPRIVILEGE' 
AND PRIVILEGE = 'ROLE ADMIN' 
AND GRANTEE NOT IN ('SYSTEM','_SYS_REPO');
```

**清单 17.3** 识别拥有 ROLE ADMIN 系统权限的被授予者的 SQL 代码

请注意，[清单 17.3](#17_003.html#l17.3) 中显示的代码从结果中排除了 `SYSTEM` 和 `_SYS_REPO` 默认帐户。

#### 审计操作员

`AUDIT OPERATOR` 系统权限允许被授予者清除审计日志，仅在必要时才应授予。通常，审计日志相关系统权限永远不会分配给安全管理员，以确保安全管理员无法更改审计策略或清除审计日志以掩盖其踪迹。

要识别拥有此权限的被授予者，请执行 [清单 17.4](#17_003.html#l17.4) 中显示的 SQL 代码。

```
SELECT * 
FROM SYS.EFFECTIVE_PRIVILEGE_GRANTEES 
WHERE OBJECT_TYPE = 'SYSTEMPRIVILEGE' 
AND PRIVILEGE = 'AUDIT OPERATOR' 
AND GRANTEE NOT IN ('SYSTEM','_SYS_REPO');
```

**清单 17.4** 识别拥有 AUDIT OPERATOR 系统权限的被授予者的 SQL 代码

请注意，[清单 17.4](#17_003.html#l17.4) 中显示的代码从结果中排除了 `SYSTEM` 和 `_SYS_REPO` 默认帐户。

#### INIFILE 管理员

`INIFILE ADMIN` 系统权限允许被授予者更改任何 SAP HANA 配置设置。对系统配置的更改在生产环境中极具风险，也可能影响非生产环境的操作。因此，此系统权限仅应授予负责实施系统配置更改的管理员。

要识别拥有此权限的被授予者，请执行 [清单 17.5](#17_003.html#l17.5) 中显示的 SQL 代码。

```
SELECT * 
FROM SYS.EFFECTIVE_PRIVILEGE_GRANTEES 
WHERE OBJECT_TYPE = 'SYSTEMPRIVILEGE' 
AND PRIVILEGE = 'INIFILE ADMIN' 
AND GRANTEE NOT IN ('SYSTEM','_SYS_REPO');
```

**清单 17.5** 识别拥有 INIFILE ADMIN 系统权限的被授予者的 SQL 代码

请注意，[清单 17.5](#17_003.html#l17.5) 中显示的代码从结果中排除了 `SYSTEM` 和 `_SYS_REPO` 默认帐户。

### 17.3.2 根包权限

当被授予者拥有根包权限时，该用户被假定在存储库中的所有包上都拥有所授予的权限。识别拥有允许对存储库进行更改的根包权限的用户非常重要。以下包权限允许对存储库进行更改：

*   `REPO.EDIT_NATIVE_OBJECTS`
*   `REPO.ACTIVATE_NATIVE_OBJECTS`
*   `REPO.MAINTAIN_NATIVE_PACKAGES`

