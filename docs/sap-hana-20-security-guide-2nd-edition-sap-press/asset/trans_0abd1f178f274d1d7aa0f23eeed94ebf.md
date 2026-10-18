

一旦安全团队定义角色并将其授予开发人员后，开发人员即可查询表格内容，并看到 `.csv` 文件的内容已导入到表格中。[图 4.22](#04_005.html#f4.22) 显示了开发人员在 SAP HANA Web-Based Development Workbench 目录界面中查询表格的示例。

[![Defining the Role Used to Provide Developers Access to Manage the Security.Tables::adusers Table](bilderklein/klein04_021.png)](img-f4.21.html)

**图 4.21** 定义用于向开发人员提供管理 `Security.Tables::adusers` 表访问权限的角色

[![Viewing the Contents of the Security.Tables::adusers table](bilderklein/klein04_022.png)](img-f4.22.html)

**图 4.22** 查看 `Security.Tables::adusers` 表的内容

### 4.5.5 创建存储库存储过程

数据已导入到表 `Security.Tables::adusers` 中，您现在可以开发一个存储过程来配置表中列出的用户帐户。

请注意存储过程以及在 E-Corporation 中以编程方式创建用户所需流程的以下基本要求：

*   该过程将根据表中 `USER_NAME` 列的值创建一个用户帐户。
*   帐户密码需要复杂且随机生成。
*   用户永远不会使用用户名和密码的组合手动对 SAP HANA 系统进行身份验证。因此，他们永远不需要知道自己的密码。
*   用户帐户将使用配置的 SAML 提供程序和 SAML 标识进行身份验证。
*   用户帐户密码将设置为永不过期。但是，将创建另一个存储过程来随机重置用户帐户密码。该过程将每 90 天执行一次。
*   您需要为表中列出的每个用户帐户配置并启用 SAML。
*   您需要将用户电子邮件地址添加到用户属性中。此信息可帮助管理员联系用户，并在适用时允许系统向单个用户发送电子邮件。

基于这些要求，您需要创建两个独立的基于存储库的存储过程。第一个过程将命名为 `CREATE_AD_USERS`，它将配置表中列出的用户，添加 SAML 标识，启用 SAML，并添加电子邮件地址。

要使用 SAP HANA Web-Based Development Workbench 编辑器创建第一个基于存储库的存储过程，请右键单击 `Security.Provisioning` 包并选择 New • File。将文件命名为 “`CREATE_AD_USERS.hdbprocedure`” 并单击 Create。将出现一个新的空文件表，允许您定义存储过程。

使用 [清单 4.11](#04_005.html#l4.11) 中显示的语法定义 `CREATE_AD_USERS` 基于存储库的存储过程。单击保存图标激活设计时脚本。

```
PROCEDURE "security_tables"."Security.Provisioning::CREATE_AD_USERS" () 
  LANGUAGE SQLSCRIPT
  /* Procedure invoker must have privileges to create users */
  SQL SECURITY INVOKER
  AS
   BEGIN
/*Use a Cursor for future use. The following only 
loops one time based on each record from SQL statement */

 DECLARE CURSOR c_users_list FOR
/* Get Active Users from table that are not currently 
provisioned in HANA */
/* We need to escape the single quote mark around 
SAMUSER and EMAILADDRESS with three single quote 
marks ''' a total of 4 are needed */

SELECT 
UT.AD_USER_NAME, 
upper(UT.USER_NAME) as HANAUSER, 
'''' || UT.AD_USER_NAME || '''' as SAMUSER, 
CAST(ROUND(RAND() * 100000000,0) as NVARCHAR(50)) as RAN_NUMBER,
'''' || UT.EMAIL_ADDRESS || '''' as EMAILADDRESS
FROM  "security_tables"."Security.Tables::adusers" UT
WHERE upper(UT.USER_NAME) NOT IN 
    (SELECT upper(USER_NAME) FROM "SYS"."USERS") 
    and UT.ACCOUNT_STATUS = 'A';

 FOR cur_row as c_users_list DO
    --- Create Users with generic complex random password
    EXEC 'CREATE USER ' || cur_row.HANAUSER 
        || ' PASSWORD "asdfSAD!' || cur_row.RAN_NUMBER || '"';
    --- Update user account so the password will not expire
    EXEC 'ALTER USER ' || cur_row.HANAUSER || ' DISABLE PASSWORD LIFETIME' ;
    --- Add SAML identity to user account
    EXEC 'ALTER USER ' || cur_row.HANAUSER || ' ADD IDENTITY ' 
        || cur_row.SAMUSER || ' FOR SAML PROVIDER TEST_SAML_PROVIDER';
    --- Enable SAML Authentication for the user account
    EXEC 'ALTER USER ' || cur_row.HANAUSER ||' ENABLE SAML';
    --- Add Email Addres to user account
    EXEC 'ALTER USER ' || cur_row.HANAUSER 
        || ' SET PARAMETER EMAIL ADDRESS = ' || cur_row.EMAILADDRESS ;    
   
 END FOR;

END;
```

**清单 4.11** 创建用户的存储过程语法

重复该过程以创建另一个存储过程 `UPDATE_USER_PASSWORDS`。该过程可以定期执行，以更改表中列出的所有用户的密码。由于您将在每个密码字符串的末尾附加一个随机数生成器，因此每个用户的密码都不同，如 [清单 4.12](#04_005.html#l4.12) 所示。

```
PROCEDURE "security_tables"."Security.Provisioning::UPDATE_USER_PASSWORDS" ( ) 
  LANGUAGE SQLSCRIPT
  /* Procedure invoker must have privileges to create users */
  SQL SECURITY INVOKER
  AS
   BEGIN
/*Use a Cursor for future use. The following only 
loops one time based on each record from SQL statement */

 DECLARE CURSOR c_users_list FOR
/* Get Active Users from table that are currently 
provisioned in HANA */
/* We need to escape the single quote mark around 
SAMUSER and EMAILADDRESS with three single quote 
marks ''' a total of 4 are needed */

SELECT 
UT.AD_USER_NAME, 
upper(UT.USER_NAME) as HANAUSER, 
'''' || UT.AD_USER_NAME || '''' as SAMUSER, 
CAST(ROUND(RAND() * 100000000,0) as NVARCHAR(50)) as RAN_NUMBER,
'''' || UT.EMAIL_ADDRESS || '''' as EMAILADDRESS
FROM  "security_tables"."Security.Tables::adusers" UT
WHERE upper(UT.USER_NAME) IN 
    (SELECT upper(USER_NAME) FROM "SYS"."USERS");

 FOR cur_row as c_users_list DO
    --- Update Users from security table with a new generic complex random password
    EXEC 'ALTER USER ' || cur_row.HANAUSER 
        || ' PASSWORD "WxgT67e#21^' || cur_row.RAN_NUMBER || '"';

 END FOR;

END;
```

**清单 4.12** 更新用户密码的存储库存储过程语法

### 4.5.6 执行存储库存储过程

要执行存储过程，请打开 SQL 控制台。如果您的帐户具有 `USER ADMIN` 系统权限，则可以执行该过程，以根据从 CSV 文件导入到表中的用户记录以编程方式创建或更新用户。执行这两个过程所需的语法在以下两个 SQL 语句中提供：

```
CALL "security_tables"."Security.Provisioning::CREATE_AD_USERS"; CALL "security_tables"."Security.Provisioning::UPDATE_USER_PASSWORDS";
```

要验证用户是否已创建，请执行 [清单 4.13](#04_005.html#l4.13) 中显示的 SQL 代码。

```
SELECT 
CASE WHEN U.USER_NAME is null 
    THEN 'Not Created' ELSE 'Created' 
    END as CREATION_STATUS,
UT.USER_NAME as REQUESTED_HANAUSER,
U.USER_NAME as PROVISIONED_HANAUSER

FROM  "security_tables"."Security.Tables::adusers" UT
LEFT OUTER JOIN "SYS"."USERS" U 
    on (upper(UT.USER_NAME) = upper(U.USER_NAME));
```

**清单 4.13** 列出未由配置流程创建的用户的 SQL 代码

表中列出但在 SAP HANA 中未配置的用户将在 `CREATION_STATUS` 列中显示 Not Created；请再次执行 `CREATE_AD_USER` 过程以创建缺失的用户帐户。您还将在 SAP HANA cockpit 的 Manage Users 区域或 SAP HANA Web-Based Development Workbench 安全管理器中看到列出的用户帐户。

## 4.6 总结

