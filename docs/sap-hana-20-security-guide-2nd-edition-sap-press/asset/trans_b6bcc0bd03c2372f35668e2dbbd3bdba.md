

要保存更改，请按 `(Ctrl)+(S)` 或单击左上角的磁盘图标以保存并激活权限。要撤销或更改对象权限，请在列表中选择该对象。如果要从授予对象中移除该对象并撤销其所有权限，请单击红色 X 并保存。如果要更改当前的权限分配，请选中或取消选中所选对象右侧框中列出的所需权限。再次保存更改，以使其在数据库系统中生效。

如果出现任何激活问题，警告消息将显示在用户管理窗口底部的状态框中。状态框具有深色背景颜色。错误消息将以红色文本显示。错误仅在尝试激活或保存更改时生成。

## 8.5 使用存储库角色授予对象权限

在 [第 6 章](#06_001.html#h6) 中，我们向您介绍了存储库角色，并描述了管理和创建它们的过程。请记住，存储库角色可以使用 `.hdbrole` 开发工件中的角色脚本语言来定义和管理。存储库角色也可以在 SAP HANA Web-Based Development Workbench 编辑器中使用 GUI 或文本编辑器来定义和管理。在本节中，我们将更深入地介绍文本编辑器语法，并展示使用存储库角色针对目录对象权限的特定流程。

### 8.5.1 基于脚本的存储库角色

在 [第 6 章](#06_001.html#h6) 中，我们概述了创建 `.hdbrole` 存储库工件所需的步骤和流程。在该脚本中，您可以为单个目录对象和架构定义目录对象权限。该脚本支持引用运行时和设计时目录对象。运行时对象是仅存在于 SAP HANA 数据库中的对象。设计时对象是在开发存储库中处于活动状态的对象。

针对单个运行时目录对象定义权限的语法如下：

```
catalog sql object <schema>.<object>: <array of privileges> ;
```

该语句以 `catalog sql object` 开头，区分大小写。该术语后跟一个完全限定的目录对象名称，包括架构名称。在目录对象之后，您将包含一个冒号，后跟一个由逗号分隔的按名称标识的权限数组。该语句以分号结束。

例如，要授予角色执行系统存储过程的权限，请使用以下语法：

```
catalog sql object "SYS"."REPOSITORY_REST": EXECUTE;
```

要授予多个单个目录对象的权限，只需为每个目录对象重复语法即可。每行都需要以分号结尾，这告诉系统语句已完成。[清单 8.3](#08_005.html#l8.3) 显示了授予三个不同目录对象权限的语法。

```
catalog sql object "dev_tables"."MyTable": SELECT, DELETE;
catalog sql object "dev_tables"."MyStoredProc": SELECT, EXECUTE, DROP, ALTER;
catalog sql object "dev_tables"."MyUDFunction": SELECT, EXECUTE, DROP, ALTER;
```

**清单 8.3** 向三个不同目录对象授予权限的存储库角色脚本

现在，让我们看看当需要将权限分配给整个运行时架构时使用的语法，如下所示：

```
catalog schema <schema name>: <array of privileges>;
```

此语法与用于授予单个目录对象的语法类似，但您将以 `catalog schema` 开头语句，后跟架构名称。例如，要为名为 `demo_schema` 的架构授予多个权限，请在 `.hdbrole` 开发脚本中使用以下语法：

```
catalog schema "demo_schema": ALTER, SELECT, EXECUTE, INSERT, UPDATE, DELETE, 
CREATE ANY, DROP, DEBUG, TRIGGER, INDEX;
```

要授予多个运行时目录架构的权限，只需为每个架构重复语法即可。请记住以分号结束每行，如 [清单 8.4](#08_005.html#l8.4) 所示。

```
catalog schema "dev_tables": SELECT, EXECUTE;
catalog schema "ECCDATA": SELECT, EXECUTE;
catalog schema "_SYS_BIC": SELECT, EXECUTE;
catalog schema "SLT_ECC_ECP": SELECT, UPDATE, ALTER, DROP;
catalog schema "ECC76DATA": SELECT;
```

**清单 8.4** 向五个不同架构授予权限的存储库角色脚本

对于设计时对象，您将使用略有不同的语法。请注意，对于运行时对象，您将在引用 SAP HANA 目录中的运行时对象之前使用短语 `catalog sql object` 和 `catalog schema`。对于设计时对象，您将简单地以短语 `schema` 或 `sql object` 开头。此外，在引用设计时目录对象时，您需要使用其完全限定的设计时名称。此完全限定的设计时名称是包层次结构、冒号，然后是设计时文件名的组合。例如，要授予存储在 Security.Schemas 包中的设计时架构 SalesMart 的 SELECT 和 EXECUTE 权限，您将使用以下语法：

```
schema Security.Schemas:SalesMart.hdbschema: SELECT, EXECUTE;
```

请注意，该架构存储在包 `Security.Schemas` 中，架构文件的名称是 `SalesMart.hdbscema`。对于架构的完全限定名称，您将使用由冒号 (`:`) 分隔的包名称，最后是设计时对象名称的命名约定。

对于其他目录对象（如表），您将使用类似的语法。例如，要授予存储在包 `Security.Tables` 中的设计时表 `adusers` 的 SELECT 和 DELETE 权限，您将使用以下语法：

```
sql object Security.Tables::adusers: SELECT, DELETE;
```

请注意，对于表对象，您没有引用其设计时脚本文件扩展名 `.hdbtable`。虽然架构对象需要扩展名 `.hdbschema`，但引用设计时目录对象不需要存储库文件扩展名引用。还请注意，在设计时表的完全限定名称中，双冒号 (`::`) 分隔包名称和目录对象名称。您会发现，这是所有设计时目录对象（基于存储库的架构除外）的常规做法。

请注意，当这些权限在 `.hdbrole` 脚本中激活时，授予对象将是系统管理用户 `_SYS_REPO`。但是，在系统允许这些权限被激活之前，目录对象的所有者必须确保 `_SYS_REPO` 帐户对对象具有完全访问权限，包括将权限授予其他用户的能力。此要求仅在对象本身是由标准用户帐户拥有的标准目录对象时才适用。但是，如果目录对象是基于存储库的，则该对象已由 `_SYS_REPO` 帐户拥有，因此您不需要向 `_SYS_REPO` 用户授予任何其他权限。如前所述，这种安排是我们建议开发人员通过基于存储库的开发流程创建目录对象的原因之一。

### 8.5.2 SAP HANA Web-Based Development Workbench GUI

SAP HANA Web-Based Development Workbench 编辑器托管在 XS 引擎中，提供了一个您可以用来构建和测试开发工件的界面。从安全角度来看，您可以使用此界面来创建和管理基于存储库的角色。此界面可帮助您使用 GUI 管理存储库角色，或使用内置文本编辑器查看和编辑其底层脚本语言。这种灵活性使安全管理员能够在单个界面中管理存储库角色。

您可以通过受支持的 Internet 浏览器访问 SAP HANA Web-Based Development Workbench 编辑器。以下 URL 可以自定义以匹配您环境的详细信息：

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/editor`

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/editor`

