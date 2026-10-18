

在 SAP HANA 管理员将 CSV 文件导入 SAP HANA 系统之前，他必须先创建一个表来存储数据。根据 E-Corporation 安全顾问的建议，管理员将创建一个新的存储库架构和一个新的基于存储库的表，以便存放导入的 LDAP 用户列表。使用专用的架构和表来托管与安全相关的数据和程序，可以简化对架构、表、存储过程以及未来支持对象的访问限制过程。

在本案例研究中，我们将引导您了解该解决方案的技术细节。我们将首先回顾将 LDAP 用户列表导入 SAP HANA 表所需的流程；然后，我们将回顾创建基于存储库的存储过程所需的流程，这些存储过程将以编程方式配置、停用和删除从 LDAP 系统导入的用户帐户。

### 4.5.1 创建存储库架构

在创建存储库架构之前，管理员决定创建几个新的包层级别，用于存储其用户配置程序的新开发对象。E-Corporation 已经有一个名为 Security 的根包。新程序将需要一个架构、一个表以及一系列存储过程。存储库架构开发工件将存储在名为 Schemas 的子包中，存储库存储过程开发工件将存储在名为 Provisioning 的子包中，而存储库表开发工件将存储在名为 Tables 的子包中。[Figure 4.18](#04_005.html#f4.18) 显示了完成的包层级别应如何在 SAP HANA Web-Based Development Workbench 编辑器中配置。

[![Package Hierarchy to Store Security-Related Development Content](bilderklein/klein04_018.png)](img-f4.18.html)

**Figure 4.18** Package Hierarchy to Store Security-Related Development Content

要创建包层级别，请登录 SAP HANA Web-Based Development Workbench 编辑器。在左侧，展开 Content。展开包层级别以显示名为 Security 的根级包节点。然后，右键单击 Security 节点并选择 New • Package 以定义 [Figure 4.18](#04_005.html#f4.18) 中显示的每个子包。例如，在 Package Name 字段中输入“Tables”以创建新的 Tables 子包。

要在包层级别中创建存储库架构，请右键单击 Schemas 包并选择 New。在弹出窗口中，选择 File。输入文件名“security_tables.hdbschema”。将出现一个新的空文件，您可以在其中定义存储库架构语法。

使用以下语法定义将用于存储与管理 SAP HANA 安全相关的存储库目录对象的存储库架构：

```
//To define the HDB schema, use the following code:     
schema_name = "security_tables";
```

单击保存图标（软盘）激活设计时脚本。[Figure 4.19](#04_005.html#f4.19) 显示了 `security_tables.hdbschema` 文件及其在 SAP HANA Web-Based Development Workbench 编辑器中的定义示例。

[![Defining the security_tables Schema in the Repository](bilderklein/klein04_019.png)](img-f4.19.html)

**Figure 4.19** Defining the security_tables Schema in the Repository

### 4.5.2 创建存储库表

在定义 `security_tables` 架构后，您现在可以创建一个基于存储库的表来托管从 CSV 文件导入的 LDAP 数据。要创建存储库表，请右键单击 `Security.Tables` 包并选择 New • File。将文件命名为“adusers.hdbtable”并单击 Create。

使用存储库表的定义语法，定义一个包含四个列的表：`USER_NAME`、`AD_USER_NAME`、`EMAIL_ADDRESS` 和 `ACCOUNT_STATUS`。[Listing 4.9](#04_005.html#l4.9) 显示了定义存储库表所需的语法。单击保存图标激活设计时脚本。

```
table.schemaName = "security_tables";
table.tableType = COLUMNSTORE;

table.columns =
 [
    {name = "USER_NAME";  sqlType = NVARCHAR;  length = 256; 
comment = "User Name in SAP HANA System"; },
    {name = "AD_USER_NAME";  sqlType = NVARCHAR;  length = 256; 
comment = "User Name in AD System"; },
    {name = "EMAIL_ADDRESS";  sqlType = NVARCHAR;  length = 256; 
comment = "Email address from AD System"; },
    {name = "ACCOUNT_STATUS";  sqlType = NVARCHAR;  length = 1; 
comment = "A for Active, D for Disabled"; }     

];    

table.primaryKey.pkcolumns = ["USER_NAME"];
```

**Listing 4.9** Repository Table Syntax

一旦存储库表脚本被激活，表 `Security.Tables::adusers` 将出现在 `security_tables` 架构中。我们现在可以将 CSV 数据加载到此表中了。

### 4.5.3 将 CSV 文件导入表中

请回顾，我们的 LDAP 系统管理员提供了一个包含超过 5,000 名用户列表的 CSV 文件。您现在需要将此 CSV 文件的内容添加到存储库中。

SAP HANA 存储库可以存储几乎任何类型的文件，包括 `.csv` 文件。为了验证解决方案的设计，假设我们的 SAP HANA 开发人员决定将 `.csv` 文件存储在存储库中，然后定义一个表导入存储库对象，以将 `.csv` 的内容加载到我们在 [Section 4.5.2](#04_005.html#h4.5.2) 中设计的 `Security.Tables::adusers` 表中。要创建 `.csv` 文件，请右键单击包 `Security.Tables` 并选择 New • File。将文件名输入为“user_list.csv”并单击 Create。将出现一个空文件选项卡。将提供的 `.csv` 文件的内容复制并粘贴到存储库中托管的 `user_list.csv` 文件中。一旦将内容放入文件中，单击保存图标以在存储库中激活该文件。[Figure 4.20](#04_005.html#f4.20) 显示了存储库中此文件的示例。

[![Defining the user_list.csv File in the Repository](bilderklein/klein04_020.png)](img-f4.20.html)

**Figure 4.20** Defining the user_list.csv File in the Repository

接下来，您需要定义一个表导入配置文件，以将 `.csv` 文件导入到 `Security.Tables::adusers` 表中。表导入配置文件使用特定的关键字和值对语法来定义源 `.csv` 文件和目标表。这些文件具有 `.hdbti` 扩展名，一旦保存并激活，源 `.csv` 文件的内容将被导入到目标表中。

要创建 `.hdbti` 文件，请右键单击包 `Security.Tables` 并选择 New • File。将文件名输入为“user_list.hdbti”并单击 Create。将出现一个空文件选项卡。输入 [Listing 4.10](#04_005.html#l4.10) 中显示的语法。

```
import = [
{
hdbtable = "Security.Tables::adusers";                   
file = "Security.Tables:user_list.csv";    
header = true;
delimField = ",";
} 
];
```

**Listing 4.10** The user_list.hdbti File Syntax

单击保存图标以保存并激活 `.hdbti` 文件。保存后，`.csv` 文件的内容将被导入到表 `Security.Tables::adusers` 中。

### 4.5.4 创建存储库角色以访问表

在开发人员和管理员可以查看 `Security.Tables::adusers` 表的内容之前，安全团队必须定义角色，以便这些用户在运行时可以访问查看表内容。为了满足此要求，我们的开发人员向安全团队提出了请求，要求定义一个新的存储库角色，然后将存储库角色授予开发人员。

安全团队定义了一个名为 `SCHEMA_ADMIN_SECURITY_TABLES` 的角色，并将其放置在 `Security.Roles` 包中。[Figure 4.21](#04_005.html#f4.21) 显示了该角色在 SAP HANA Web-Based Development Workbench 编辑器中定义的示例。

