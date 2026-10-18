

### 10.5.2 基于动态 SQL 的分析权限

基于动态 SQL 的分析权限提供了根据用户名与筛选条件之间的映射，对筛选条件进行编程查找的功能。基于 XML 的动态分析权限需要单个数据值，但基于 SQL 的动态分析权限需要筛选条件，类似于 SQL WHERE 子句中的筛选条件。使用筛选条件支持为给定用户动态生成的复杂且多样的筛选条件。例如，您可以在同一条件子句中引用多个属性列和筛选运算符类型。相比之下，每个基于 XML 的动态分析权限限制仅限于单个属性列和筛选值数组。

为了适应查找，必须存在一个表，将每个用户帐户映射到一个或多个筛选条件。[表 10.2](#10_005.html#t10.2) 显示了该表及其数据结构的基本示例。表可以更复杂，但至少必须遵循此结构。

| User Name || Filter Condition |

| --- | --- |

| JHARRIS01 || ("REGION" = ' North Central') |

| --- | --- |

| TTIM03 || ("REGION" = ' South West') |

| WTRAN05 || ("REGION" = ' North Central') |

| TIMG05 || ("REGION" = ' South Central') |

**表 10.2** 用于基于 SQL 的动态分析权限的示例映射

在表中，左列包含用户名。用户名值应与配置的 SAP HANA 用户帐户名称完全匹配。右列提供筛选条件，这些条件将被检索并添加到信息视图的执行中。这些条件应以一种方式构建，以将属性列与数据值匹配。同样，此构建类似于 SQL WHERE 子句中的筛选条件。以下语法表示构建基本单列筛选条件：

```
( <"COLUMN"> operator <'VALUE'> )
```

建议在整个条件语句周围加上括号。属性列应使用双引号。支持的运算符为 `=`、`<=`、`<`、`>=`、`>`、`LIKE`、`BETWEEN` 和 `IN`。如果值为字符串值，则应使用单引号。数字类型值不需要单引号。请注意，此模式不支持子查询筛选条件。

与基于 XML 的分析权限不同，返回这些条件的存储过程必须仅支持单值字符串输出变量。如果表中为给定用户存储了多行，则存储过程代码需要将这些行压缩为单个值。或者，存储在表中的条件可以非常复杂，使用列和运算符的混合，并消除为给定用户存储多个值的需求。例如，对于给定用户，以下条件也受支持：

```
((REGION IN ('NE','NW','SW','NC') ) or (PLANT IN ('1001','1005','1006')))
```

同样，为了适应从表中查找值，您需要创建一个存储过程。理想情况下，您应创建基于存储库的存储过程，但也支持基于目录的存储过程。请记住，`_SYS_REPO` 系统帐户将需要访问表和存储过程。因此，最好在存储库中创建这些对象，`_SYS_REPO` 将作为所有者并拥有完全访问权限。当在存储库中创建这些对象时，它们在交付单元中也可传输。

存储过程的结构必须符合几个条件。首先，存储过程必须配置为基于 `DEFINER` 的过程。换句话说，执行时将使用过程创建者进行验证。其次，该过程必须被视为只读，且应仅返回值而不执行任何数据操作语言 (DML) 语句。第三，存储过程不能包含任何输入参数。第四，该过程只能包含一个单值输出参数，数据类型为 `VARCHAR` 或 `NVARCHAR`。最后，`_SYS_REPO` 必须对过程及其引用的任何表拥有完全访问权限。

为了更好地理解该过程，让我们逐步了解实现动态分析权限所需的三个主要步骤。首先，您必须创建一个表来托管用户和数据元素映射。其次，您必须创建一个存储过程来执行值的查找。最后，您将构建一个基于 SQL 的动态分析权限。

#### 创建基于存储库的安全表

为了简化设计，您将创建一个基于存储库的表。您可以使用 SAP HANA Web-Based Development Workbench 编辑器创建此表。找到一个安全的包位置来托管基于存储库的表。右键单击所需的包节点并选择 New • File。将出现一个名为 Create File 的窗口。在 File Name 字段中，输入基于存储库的表的名称。例如，输入“`RLS_CUSTOMERKEY_ACCESS.hdbtable`”。单击 Create 以定义表。[图 10.9](#10_005.html#f10.9) 显示了可用于定义此表的脚本示例。

[![Example Repository-Based Table Definition Script](bilderklein/klein10_009.png)](img-f10.9.html)

**图 10.9** 基于存储库的表定义脚本示例

示例表配置了两列。第一列包含筛选条件；在我们的示例中，使用了 `CUSTOMER_FILTERS` 列，其中包含用于筛选数据中 `CUSTOMER_REGION` 的条件。第二列是 `USER_NAME`，将根据 `SESSION_USER` 变量进行筛选。

创建表后，您现在必须用映射数据填充表。有多种选项可用于填充此表。您可以从文件导入数据，使用 SQL 手动插入记录，或使用受支持的工具从其他来源提取数据并将其加载到安全表中。[图 10.10](#10_005.html#f10.10) 显示了表中的示例数据。

[清单 10.2](#10_005.html#l10.2) 显示了如何使用 SQL 插入语句在示例表中填充数据的示例。请注意，您必须在 `CUSTOMER_REGION` 数据值周围使用两个连续的单引号，而不是双引号。在 SAP HANA 中，单引号是转义字符。当将静态值插入表中时，您必须用另一个单引号“转义”插入的单引号，以便表值仅存储一个单引号，如 [图 10.10](#10_005.html#f10.10) 所示。

```
INSERT INTO "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('JHARRIS01', '("CUSTOMER_REGION" = ''North Central'')');
INSERT INTO "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('TTIM03', '("CUSTOMER_REGION" = ''South West'')');
INSERT INTO "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('WTRAN05', '("CUSTOMER_REGION" in (''South West'',''North Central''))');
INSERT INTO "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('TIMG05', '("CUSTOMER_REGION" in (''South Central'',''North Central''))');
INSERT INTO "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('TIMG05', '("CUSTOMER_REGION" = (''South Central''))');
INSERT INTO  "security_tables"."Security.Tables::RLS_CUSTOMERKEY_ACCESS"
VALUES ('SYSTEM', '_ALL');
```

**清单 10.2** 用于填充示例表的一系列六个 SQL INSERT 语句

[![Example Filter Conditions in Security Table](bilderklein/klein10_010.png)](img-f10.10.html)

**图 10.10** 安全表中的示例筛选条件

#### 创建基于存储库的存储过程

