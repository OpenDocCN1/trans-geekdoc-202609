

### 10.4.2 创建基于静态 SQL 的分析权限

创建基于静态 SQL 的分析权限的过程与其经典 XML 版本几乎相同。要创建基于静态 SQL 的分析权限，请打开 SAP HANA Web-Based Development Workbench 编辑器。在存储库中，找到安全位置中的一个包。右键单击该包并选择 New • Analytic Privilege…。将出现一个标记为 New Analytic Privilege 的弹出窗口，如 [图 10.7](#10_004.html#f10.7) 所示。

[![New SQL-Based Analytic Privilege Window](bilderklein/klein10_007.png)](img-f10.7.html)

**图 10.7** New SQL-Based Analytic Privilege Window

要指定使用 SQL 分析权限，Type 下拉列表必须设置为 SQL。除此之外，过程与我们在 [第 10.4.1 节](#10_004.html#h10.4.1) 中概述的过程相同。在 New Analytic Privilege 窗口中，在 Name 字段中指定分析权限的技术名称。名称只能包含字符 A–Z、a–z 和下划线 (`_`) 特殊字符。在 Label 字段中，输入描述。在 Type 下拉列表中，根据引用的信息视图选择适当的选项。例如，为配置为使用 SQL 分析权限的引用信息视图选择 SQL 选项。单击 Create 继续。

基于 SQL 的分析权限管理窗口与用于管理基于 XML 的分析权限的窗口几乎相同。一个关键区别是，基于 SQL 的分析权限窗口有三个额外的单选按钮选项，如 [图 10.8](#10_004.html#f10.8) 所示，位于 Privilege Validity 部分上方。这三个选项是 Attributes、SQL Editor 和 Dynamic。

[![SQL-Based Analytic Privileges Management Window](bilderklein/klein10_008.png)](img-f10.8.html)

**图 10.8** SQL-Based Analytic Privileges Management Window

要配置静态分析权限，必须选择 Attributes 选项。本章后面，我们将探讨其余两个选项的使用：Dynamic（[第 10.5.2 节](#10_005.html#h10.5.2)）和 SQL Editor（[第 10.6 节](#10_006.html#h10.6)）。

选择 Attributes 选项后，Secured Models、Associated Attribute Restrictions 和 Privilege Validity 部分的配置与我们在 [第 10.4.1 节](#10_004.html#h10.4.1) 中提供的步骤相同。

请注意，如果您在 Secure Models 部分引用信息视图但未定义任何限制，则授予此分析权限的角色将对引用的信息视图及其管辖的任何数据拥有完整查询访问权限。即使被授予者针对同一信息视图还拥有多个相互矛盾的基于 SQL 的分析权限，此规则也适用。根据测试，在这种情况下，过滤条件 `1 = 1` 将被有效推导并应用为限制。由于 `1 = 1` 对所有记录都为真，所有其他限制都将被有效忽略。

## 10.5 管理动态分析权限

您可以创建基于 XML 或基于 SQL 的动态分析权限。这些选项相似，但存在一些主要区别。请注意，SAP 文档指出基于 XML 的分析权限将在未来由基于 SQL 的分析权限取代，因此我们建议所有新开发均基于 SQL 分析权限工作流。在本节中，我们将首先简要介绍基于 XML 的分析权限。然后，由于基于 SQL 的分析权限是未来推荐的方法，我们将对其端到端创建过程进行更详细的讨论。

### 10.5.1 基于 XML 的动态分析权限

基于 XML 的动态分析权限是在用于定义基于 XML 的静态分析权限的同一界面中设置的（[第 10.4.1 节](#10_004.html#h10.4.1)）。但是，要将分析权限配置为动态，必须在管理界面的 Assign Restrictions 部分中选择不同的选项。在此部分中，必须将 Restriction Type 列的值从 Fixed 更改为 Catalog Procedure 或 Repository Procedure。Operator 列应包含一个运算符，以便于 Value 列中所选存储过程的结果。在大多数情况下，您将选择 IN 运算符，因为该过程将返回一个值数组。

在讨论存储过程的配置之前，让我们先回顾一下基于 XML 的动态权限的结构。这些分析权限本质上被配置为在目录表中执行查找，以检索给定用户的过滤值数组。查找基于用户名，该用户名从查询引用信息视图的 SAP HANA 用户帐户中推导而来。存储映射数据的表至少需要两列：第一列包含用户名，第二列包含过滤值。[表 10.1](#10_005.html#t10.1) 显示了该表的结构示例，并包含一些示例数据。

| USER_NAME | FILTER_VALUE |
| --- | --- |
| SHODGE01 | North Central |
| CBESSLER04 | South West |
| WTRAN05 | North Central |
| WTRAN05 | South Central |

**表 10.1** 用于促进基于 XML 的动态分析权限的映射

选定用于与分析权限配合使用的存储过程必须配置为从此表返回单个值或值数组。因此，存储过程的输出变量必须配置为表类型。表类型是充当一种虚拟表的目录对象，最常用于临时定义存储过程的表格输出。例如，您可以使用以下 SQL 代码定义容纳此存储过程输出所需的表类型：

```sql
CREATE TYPE "SECURITY"."CUSTOMER_ACCESS" AS TABLE ( "CUSTOMERKEY" int);
```

该过程本身被定义为基于包含用户到值映射的表输出一条或多条记录。[清单 10.1](#10_005.html#l10.1) 中显示的 SAP HANA 特定 SQLScript 将创建一个满足这些要求的过程。

```sql
CREATE PROCEDURE "SECURITY"."SP_RLS_CUSTOMER" ( OUT VAL     "SECURITY"."CUSTOMER_ACCESS" )        
LANGUAGE SQLSCRIPT     
SQL SECURITY DEFINER     
READS SQL DATA AS    
BEGIN
      VAL = SELECT FILTER_VALUE FROM "SECURITY"."RLS_CUSTOMER_ACCESS”  
WHERE USER_NAME = SESSION_USER;    
END;
```

**清单 10.1** 用于基于 XML 的动态分析权限的存储过程

在 SQLScript 代码中，请注意以 `VAL = SELECT FILTER_VALUE FROM` 开头的行。此行中的 SELECT 语句查询表，并使用 `USER_NAME = SESSION_USER` 的 WHERE 子句来细化返回的值。`SESSION_USER` 变量为 SAP HANA 系统所知，并在运行时替换为分配了此分析权限的用户名。

例如，假设用户帐户 `WTRAN05` 用于在查询信息视图时对 SAP HANA 进行身份验证。该用户帐户被授予基于 XML 的动态分析权限。当 `WTRAN05` 查询动态分析权限引用的信息视图时，存储过程中的过滤条件将从 `USER_NAME = SESSION_USER` 更改为 `USER_NAME = WTRAN05`。与 `WTRAN05` 关联的表中的所有值将由表类型输出变量返回。该值数组随后将传递给执行引擎并用于过滤信息视图。根据 [表 10.1](#10_005.html#t10.1)，值 North Central 和 South Central 将用作过滤条件。

您现在应该对基于 XML 的动态分析权限的结构有基本了解。请记住，此类分析权限将被基于 SQL 的动态分析权限取代。在下一节中，我们将详细回顾创建基于 SQL 的动态分析权限的过程。

