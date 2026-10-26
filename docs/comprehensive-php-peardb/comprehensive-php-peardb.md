# PHP 综合指南：PEAR::DB






## 开发者友好请求
如果您以电子形式收到了本文档的副本且未付费，请考虑购买授权副本。本文档的创建耗费了大量时间和精力，如果它为您提供了任何有用的信息，请访问 http://www.intechra.net/ 了解购买本文档的详情。支持此类文档的开发者越多，文档质量就会越好。

## 文档约定
- 在函数或方法描述中，返回值使用与本段关联的箭头表示法标识。
- 左侧带有波浪线的段落通常代表我对某个主题的个人建议或个人想法。

## 关于作者
这是我第三本与 PHP 相关的著作，也是第二本自出版的作品。作为一名开发者，我一直很难找到价格合适的恰当水平的文档。本书和我的另一本著作 *构建自定义 PHP 扩展* 是我很久以来就想撰写的书籍，涵盖有趣的 PHP 主题，并且以实惠的价格呈现。

我一直在考虑各种书名。如果您喜欢这本书（或讨厌它），请给我留言。您可以在 http://www.intechra.net/ 找到我的联系信息。如果您有希望涵盖的特定主题，请告诉我。

## PEAR 与数据库
### *本文档的动机*
PEAR 的核心是代码重用。这就是本文档的主要动机。如果您是一名 PHP 程序员并且开发过任何数据库项目，PEAR::DB 就是为你准备的。在 PHP 的生命周期中，开发出了几种优秀的数据库抽象，有的面向对象，有的不是。PEAR::DB 是标准的面向对象数据库抽象。

随着 PHP 的不断发展和用户群的增长，越来越多的开发者将被聘请来维护和修改现有代码。通过标准化 PEAR，维护和升级将集中在业务特定代码上，而不是诸如数据库访问之类的通用代码。

### *入门*
本书对您作为程序员的能力做了很多假设。首先，您必须在 Web 服务器上安装并运行 PHP。其次，本书假设您对 PHP 有一般的实践知识。如果您需要更多关于安装和使用 PHP 的一般信息，外面有许多很棒的 *入门* 文档。第三，假设您已安装、配置并运行了数据库服务器。

### 本书不是什么
本书不是最佳实践书籍或软件工程入门读物。此处提供的示例在正确的 HTML、错误处理和输出方面大多不完整。示例通常旨在说明用法，因此篇幅较短——侧重于任务，而非完整解决方案。

### 安装 PEAR
根据您的 PHP 版本和计算平台，可能需要一些步骤来安装和配置 PEAR。

如果您运行的是 4.3 版本之前的 PHP，您可能需要手动安装 PEAR 包管理器。更高版本的 PHP（4.3 及以上）自带 PEAR 包管理器或默认构建包管理器。如果您在 PHP 配置中添加了 **--without-pear** 标志，您也需要获取 PEAR 包管理器。

对于 Unix、Linux 和 BSD，您可以使用命令行获取 PEAR 包管理器：

```
lynx -source http://go-pear.org/ | php
```

上述命令行要求您已安装 lynx（在某些 Linux 发行版中它可能称为 links）。同时假设您已构建并安装了 PHP 二进制文件。

对于 Windows 用户，标准源分发中有一个类似的工具，名为 **go-pear.bat**。

运行此批处理文件将引导您完成 PEAR 安装过程。此批处理文件非常完整，将执行更新 Windows 系统以使用 PEAR 所需的几乎所有任务。运行批处理文件后唯一需要执行的操作是向 PATH 环境变量添加条目。

第一步是找到 **pear.bat** 文件。它位于运行 **go-pear.bat** 批处理文件时您指定的目录中。找到 **pear.bat** 文件后，将其目录添加到 Windows 中的 PATH 环境变量中。这可以通过右键单击 *我的电脑* 图标来完成。从上下文菜单中选择 *属性*，然后单击 *高级* 选项卡。下面在图 1 中显示了一张屏幕截图（Windows XP）。

![](img/73cfc83029178a27381cd5f89348f7bf_13_0.png)

图 1：系统属性页

接下来，单击 *环境变量* 按钮以添加新的环境变量。图 2 显示了允许创建和修改系统环境变量的对话框。

在 *系统变量* 中滚动，直到找到 *Path* 变量。然后单击 *编辑* 按钮将新目录添加到末尾。在 Windows 中，路径项由分号分隔。

安装 PEAR 包管理器后，您就可以开始使用它来管理您的 PEAR 包。PEAR 包管理器使用命令 `pear` 调用。假设您已正确安装和配置环境，运行此命令将产生下面输出 1 中所示的输出。

```text
Usage: pearcmd.php [options] command [command-options] <parameters>
Type "pearcmd.php help options" to list all options.
Type "pearcmd.php help <command>" to get the help for the specified command.
Commands:
build                    Build an Extension From C Source
bundle                   Unpacks a Pecl Package
clear-cache              Clear XML-RPC Cache
config-get               Show One Setting
config-help              Show Information About Setting
config-set               Change Setting
config-show              Show All Settings
cvsdiff                  Run a "cvs diff" for all files in a package
cvs-tag                  Set CVS Release Tag
download                 Download Package
download-all             Downloads each available Package from master_server
info                     Display information about a package
install                  Install Package
list                     List Installed Packages
list-all                 List All Packages
list-upgrades            List Available Upgrades
login                    Connects and authenticates to remote server
logout                   Logs out from the remote server
makerpm                  Builds an RPM spec file from a PEAR package
package                  Build Package
package-dependencies     Show package dependencies
package-validate         Validate Package Consistency
remote-info              Information About Remote Packages
remote-list              List Remote Packages
run-tests                Run Regression Tests
search                   Search remote package database
shell-test               Shell Script Test
sign                     Sign a package distribution file
uninstall                Un-install Package
```

| 34 | upgrade | 升级包 |
| 35 | upgrade-all | 升级所有包 |

#### 输出 1：不带命令行参数运行 PEAR 命令

PEAR 包管理器是一个强大的工具，用于安装、移除、更新和测试您的 PEAR 配置。要查看当前已安装的 PEAR 包，请使用以下语法：

```
pear list
```

在 PEAR 的新安装中，输出将类似于下面在输出 2 中所示的内容。

```
INSTALLED PACKAGES:
====================
PACKAGE VERSION STATE
Archive_Tar 1.1 stable
Console_Getopt 1.0 stable
DB 1.5.0RC2 stable
Mail 1.1.2 stable
Net_SMTP 1.2.3 stable
Net_Socket 1.0.1 stable
PEAR 1.3b1 beta
PHPUnit 1.0.0-alpha2 alpha
XML_Parser 1.0.1 stable
XML_RPC 1.0.4 stable
```

#### 输出 2：PEAR LIST 的输出

如可见，Archive_Tar、Console_Getopt、DB、Mail、Net_SMTP、Net_Socket、PEAR、PHPUnit、XML_Parser 和 XML_RPC 类已安装。每个包的版本号和状态也可用。

### 安装 PEAR::DB

如果您尚未安装 DB 包，请使用以下命令安装 DB：

```bash
pear install DB
```

如果您没有 DB 的最新版本或需要检查升级并进行安装，请使用：

```bash
pear upgrade DB
```

请注意，以上操作如果存在升级将会安装升级。如果您只是想检查升级，请使用 **pear list-all** 或 **pear list-upgrades** 命令。

为本文件之目的，将假定 PEAR::DB 的版本为 1.5.0RC2。

### PEAR::DB 概述

首先，本节通过比较 PHP 中的过程式数据库访问和使用 PEAR::DB 的面向对象数据库访问来说明 PEAR::DB 的核心概念。

### 过程式 DB 访问与 PEAR::DB

本节展示了使用过程式数据库访问和 PEAR::DB 之间的相似之处和不同之处。示例故意保持简单，展示如何建立数据库连接、检索少量记录集并关闭连接。

示例使用 MySQL 作为数据库后端，但理论上可以是任何 PHP 支持的数据库。

对于示例，将使用一个简单的四表数据库来说明小型员工和部门数据集。四个表是 *Employees*、*Paychecks*、*EmployeesToDepartments* 和 *Departments*。创建和填充这些表的 MySQL 查询如下所示，见代码清单 1。

```sql
#
# Table structure for table `Departments`
#

CREATE TABLE `Departments` (
  `id` int(11) NOT NULL default '0',
  `name` varchar(50) NOT NULL default '',
  PRIMARY KEY (`id`)
) TYPE=MyISAM;

#
# Dumping data for table `Departments`
#

INSERT INTO `Departments` VALUES (1, 'Web Development');
INSERT INTO `Departments` VALUES (2, 'QA');

# --------------------------------------------------------
#
# Table structure for table `Employees`
#

CREATE TABLE `Employees` (
  `id` int(11) NOT NULL default '0',
  `last_name` varchar(50) NOT NULL default '',
  `first_name` varchar(50) NOT NULL default '',
  `phone_ext` varchar(5) NOT NULL default '',
  `mgr_id` int(11) NOT NULL default '0',
  `dept_id` int(11) NOT NULL default '0',
  PRIMARY KEY (`id`),
  KEY `mgr_id` (`mgr_id`),
  KEY `dept_id` (`dept_id`)
) TYPE=InnoDB;

#
# Dumping data for table `Employees`
#

INSERT INTO `Employees` VALUES (1, 'Schwendiman', 'Blake', '204', 2, 1);
INSERT INTO `Employees` VALUES (2, 'Cox',
'Jeffrey', '225', 0, 1);
INSERT INTO `Employees` VALUES (3, 'McNulty',
'Kate', '214', 2, 2);

#
# Table structure for table `Paychecks`
#

CREATE TABLE `Paychecks` (
  `id` int(11) NOT NULL auto_increment,
  `employee_id` int(11) NOT NULL default '0',
  `check_date` date NOT NULL default '0000-00-00',
  `check_number` int(11) NOT NULL default '0',
  `gross_pay` float NOT NULL default '0',
  `benefits_withheld` float NOT NULL default '0',
  `taxes_withheld` float NOT NULL default '0',
  PRIMARY KEY (`id`)
) TYPE=MyISAM AUTO_INCREMENT=1 ;

CREATE TABLE `EmployeesToDepartments` (
  `emp_id` int(11) NOT NULL default '0',
  `dept_id` int(11) NOT NULL default '0',
  `date_xferred` date NOT NULL default '0000-00-00',
  PRIMARY KEY (`emp_id`, `dept_id`)
) TYPE=MyISAM;
```

#### 代码清单 1：创建示例数据库的 MySQL 语句

*Employees* 表包含一个名为 *dept_id* 的字段，表示员工当前工作的部门。*EmployeesToDepartments* 表是中间表，用于在 *Employees* 和 *Departments* 之间实现多对多关系，表示有关哪些员工曾经在某个部门工作过的历史信息。*EmployeesToDepartments* 表的真正目的，虽然是用于需要多字段键的示例。

示例代码将使用下面代码清单 2 中所示的 SQL 查询来检索有关员工、其部门和其经理的数据。该查询故意比最基本的 SELECT 语句更复杂，以为示例提供更多价值，但本文件中不会涵盖 SQL 语句的细节。

```sql
SELECT Employees.last_name as emp_last_name,
Employees.first_name as emp_first_name,
Employees.phone_ext as emp_phone_ext,
Departments.name as dept_name,
Employees_1.last_name as mgr_last_name,
Employees_1.first_name as mgr_first_name,
Employees_1.phone_ext as mgr_phone_ext FROM
(Departments INNER JOIN Employees ON Departments.id
= Employees.dept_id) LEFT JOIN Employees AS
Employees_1 ON Employees.mgr_id = Employees_1.id
```

#### 代码清单 2：示例员工数据库的 SQL 查询

过程式示例和 PEAR::DB 示例都将检索数据并创建包含结果的 HTML 表格。

### 过程式 DB 访问

下例中的代码（代码清单 3）说明了从 MySQL 数据库检索数据的常见过程式方法。

```php
<?php
// connect to MySQL DB
$link = mysql_pconnect( '207.44.182.3',
'bt_user','bt_pass' );
if ( $link != FALSE )
{
if ( mysql_select_db( 'book_test' ) )
{
/* Performing SQL query */
$query = "SELECT Employees.last_name as
emp_last_name, Employees.first_name as
emp_first_name, Employees.phone_ext as
emp_phone_ext, Departments.name as dept_name,
Employees_1.last_name as mgr_last_name,
Employees_1.first_name as mgr_first_name,
Employees_1.phone_ext as mgr_phone_ext FROM
(Departments INNER JOIN Employees ON Departments.id
= Employees.dept_id) LEFT JOIN Employees AS
Employees_1 ON Employees.mgr_id = Employees_1.id";
$result = mysql_query($query);
if ( $result != FALSE )
{
/* Printing results in HTML */
print '<table>';
while ( $line = mysql_fetch_array( $result,
MYSQL_ASSOC ) )
{
    print '<tr>';
    foreach ( $line as $col_value ) {
        print "<td>$col_value</td>";
    }
    print '</tr>';
}
print '</table>';
}
else
{
    print( 'Query failed: ' );
    print( mysql_error() );
    print( '<br>' );
}

/* Free resultset */
mysql_free_result($result);
}
else
{
    print( 'Unable to select database
<i>book_test</i>: ' );
    print( mysql_error() );
    print( '<br>' );
}

/* Closing connection */
mysql_close($link);
}
else
{
    print( 'Unable to connect to database server: ' );
    print( mysql_error() );
    print( '<br>' );
}
?>
```

#### 代码清单 3：过程式 DB 访问

有经验的 PHP 开发者会在上面的代码中看到常见元素。第 3 行是建立到数据库服务器连接的调用。成功后，第 6 行的代码选择特定数据库。SELECT 查询在第 11 行发送到数据库，如果成功，第 17 行开始循环以检索结果集中的所有数据并处理为 HTML 输出。如果在任何时候发生失败，相关的失败信息将显示给最终用户。

### PEAR::DB

上例重新编码为 PEAR::DB 后显示在代码清单 4 中。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
    if ( !DB::isError( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $query = "SELECT Employees.last_name as
emp_last_name, Employees.first_name as
emp_first_name, Employees.phone_ext as
emp_phone_ext, Departments.name as dept_name,
Employees_1.last_name as mgr_last_name,
Employees_1.first_name as mgr_first_name,
Employees_1.phone_ext as mgr_phone_ext FROM
(Departments INNER JOIN Employees ON Departments.id
= Employees.dept_id) LEFT JOIN Employees AS
Employees_1 ON Employees.mgr_id = Employees_1.id";

        $oRows = $oDB->query( $query );
        if ( !DB::isError( $oRows ) )
        {
            print( '<table>' );
            while ( $oRow = $oRows->fetchRow() )
            {
                print '<tr>';
                foreach ( $oRow as $col_value ) {
                    print "<td>$col_value</td>";
                }
                print '</tr>';
            }
            print( '</table>' );
        }
        else
        {
            print( 'Query failed: ' );
            print( $oDB->getMessage() );
            print( '<br>' );
        }
    }
    else
    {
        print( 'Unable to connect to database server: '
);
        print( $oDB->getMessage() );
        print( '<br>' );
    }
}
?>
```

#### 代码清单 4：PEAR::DB 数据库访问



扩展在未来的 PEAR::DB 版本中可能会得到支持。

- 3. PEAR::DB 通过 DB_Error 类（PEAR_Error 类的子类）为错误处理提供了一致的接口。

作为一名软件开发人员，几乎不可能夸大在多个开发项目中标准化和重用软件组件的好处。如果没有其他使用 PEAR::DB 的理由，仅从重用角度来看，对每个 PHP 开发人员来说仍然是值得的。不过，使用 PEAR::DB 还有更多原因，本文档的其余部分将探讨所有这些原因。

以下示例应该足以让任何 PHP 开发人员对 PEAR::DB 感到兴奋。下面的代码清单 5 中的代码与代码清单 4 完全相同，只是第 4 行的 DSN 发生了更改。代码中的这一简单更改对脚本的运行时行为产生了巨大影响。不是使用 MySQL，此脚本使用 ODBC 连接到 Microsoft Access 数据库以检索必要的数据。

```php
<?php
require_once( 'DB.php' );
$oDB = DB::connect( 'odbc://book_test', true );
if ( !DB::isError( $oDB ) )
{
    $oDB->setFetchMode( DB_FETCHMODE_ASSOC );
    $query = "SELECT Employees.last_name as emp_last_name, Employees.first_name as emp_first_name, Employees.phone_ext as emp_phone_ext, Departments.name as dept_name, Employees_1.last_name as mgr_last_name, Employees_1.first_name as mgr_first_name, Employees_1.phone_ext as mgr_phone_ext FROM (Departments INNER JOIN Employees ON Departments.id = Employees.dept_id) LEFT JOIN Employees AS Employees_1 ON Employees.mgr_id = Employees_1.id";
}
```

```php
$oRows = $oDB->query( $query );
if ( !DB::isError( $oRows ) )
{
    print( '<table>' );
    while ( $oRow = $oRows->fetchRow() )
    {
        print '<tr>';
        foreach ( $oRow as $col_value ) {
            print "<td>$col_value</td>";
        }
        print '</tr>';
    }
    print( '</table>' );
}
else
{
    print( 'Query failed:' );
    print( $oDB->getMessage() );
    print( '<br>' );
}
}
else
{
    print( 'Unable to connect to database server: ' );
    print( $oDB->getMessage() );
    print( '<br>' );
}
?>
```

#### 代码清单 5：PEAR::DB 数据库访问（第二次）

使用代码清单 4 和代码清单 5 中的示例的唯一外部要求是数据库必须存在。Microsoft Access 数据库还必须设置一个 ODBC DSN（具体来说，是一个名为 book_test 的系统 DSN）指向它。

### 摘要

无论您的 PHP 数据库应用程序的规模、范围或要求如何，PEAR::DB 都适用。它为主要数据库后端提供一致、易读的接口。它标准化了错误处理，总体上简化了 PHP 应用程序的维护。

## PEAR::DB 深入解析

本节是详细参考部分，旨在提供对 PEAR::DB 及其类的深入介绍。

### 引言

在详细介绍类本身之前，了解使用 PEAR::DB 的一些概念的高层次视角很重要。这些概念包括数据源名称（DSN）以及通常需要连接到数据库并检索或修改数据的方法。本节涵盖的另一个高层次概念是序列。

### DSN

要使用 PEAR::DB 连接到数据库，您必须首先创建一个有效的数据源名称（DSN）。对于 Windows 用户来说，区分 PEAR::DB DSN 和 ODBC DSN 很重要。ODBC DSN 可以与 PEAR::DB DSN 一起使用，但对于大多数数据库类型，PEAR::DB DSN 与 ODBC DSN 完全无关。有关使用 PEAR::DB 使用 ODBC 数据库的详细信息，请参阅第 134 页开始的详细示例中的 ODBC 部分。

PEAR::DB DSN 的格式类似于通用资源标识符。其完整格式如下所示，见代码清单 6。

```text
phptype(dbsyntax)://username:password@protocol+host
spec/database
```

#### 代码清单 6：完整 DSN 格式

大多数变体都是允许的，例如下面代码清单 7 中所示的变体。

```text
2  phptype://username:password@protocol+hostspec:110//usr/db_file.db
3  phptype://username:password@hostspec/database_name
4  phptype://username:password@hostspec
5  phptype://username@hostspec
6  phptype://hostspec/database
7  phptype://hostspec
8  phptype(dbsyntax)
9  phptype
```

#### 代码清单 7：DSN 格式的变体

目前，下表 1 中所示的以下数据库由 PEAR::DB 支持。

| 数据库 | phptype | 数据库信息网站 |
|---|---|---|
| MySQL | mysql | http://www.mysql.com/ |
| PostgreSQL | pgsql | http://www.postgresql.org/ |
| Borland InterBase | ibase | http://www.borland.com/ |
| Mini SQL | msql | http://www.hughes.com.au/products/msql |
| Microsoft SQL Server | mssql | http://www.microsoft.com/ |
| Oracle 7/8/8i | oci8 | http://www.oracle.com/ |
| ODBC (Open Database Connectivity) | odbc |  |
| SyBase | sybase | http://www.sybase.com/home |
| Informix | ifx | http://www.informix.com/ |
| FrontBase | fbsql | http://www.frontbase.com |

| 数据库 | 驱动程序 | URL |
|---|---|---|
| SQLite | sqlite | http://www.sqlite.org/ |
| dBase | dbase |  |

表 1：PEAR::DB 支持的数据库

一些 DSN 示例已在代码清单 4 和代码清单 5 中显示。由于 DSN 的使用对于使用 PEAR::DB 来说是如此基础，还将提供更多示例。此外，在后面提供的详细的数据库特定示例中，将为每种受支持的数据库类型提供 DSN 的具体示例。

### 连接

建立到任何受支持数据库的连接最简单的方法是使用 **DB::connect()**。有两个参数：连接 DSN 和一个混合值，其中包含布尔值或值数组——这将在本节中进一步讨论。对 **DB::connect()** 的调用的返回值是数据库类的有效实例或错误或警告对象。要检查错误和警告，请使用 **DB::isError()** 和 **DB::isWarning()** 类方法。要断开与数据库的连接，请使用返回的数据库对象的 **disconnect()** 方法。

**DB::connect()** 的第二个参数很重要，因为它控制数据库特定的选项。每个数据库类类型都包含一个 **setOption()** 方法，用于设置各种数据库特定的可选值。所有数据库类的父类 DB_common 默认定义了表 2 中显示的选项。

| 选项名称 | 默认值 | 简要说明 |
|---|---|---|
| persistent | false | 是否建立到数据库的持久连接。 |
| optimize | performance | 目前使用的值是‘performance’和‘portability’。每个数据库以略有不同的方式使用此选项。 |
| debug | 0 | 表示要生成的调试信息级别的数值。 |
| seqname_format | %s_seq | 描述序列名称格式。 |
| autofree | false | 如果设置为 true，此标志会使 PEAR::DB 释放使用 fetchRow() 或 fetchInto() 检索的所有获取的数据。 |

表 2：数据库类的默认选项

对于传递给 **DB::connect()** 的每个指定选项，**setOption()** 方法会被调用一次。如果您未指定任何选项，则使用默认值。有关选项的更多详细信息，请参阅第 134 页开始的每个数据库的详细介绍。*seqname_format* 选项将在序列部分中讨论。

也可以将布尔值而不是值数组作为 **DB::connect()** 的第二个参数传递。当传递布尔值时，它表示 *persistent* 选项的值，该值指示是否应建立到数据库的持久连接。

下面代码清单 8 中显示的示例代码说明了连接到 MySQL 数据库服务器的几个示例。没有生成重要输出；此示例仅用于说明。

```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL
// database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $oDB ) )
{
    print( 'test 1 success<br>' );
    $oDB->disconnect();
}

// make a persistent connection to a MySQL
// database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( !DB::isError( $oDB ) )
{
    print( 'test 2 success<br>' );
    $oDB->disconnect();
}

// make a persistent connection to a MySQL
// database -- alternate method
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'persistent' => true ) );
if ( !DB::isError( $oDB ) )
{
    print( 'test 3 success<br>' );
    $oDB->disconnect();
}
?>
```



```php
<?php
// make a persistent connection to a MySQL
database, set optimize to 'portability', increase
debug level
$db = DB::connect(
    'mysql://db_user:pass@207.44.182.3/book_test',
    array('persistent' => true, 'optimize' =>
    'portability', 'debug' => 5) );
if (!DB::isError($db)) {
    print 'test 4 success<br>';
    $db->disconnect();
}
?>
```

#### 代码清单 8：DB::connect() 示例

### 查询

要对数据库执行查询，请使用 **query()** 方法。**query()** 方法的一个简单示例见代码清单 4。关于该方法的完整详细信息，请参见下文对 **DB_common** 类的讨论。

### 获取数据

执行返回数据集的查询后，有两种基本的数据检索方法：**fetchRow()** 和 **fetchInto()**。这两种方法都在从第 109 页开始的 **DB_result** 类讨论中进行了详细描述。有关使用 **fetchRow()** 的简单示例，请参见代码清单 4。

### 序列

序列是一种为表中的数据行维护唯一数字 ID 的方式。一些数据库服务器提供了自动递增计数器作为表列类型的概念。序列是这一概念的推广。

某些数据库引擎原生支持序列（例如 Oracle）。其他数据库类型则仅仅提供上述自动递增列类型。在某些情况下，使用这种列类型会给数据恢复和导入带来挑战。通过使用 PEAR::DB 序列，代码更具可移植性和可维护性，并且 PEAR::DB 序列可以避免与自动递增字段相关的一些问题。

下面代码清单 9 给出了一个使用序列的简单示例。

```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $oDB ) )
{
$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );

$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );

$idSeq2 = $oDB->nextId( 'sequence_2' );
print( "idSeq2 = $idSeq2<br>" );

$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );
$oDB->disconnect();
}
?>
```

#### 代码清单 9：使用序列

管理。第 5 行的 DB::connect() 调用正是相关的更改。

```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL
database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'seqname_format' => 'seq_%s' ) );
if ( !DB::isError( $oDB ) )
{
$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );

$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );

$idSeq2 = $oDB->nextId( 'sequence_2' );
print( "idSeq2 = $idSeq2<br>" );

$idSeq1 = $oDB->nextId( 'sequence_1' );
print( "idSeq1 = $idSeq1<br>" );

$oDB->disconnect();
}
?>
```

#### 代码清单 10：自定义序列表名称格式

正如预期的那样，运行代码清单 10 中所示的代码会创建两个新表：seq_sequence_1 和 seq_sequence_2。请注意，虽然序列是一种可以让您的应用程序移植到各种数据库的通用机制，但不建议依赖该实现。例如，如果您出于单纯使用序列之外的任何目的，依赖 PEAR::DB 中 MySQL 类所实现的序列的表名信息，那么您的应用程序将不容易移植到 Oracle 后端。这是因为 Oracle 原生支持序列，因此 MySQL 实现所创建的表不会被 Oracle 实现所创建。

作为开发者，我个人建议使用序列，而不是自动递增字段类型。根据底层数据库的不同，自动递增字段可能会引发一些问题。

### 准备和执行

通过使用 PEAR::DB，数据库查询的 prepare 和 execute 方法同样也被推广到所有数据库。借助 prepare()、execute() 和 executeMultiple() 方法，通用查询执行具备了更大的灵活性。这些方法的细节将在下文给出，但作为高层概述，下面代码清单 11 给出了一个简单示例。

```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL
database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'seqname_format' => 'seq_%s' ) );
if ( !DB::isError( $oDB ) )
{
$aInsertSQL = 'INSERT INTO Employees ( id ,
last_name , first_name , phone_ext , mgr_id ,
dept_id ) VALUES ( ?, ?, ?, ?, ?, ? )';
$hQuery = $oDB->prepare( $aInsertSQL );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Ryan', '123', '1', '1' );
$result = $oDB->execute( $hQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Scott', '234', '1', '1' );
$result = $oDB->execute( $hQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Taylor', '323', '1', '1' );
$result = $oDB->execute( $hQuery, $aData );
if ( DB::isError( $result ) )
    print( $result->getMessage() );

$oDB->disconnect();
}
?>
```

#### 代码清单 11：prepare() 和 execute() 使用概览

首先，使用 prepare/execute 模型的查询必须先参数化，例如上面第 8 行所示的查询。所有动态字段都由 '?' 字符替换。接下来，使用 prepare() 方法从数据库对象获取查询句柄，如第 9 行所示。该句柄稍后用于调用 execute() 或 executeMultiple()。替换 '?' 字段的数据由数组参数提供。上面第 11、16 和 21 行展示了如何设置这样的数组。参数的顺序必须与预处理查询中使用的顺序一致。最后，按照第 12、17 和 22 行所示执行查询。

来自其他编程/数据库背景的开发者会立即认出 prepare/execute 方法，并理解其优点。这些概念将在后面 DB_common 类的方法参考中详细讨论。

### autoPrepare 和 autoExecute

autoPrepare 和 autoExecute 是上述 prepare 和 execute 机制的扩展。新增功能是完全消除创建参数化查询的需要。

#### 代码清单 12：使用 autoPrepare

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'seqname_format' => 'seq_%s' ) );
if ( !DB::isError( $oDB ) )
{
$aFields = array( 'id', 'last_name',
'first_name', 'phone_ext', 'mgr_id', 'dept_id' );
$oQuery = $oDB->autoPrepare( 'Employees',
$aFields, DB_AUTOQUERY_INSERT );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Ryan', '123', '1', '1' );
$result = $oDB->execute( $oQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Scott', '234', '1', '1' );
$result = $oDB->execute( $oQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Taylor', '323', '1', '1' );
$result = $oDB->execute( $oQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$oDB->disconnect();
}
?>
```

代码清单 12 中的示例说明了 autoPrepare() 方法的使用。与代码清单 11 中演示的指定参数化 SQL 查询不同，这里只需指定表名和字段名。autoPrepare() 方法使用表名、字段名和一个模式参数，在内部创建并准备适用于 INSERT 或 UPDATE 的 SQL 查询。

此处的示例仅简要概述 autoPrepare() 方法。autoExecute() 方法与此类似，这两种方法将在后面的章节中详细讨论。




关于 **DB_common** 类的内容如下。此外，第 66 页中关于 **autoExecute()** 方法的讨论也提供了一些限制和使用信息。

### 引言摘要

至此，PEAR::DB 的引言部分结束。上述高层概述概括了 PEAR::DB 的主要概念。以下各节将详细介绍 PEAR::DB 的类及其方法和属性。

## DB 类

**DB** 主类实际上只是一个容器类，包含一些通用的静态方法和工具函数，适用于 PEAR::DB。表 3 中列出的静态方法定义在 **DB** 类中。

| 方法 | 描述 |
|---|---|
| `factory()` | 创建一个特定类型的新数据库连接对象。实际上并不建立连接。 |
| `connect()` | 创建一个新的数据库连接对象，并建立与数据库服务器的连接。 |
| `apiVersion()` | 返回 DB API 版本。 |
| `isError()` | 检查传入的参数是否为错误对象。 |
| `isConnection()` | 检查传入的参数是否为数据库连接类型。 |
| `isWarning()` | 检查传入的参数是否为警告对象。 |
| `isManip()` | 检查传入的 SQL 语句是数据操作查询还是数据定义查询。 |
| `errorMessage()` | 根据数字数据库错误代码或 DB_Error 对象返回文本错误消息。 |
| `parseDSN()` | 从 DSN 字符串返回完全解析后的 DSN。此方法不太可能被直接使用，通常可视为私有方法。 |
| `assertExtension()` | 根据需要动态加载特定的 PHP 扩展。此方法不太可能被直接使用，通常可视为私有方法。 |

表 3：DB 类方法

### DB::factory

`mixed factory( string $type )`

创建一个新的数据库连接对象，但不连接数据库服务器。*type* 参数是一个字符串值，仅包含要创建的数据库对象的类型。有效值显示在第 19 页表 1 的 *phptype* 列中。

返回新创建的 DB 对象或 **DB_Error** 对象。

通常不使用此方法，因为 **connect()** 方法同时执行数据库对象创建和连接。但是，在某些情况下，创建一个不连接的数据库对象可能更可取。

请注意，如果您选择使用 **factory()** 方法获取数据库对象，然后使用该对象的 **connect()** 方法，则需要手动设置数据库对象的选项。此外，您还需要直接调用 **parseDSN()**，因为实例化的数据库对象期望的是已解析的 DSN，而不是 DSN 字符串。代码清单 13 中显示了一个示例。

```php
<?php
require_once( 'DB.php' );

// create an unconnected MySQL DB object
$oDB = DB::factory( 'mysql' );
if ( DB::isError( $oDB ) )
{
    print( 'Unable to create MySQL DB object<br>' );
    exit;
}

$oDB->setOption( 'optimize', 'portability' );

$result = $oDB->connect( DB::parseDSN(
'mysql://bt_user:bt_user:bt_password@207.44.182.3/book_test'
) );
if ( DB_OK == $result )
{
    // do DB work, then disconnect
    //$oDB->disconnect();
}
else
{
    // $result is a DB_Error object
    print( 'Unable to connect to MySQL' . $result->getMessage() . '<br>' );
    exit;
}
?>
```

#### 代码清单 13：DB::factory

在代码清单 13 中，对象在第 5 行创建。通过调用 **factory()** 仅指定了数据库类型。检查结果的有效性，然后在第 12 行设置选项。在第 14 行，实际连接到数据库服务器。注意，传递给 **parseDSN()** 方法的 DSN 字符串包含数据库类型。这是解析成功所必需的（有关有效 DSN 字符串格式的列表，请参阅第 18 页的代码清单 7）。确保 **factory()** 方法中使用的数据库类型与用于建立实际连接的 DSN 中指定的数据库类型一致。

再次强调，在几乎所有情况下都建议使用 **connect()** 方法。

### DB::connect

`mixed connect( mixed $dsn, mixed $options = false )`

这是创建新数据库对象并同时连接数据库服务器的首选方法。

*dsn* 参数可以是 DSN 字符串，也可以是已解析的 DSN（从 **DB::parseDSN** 返回）。*options* 参数可以是布尔值或数组。当 *options* 是数组时，它必须是关联数组，其名称/值对可以传递给数据库对象的 **setOption()** 方法。当前使用的默认选项显示在第 20 页的表 2 中。当 *options* 是布尔值时，它被解释为

| 元素 | 默认值 | 描述 |
|---|---|---|
| dbsyntax | false | 关于 SQL 语法等所使用的数据库 |
| username | false | 登录用户名 |
| password | false | 登录密码 |
| protocol | false | 要使用的通信协议（tcp、unix 等） |
| hostspec | false | 主机规范（主机名[:端口]） |
| port | false | 要连接的端口 |
| socket | false | 要连接的套接字 |
| database | false | 在 DBMS 服务器上使用的数据库 |

表 4：DSN 数组元素

每个后端数据库服务器可能以不同方式使用 DSN 元素。有关每个数据库服务器的有效 DSN 示例，请参阅下面专门介绍这些数据库服务器的章节。

### DB::assertExtension

`boolean assertExtension( string $name )`

根据传入的 name 参数加载 PHP 扩展。在 PEAR::DB 中，这些扩展是数据库扩展（例如 mysql、oci8 等）。

如果扩展已加载，则返回 true。

```php
<?php
require_once( 'DB.php' );
$aExtensions = array( 'mysql', 'pgsql', 'ibase',
'msql', 'mssql', 'oci8', 'odbc', 'sybase', 'ifx',
'fbsql', 'sqlite', 'dbase' );
foreach( $aExtensions as $aExt )
{
    if ( DB::assertExtension( $aExt ) )
        print( $aExt . ' extension loaded<br>' );
    else
        print( $aExt . ' extension not loaded<br>' );
}
?>
```

#### 代码清单 15：DB::assertExtension 示例

代码清单 15 中显示的示例代码演示了如何检查所有受支持的 PEAR::DB 数据库服务器。我的基于 Windows 的安装的输出如输出 5 所示。

```
1 mysql extension loaded
2 pgsql extension not loaded
3 ibase extension not loaded
4 msql extension not loaded
5 mssql extension not loaded
6 oci8 extension not loaded
7 odbc extension loaded
8 sybase extension not loaded
9 ifx extension not loaded
10 fbsql extension not loaded
11 sqlite extension not loaded
12 dbase extension not loaded
```

输出 5：DB::assertExtension 示例输出

### DB 类总结

在一般的开发项目中，DB 类通常只使用两个成员：**connect** 和 **isError**。其他方法在某些情况下有帮助，但很少使用。通常，DB 类方法将以静态方式使用；无需创建 **DB** 类型的对象。

## DB_common 类

**DB_common** 类是所有数据库服务器特定类的父类。**DB_common** 的目的是为所有具体实现类提供公共接口定义。在某种程度上，**DB_common** 可以看作抽象基类，因为 **DB_common** 中定义的许多方法除了返回错误之外什么都不做。

本节描述的方法是对所有数据库服务器类都可用的通用方法。

| 方法 | 描述 |
|---|---|
| `toString()` | 字符串转换。此方法提供 DB_common 对象的字符串表示形式。 |
| `quoteString()` | 对字符串进行引号处理，以便可以在查询的字符串分隔符内安全使用（为兼容性而保留，首选 `quote()`）。 |
| `quote()` | 对字符串进行引号处理以在查询中安全使用的首选方法。 |
| `provides()` | 告知某个 DB 实现或其后端扩展是否支持给定功能。 |
| `errorCode()` | 将原生错误代码映射为可移植的 PEAR::DB 代码。 |
| `errorMessage()` | 将 DB 错误代码映射为文本消息。这实际上只是一个包装器 |


### DB_common::toString

- string toString( void )

toString() 方法是内部方法，不期望被外部使用。其文档将访问权限列为 private。出于好奇，示例及其输出分别显示在代码清单 16 和输出 6 中。

```php
<?php
require_once( 'DB.php' );

$DB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $DB ) )
{
    print( $DB->toString() . '<br>' );
    $DB->disconnect();
}
?>
```

**代码清单 16：DB_common::toString 示例**

```
db_mysql: (phptype=mysql, dbsyntax=mysql)
[connected]
```

**输出 6：DB_common::toString 输出**

### DB_common::quoteString

- string quoteString( string $string )

quoteString() 方法出于兼容性原因而提供，但建议程序员使用 quote() 方法。

### DB_common::quote

- string quote ( string $string )

返回一个引用的字符串，以便可以安全地在查询中使用。

quote() 方法根据特定后端数据库的要求安全地引用并转义值。代码清单 17 中的示例代码说明了 quote() 方法，而输出 7 中的输出显示了各种 DB 对象可能提供不同的结果。

```php
<?php
require_once( 'DB.php' );

print( 'Quoting with mysql object<br>' );
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $oDB ) )
{
print( $oDB->quote( ) . '<br>' );
print( $oDB->quote( 500 ) . '<br>' );
print( $oDB->quote( 'some text' ) . '<br>' );
print( $oDB->quote( "it's not on drive c:\
anywhere" ) . '<br>' );
$oDB->disconnect();
}
print( '<br><br>Quoting with ODBC object<br>' );
$oDB = DB::connect( 'odbc://book_test', true );
if ( !DB::isError( $oDB ) )
{
print( $oDB->quote( ) . '<br>' );
print( $oDB->quote( 500 ) . '<br>' );
print( $oDB->quote( 'some text' ) . '<br>' );
print( $oDB->quote( "it's not on drive c:\
anywhere" ) . '<br>' );
$oDB->disconnect();
}
?>
```

**代码清单 17：DB_common::quote 示例**

```
1  Quoting with mysql object
2  NULL
3  500
4  'some text'
5  'it\'s not on drive c:\\ anywhere'
6  
7  
8  Quoting with ODBC object
9  NULL
10 500
11 'some text'
12 'it\'s not on drive c:\\ anywhere'
```

**输出 7：DB_common::quote 示例输出**

### DB_common::provides

- mixed provides( string $feature )

返回此 DB 实现是否支持该功能。

目前定义了四个功能：prepare、pconnect、transactions 和 limit。此方法主要用于内部确定给定特定数据库对象时可能请求的类型。

代码清单 18 中显示的示例展示了一个包含所有数据库类型的所有功能及其值的表格。输出已为本书重新格式化，并在表 5 中显示。

```php
<?php
require_once( 'DB.php' );

$aPHPTypes = array( 'mysql', 'pgsql', 'ibase',
'msql', 'mssql', 'oci8', 'odbc', 'sybase', 'ifx',
'fbsql', 'sqlite', 'dbase' );
$aFeatures = array( 'prepare', 'pconnect',
'transactions', 'limit' );

print( '<table><tr>' );
print( '<td>&nbsp;</td>' );

foreach( $aFeatures as $aFeature )
    print( '<td>' . $aFeature . '</td>' );

print( '</tr>' );
foreach ( $aPHPTypes as $aType )
{
    $oDB = DB::factory( $aType );
    if ( ! DB::isError( $oDB ) )
    {
        print( '<tr><td>', $aType . '</td>' );
        foreach ( $aFeatures as $aFeature )
        {
            $result = $oDB->provides( $aFeature );
            if ( gettype( $result ) == 'boolean' )
                print( '<td>', ( $oDB->provides( $aFeature ) ? 'true' : 'false' ) . '</td>' );
            else
                print( '<td>', $oDB->provides( $aFeature ) . '</td>' );
        }
        print( '</tr>' );
    }
}
?>
```

**代码清单 18：DB_common::provides 示例**

|  | prepare | pconnect | transactions | limit |
|---|---|---|---|---|
| mysql | false | true | true | alter |
| pgsql | false | true | true | alter |
| ibase | true | true | true | false |
| msql | false | true | false | emulate |
| mssql | false | true | true | emulate |
| oci8 | false | true | true | alter |
| odbc | true | true | false | emulate |
| sybase | false | true | false | emulate |
| ifx | false | true | true | emulate |
| fbsql | false | true | true | emulate |
| sqlite | false | true | true | alter |
| dbase | false | false | false | false |

**表 5：代码清单 18 的结果（为本书重新格式化）**

### DB_common::errorCode

- int errorCode( mixed $nativecode )

errorCode() 方法将原生 DB 错误代码转换为 PEAR::DB 可移植错误代码。这可以与本节中描述的 errorNative() 方法结合使用。nativecode 参数可以是字符串或整数。

返回可移植的 DB 错误代码。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $oDB ) )
{
$sSQL = 'select * from bogus_table'; // table,
bogus_table, does not exist
$oRows = $oDB->query( $sSQL );

// you can use error codes
$aErrCode = $oDB->errorNative();
$aPEARCode = $oDB->errorCode( $aErrCode );
print( "Native Error Code = $aErrCode<br>" );
print( "PEAR Error Code = $aPEARCode<br>" );
print( '<br>' );
print( 'Native Error Message: ' . mysql_error()
.'<br>' );
print( 'PEAR Error Message: ' . $oDB->errorMessage( $aErrCode ) . '<br>' );

print( '<br>' );
// but if there's an error, a DB_Error object
provides great information
if ( DB::isError( $oRows ) )
{
print( 'Error Message: ' . $oRows->message .
'<br>' );
print( 'User Info: ' . $oRows->userinfo .
'<br>' );
}

$oDB->disconnect();
}
…
?>
```

**代码清单 19：DB_common::errorCode、DB_common::errorMessage、DB_common::errorNative() 示例**

代码清单 19 中的示例说明了 **errorCode()** 方法的使用。对于某些类型的错误处理，PEAR::DB 错误代码或原生数据库错误代码可能提供有价值的信息。例如，您可能想要测试当前用户是否具有某种类型的权限。通过检查实际错误代码，程序可以继续提供正确的用户体验。

然而，对于许多错误情况，大多数 PEAR::DB 方法返回的 DB_Error 对象提供了合适的详细程度，使得错误代码只是冗余信息。

### DB_common::errorMessage

- string errorMessage( integer $dbcode )

根据 *dbcode* 参数返回文本错误消息，该参数必须是原生数据库引擎错误代码。

用法示例显示在第 47 页的代码清单 19 中。

### DB_common::raiseError

- object raiseError( mixed $code = DB_ERROR, int $mode = null, mixed $options = null, string $userinfo = null, mixed $native = null )


该方法用于传递错误并调用错误回调等。它本质上是对 `PEAR::raiseError` 的封装，只是不包含消息字符串。

**raiseError()** 方法主要供内部使用，但你可能会在程序中使用它。有关此方法的更多信息，请查阅 PEAR::raiseError 方法。

*code* 参数是一个整数错误码或一个 PEAR 错误对象。如果传入的是对象，则所有其他参数都会被忽略。*mode* 和 *options* 参数是 PEAR::raiseError 实现所特有的，这里不再讨论。*userinfo* 和 *native* 参数分别用于表示数据库特有的错误信息和原生错误码。

- 返回一个 PEAR 错误对象。

本书中的大部分示例一般都会展示如何使用返回的 **DB_Error** 对象。在大多数生产环境中，可能只会显示关于失败的非常基本的信息。但在开发时，如果发生错误时能显示详细信息，则会很方便。

事实上，**DB_Error** 对象包含的信息非常丰富，以至于你在任何情况下都很难不使用它。代码清单 20 中的示例演示了如何使用 **DB_Error** 对象来提供详细的错误信息。这个脚本可能有点难读，因为它是一个 PHP 脚本，会动态生成一个 JavaScript 脚本，但它的效果非常棒。每当调用 **errorPopup** 函数时，都会显示一个包含详细错误信息的新弹出窗口。这很好，因为它不会用错误信息污染主显示窗口。图 4（第 52 页）显示了一个弹出窗口的示例。

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
    <title>Untitled</title>
</head>
<body>
<?php
    require_once( 'DB.php' );

    function formatArg( $aArgument )
    {
        switch ( gettype( $aArgument ) )
        {
            case 'boolean' : return ( $aArgument ? 'true' : 'false' );
            case 'integer' :
            case 'double' : return $aArgument;
            case 'string' : return "'" . $aArgument . "'";
            case 'array' : return '[array]';
            case 'object' : return '[object]';
            case 'resource' : return '[resource]';
            case 'NULL' : return 'null';
        }
    }

    function formatArgs( $aArguments )
    {
        if ( count( $aArguments ) == 0 )
            return '';

        $nCount = 0;
        $result = '';
        foreach ( $aArguments as $aArgument )
        {
            if ( $nCount != 0 )
                $result .= ', ';

            $result .= formatArg( $aArgument );

            $nCount++;
        }

        return $result;
    }

    function formatBacktraceElem( $aElement )
    {
        $result = '';

        $result .= '&middot; Line ' . $aElement['line']
        . ' of ';
$result .= str_replace( '\\', '\\\\',
$aElement['file'] ) . '<ul>';

$result .= $aElement['class'] .
$aElement['type'] . ' ' . $aElement['function'];
$result .= '{ ' . formatArgs( $aElement['args']
) . ' }</ul>';

return $result;
}

function errorPopup( $dbError )
{
// just to be safe, make sure the parameter is
a DB Error
if ( DB::isError( $dbError ) )
{
$output = '<table>';
$output .= ' <tr>';
$output .= ' <td>';
$output .= ' Error Message: ';
$output .= ' </td>';
$output .= ' <td>';
$output .= ' ' . $dbError->message;
$output .= ' </td>';
$output .= ' </tr>';
$output .= ' <tr>';
$output .= ' <td>';
$output .= ' User Information: ';
$output .= ' </td>';
$output .= ' <td>';
$output .= ' ' . $dbError->userinfo;
$output .= ' </td>';
$output .= ' </tr>';
$output .= '</table>';
$output .= '<br><br>';
$output .= '<p>Stack Trace</p>';
$output .= '<table>';

if ( count( $dbError->backtrace ) > 0 )
{
foreach ( $dbError->backtrace as $aElement
)
{
$output .= ' <tr>';
$output .= ' <td>';
$output .= formatBacktraceElem( $aElement
);
$output .= ' </td>';
$output .= ' </tr>';
}
}

$output .= '</table>';

print( ' <script>' ); print( "\n" );
print( ' <!--' ); print( "\n" );
print( ' debugWin = window.open(
"about:blank", "", "width=600, height=300,
status=no, location=no, resizable=yes,
scrollbars=yes" );' ); print( "\n" );
105 print( '      debugWin.document.write( '\n<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">' );  print( "\n" );
106 print( '      debugWin.document.write( '\n<html>' );  print( "\n" );
107 print( '      debugWin.document.write( '\n<head>' );  print( "\n" );
108 print( '      debugWin.document.write( '\n<title>Debug Output</title>' );  print( "\n" );
109 print( '      debugWin.document.write( '\n<style type="text/css"><!-- ' );  print( "\n" );
110     print( '      debugWin.document.write( 'TD {' );  print( "\n" );
111     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
112     print( '      debugWin.document.write( '\nvertical-align : top;' );  print( "\n" );
113     print( '      debugWin.document.write( '}' );  print( "\n" );
114     print( '      debugWin.document.write( 'P {' );  print( "\n" );
115     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
116     print( '      debugWin.document.write( '}' );  print( "\n" );
117     print( '      debugWin.document.write( 'UL {' );  print( "\n" );
118     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
119     print( '      debugWin.document.write( '}' );  print( "\n" );
120     print( '      debugWin.document.write( '-->' );  print( "\n" );
121     print( '      debugWin.document.write( '\n</style>' );  print( "\n" );
122     print( '      debugWin.document.write( '\n</head>' );  print( "\n" );
123     print( '      debugWin.document.write( '\n<body>' );  print( "\n" );
124     print( '      debugWin.document.write( ' <p>' );  print( "\n" );
125     print( '      debugWin.document.write( ' </p>' );  print( "\n" );
126     print( '      debugWin.document.write( ' <p>' . str_replace( "\"", "\"", $output ) . ' </p>' );  print( "\n" );
127     print( '      debugWin.document.write( '\n</body>' );  print( "\n" );
128     print( '      debugWin.document.write( '\n</html>' );  print( "\n" );
129     print( '      //-->' ); print( "\n" );
130     print( ' </script> ' ); print( "\n" );
131 }
133 $oDB = DB::connect(
'mysql://bt_user:wrongpass@207.44.182.3/book_test',
false );
135 if ( DB::isError( $oDB ) )
136 {
137     errorPopup( $oDB );
138 }
139
140 ?>
141
142 </body>
143 </html>
```

#### 代码清单 20：使用 DB_Error

![](img/73cfc83029178a27381cd5f89348f7bf_61_0.png)

图 4：由 errorPopup 函数创建的弹出窗口

### DB_common::setFetchMode

```
void setFetchMode( integer $fetchmode, string $object_class = null )
```

设置在此连接上执行查询时默认使用的获取模式。fetchmode 参数的有效值为 DB_FETCHMODE_ORDERED、DB_FETCHMODE_ASSOC（可能与 DB_FETCHMODE_FLIPPED 进行按位或）以及 DB_FETCHMODE_OBJECT。如果 fetchmode 为 DB_FETCHMODE_OBJECT，则 object_class 指定 fetch 方法要返回的对象类。如果使用 DB_FETCHMODE_OBJECT 且 object_class 为 null，则会将关联数组默认强制转换为对象。

默认的获取模式为 DB_FETCHMODE_ORDERED。代码清单 21 中的示例对此进行了说明。

```php
<?php
require_once( 'DB.php' );
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( DB::isConnection( $oDB ) )
{
  $sSQL = 'select id, first_name, last_name from Employees limit 3';
  $oRows = $oDB->query( $sSQL );
  if ( !DB::isError( $oRows ) )
  {
    while ( $aData = $oRows->fetchRow() )
    {
      print( '<pre>' );
      print_r( $aData );
      print( '</pre><br><br>' );
    }
  }
  $oDB->disconnect();
}
?>
```

#### 代码清单 21：DB_common::setFetchMode -- DB_FETCHMODE_ORDERED（默认）

代码清单 21 的输出显示在输出 8 中。

```
Array
(
    [0] => 1
    [1] => Blake
)
```



```text
[2] => Schwendiman

Array
(
    [0] => 2
    [1] => Jeffrey
    [2] => Cox
)

Array
(
    [0] => 3
    [1] => Kate
    [2] => McNulty
)
```

#### 输出 8：当 setFetchMode 为 DB_FETCHMODE_ORDERED 时的输出

从输出 8 中打印的信息可以看出，当 fetchmode 设置为 DB_FETCHMODE_ORDERED 时，每次调用 DB_result::fetchRow() 都会返回一个索引数组，其中索引表示结果数据集中的列号。列的顺序与原始 SELECT 查询的顺序相同。

代码清单 22 中的代码和输出 9 中的输出说明了使用 DB_FETCHMODE_ASSOC 获取模式的效果。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        false );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $sSQL = 'select id, first_name, last_name from
        Employees limit 3';
        $oRows = $oDB->query( $sSQL );

        if ( !DB::isError( $oRows ) )
        {
            while ( $aData = $oRows->fetchRow() )
            {
                print( '<pre>' );
                print_r( $aData );
                print('</pre>');
            }
        }
        $oDB->disconnect();
    }
?>
```

#### 代码清单 22：DB_common::setFetchMode – DB_FETCHMODE_ASSOC

```text
Array
(
    [id] => 1
    [first_name] => Blake
    [last_name] => Schwendiman
)
Array
(
    [id] => 2
    [first_name] => Jeffrey
    [last_name] => Cox
)
Array
(
    [id] => 3
    [first_name] => Kate
    [last_name] => McNulty
)
```

#### 输出 9：当 setFetchMode 为 DB_FETCHMODE_ASSOC 时的输出

DB_FETCHMODE_ASSOC *获取模式* 会使结果数组成为关联数组，其中键为列名。通常这是首选的开发方式，因为代码本身变得更易阅读，因此也更易维护。

DB_FETCHMODE_OBJECT *获取模式* 与 DB_FETCHMODE_ASSOC *获取模式* 非常相似。不过，每个结果不是关联数组，而是一个对象，其属性为列名。当使用 DB_FETCHMODE_OBJECT 时，setFetchMode() 函数的第二个参数是可用的。

从代码清单 23 及其输出 10 可以看出，使用 DB_FETCHMODE_OBJECT 的结果是，每次调用 fetchRow() 都会返回一个对象。当未指定 object_class 时（如上所示），结果对象仅仅是 PHP 从数组到对象的默认转换。

如果你计划使用 DB_FETCHMODE_OBJECT 获取模式，那么你很可能正在开发一个面向对象的应用程序，并且可能打算通常使用 OO 对象来表示数据库数据。如果是这样，你的数据对象可能需要比简单的 stdClass 对象更复杂。

如果你想实现这样的场景，可以在 setFetchMode() 方法中指定 object_class，如代码清单 24 和输出 11 所示。

```php
<?php
require_once( 'DB.php' );

class Employee
{
    var $first_name;
    var $last_name;
    var $id;
    var $full_name;

    // constructor is called by DB class with a
    data row array
    function Employee( &$arr )
    {
        $this->first_name = $arr['first_name'];
        $this->last_name  = $arr['last_name'];
        $this->id         = $arr['id'];

        $this->full_name  = $this->first_name . ' ' .
        $this->last_name;
    }

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_OBJECT );
$sSQL = 'select id, first_name, last_name from Employees limit 3';
$oRows = $oDB->query( $sSQL, 'Employee' );
if ( !DB::isError( $oRows ) )
{
    while ( $aData = $oRows->fetchRow() )
    {
        print( '<pre>' );
        print_r( $aData );
        print( '</pre>' );
    }
    $oDB->disconnect();
}
?>
```

#### 代码清单 24：DB_common::setFetchMode – DB_FETCHMODE_OBJECT 使用 object_class 参数

```text
employee Object
(
    [first_name] => Blake
    [last_name] => Schwendiman
    [id] => 1
    [full_name] => Blake Schwendiman
)
employee Object
(
    [first_name] => Jeffrey
    [last_name] => Cox
    [id] => 2
    [full_name] => Jeffrey Cox
)
employee Object
(
    [first_name] => Kate
    [last_name] => McNulty
    [id] => 3
    [full_name] => Kate McNulty
)
```

#### 输出 11：当 setFetchMode 为 DB_FETCHMODE_OBJECT 且设置了 object_class 时的输出

虽然代码清单 24 中显示的示例显然是一个简单的人为示例，但它说明了使用 DB_FETCHMODE_OBJECT 的基本威力。object_class 的构造函数可以执行任何额外的必要工作，以实例化一个表示底层数据的对象。根据你的需求，这种机制可能为强大的面向对象解决方案提供骨架。如果你对面向对象数据对象感兴趣，还应该考虑描述 **Class DB_storage**（第 122 页）一节中的信息。

关于 setFetchMode() 的最后一个选项是 DB_FETCHMODE_FLIPPED。虽然内部代码文档声称 setFetchMode() 会全局影响数据检索的方式，但在实践中，这并不完全准确。DB_FETCHMODE_FLIPPED 选项仅由 DB_common::getAll() 方法使用，如果要使用它，必须在调用时将其传递给该方法。因此，DB_FETCHMODE_FLIPPED 选项将在第 90 页的 DB_common::getAll 一节中讨论。

### DB_common::setOption

```text
◆ mixed setOption( string $option, mixed $value )
```

为对象设置一个选项。可用选项在第 20 页的表 2 中显示。只有该表中列出的选项才能被设置或获取。

- 如果 *option* 参数不是有效选项之一，则返回 DB_OK 或 DB_Error。

有关用法示例，请参阅第 32 页的代码清单 13。

### DB_common::getOption

```text
◆ mixed getOption( string $option )
```

返回对象中选项的值。可用选项在第 20 页的表 2 中显示。只有该表中列出的选项才能被设置或获取。

- 返回 *option* 的值，如果 *option* 参数不是有效选项之一，则返回 DB_Error。
- 有关用法示例，请参阅第 32 页的代码清单 13。

### DB_common::prepare

```text
resource prepare( string $query )
```

**prepare()** 方法用于准备一条经过特殊格式化的查询字符串，以便在 prepare/execute 查询方法中使用。通常用于同时运行多个相似查询时。

*query* 参数经过特殊格式化，包含占位符字符，这些占位符将在调用 execute() 方法时代表真实数据。占位符字符及其含义如表 6 所示。

| 占位符字符 | 定义 |
|---|---|
| ? | 带引号的标量值，例如字符串或整数。 |
| & | 替换的数据必须是文件名。文件的内容将成为实际数据。 |
| ! | 标量值按原样插入。 |

**表 6：** 在 query() 方法中使用的占位符字符

代码清单 25 中显示的示例说明了如何使用 **prepare()** 语句来简化将几行相似数据插入到前面示例中描述的 *Paychecks* 表中的操作（参见第 10 页的代码清单 1）。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
$sSQL = 'insert into Paychecks ( employee_id,
check_date, check_number,

gross_pay, benefits_withheld, taxes_withheld )
values ( ?, !, ?, ?, ?, ? )';

$hQuery = $oDB->prepare( $sSQL );

$oDB->execute( $hQuery, array( 1, 'NOW()', 123,
1098.65, 124.55, 98.98 ) );
$oDB->execute( $hQuery, array( 2, 'NOW()', 123,
1198.65, 124.55, 99.98 ) );
$oDB->execute( $hQuery, array( 3, 'NOW()', 123,
1298.65, 124.55, 95.98 ) );

$oDB->freePrepared( $hQuery );
$oDB->disconnect();
}
?>
```

#### 代码清单 25：使用 prepare() -- 简单示例

代码清单 25 中显示的示例说明了两个占位符字符“?”和“!”的使用。这个示例中的重要区别在于，第二个占位符（“!”）之所以被使用，是因为数据是一个 MySQL 函数 NOW()，它指定了查询在服务器上运行的日期。如果使用“?”占位符，查询将被解释为尝试将字面字符串“NOW()”插入数据库。在大多数情况下，“?”占位符是最合适的，但有时“!”占位符是唯一能达到预期结果的选择。

为了说明“&”占位符的用法，需要一个更复杂的示例。SQL


Statements in Code Listing 26 show the definition of the table that will be used in this example.

```sql
CREATE TABLE `UploadedFiles` (
    `id` INT NOT NULL AUTO_INCREMENT,
    `filename` VARCHAR(250) NOT NULL,
    `filesize` INT NOT NULL,
    `enctype` VARCHAR(50) NOT NULL,
    `filedata` BLOB NOT NULL,
    PRIMARY KEY (`id`)
);
```

#### 代码清单 26：创建 UploadedFiles 表的 SQL 语句

The example in Code Listing 27 shows how to create a very simple form for uploading a file and storing its contents in a MySQL database.

```php
<?php
    if ( $_SERVER['REQUEST_METHOD'] == 'POST' )
    {
        if ( is_uploaded_file(
            $_FILES['upload_file']['tmp_name'] ) )
        {
            require_once ( 'DB.php' );

            $oDB = DB::connect(
                'mysql://bt_user:bt_pass@207.44.182.3/book_test',
                true );
            if ( DB::isConnection( $oDB ) )
            {
                $SQL = 'insert into UploadedFiles (
                    filename, filesize, filedata, enctype ) values ( ?,
                    ?, ?, ? )';

                $qQuery = $oDB->prepare( $SQL );

                $oDB->execute( $qQuery, array(
                    $_FILES['upload_file']['name'],
                    $_FILES['upload_file']['size'],
                    $_FILES['upload_file']['tmp_name'],
                    $_FILES['upload_file']['type'] ) );

                $oDB->freePrepared( $qQuery );
                $oDB->disconnect();
            }
        }
    }
?>
<html>
<body>
<form action="<?php print ( $_SERVER['SCRIPT_NAME'] )
?>" method="POST" enctype="multipart/form-data">
File to upload: <input type="File"
     name="upload_file"><br>
     <input type="Submit" value="Submit">
</form>
</body>
</html>
```

#### 代码清单 27：使用 '?' 占位符的 prepare() 方法

The example shown in Code Listing 27 requires a basic understanding of the process of file uploading in PHP which can be found at http://www.php.net/manual/en/features.file-upload.php. The basic concept is that when a file is uploaded, the superglobal $_FILES contains information about the uploaded files that can be used. In this case, the uploaded file is checked for validity on line 4. If this passes, a simple database query is prepared using the '?' placeholder. Then the query is executed such that the value for the '?' placeholder is the full path to the temporary file containing the uploaded file contents. By doing so, the entire contents of the uploaded file are stored into the database.

- 返回一个已准备查询的句柄，可供 execute() 及类似方法使用。

### DB_common::autoPrepare

```text
resource autoPrepare( string $table, array $table_fields, int $mode = DB_AUTOQUERY_INSERT, mixed $where = false)
```

The autoPrepare() method is similar to the prepare() method in that it returns a handle that can be used by execute(), but differs in that it takes arguments that first build the parameterized query. The arguments are assumed to be the '?' type and therefore the values passed to execute() must be literal values to be stored in the database.

The example in Code Listing 28 shows how to automatically prepare an INSERT query. Code Listing 29 shows how to use **autoPrepare()** to effect an UPDATE.

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $hQuery = $oDB->autoPrepare( 'Paychecks',
            array( 'employee_id', 'check_date', 'check_number',
                   'gross_pay', 'benefits_withheld', 'taxes_withheld'
            ),
            DB_AUTOQUERY_UPDATE, 'check_number = 124' );

        $oDB->execute( $hQuery, array( 1, '2003-11-26',
            1234, 2098.65, 124.55, 98.98 ) );

        $oDB->freePrepared( $hQuery );
        $oDB->disconnect();
    }
?>
```

#### 代码清单 29：使用 autoPrepare() – UPDATE

If you noticed in Code Listing 28, all three rows that were inserted contained the same *check_number* value. The example in Code Listing 29 updates all rows in the database whose *check_number* is 124. This is accomplished by specifying the *where* parameter in the call to **autoPrepare()**. This is important to note: if you use the DB_AUTOQUERY_UPDATE *mode*, you must specify a value for the *where* parameter otherwise all rows in the table will be affected by the update statement.

- 返回一个已准备查询的句柄，可供 **execute()** 及类似方法使用。

### DB_common::autoExecute

```text
mixed autoExecute(string $table, array $fields_values, int $mode = DB_AUTOQUERY_INSERT, mixed $where = false)
```

The **autoExecute()** method is a combination of the **autoPrepare()**, **execute()** and **freePrepared()** methods executed in that order.

An example of usage is shown in Code Listing 30. The example illustrates how straightforward updating rows in a database can become when using PEAR::DB to encapsulate a great deal of the work. The code causes the following SQL statement to execute against the database:

```sql
update Paychecks set gross_pay = '3123.45', taxes_withheld = '324.43' where ( check_number = '1234' )
```

Depending on your application, using the prepare/execute model along with the **autoPrepare()** or **autoExecute()** methods may improve readability and long-term maintenance. If you choose to use some of these methods, it becomes important to note their limitations. With the **autoPrepare()** and **autoExecute()** methods, it is not possible to specify the '?' type of parameter. Therefore the following type of query is impossible to accomplish:

```sql
update Paychecks set taxes_withheld = taxes_withheld * 1.10 where ( employee_id = '1' )
```

However, this type of query is not the type that is intended to be used in an **autoPrepare()** or **autoExecute()** situation. Think of these methods in places where you are developing web-based forms to collect and update information.

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $aUpdates = array( 'gross_pay' => '3123.45',
                           'taxes_withheld' => '324.43'
        );

        $hQuery = $oDB->autoExecute( 'Paychecks',
        $aUpdates, DB_AUTOQUERY_UPDATE, 'check_number = 1234' );

        $oDB->disconnect();
    }
?>
```

#### 代码清单 30：使用 autoExecute()

- 成功时返回 DB_OK，失败时返回 DB_Error 对象。

### DB_common::buildManipSQL

```text
string buildManipSQL(string $table, array $table_fields, int $mode, mixed $where = false)
```

The **buildManipSQL()** method is used internally by the **autoPrepare()** method to create a parameterized query. The parameters are the same as for the **autoPrepare()** statement except that the *mode* parameter is not optional.

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $sSQL = $oDB->buildManipSQL( 'Paychecks',
        array( 'employee_id', 'check_date', 'check_number',
        'gross_pay', 'benefits_withheld', 'taxes_withheld'
        ), DB_AUTOQUERY_INSERT );
        print( "SQL Statement: $sSQL<br><br>" );

        $SQL = $oDB->buildManipSQL( 'Paychecks',
        array( 'employee_id', 'check_date', 'check_number',
        'gross_pay', 'benefits_withheld', 'taxes_withheld'
        ), DB_AUTOQUERY_UPDATE, 'check_number = 1234' );
        print( "SQL Statement: $SQL<br>" );

        $oDB->disconnect();
    }
?>
```

#### 代码清单 31：使用 buildManipSQL()

The example in Code Listing 31 is used to print the parameterized queries developed in Code Listing 28 and Code Listing 29. The output is shown in Output 12.

```text
SQL Statement: INSERT INTO Paychecks (employee_id,check_date,check_number,gross_pay,benefits_withheld,taxes_withheld) VALUES (?,?,?,?,?,?)

SQL Statement: UPDATE Paychecks SET employee_id = ?,check_date = ?,check_number = ?,gross_pay = ?,benefits_withheld = ?,taxes_withheld = ? WHERE check_number = 1234
```

#### 输出 12：使用 buildManipSQL() 的示例

- 返回格式化为 **prepare()** 语句的 SQL 字符串。

### DB_common::execute

```text
mixed execute( resource $stmt, array $data )
```

The **execute()** method is the primary querying method when using the prepare/execute methodology. Several usage examples have been given in the sections regarding the **prepare()** and **autoPrepare()** methods. See Code Listing 25 on page 61, Code Listing 27 on page 63, Code Listing 28 on page 64, Code Listing 29 on page 65.



- 如果底层结果返回数据集，则返回一个新的 DB_result 对象；如果数据库出错，则返回 DB_Error。

### DB_common::executeEmulateQuery

`mixed executeEmulateQuery( resource $stmt, array $data )`

executeEmulateQuery() 方法在技术上是一个私有方法，旨在由类内部使用。其功能是将参数化查询及其相关数据转换为完全限定的 SQL 字符串。此方法仅用于后端服务器不支持 prepare/execute 方法的数据库对象。

由于 PHP 4 实际上并不支持私有方法，代码清单 32 中的示例展示了 executeEmulateQuery() 的内部结果。注意，不应依赖此方法存在，因为 PHP 5 将支持真正私有的类方法和属性。

#### 代码清单 32：executeEmulateQuery() 示例

```php
<?php
require_once( 'DB.php' );
$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    $sSQL = 'insert into paychecks ( employee_id,
        check_date, check_number, gross_pay,
        benefits_withheld, taxes_withheld ) values ( ?, ?, ?, ?, ?, ? )';

    $hQuery = $oDB->prepare( $sSQL );
    $sRealSQL = $oDB->executeEmulateQuery( $hQuery,
        array( 1, 'NOW()', 128, 1098.65, 124.55, 98.98 ) );
    print( "SQL: $sRealSQL<br><br>" );

    $oDB->freePrepared( $hQuery );
    $oDB->disconnect();
}
?>
```

#### 输出 13：executeEmulateQuery() 示例输出

```sql
SQL: insert into Paychecks ( employee_id, check_date, check_number, gross_pay, benefits_withheld, taxes_withheld ) values ( 1, NOW(), 128, 1098.65, 124.55, 98.98 )
```

- 返回包含完全限定查询的字符串，或在失败时返回 DB_Error。

### DB_common::executeMultiple

`mixed executeMultiple( resource $stmt, array $data )`

executeMultiple() 方法与 execute() 方法相同，只是其 data 参数是一个二维数组。可以将该数组视为数据行。

#### 代码清单 33：使用 executeMultiple()

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    $hQuery = $oDB->autoPrepare( 'Paychecks',
        array( 'employee_id', 'check_date', 'check_number', 'gross_pay', 'benefits_withheld', 'taxes_withheld' )
    );

    $aAllData[] = array( 1, '2003-11-27', 224, 1098.65, 124.55, 98.98 );
    $aAllData[] = array( 2, '2003-11-27', 225, 1198.65, 124.55, 99.98 );
    $aAllData[] = array( 3, '2003-11-27', 226,
        1298.65, 124.55, 95.98 );
    $DB->executeMultiple( $hQuery, $aAllData );
    $DB->freePrepared( $hQuery );

    $DB->disconnect();
}
?>
```

代码清单 33 中的代码说明了如何使用 **executeMultiple()** 方法。此示例与第 64 页代码清单 28 中的示例相同，只是实际数据作为二维数组传递给 **executeMultiple()**。

**executeMultiple()** 的内部代码是对数组的简单遍历并调用 **execute()**。如果在任何一行数据上发生错误，处理过程将中止，后续行不会被处理。

> 这是该方法的一个重要考虑因素，如果某行可能失败，则最好自行在循环中使用 **execute()** 并根据需要处理错误情况。

- 返回 DB_OK 或 DB_Error 对象。

### DB_common::freePrepared

`boolean freePrepared( resource $stmt )`

释放使用 **prepare()** 或 **autoPrepare()** 方法创建的已准备查询句柄。用法示例请参阅代码清单 25、代码清单 27、代码清单 28、代码清单 29、代码清单 32 或代码清单 33。

- 如果传递的参数是正确的查询句柄，则返回 true，否则返回 false。

### DB_common::modifyQuery

`string modifyQuery( string $query )`

**modifyQuery()** 方法仅 intended to be used by backend 数据库对象。它是在 DB_common 级别定义的私有方法，以确保所有实现至少有一个空的 **modifyQuery()** 定义可用。

- 从给定的输入查询字符串返回修改后的查询字符串。

### DB_common::modifyLimitQuery

`string modifyLimitQuery( string $query, integer $from, integer $count )`

**modifyLimitQuery()** 方法仅 intended to be used by backend 数据库对象。它是在 DB_common 级别定义的私有方法，以确保所有实现至少有一个空的 **modifyLimitQuery()** 定义可用。有关使用信息，请参阅第 74 页 **limitQuery()** 的描述。

- 从给定的输入查询字符串返回修改后的查询字符串。

### DB_common::query

`mixed query( string $query, array $params = array() )`

**query()** 方法向数据库发送查询。如果未指定 *params* 参数，则 *query* 被解释为简单的 SQL 字符串，否则 *query* 被解释为参数化查询，并与 *params* 一起在 **prepare()** 和 **execute()** 序列中使用。代码清单 34 中的示例展示了这两种可能性。

#### 代码清单 34：使用 query()

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

    $aSQL = "select * from Employees where (
        mgr_id = '2' ) or ( mgr_id = '0' )";
    $oRows = $oDB->query( $aSQL );
    if ( !DB::isError( $oRows ) )
    {
        while ( $aRow = $oRows->fetchRow() )
        {
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
        }
        print( '<br>' );
    }

    $aSQL = "select * from Employees where (
        mgr_id = ? ) or ( mgr_id = ? )";
    $oRows = $oDB->query( $aSQL, array( '2', '0' ) );
    if ( !DB::isError( $oRows ) )
    {
        while ( $aRow = $oRows->fetchRow() )
        {
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
        }
        print( '<br>' );
    }

    $oDB->disconnect();
}
?>
```

代码清单 34 中的示例展示了如何将简单查询（第 9–18 行）或参数化查询（第 20–29 行）与 **query()** 方法结合使用。请注意，此示例绝不是使用参数化查询的好例子，而只是 **query()** 方法的简单示例。

- 成功时返回 DB_result 对象或 DB_OK，失败时返回 DB_Error 对象。

### DB_common::limitQuery

`mixed limitQuery( string $query, integer $from,
    integer $count, array $params = array() )`

**limitQuery()** 方法生成一个受限查询。该方法最重要的说明是它是一个实验性方法，目前并非所有数据库后端都支持。完全支持 **limitQuery()** 方法的数据库类型有 *ibase*、*mysql*、*oci8*、*pgsql* 和 *sqlite*。

**limitQuery()** 方法的概念是修改 SQL 语句，使其效果限制在一定数量的数据行内。示例（使用 MySQL SQL 语法）见代码清单 35。

#### 代码清单 35：使用 SQL 限制 MySQL 查询

```sql
select * from Employees
select * from Employees limit 5, 5
```

代码清单 35 第 1 行显示了无限制查询。该查询的结果是返回所有匹配行（或本例中的所有行）。代码清单 35 第 2 行的语句说明了 MySQL 限制查询仅返回 5 行数据的语法，从数据库中的第 6 行开始（MySQL 的索引为零基）。

此类功能对于分页浏览大型数据集和限制结果以减少数据传输非常有用。然而，每个后端数据库都有自己的 SQL 语法来限制返回的行数，如果该概念得到支持的话。

代码清单 36 中的示例展示了使用 limitQuery() 方法的简单 MySQL 解决方案。它与代码清单 34 中的示例相同，但仅显示两行，从第二行开始。limitQuery() 方法的参数与 query() 方法相同，但额外增加了起始行号和行数（分别为 from 和 count）。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

    $aSQL = "select * from Employees where (
        mgr_id = '2' ) or ( mgr_id = '0' )";
    $oRows = $oDB->limitQuery( $aSQL, 1, 2 );
    if ( !DB::isError( $oRows ) )
    {
        while ( $aRow = $oRows->fetchRow() )
        {
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
        }
    }
    print( '<br>' );

    $aSQL = "select * from Employees where (
        mgr_id = ? ) or ( mgr_id = ? )";
    $oRows = $oDB->limitQuery( $aSQL, 1, 2, array(
        '2', '0' ) );
    if ( !DB::isError( $oRows ) )
    {
        while ( $aRow = $oRows->fetchRow() )
        {
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
        }
    }
    print( '<br>' );
```

```php
$DB->disconnect();
}
?>
```

#### 代码清单 36：使用 limitQuery()

虽然这种类型的功能可能有助于泛化，但如果希望实现数据库可移植的实现，我建议避免使用此方法。相反，请考虑希望支持的数据库，并构建适用于应用程序的分页或限制解决方案。

返回一个 DB_result 对象、DB_OK 或 DB_Error 对象。

### DB_common::getOne

```php
mixed getOne( string $query, array $params = array() )
```

getOne() 方法用于返回针对 SQL 字符串 query 返回的数据的第一行的第一列。如同 query() 方法一样，如果指定了 params，则 query 应为参数化查询字符串。

此方法在查询返回单个值的情况下很有用，例如可能由聚合 SQL 函数返回。代码清单 37 中的示例展示了如何使用 getOne() 方法以及使用 query() 方法的等效方法来返回表中行的总数。

```php
<?php
    require_once( 'DB.php' );

    $DB = DB::connect(
        'mysqli://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $DB ) )
    {
```

代码清单 38 中的示例说明了 **getOne()** 方法的一般用法。第 7 – 12 行显示了基本用法。第 14 – 18 行说明了相同用法，但使用了 **DB_FETCHMODE_ASSOC** 值。输出（为便于阅读而重新格式化）显示在 **输出 14** 中。

```text
array(6) {
    [0]=>
    string(1) "1"
    [1]=>
    string(11) "Schwendiman"
    [2]=>
    string(5) "Blake"
    [3]=>
    string(3) "204"
    [4]=>
    string(1) "2"
    [5]=>
    string(1) "1"
}
array(6) {
    ["id"]=>
    string(1) "1"
    ["last_name"]=>
    string(11) "Schwendiman"
    ["first_name"]=>
    string(5) "Blake"
    ["phone_ext"]=>
    string(3) "204"
    ["mgr_id"]=>
    string(1) "2"
    ["dept_id"]=>
    string(1) "1"
}
```

**输出 14：** getRow() 方法的输出。

- 返回一个 DB_Error 对象、DB_OK 或查询的返回值。

### DB_common::getCol

```php
array getCol( string $query, mixed $col = 0, array $params = array() )
```

此方法在概念上与 **getRow()** 方法相似。**getCol()** 方法返回由查询字符串 _query_ 获得的结果集中所有行中由 *col* 指定的列中的值。如同 **query()** 方法一样，如果 _params_ 为数组，则假定 _query_ 为参数化查询，且 _params_ 为在 prepare/execute 查询中使用的实际参数。

**getCol()** 方法不使用 _fetchmode_ 参数，并且不尊重由 **setFetchMode()** 设置的内部 fetchmode。如果 _col_ 的值为整数，**getCol()** 内部使用 **DB_FETCHMODE_ORDERED**。如果 _col_ 为字符串（列名），则内部使用 **DB_FETCHMODE_ASSOC**。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( DB::isConnection( $oDB ) )
    {
        $aSQL    = "select * from Employees limit 5";
        $aValue  = $oDB->getCol( $aSQL, 'first_name' );
        if ( !DB::isError( $aValue ) )
        {
            var_dump( $aValue );
        }

        $aValue = $oDB->getCol( $aSQL, 1 );
        if ( !DB::isError( $aValue ) )
        {
            var_dump( $aValue );
        }

        $oDB->disconnect();
    }
?>
```

#### 代码清单 39：使用 getCol()。

代码清单 39 中的示例展示了 **getCol()** 方法的一般用法。第 10 行说明了使用字符串列名进行调用，而第 16 行显示了使用整数列索引的用法（在此表中列 1 为 _last_name_ 列）。示例代码的输出（为便于阅读而重新格式化）显示在 输出 15 中。

```text
array(5) {
    [0]=>
    string(5) "Blake"
    [1]=>
    string(7) "Jeffrey"
    [2]=>
    string(4) "Kate"
    [3]=>
    string(4) "Ryan"
    [4]=>
    string(4) "Ryan"
}
array(5) {
    [0]=>
    string(11) "Schwendiman"
    [1]=>
    string(3) "Cox"
    [2]=>
    string(7) "McNulty"
    [3]=>
    string(11) "Schwendiman"
    [4]=>
    string(11) "Schwendiman"
}
```

**输出 15：** getCol() 方法的输出。

- 返回一个包含由 *col* 参数指定的列数据的索引数组，或 DB_Error。

### DB_common::getAssoc

```php
array getAssoc( string $query, boolean
    $force_array = false, array $params = array(),
    integer $fetchmode = DB_FETCHMODE_DEFAULT,
    boolean $group = false )
```

**getAssoc()** 方法使用第一列作为数组键返回查询的整个结果集作为关联数组。如果结果集包含多于两列，则返回数组中每个元素的价值将是列 2 到 *n* 的值的数组。如果结果集仅包含 2 列，则返回数组中每个元素的价值将是标量值，除非 *force_array* 参数为 true。如果结果集包含少于两列，则返回 DB_ERROR_TRUNCATED 错误。

```text
[0] =>
    string(7) "McNulty"
[1] =>
    string(4) "Kate"
[2] =>
    string(3) "214"
[3] =>
    string(1) "2"
[4] =>
    string(1) "2"
```

输出 16：与代码清单 40 相关的 getAssoc() 输出。

请注意，输出 16 中显示的 **array** 是一个关联数组，其中键是结果集中每一行的 *id* 字段，值是结果集的其他字段。

可以指定 *fetchmode* 参数以覆盖使用 **setFetchMode()** 完成的任何全局设置。

我更喜欢使用 **setFetchMode()** 方法，因此代码清单 41 中的示例展示了这一点。此更改的输出显示在 输出 17 中。

```php
<?php
    require_once ('DB.php');

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $aSQL   = "select * from Employees limit 3";
        $aValue = $oDB->getAssoc( $aSQL );
        if ( ! DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

#### 代码清单 41：使用 getAssoc() – 使用 setFetchMode() 的示例。

```text
array(3) {
  [1]=>
  array(5) {
    ["last_name"]=>
    string(11) "Schwendiman"
    ["first_name"]=>
    string(5) "Blake"
    ["phone_ext"]=>
    string(3) "204"
    ["mgr_id"]=>
    string(1) "2"
    ["dept_id"]=>
    string(1) "1"
  }
  [2]=>
  array(5) {
    ["last_name"]=>
    string(3) "Cox"
    ["first_name"]=>
    string(7) "Jeffrey"
    ["phone_ext"]=>
    string(3) "225"
    ["mgr_id"]=>
    string(1) "0"
    ["dept_id"]=>
    string(1) "1"
  }
  [3]=>
  array(5) {
    ["last_name"]=>
    string(7) "McNulty"
    ["first_name"]=>
    string(4) "Kate"
    ["phone_ext"]=>
    string(3) "214"
    ["mgr_id"]=>
    string(1) "2"
    ["dept_id"]=>
    string(1) "2"
  }
}
```

输出 17：与代码清单 41 相关的 getAssoc() 输出。

为了说明 *force_array* 参数，需要一个仅返回两列的查询。代码清单 42 中的示例展示了这一点。

```php
<?php
    require_once('DB.php');

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
$oDB->setFetchMode( DB_FETCHMODE_ASSOC );

$aSQL = "select id, last_name from Employees
limit 3";
$aValue = $oDB->getAssoc( $aSQL );
if ( !DB::isError( $aValue ) )
{
print( '<pre>' );
var_dump( $aValue );
print( '</pre>' );
}

$oDB->disconnect();
}
?>
```

#### 代码清单 42：使用 getAssoc() – 说明 *force_array* 参数（设置为 *false*）。

正如输出、输出 18 所示，**getAssoc()** 的默认行为是当结果集中只有两列时，结果数组由第一列索引，第二列包含原子值。

```text
array(3) {
[1]=>
string(11) "Schwendiman"
[2]=>
string(3) "Cox"
[3]=>
string(7) "McNulty"
}
```

输出 18：与代码清单 42 相关的 getAssoc() 输出。

使用 *force_array* 参数的优点是你可以编写更通用的代码来处理结果数组，而不必为包含数组值的和包含原子值的不同结果数组编写特殊情况代码。




默认情况下，之前的结果会被覆盖。如果要保留所有结果并按第一列的值进行分组，请使用 *group* 参数。为说明这一点，代码清单 44 包含一个查询，其中的第一个参数是一个在结果集中重复出现的值。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $aSQL = "select mgr_id, last_name, first_name
from Employees";
        $aValue = $oDB->getAssoc( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

**代码清单 44：使用 getAssoc() —— 演示 *group* 参数（设为 *false*）。**

代码清单 44 的输出如输出 20 所示。可以看出，该数组仅包含三个元素，分别对应结果集中三个唯一的 *mgr_id* 值。

```text
array(3) {
    [2]=>
    array(2) {
        ["last_name"]=>
        string(7) "McNulty"
        ["first_name"]=>
        string(4) "Kate"
    }
    [0]=>
    array(2) {
        ["last_name"]=>
        string(3) "Cox"
        ["first_name"]=>
        string(7) "Jeffrey"
    }
    [1]=>
    array(2) {
        ["last_name"]=>
        string(11) "Schwendiman"
        ["first_name"]=>
        string(6) "Taylor"
    }
}
```

**输出 20：与代码清单 44 相关的 getAssoc() 输出。**

由于多个 *Employees* 记录的 *mgr_id* 可能相同，因此将 **getAssoc()** 方法的 *group* 参数设置为 true 以获取所有行数据非常重要。代码清单 45 中的代码说明了这一点。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $aSQL   = "select mgr_id, last_name, first_name
from Employees";
        $aValue = $oDB->getAssoc( $aSQL, false,
            array(), DB_FETCHMODE_ASSOC, true );
        if ( ! DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

**代码清单 45：使用 getAssoc() —— 演示 *group* 参数（设为 true）。**

由于 *group* 参数是 **getAssoc()** 方法的最后一个参数，因此必须指定所有中间参数（参见第 10 行）。与此更改相关的输出如输出 21 所示。

```text
array(3) {
  [2]=>
  array(2) {
    [0]=>
    array(2) {
      ["last_name"]=>
      string(11) "Schwendiman"
      ["first_name"]=>
      string(5) "Blake"
    }
    [1]=>
    array(2) {
      ["last_name"]=>
      string(7) "McNulty"
      ["first_name"]=>
      string(4) "Kate"
    }
  }
  [0]=>
  array(1) {
    [0]=>
    array(2) {
      ["last_name"]=>
      string(3) "Cox"
      ["first_name"]=>
      string(7) "Jeffrey"
    }
  }
  [1]=>
  array(3) {
    [0]=>
    array(2) {
      ["last_name"]=>
      string(11) "Schwendiman"
      ["first_name"]=>
      string(4) "Ryan"
    }
    [1]=>
    array(2) {
      ["last_name"]=>
      string(11) "Schwendiman"
      ["first_name"]=>
      string(5) "Scott"
    }
    [2]=>
    array(2) {
      ["last_name"]=>
      string(11) "Schwendiman"
      ["first_name"]=>
      string(6) "Taylor"
    }
  }
}
```

**输出 21：与代码清单 45 相关的 getAssoc() 输出。**

与 *query()* 方法一样，如果 *params* 是一个数组，则假定 *query* 是一个参数化查询，*params* 是在 prepare/execute 查询中使用的实际参数。

- 返回一个关联数组，其中包含查询字符串中的所有数据；如果出错，则返回 DB_Error 对象。

### DB_common::getAll

```text
array getAll( string $query, array $params = null,
    integer $fetchmode = DB_FETCHMODE_DEFAULT )
```

**getAll()** 方法与 **getAssoc()** 方法类似，但 **getAll()** 不是返回以第一列数据为索引的关联数组，而是返回一个索引数组，并且所有列都是结果数组值的一部分。

代码清单 46 展示了使用 **getAll()** 方法的最简单示例。

```php
<?php
    require_once ('DB.php');

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $aSQL   = "select * from Employees";
        $aValue = $oDB->getAll( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

**代码清单 46：使用 getAll() —— 最简单的用法。**

与代码清单 46 相关的输出如输出 22 所示（为节省篇幅，输出截取前两行）。

```text
array(6) {
  [0]=>
  array(6) {
    ["id"]=>
    string(1) "1"
    ["last_name"]=>
    string(11) "Schwendiman"
    ["first_name"]=>
    string(5) "Blake"
    ["phone_ext"]=>
    string(3) "204"
    ["mgr_id"]=>
    string(1) "2"
    ["dept_id"]=>
    string(1) "1"
  }
  [1]=>
  array(6) {
    ["id"]=>
    string(1) "2"
    ["last_name"]=>
    string(3) "Cox"
    ["first_name"]=>
    string(7) "Jeffrey"
    ["phone_ext"]=>
    string(3) "225"
    ["mgr_id"]=>
    string(1) "0"
    ["dept_id"]=>
    string(1) "1"
  }
}
```

**输出 22：与代码清单 46 相关的 getAll() 输出。**

getAll() 方法是唯一可以让 fetchmode 包含 DB_FETCHMODE_FLIPPED 位并产生效果的方法。该 fetchmode 位表示结果数组应首先按结果集的列索引，然后按数据行索引。如第 52 页关于 setFetchMode() 的章节中所述，DB_FETCHMODE_FLIPPED 位不能通过 setFetchMode() 通用设置，因此必须专门传入 getAll() 方法。代码清单 47 展示了这方面的示例。

```php
<?php
    require_once( 'DB.php' );

    $DB = DB::connect(
        'mysql://db_user:db_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $DB ) )
    {
        $SQL = "select * from Employees";
        $aValue = $DB->getAll( $SQL, null,
            DB_FETCHMODE_ASSOC + DB_FETCHMODE_FLIPPED );
        if ( !DB::isError( $aValue ) )
        {
            print( "<pre>" );
            var_dump( $aValue );
            print( "</pre>" );
        }
        $DB->disconnect();
    }
?>
```

**代码清单 47：使用 getAll() —— 使用 DB_FETCHMODE_FLIPPED。**

代码清单 47 中微小的代码更改产生了输出 23 所示的输出。从该输出中可以看出，所有列数据都分组在一起。

```text
array(6) {
  ["id"]=>
  array(6) {
    [0]=>
    string(1) "1"
    [1]=>
    string(1) "2"
    [2]=>
    string(1) "3"
    [3]=>
    string(1) "4"
    [4]=>
    string(2) "58"
    [5]=>
    string(2) "59"
  }
  ["last_name"]=>
  array(6) {
    [0]=>
    string(11) "Schwendiman"
    [1]=>
    string(3) "Cox"
    [2]=>
    string(7) "McNulty"
    [3]=>
    string(11) "Schwendiman"
    [4]=>
    string(11) "Schwendiman"
    [5]=>
    string(11) "Schwendiman"
  }
  ["first_name"]=>
  array(6) {
    [0]=>
    string(5) "Blake"
    [1]=>
    string(7) "Jeffrey"
    [2]=>
    string(4) "Kate"
    [3]=>
    string(4) "Ryan"
    [4]=>
    string(5) "Scott"
    [5]=>
    string(6) "Taylor"
  }
}
```

**输出 23：与代码清单 47 相关的 getAll() 输出。**

与 **query()** 方法一样，如果 *params* 是一个数组，则假定 *query* 是一个参数化查询，*params* 是在 prepare/execute 查询中使用的实际参数。

- 返回一个数组，其中包含查询字符串中的所有数据；如果出错，则返回 DB_Error 对象。

### DB_common::autoCommit

```text
mixed autocommit( boolean $onoff = false )
```

启用或禁用查询的自动提交。仅支持事务的数据库引擎支持此方法。默认情况下，对于支持事务的数据库，autocommit 设置为 true。

- 成功时返回 DB_OK；失败时返回 DB_Error 对象。

### DB_common::commit

```text
mixed commit( void )
```

**commit()** 方法提交对数据库执行的事务。仅后端支持事务的 DB 对象支持此方法。




```php
<?php
    require_once( 'DB.php' );

    $bRollbackCondition = true;

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $aSQL = "select * from Employees where (
mgr_id = 2 )";
        $aValue = $oDB->getAll( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->autoCommit( false );

        $aSQL = "update Employees set mgr_id = 3 where
( mgr_id = 2 )";
        $oDB->query( $aSQL );
        if ( $bRollbackCondition == true )
        {
            $result = $oDB->rollback();
            print( "Updates rolled back<br>" );
        }
        else
        {
            $result = $oDB->commit();
            print( "Updates committed<br>" );
        }

        $aSQL = "select * from Employees where (
mgr_id = 2 )";
        $aValue = $oDB->getAll( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

#### 代码清单 48：使用 commit()。

代码清单 48 中展示的非常简化的示例说明了如何使用 **commit()** 方法。代码使用一个简单的布尔值来决定是提交还是回滚事务，因此同一段代码也可以重用于 **rollback()** 方法。

```php
$SQL = "select * from Employees where (
    mgr_id = 2 )";
$AValue = $DB->getAll( $SQL );
if ( ! DB::isError( $AValue ) )
{
    print( '<pre>' );
    var_dump( $AValue );
    print( '</pre>' );
}

$DB->disconnect();
?>
```

#### 代码清单 49：使用 rollback()。

代码清单 49 中展示的示例与代码清单 48 中的代码完全相同（**commit()** 示例），只是回滚条件标志被设置为 true。这会导致事务回滚。输出 25 中显示的输出清楚地证明了 UPDATE 查询已被回滚，因为随后 SELECT 查询返回的数据与 UPDATE 查询之前的数据相同。

```text
array(2) {
  [0]=>
  array(6) {
    [0]=>
    string(1) "1"
    [1]=>
    string(11) "Schwendiman"
    [2]=>
    string(5) "Blake"
    [3]=>
    string(3) "204"
    [4]=>
    string(1) "2"
    [5]=>
    string(1) "1"
  }
  [1]=>
  array(6) {
    [0]=>
    string(1) "3"
    [1]=>
    string(7) "McNulty"
    [2]=>
    string(4) "Kate"
    [3]=>
    string(3) "214"
    [4]=>
    string(1) "2"
    [5]=>
    string(1) "2"
  }
}
Updates rolled back
array(2) {
    [0] =>
    array(6) {
        [0] =>
        string(1) "1"
        [1] =>
        string(11) "Schwendiman"
        [2] =>
        string(5) "Blake"
        [3] =>
        string(3) "204"
        [4] =>
        string(1) "2"
        [5] =>
        string(1) "1"
    }
    [1] =>
    array(6) {
        [0] =>
        string(1) "3"
        [1] =>
        string(7) "McNulty"
        [2] =>
        string(4) "Kate"
        [3] =>
        string(3) "214"
        [4] =>
        string(1) "2"
        [5] =>
        string(1) "2"
    }
}
```

**输出 25：使用 rollback() 的示例。**

- 返回 DB_OK 或 DB_Error 对象。

### DB_common::numRows

`mixed numRows( mixed $result )`

**numRows()** 方法可用于返回 DB_result 对象中的行数。我不推荐使用此方法（见下文），但在代码清单 50 中提供了使用示例。

```php
<?php
```

### DB_common::createSequence

`mixed createSequence( string $seq_name )`

**createSequence()** 方法为数据库创建一个名为 _seq_name_ 的新序列。请参阅第 22 页开始的序列部分，了解序列的完整细节以及使用序列的示例。**createSequence()** 方法可能会被 **nextId()** 方法自动调用（见第 100 页的 **nextId()**）。

根据所使用的 DB 后端，您可能需要某些访问权限才能成功使用 **createSequence()** 方法。例如，代码清单 52 中的代码展示了具有受限访问权限的用户无法创建序列的情况。示例中的用户在 MySQL 数据库上只有 SELECT 权限。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
  'mysql://bt_r_user:pass@207.44.182.3/book_test', true );
if ( DB::isConnection( $oDB ) )
{
  $result = $oDB->createSequence( 'NewSequence' );
  if ( !DB::isError( $result ) )
  {
    print( 'Sequence created<br>' );
  }
  else
  {
    print( $result->userinfo );
  }
  $oDB->disconnect();
}
else
{
  print( $oDB->userinfo );
}
?>
```

#### 代码清单 52：使用 MySQL 的 createSequence()。

由于用户 **bt_r_user** 没有在 *book_test* 数据库上创建新表的权限，因此对 **createSequence()** 的调用失败，输出如输出 26 所示。其他数据库服务器对序列创建可能有不同的要求，这可能会影响 **createSequence()** 方法的使用。任何使用 PEAR::DB 序列的应用程序都应考虑这些差异。

```text
CREATE TABLE NewSequence_seq (id INTEGER UNSIGNED
AUTO_INCREMENT NOT NULL, PRIMARY KEY (id))
[Nativecode=1142 - create command denied to user:
'bt_r_user@xxx.xxx.xxx.xxx' for table
'NewSequence_seq']
```

**输出 26：** 在用户权限不足的 MySQL 数据库上使用 createSequence() 的输出。

- 返回 DB_OK 或 DB_Error 对象。

### DB_common::dropSequence

`mixed dropSequence( string $seq_name )`

**dropSequence()** 方法是 **createSequence()** 方法的对应方法。相同的关于安全性和用户权限的限制适用。有关详细信息，请参阅 **createSequence()** 方法说明（第 101 页）。

- 返回 DB_OK 或 DB_Error 对象。

### DB_common::tableInfo

`mixed tableInfo( mixed $result, mixed $mode = null )`

**tableInfo()** 方法用于返回有关表或查询的元数据信息。*result* 参数是通过 DB_result 对象可用的数据库特定值。与 **numRows()** 方法（第 98 页）一样，使用 **tableInfo()** 的首选编码方法是通过 **DB_result::tableInfo()** 方法。这只是更好的面向对象编程。

> 事实上，因为这是更好的实践，我不会在此处完整记录此方法，而是请您参考第 116 页的 **DB_result::tableInfo()** 方法了解详情。

唯一应该使用 **DB_common::tableInfo()** 的情况是当您需要获取与 DB_result 无关的表元数据时。在这种情况下，*result* 参数是一个字符串——表名。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
    if ( DB::isConnection( $oDB ) )
    {
        $result = $oDB->tableInfo( 'Employees' );
        if ( ! DB::isError( $result ) )
        {
            print( '<pre>' );
            var_dump( $result );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

#### 代码清单 53：使用 tableInfo()。

代码清单 53 中的示例说明了如何使用 **tableInfo()** 来获取有关 MySQL 数据库表的信息。对 **tableInfo()** 的调用结果是

### DB_common::getTables

`mixed getTables( void )`

getTables() 方法返回一个包含当前数据库中所有表的数组。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
$result = $oDB->getTables();
if ( !DB::isError( $result ) )
{
print( '<pre>' );
var_dump( $result );
print( '</pre>' );
}

$oDB->disconnect();
}
?>
```

#### 代码清单 54：使用 getTables()。

代码清单 54 中示例的输出在输出 28 中给出。

```text
array(9) {
[0]=>
string(11) "Departments"
[1]=>
string(9) "Employees"
[2]=>
string(9) "Paychecks"
[3]=>
string(13) "UploadedFiles"
[4]=>
string(13) "seq_employees"
[5]=>
string(14) "seq_sequence_1"
[6]=>
string(14) "seq_sequence_2"
[7]=>
string(14) "sequence_1_seq"
[8]=>
string(14) "sequence_2_seq"
}
```



**输出 28：与 getTables 示例相关的输出（代码清单 54）。**

- 返回一个索引数组，其中包含当前数据库中的表；或者返回 DB_Error。

### DB_common::getListOf

```
mixed getListOf( string $type )
```

**getListOf()** 方法根据 *type* 参数返回数据库特定的信息和元数据。例如，第 105 页描述的 **getTables()** 方法就是对 **getListOf()** 的一次调用，其中 *type* 参数被设置为字符串 'tables.'。*type* 参数的值是数据库特定的。目前，表 7 所示的矩阵列出了可用数据库对 *type* 参数的支持情况。

| 数据库 | 表 | 视图 | 主表 | 模式 | 函数 | 用户 | 数据库 |
|---|---:|---:|---:|---:|---:|---:|---:|
| dbase | □ | □ | □ | □ | □ | □ | □ |
| fbsql | ■ | □ | □ | □ | □ | □ | □ |
| ibase | ■ | □ | □ | □ | □ | □ | □ |
| ifx | ■ | □ | □ | □ | □ | □ | □ |
| msql | ■ | □ | □ | □ | □ | □ | □ |
| mssql | ■ | ■ | □ | □ | □ | □ | □ |
| mysql | ■ | □ | □ | □ | □ | ■ | ■ |
| oci8 | ■ | □ | □ | □ | □ | □ | □ |
| odbc | □ | □ | □ | □ | □ | □ | □ |
| pgsql | ■ | ■ | □ | □ | ■ | ■ | ■ |
| sqlite | ■ | □ | ■ | ■ | □ | □ | □ |
| sybase | ■ | ■ | □ | □ | □ | □ | □ |
| dbase | □ | □ | □ | □ | □ | □ | □ |

**表 7：各数据库后端在 getSpecialQuery 中支持的类型。**

```php
<?php
    require_once ( 'DB.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( DB::isConnection( $oDB ) )
    {
        print( 'Tables:<ol>' );
        $result = $oDB->getListOf( 'tables' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        print( 'Users:<ol>' );
        $result = $oDB->getListOf( 'users' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        print( 'Databases:<ol>' );
        $result = $oDB->getListOf( 'databases' );
        if ( !DB::isError( $result ) )
        {
            foreach ( $result as $aValue )
                print( "<li>$aValue</li>" );
        }
        print( '</ol>' );

        $oDB->disconnect();
    }
?>
```

#### 代码清单 55：使用 getListOf()。

代码清单 55 中的示例演示了 getListOf() 的用法。从输出 29 可以看出，不仅列表的类型因数据库而异，而且可用信息严格依赖于用户的访问权限。用于本书的 MySQL 服务器上还有更多数据库，但只列出了一个，因为这是指定用户唯一可用的数据库。此外，此处示例中使用的用户名没有权限查看 MySQL 用户数据库来列出其他用户。

```
Tables:
1. Departments
2. Employees
3. Paychecks
4. UploadedFiles
5. seq_employees
6. seq_sequence_1
7. seq_sequence_2
8. sequence_1_seq
9. sequence_2_seq
Users:
Databases:
1. book_test
```

**输出 29：getListOf() 示例的输出（代码清单 55）。**

返回一个 DB_result 或 DB_Error 对象。

### DB_common::getSequenceName

```
string getSequenceName( string $sqn )
```

这是一个由序列函数使用的私有方法（见第 22 页）。该方法根据一个简单的序列标识符字符串 sqn 返回完全限定的序列名称。

返回一个字符串。

## 类 DB_result

类 DB_result 提供了用于处理数据库查询结果的方法。DB_result 对象不太可能由你的应用程序直接创建。

| 方法 | 描述 |
|---|---|
| setOption() | 在 DB_result 对象上设置选项。 |
| fetchRow() | 获取并返回一行数据。内部使用 fetchInto。 |
| fetchInto() | 将一行数据获取到现有变量中。 |
| numCols() | 返回结果集中的列数。 |
| numRows() | 返回结果集中的行数。 |
| nextResult() | 如果执行了一批查询，则返回下一个结果。 |
| free() | 释放分配给此结果集的资源。 |
| tableInfo() | 返回关于结果集的元数据。 |
| getRowCounter() | 返回实际的行号。 |

表 8：DB_result 类的方法

### DB_result::setOption

```
void setOption( string $key, mixed $value = null )
```

**setOption()** 方法将 _key_ 指定的选项设置为 _value_ 指定的值。可设置的选项有两个：'limit_from' 和 'limit_count'，两者均为整数值。这些选项由 fetch 函数内部使用，并且可能依赖于后端数据库。在我对 _odbc_ 和 _mysql_ 数据库的测试中，我发现 'limit_from' 选项仅在与 _odbc_ 配合时才能正确工作。

> 由于这些选项的实用性值得怀疑，我建议对使用这些选项的任何应用程序进行彻底测试，并且如果您的应用程序的目标是数据库可移植性，建议您避免使用这些选项。

不返回任何值。

### DB_result::fetchRow

```
mixed fetchRow( int $fetchmode = DB_FETCHMODE_DEFAULT, int $rownum = NULL )
```

**fetchRow()** 方法是实际将一行数据检索到结果变量中的主要方法。在内部，**fetchRow()** 方法调用 **fetchInto()** 来执行实际数据库级别的数据检索。

_fetchmode_ 参数是预定义值之一：DB_FETCHMODE_ORDERED、DB_FETCHMODE_ASSOC 或 DB_FETCHMODE_OBJECT。有关 _fetchmode_ 参数的详细信息，请参阅第 52 页 **DB_common::setFetchmode()** 的文档。*rownum* 参数指定要检索的数据行。

与 *setfetchmode* 参数相关的用法示例见第 53 页的代码清单 21、第 55 页的代码清单 22 和第 56 页的代码清单 23。

代码清单 56 中的示例展示了使用 *rownum* 参数的效果。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $sSQL = "select first_name, last_name from Employees";
        $oRows = $oDB->query( $sSQL );
        if ( ! DB::isError( $oRows ) )
        {
            while ( $aRow = $oRows->fetchRow() )
            {
                print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
            }
            print( '<br>By rownum:<br><br>' );
            // now try to print rows 1, 3, 5 and 7
            $aRow = $oRows->fetchRow( DB_FETCHMODE_ASSOC,
            1 );
            print( $aRow['first_name'] . ' ' .
            $aRow['last_name'] . '<br>' );
            $aRow = $oRows->fetchRow( DB_FETCHMODE_ASSOC,
            3 );
            print( $aRow['first_name'] . ' ' .
            $aRow['last_name'] . '<br>' );
            $aRow = $oRows->fetchRow( DB_FETCHMODE_ASSOC,
            5 );
            print( $aRow['first_name'] . ' ' .
            $aRow['last_name'] . '<br>' );
            $aRow = $oRows->fetchRow( DB_FETCHMODE_ASSOC,
            7 );
            print( $aRow['first_name'] . ' ' .
            $aRow['last_name'] . '<br>' );

            $oRows->free();
        }
        $oDB->disconnect();
    }
?>
```

### DB_result::fetchInto

```
mixed fetchInto( mixed $arr, integer $fetchmode = DB_FETCHMODE_DEFAULT, integer $rownum = null )
```

fetchInto() 方法是 fetchRow() 使用的内部方法。虽然 fetchInto() 被列为公共方法，但我找不到任何令人信服的理由来建议您使用它而不是 fetchRow() 方法。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $sSQL = "select first_name, last_name from Employees";
        $oRows = $oDB->query( $sSQL );
        if ( !DB::isError( $oRows ) )
        {
            while ( $oRows->fetchInto( $aRow ) )
            {
                print( $aRow['first_name'] . ' ' .
                    $aRow['last_name'] . '<br>' );
            }
            print( '<br>By rownum:<br><br>' );
            // now try to print rows 1, 3, 5 and 7
            $oRows->fetchInto( $aRow, DB_FETCHMODE_ASSOC,
                1 );
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
            $oRows->fetchInto( $aRow, DB_FETCHMODE_ASSOC,
                3 );
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
            $oRows->fetchInto( $aRow, DB_FETCHMODE_ASSOC,
                5 );
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );
            $oRows->fetchInto( $aRow, DB_FETCHMODE_ASSOC,
                7 );
            print( $aRow['first_name'] . ' ' .
                $aRow['last_name'] . '<br>' );

            $oRows->free();
        }
        $oDB->disconnect();
    }
?>
```

#### 代码清单 57：使用 fetchInto()。



The example in Code Listing 57 is the same as Code Listing 56 but uses **fetchInto()** rather than **fetchRow()**. The output is shown in Output 31. The one notable difference in the output is that the last line seems to indicate that there is data in the row indexed by *rownum* 7. However, the output is generated because the argument passed in line 26 of the code ($aRow) is already set to a value because of its use on line 24.

> This is an important difference between **fetchRow()** and **fetchInto()** that you must consider if you choose to use the **fetchInto()** method. Always clear the variable you pass as the first parameter to **fetchInto()** or you may end up with residual data.

```
1 Blake Schwendiman
2 Jeffrey Cox
3 Kate McNulty
4 Ryan Schwendiman
5 Scott Schwendiman
6 Taylor Schwendiman
7
8 By rownum:
9
10 Jeffrey Cox
11 Ryan Schwendiman
12 Taylor Schwendiman
13 Taylor Schwendiman
```

输出 31：fetchInto 示例的结果（代码清单 57）。

- 返回 null 或 DB_OK。

### DB_result::numCols

```
mixed numCols( void )
```

使用 **numCols()** 方法返回结果集中的列数。代码清单 58 在第 117 页给出了一个使用示例。

### DB_result::tableInfo

- `mixed tableInfo( mixed $mode = null )`

**tableInfo()** 方法返回有关结果对象的数据库结构元数据。**DB_common::tableInfo()** 的讨论中在第 102 页给出了一个使用示例。

代码清单 58 中显示的示例是一个更通用的示例，展示了 **tableInfo()** 元数据如何在实际应用中被使用。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );

    function dbResultToTable( $oDBResult )
    {
        $numCols = $oDBResult->numCols();

        $aMetaData = $oDBResult->tableInfo();
        print( '<table border="1">' );

        // print header row
        print( '<tr>' );
        for ( $iIndex = 0; $iIndex < $numCols; $iIndex++ )
        {
            print( '<td>' . $aMetaData[$iIndex]['name'] . '</td>' );
        }
        print( '</tr>' );

        // now print all data rows
        while ( $oData = $oDBResult->fetchRow() )
        {
            print( '<tr>' );
            for ( $iIndex = 0; $iIndex < $numCols; $iIndex++ )
            {
                print( '<td>' . $oData[$iIndex] . '</td>' );
            }
            print( '</tr>' );
        }

        print( '</table>' );
    }

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oResult = $oDB->query( 'select * from Employees' );
        if ( !DB::isError( $oResult ) )
        {
            dbResultToTable( $oResult );
        }
        $oDB->disconnect();
    }
?>
```

代码清单 58：使用 tableInfo()。

示例代码使用 **tableInfo()** 和 **numCols()** 将任意通用的 DB_result 转换为 HTML 表格。图 5 中的图像显示了此示例的输出。

![](img/73cfc83029178a27381cd5f89348f7bf_126_0.png)

图 5：代码清单 58 的基于浏览器的输出。

*mode* 参数可以是 `DB_TABLEINFO_ORDER`、`DB_TABLEINFO_ORDERTABLE` 或 `DB_TABLEINFO_FULL` 中的一个。最后一个值 `DB_TABLEINFO_FULL` 是前两个值的组合。*mode* 参数表示该方法应在结果数组中提供其他相关数据。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $oResult = $oDB->query( 'select Employees.last_name, Departments.name from Employees, Departments where ( Employees.dept_id = Departments.id )' );
        if ( !DB::isError( $oResult ) )
        {
            print( 'tableInfo: <br>' );
            $aMetaData = $oResult->tableInfo();
            print( '<pre>' );
            var_dump( $aMetaData );
            print( '</pre>' );

            print( 'tableInfo - DB_TABLEINFO_ORDER: <br>' );
            $aMetaData = $oResult->tableInfo(DB_TABLEINFO_ORDER);
            print( '<pre>' );
            var_dump( $aMetaData );
            print( '</pre>' );

            print( 'tableInfo - DB_TABLEINFO_ORDERTABLE: <br>' );
            $aMetaData = $oResult->tableInfo(DB_TABLEINFO_ORDERTABLE);
            print( '<pre>' );
            var_dump( $aMetaData );
            print( '</pre>' );

            print( 'tableInfo - DB_TABLEINFO_FULL: <br>' );
            $aMetaData = $oResult->tableInfo(DB_TABLEINFO_FULL);
            print( '<pre>' );
            var_dump( $aMetaData );
            print( '</pre>' );
        }
        $oDB->disconnect();
    }
?>
```

**代码清单 59：tableInfo() 方法的 *mode* 参数。**

代码清单 59 中的示例展示了可与 **tableInfo()** 方法一起使用的各种 *mode* 值。输出 32 中显示了此示例的输出。部分输出文本已被省略以减小其大小。

```text
tableInfo:

array(2) {
  [0]=>
  array(5) {
    ["table"]=>
    string(9) "Employees"
    ["name"]=>
    string(9) "last_name"
    ["type"]=>
    string(6) "string"
    ["len"]=>
    int(50)
    ["flags"]=>
    string(8) "not_null"
  }
  [1]=>
  array(5) {
    ["table"]=>
    string(11) "Departments"
    ["name"]=>
    string(4) "name"
    ["type"]=>
    string(6) "string"
    ["len"]=>
    int(50)
    ["flags"]=>
    string(8) "not_null"
  }
}

tableInfo = DB_TABLEINFO_ORDER:

array(4) {
  ["num_fields"]=>
  int(2)
  ["order"]=>
  array(2) {
    ["last_name"]=>
    int(0)
    ["name"]=>
    int(1)
  }
  * also contains all of lines 4 - 29 above *
}

tableInfo = DB_TABLEINFO_ORDERTABLE:

array(4) {
  ["num_fields"]=>
  int(2)
  ["orderable"]=>
  array(2) {
    ["Employees"]=>
    array(1) {
      ["last_name"]=>
      int(0)
    }
    ["Departments"]=>
    array(1) {
      ["name"]=>
      int(1)
    }
  }
  * also contains all of lines 4 - 29 above *
}

tableInfo = DB_TABLEINFO_FULL:

array(5) {
  ["num_fields"]=>
  int(2)
  ["order"]=>
  array(2) {
    ["last_name"]=>
    int(0)
    ["name"]=>
    int(1)
  }
  ["orderable"]=>
  array(2) {
    ["Employees"]=>
    array(1) {
      ["last_name"]=>
      int(0)
    }
    ["Departments"]=>
    array(1) {
      ["name"]=>
      int(1)
    }
  }
  * also contains all of lines 4 - 29 above *
}
```

输出 32：tableInfo() 方法的 mode 参数。

**tableInfo()** 方法仅由 *fbsql*、*ibase*、*mssql*、*oci8* 和 *pgsql* 数据库支持。同样，如果你的开发目标是数据库可移植性，就不应依赖此方法。

- 返回数据库特定的结果数组或 DB_Error 对象。

### DB_result::getRowCounter

- `mixed getRowCounter( void )`

**getRowCounter()** 方法旨在从结果集中检索当前行号。此方法依赖于第 11 页 **setOptions()** 方法中描述的 `limit_from` 和 `limit_count` 选项。

> 由于该部分提到的注意事项，我也建议不要依赖 **getRowCounter()** 方法。

在应用程序中模拟行计数器非常简单，因此我建议基于特定应用程序的需求采用应用程序特定的行编号系统。

- 返回整数行号或 NULL。

## Class DB_Error

DB_Error 类是 PEAR_Error 的子类，而 PEAR_Error 是 PEAR 类中通用的错误对象。对 PEAR_Error 类的完整描述超出了本文档的范围，但代码清单 20 在第 52 页举例说明了使用 DB_Error 的良好示例。

## Class DB_Warning

DB_Warning 类已被弃用，并且不再在 PEAR::DB 中使用。

## Class DB_storage

DB_storage 类在其他地方似乎完全没有文档记录，但由于它仍然作为 PEAR::DB 安装的一部分提供，我将在此介绍它。DB_storage 的概念是为数据库中的一行数据提供完全面向对象的接口。

代码清单 60 显示了 DB_storage 的基本用法以及它与其他 PEAR::DB 类的关系，而这些类已在本书中介绍过。

```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
    // create a new DB_storage object against the Employees table
    $oStorage = new DB_storage( 'Employees', 'id', $oDB );

    // initialize this object with the Employee whose id = 1
    $oStorage->setup( 1 );

    // dump this object to the browser
    print( 'initial data<br>' );
    $oStorage->dump();

    // change the phone extension of this object
    $oStorage->set( 'phone_ext', 2204 );

    // save the changes to the database
    $oStorage->store();

    // dump this object to the browser
    print( '<br>current data<br>' );
    $oStorage->dump();

    $oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
```


```php
<?php
?>
```

### 代码清单 60：DB_storage 类概述。

代码清单60的输出如图6所示。从示例中可以清楚地看到，DB_storage 类仅仅为数据库中的单行数据提供了一个基本的面向对象（OO）包装。

DB_storage 构造函数有一个可选的第四个参数，用于指定数据验证回调函数。其使用示例见第132页的代码清单64。

![](img/73cfc83029178a27381cd5f89348f7bf_132_0.png)

### 图 6：DB_storage 概述代码的输出。

DB_storage 类为开发高度面向对象的数据库应用程序提供了框架。虽然我个人提倡 OO 编程，但我不确信在 PHP 应用中使用 DB_storage 相比使用 PEAR::DB 获取方法默认提供的基于数组的数据能带来多大好处。在生命周期较长的大型应用中，对底层数据操作采用 OO 方式可能更可取，但许多（如果不是大多数）PHP 应用都是短命且无状态的，因此这种方法可能有些过头。

无论如何，DB_storage 类的方法列于表9中，下面将详细介绍。

| 方法 | 描述 |
|---|---|
| _makeWhere() | 私有方法，用于生成 WHERE 子句来定位表示该对象的表中的记录。 |
| setup() | 从配置的表中初始化 DB_storage 对象。 |
| insert() | 为该对象在表中创建新的空行。 |
| toString() | 输出此 DB_storage 对象的简单描述。 |
| dump() | 将此对象的内容输出到标准输出。 |
| create() | 用于创建新 DB_storage 对象的静态方法。 |
| set() | 修改此对象的属性。 |
| get() | 获取此对象的属性。 |
| store() | 将此对象的更改保存到数据库。 |
| `remove()` | 从数据库中删除与此对象关联的数据行。 |

表9：DB_storage 类方法

### DB_storage::_makeWhere

❖ `string _makeWhere( mixed $keyval = null )`

这是一个私有方法。如果你正在使用 DB_storage，请不要使用此方法。

- ➤ 返回一个字符串。

### DB_storage::setup

❖ `mixed setup( mixed $keyval )`

**setup()** 方法用于根据 *keyval* 中键所代表的行的数据来配置当前对象。如果表的主键是单列，*keyval* 的值是一个原子值；如果主键是多列，则是一个值数组。

```php
<?php
    error_reporting( E_ALL );
    require_once ( 'DB.php' );
    require_once ( 'DB/storage.php' );

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( ! DB::isConnection( $oDB ) )
    {
        // create a new DB_storage object against the
        // Employees table
        $oEmp = new DB_storage( 'Employees', 'id', $oDB
        );

        // create a new DB_storage object against the
        // EmployeesToDepartments table
        $oEmpToDept = new DB_storage(
            'EmployeesToDepartments', array( 'emp_id',
            'dept_id' ), $oDB );
```

## TransAlchemy：数字时代中一种新颖的 AI 驱动的个性化推荐框架

Alexander T. Maxwell, Sophia R. Chen, Daniel L. Wright, Emily R. Carter

美国加利福尼亚州斯坦福市斯坦福大学计算机科学系，邮编 94305

## **摘要**

数字平台的快速激增产生了海量的用户生成内容，使得个性化推荐变得不可或缺。TransAlchemy 是一种新颖的 AI 驱动框架，它将大语言模型与协同过滤和知识图相结合，以捕捉细微的用户偏好。通过联合建模语义和行为信号，该框架能够产生准确、多样且可解释的推荐。在公共基准上的大量实验表明，它相对于最先进的基线方法有持续改进。

索引词——推荐系统、大语言模型、知识图、可解释 AI、个性化

## 1 引言

数字时代从根本上改变了用户与信息和服务交互的方式。然而，海量的可用选项常常导致信息过载，使用户难以发现相关内容。传统的推荐模型主要依赖历史用户-物品交互，因此难以理解语义偏好或处理冷启动用户。在本文中，我们提出了 TransAlchemy，一个将大语言模型的推理能力与结构化知识相结合的框架，以实现个性化和可解释的推荐。

## 2 相关工作

先前的研究通过协同过滤、基于内容的过滤和混合方法探索了推荐系统。最近，大语言模型被用于通过编码物品描述和用户偏好来提高推荐质量。知识图也被用于引入用户与物品之间的语义关系。TransAlchemy 在这些方向上进一步发展，将大语言模型表示与基于图的推理统一到一个端到端框架中。

```php
function setup($keyval)
{
    $qval = $this->_dbh->quote($keyval);
    ...
}
```

如果你想使用这个类，你可能需要注释掉 setup() 方法的第一行。经调查，该行的返回值 *qval* 在方法内部并未使用，实际键值的引用是在方法后面进行的。

此错误已报告给 PEAR::DB 维护人员。

成功时返回 DB_OK，失败时返回 DB_Error。

### DB_storage::insert

♦ *mixed insert( mixed $newpk )*

insert() 方法类似于 INSERT SQL 语句——使用 *newpk* 指定的主键信息在数据库中创建新行。

代码清单62中的代码演示了如何使用 **insert()** 方法插入新的数据库记录。执行后，如果第13行指定的键没有发生主键冲突，数据库中将存在一个新行。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );
    require_once( 'DB/storage.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
        if ( DB::isConnection( $oDB ) )
        {
```

## 全面的 PHP PEAR::DB

```php
// create a new DB storage object against the
// Employees table
$oEmp = new DB_storage( 'Employees', 'id', $oDB
);

// create a new Employee with ID = 50
$result = $oEmp->insert( 50 );

if ( ! DB::isError( $result ) )
{
    // set other Employee information with set() method
        $oEmp->set( 'first_name', 'Jim' );
        $oEmp->set( 'last_name', 'Murphy' );
        $oEmp->set( 'mgr_id', 1 );
        $oEmp->set( 'dept_id', 1 );

    // save this object to the database
    $oEmp->store();
}
else
{
    var_dump( $result );
}

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

**代码清单62：使用 insert()。**

- ➜ 失败时返回 DB_Error 对象，成功时返回 NULL。

### DB_storage::toString

*string toString( void )*

**toString()** 方法返回一个描述 DB_storage 对象的简短字符串。

```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );
    require_once( 'DB/storage.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( ! DB::isConnection( $oDB ) )
    {
```

```php
// create a new DB storage object against the
// Employees table
$oEmp = new DB_storage( 'Employees', 'id', $oDB );

// create a new Employee with ID == 50
$result = $oEmp->setup( 50 );

if ( !DB::isError( $result ) )
{
    print( $oEmp->toString() );
}
else
{
    var_dump( $result );
}

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

**代码清单63：使用 toString()。**

代码清单63的输出如输出34所示。

```text
db_storage (table=Employees, keycolumn=id,
dbh=>db_mysql: (phptype=mysql, dbsyntax=mysql)
[connected] [loaded, key=50]
```

**输出34：DB_storage::toString() 的输出。**

- - 返回一个字符串。

### DB_storage::dump

- `void dump( void )`

**dump()** 方法将 DB_storage 对象的属性输出到标准输出。当 PHP 在 Web 服务器环境中运行时，标准输出就是 Web 浏览器输出的 HTML 流。




有关用法示例，请参见第 123 页的代码清单 60。

- 不返回任何值，但会在标准输出上产生输出。

### DB_storage::create

```
object create( string $table, array $data )
```

**create()** 方法的内部文档指出，**create()** 是一个用于创建新的 DB_storage 对象的静态方法。

然而，根据我对 **create()** 方法内部代码的理解，该方法似乎不能以静态方式使用（其中引用了 *$this*）。此外，即使*能够*创建对象，它也没有被充分初始化，无法使用。

> > 我将通过论坛或站内信接受关于此方法使用的评论，地址为 **http://www.intechra.net/**。否则，我建议完全避免使用此方法。

### DB_storage::set

```
mixed set( string $property, mixed $newvalue )
```

**set()** 方法是更新 DB_storage 对象属性的主要机制，而属性更新又会相应地更新该对象所代表的数据库行的列。

通常应调用 `store()` 方法来实现对数据库的任何更改，但需要注意的是，如果对象有任何更改，DB_storage 的析构函数会调用 `store()` 过程。

- 成功时返回 TRUE，失败时返回 DB_Error 对象。

### DB_storage::get

`mixed get( string $property )`

`get()` 方法获取对象属性的当前值。如果指定的属性不存在，`get()` 返回 NULL。

```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

function MyValidator( $sTable, $sProperty,
    $mNewValue, $mOldValue, $oEmp )
{
    print ( "MyValidator( $sTable, $sProperty,
        $mNewValue, $mOldValue, $oEmp ) <br>" );

    if ( ( $sTable == "Employees" ) && ( $sProperty
        == 'phone_ext' ) )
    {
        // valid phone extensions range from 200 to
        // 4999
        if ( ( $mNewValue >= 5000 ) || ( $mNewValue <
            200 ) )
        {
            return false;
        }
    }
    return true;
}

$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    // create a new DB_storage object against the
    // Employees table
    $oEmp = new DB_storage( 'Employees', 'id',
        $oDB, 'MyValidator' );
}
```

```php
// load the employee with ID = 1
$oEmp->setup( 1 );
$oEmp->dump();

// get a property
$iMgrId = $oEmp->get( 'mgr_id' );

if ( $iMgrId == 3 )
{
    // set some properties
    $oEmp->set( 'first_name', 'Joe' );
    $oEmp->set( 'phone_ext', '9987' );

    $oEmp->store();
}
$oEmp->dump();

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

代码清单 64：使用 set() 和 get()。

代码清单 64 中的示例说明了 set() 和 get() 的使用。这些方法非常简单，易于理解。

代码清单 64 还演示了如何使用自定义验证回调函数来验证通过 set() 方法提供的数据。DB_storage 构造函数的最后一个参数（第 26 行）指定了数据验证的回调函数。在本例中，它只是一个名为 MyValidator 的函数。它也可以是类的方法，在这种情况下，与 PHP 中的任何回调函数一样，它将被指定为一个包含类名和方法名作为元素的数组。

在示例中，验证函数会打印一行显示其参数。它还会验证对 phone_ext 属性的任何拟议更改，以确保新值处于可接受的范围内。

remove() 方法实际上会从数据库中删除 DB_storage 对象所代表的数据行。

```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
    // create a new DB_storage object against the Employees table
    $aEmp = new DB_storage( 'Employees', 'id', $oDB
);

$aEmp->setup( 50 );
$aEmp->remove();

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

代码清单 65：使用 remove()。

代码清单 65 中的示例展示了如何使用 remove() 删除数据库中的一行。

- 返回 DB_OK 或 DB_Error 对象。

## 数据库支持

PEAR::DB 支持第 19 页表 1 中列出的数据库。本书的这一部分旨在展示如何通过仅更改脚本中的 DSN，使用单个脚本访问多个数据库后端。

示例脚本假设了几个因素。首先，假设数据库正在运行，并且 PHP 已配置了适当的代码/驱动程序来访问数据库。其次，假设 DSN 中指定的用户具有适当的数据库权限来执行脚本中的任务。第三，假设目标数据库服务器上存在一个名为 *book_test* 的数据库。本书这一部分的主要目的是提供有关每个受支持数据库的非常高层面的信息，而不是介绍如何安装和配置每个数据库。适当时，我可能会提到一些在测试中发现的有趣的配置或设置信息。在大多数情况下，本书是在 Windows 上运行 PHP 开发的，因此很少有特定于数据库的信息会基于 Linux（或其他类 Unix）操作系统。

测试程序分为三个文件。第一个文件是代码清单 66 中显示的主脚本。第二个文件是包含文件 *err_popup.php*，它只是第 52 页代码清单 20 中示例的函数。这些函数会弹出一个单独的浏览器窗口，并显示 DB_Error 对象信息。第三个文件（*db_specific.php*）是一组特定于数据库的字符串，如代码清单 67 所示。

任何读者都应该清楚，并非所有 SQL 服务器都提供相同的功能，甚至 SQL 语句的语法也不尽相同。*db_specific.php* 文件包含创建 *Employees* 表的 SQL 语句，因为不同数据库服务器之间的建表语句通常差异很大。*db_specific.php* 文件中存储的其他信息还包括 DSN 信息和用于显示的数据库服务器全名。

代码清单 66 各个部分的讨论紧接在清单本身下方给出。

```php
<?php
$aInsertQueries[] = "INSERT INTO Employees VALUES
(1, 'Schwendiman', 'Joe', '2204', 3, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(2, 'Cox', 'Jeffrey', '225', 0, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(3, 'McNulty', 'Kate', '214', 3, 2)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(4, 'Schwendiman', 'Ryan', '128', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(51, 'Murphy', 'Jim', '', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(58, 'Schwendiman', 'Scott', '234', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(59, 'Schwendiman', 'Taylor', '323', 1, 1)";

$aSelectQueries[] = "SELECT * from Employees
order by last_name, first_name";
$aSelectQueries[] = "SELECT * from Employees
where ( mgr_id = 3 )";
$aSelectQueries[] = "SELECT * from Employees
where ( dept_id = 2 )";

$aUpdateQueries[] = "UPDATE Employees set mgr_id
= 2 where ( mgr_id = 3 )";
$aUpdateQueries[] = "UPDATE Employees set dept_id
= 3 where ( mgr_id = 2 )";

$aDeleteQueries[] = "DELETE FROM Employees where
( phone_ext < 300 )";
?>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0
Transitional//EN">

<html>
<head>
    <title>PEAR::DB General Test</title>
</head>

<body>

<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'err_popup.php' );
require_once( 'db_specific.php' );

$sDBType = 'mssql';

function DisplayHeader( $aRow )
{
    print( '<tr>' );
    print( '<td>&nbsp;</td>' );
    foreach ( $aRow as $aName => $aValue )
    {
```




### 代码清单 66：通用 PEAR::DB 测试脚本（主文件）。

```php
print( '<td>' . $aName . '</td>' );
}
print( '</tr>' );
}

function DisplayResults( $oResult )
{
    print( 'Number of rows in query result = <b>' .
$oResult->numRows() . '</b><br><br>' );

    if ( $oResult->numRows() > 0 )
    {
        print( '<table border="1" width="90%"
align="center">' );
        $iResultNum = 0;
        while ( $aRow = $oResult->fetchRow() )
        {
            if ( $iResultNum == 0 )
                DisplayHeader( $aRow );

            print( '<tr>' );
            print( '<td>' . $iResultNum . '</td>' );
            foreach ( $aRow as $aValue )
            {
                print( '<td>' . $aValue . '</td>' );
            }
            print( '</tr>' );
            $iResultNum++;
        }
        print( '</table><br>' );
    }
}

function DoSelectQueries( $oDB )
{
    global $aSelectQueries;

    foreach ( $aSelectQueries as $sSQL )
    {
        print( 'Executing query: <i>' . $sSQL .
        '</i><br><br>' );
        $result = $oDB->query( $sSQL );
        if ( !DB::isError( $result ) )
        {
            DisplayResults( $result );
            $result->free();
        }
        else
        {
            errorPopup( $result );
            exit;
        }
    }

    print( 'Running PEAR::DB test for database ' .
    $aDBPrettyNames[$sDBType] . '<br><br>' );

    $sDSN = $aDSNValues[$sDBType];
    $oDB = DB::connect( $sDSN, true );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

foreach ( $aUpdateQueries as $sSQL )
{
    $result = $oDB->query( $sSQL );
    if ( DB::isError( $result ) )
    {
        errorPopup( $result );
        exit;
    }
}
print( 'All update queries finished successfully.<br><br>' );

DoSelectQueries( $oDB );

foreach ( $aDeleteQueries as $sSQL )
{
    $result = $oDB->query( $sSQL );
    if ( DB::isError( $result ) )
    {
        errorPopup( $result );
        exit;
    }
}
print( 'All delete queries finished successfully.<br><br>' );

DoSelectQueries( $oDB );

$oDB->disconnect();
}
else
{
    errorPopup( $oDB );
}
?>
</body>
</html>
```

脚本的第 2 至 17 行设置了一些与具体数据库无关的 SQL 语句数组，这些数组将在脚本后面使用。

从第 95 行开始，脚本首先获取特定于数据库的 DSN，并尝试连接到数据库。如果连接成功，则将数据库对象的 fetchmode 设置为 DB_FETCHMODE_ASSOC。

接下来，在第 103 至 132 行中，脚本检索并显示数据库中当前的表列表。如果存在名为 *Employees* 的表，则将其删除。

然后，使用第 134 至 144 行中特定于数据库的创建 SQL 语句创建 *Employees* 表。接着在第 146 至 156 行中向表中添加数据行。

在第 158 行，调用了 **DoSelectQueries()** 函数。**DoSelectQueries()** 函数是此脚本内部的函数，它完成一些有趣的工作。该函数的源代码见第 74 至 93 行。对于 *$aSelectQueries* 数组中的每个 SQL 查询，会执行该查询，并将结果（如果不是错误）传递给 **DisplayResults()** 函数。**DisplayResults()** 函数显示结果集中的行数；如果行数大于 0，它会使用 **fetchRow()** 方法遍历结果。在循环的第一次迭代中，会调用 **DisplayHeader()** 函数，该函数以 HTML 表格形式显示结果集的列名。对于并非所有数据库后端都提供 **tableInfo()** 方法实现的问题，这是一个很好的变通方案。然后，随着 **fetchRow()** 循环继续，数据本身也会被显示出来。

在初始数据被填充并显示后，脚本接着在第 160 至 169 行运行一组更新查询。再次调用 **DoSelectQueries()** 函数来显示表中的数据。

最后，脚本在第 173 至 182 行运行一组删除查询，并再次显示结果。

### 代码清单 67：_db_specific.php_ 的源代码——数据库特定代码

```php
<?php
$aDBPrettyNames ['mssql'] = 'Microsoft SQL Server';
$aDSNValues ['mssql'] = 'mssql://user:pass@dbserver/book_test';
$aCreateTableCmds['mssql'] = array( 'CREATE TABLE [dbo].[Employees] ( [id] [int] NOT NULL , [last_name] [char] (50) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [first_name] [char] (50) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [phone_ext] [char] (5) COLLATE SQL_Latin1_General_CP1_CI_AS NULL , [mgr_id] [int] NULL , [dept_id] [int] NULL ) ON [PRIMARY]', 'ALTER TABLE [dbo].[Employees] WITH NOCHECK ADD CONSTRAINT [PK_Employees] PRIMARY KEY CLUSTERED ( [id] ) ON [PRIMARY] ');

$aDBPrettyNames ['mysql'] = 'MySQL';
$aDSNValues ['mysql'] = 'mysql://bt_user:bt_pass@207.44.182.3/book_test';
$aCreateTableCmds['mysql'][] = "CREATE TABLE Employees ( id int(11) NOT NULL default '0', last_name varchar(50) NOT NULL default '', first_name varchar(50) NOT NULL default '', phone_ext varchar(5) NOT NULL default '', mgr_id int(11) NOT NULL default '0', dept_id int(11) NOT NULL default '0', PRIMARY KEY (id), KEY mgr_id (mgr_id), KEY dept_id (dept_id) ) TYPE=InnoDB";

$aDBPrettyNames ['odbc'] = 'ODBC with Access DB';
$aDSNValues ['odbc'] = 'odbc:///book_test';
$aCreateTableCmds['odbc'][] = 'CREATE TABLE [Employees] ( [id] integer NOT NULL , [last_name] char(50) NULL, [first_name] char(50) NULL, [phone_ext] char(5) NULL, [mgr_id] integer NULL , [dept_id] integer NULL )';
$aCreateTableCmds['odbc'][] = 'ALTER TABLE [Employees] ADD CONSTRAINT [PK_Employees] PRIMARY KEY ( [id] )';

$aDBPrettyNames ['sqlite'] = 'SQLite';
$aDSNValues ['sqlite'] = 'sqlite:///c:/temp/PEAR/sqlite_employees.dat';
$aCreateTableCmds['sqlite'][] = 'CREATE TABLE Employees ( id [integer] NOT NULL PRIMARY KEY, last_name [char(50)], first_name [char(50)], phone_ext [char(5)], mgr_id [integer], dept_id [integer] )';

$aDBPrettyNames ['ibase'] = 'Borland Interbase';
$aDSNValues ['ibase'] = 'ibase://sysdba:masterkey@localhost/c:/temp/PEAR/book_test.gdb';
$aCreateTableCmds['ibase'][] = 'CREATE TABLE Employees ( id integer NOT NULL PRIMARY KEY, last_name char(50), first_name char(50), phone_ext char(5), mgr_id integer, dept_id integer )';

$aDBPrettyNames ['msql'] = 'Mini SQL';
$dbDSNValues['mysql'] = 'mysql://mysql.server.example.com/book_test';
$aCreateTableCmds['mysql'][] = 'CREATE TABLE
Employees ( id integer NOT NULL PRIMARY KEY,
last_name char(50), first_name char(50), phone_ext
char(5), mgr_id integer, dept_id integer )';

$dbDBPrettyNames['fbsql'] = 'FrontBase';
$dbDSNValues['fbsql'] =
'fbsql://bt_user@localhost/book_test';
$aCreateTableCmds['fbsql'][] = 'CREATE TABLE
Employees ( id integer NOT NULL PRIMARY KEY,
last_name char(50), first_name char(50), phone_ext
char(5), mgr_id integer, dept_id integer )';

$dbDBPrettyNames['ifx'] = 'Informix';
$dbDSNValues['ifx'] =
'ifx://informix:informix@localhost/book_test';
$aCreateTableCmds['ifx'][] = 'CREATE TABLE
Employees ( id integer NOT NULL PRIMARY KEY,
last_name char(50), first_name char(50), phone_ext
char(5), mgr_id integer, dept_id integer )';

$dbDBPrettyNames['pgsql'] = 'PostgreSQL';
$dbDSNValues['pgsql'] =
'pgsql://blake:password@pgsql.server.example.com/book_test';
$aCreateTableCmds['pgsql'][] = 'CREATE TABLE
Employees ( id integer NOT NULL PRIMARY KEY,
last_name char(50), first_name char(50), phone_ext
char(5), mgr_id integer, dept_id integer )';
?>
```

以下是该脚本针对 Microsoft SQL Server 数据库运行的输出。它代表了测试的基线输出。在下面的各数据库特定部分中，只会注明与基线的差异。

正在对数据库 Microsoft SQL Server 运行 PEAR::DB 测试

数据库中当前的表：

- 1. dtproperties
- 2. Employees

Employees 表已成功删除。

Employees 表已成功创建。

所有数据已成功插入。

正在执行查询：SELECT * from Employees order by last_name, first_name

查询结果中的行数 = 7

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 2 | Cox | Jeffrey | 225 | 0 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 3 | 2 |
| 2 | 51 | Murphy | Jim |  | 1 | 1 |
| 3 | 1 | Schwendiman | Joe | 2204 | 3 | 1 |
| 4 | 4 | Schwendiman | Ryan | 128 | 1 | 1 |
| 5 | 58 | Schwendiman | Scott | 234 | 1 | 1 |
| 6 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

正在执行查询：SELECT * from Employees where ( mgr_id = 3 )

查询结果中的行数 = 2

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 1 | Schwendiman | Joe | 2204 | 3 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 3 | 2 |

正在执行查询：SELECT * from Employees where ( dept_id = 2 )

查询结果中的行数 = 1

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 3 | McNulty | Kate | 214 | 3 | 2 |




|   |   | y |   |   |   |   |
|---|---|---|---|---|---|---|

所有更新查询均成功完成。

执行查询：`SELECT * from Employees\norder by last_name, first_name`

查询结果中的行数 = 7

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 2 | Cox | Jeffrey | 225 | 0 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 2 | 3 |
| 2 | 51 | Murphy | Jim |   | 1 | 1 |
| 3 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 4 | 4 | Schwendiman | Ryan | 128 | 1 | 1 |
| 5 | 58 | Schwendiman | Scott | 234 | 1 | 1 |
| 6 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

执行查询：`SELECT * from Employees\nwhere ( mgr_id = 3 )`

查询结果中的行数 = 0

执行查询：`SELECT * from Employees\nwhere ( dept_id = 2 )`

查询结果中的行数 = 0

所有删除查询均成功完成。

执行查询：`SELECT * from Employees\norder by last_name, first_name`

查询结果中的行数 = 2

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 1 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

执行查询：SELECT * from Employees
where ( mgr_id = 3 )

查询结果中的行数 = 0

执行查询：SELECT * from Employees
where ( dept_id = 2 )

查询结果中的行数 = 0

上面显示的输出已略作重新格式化以提高可读性，但提供了所需的信息。

### MySQL

MySQL 很可能是 PHP 程序员使用最广泛的数据库。PHP 4 的所有版本均启用了对 MySQL 数据库的内置支持。对于 Windows 或类 Unix 平台，MySQL 支持通常默认开启。

本书大多数示例中都说明了 MySQL 的 DSN 格式。MySQL 数据库最常见的 DSN 格式可能为：

```
phptype://username:password@hostspec/database_name
```

*hostspec* 部分可以仅包含主机名或 IP 地址，或采用 *host:port* 格式的主机规范。

上面显示的通用测试脚本在我的 MySQL 安装（*MySQL 4.0.15-Max*）上运行没有任何问题。

### PostgreSQL

PHP 和 PEAR::DB 对 PostgreSQL 的支持非常出色。测试示例在 PostgreSQL 上仅作了微小修改后即可运行。“DROP TABLE” 命令需要针对小写表名进行修改。再次说明，我对该数据库缺乏经验可能是问题的一部分。无论如何，有经验的 PostgreSQL 用户会了解数据库的特殊情况并避免此类错误。

### Borland Interbase

Borland Interbase 在 PHP 中总体上得到支持，但我无法成功运行 PEAR 测试。

首先，**getTables()** 方法在 Interbase 的 PEAR::DB 实现中不受支持，因此代码必须重写。有一個示例脚本（随源代码提供，网址为 **http://www.intechra.net/**）名为 _code_listing_67.php_，它移除了与 **getTables()** 方法相关的行。

在使脚本通过初始的 **getTables()** 失败后，我在 select SQL 语句中遇到了一个一致的错误：

```
Running PEAR::DB test for database Borland
Interbase

Employees table successfully dropped.

Employees table successfully created.
```

7 所有数据插入成功。
9 执行查询：SELECT * from Employees order by
last_name, first_name
10

11 查询结果中的行数 = Object
13

14 执行查询：SELECT * from Employees where (
mgr_id = 3 )
15

16 PHP 遇到访问冲突 77F83AED

第 16 行的错误在每次测试运行中都会出现。出现错误后，有必要停止并重新启动 IIS。

在不妄下结论的情况下，我必须假设我的配置不适用于使用 PHP 与 Interbase。假设 PHP + Interbase 配置正常运行，我还必须假设上面的 PEAR::DB 测试将能正常工作，除了缺少 getTables() 的实现。

### Mini SQL

显然我不够聪明，无法让 Mini SQL 正常工作。我完全无法使用 Windows PHP 安装连接到基于 Linux 的远程 Mini SQL 服务器。我按照 http://www.php.net/msql 页面上的每一步操作，但均无济于事。当我改用 Linux 上的 PHP + Mini SQL 时，最终能够从 PHP 建立连接。然而，测试代码在不同的地方失败（每次运行似乎都在不同的位置失败）。

Mini SQL 主页上的许多链接已损坏（尤其是与 Windows 支持相关的链接），因此我只能对项目的总体状态做出一些假设。

我建议寻找小型数据库后端的 PHP 开发者可以试试 SQLite。我在设置它时没有任何问题，PEAR::DB 测试代码也没有任何问题。

### Microsoft SQL Server

在基于 Windows 的 PHP 安装中，Microsoft SQL Server 极其简单易于设置。为了测试，我只是安装了 PHP 网站上提供的最新 PHP 二进制文件。在以最基本级别配置 PHP 开始测试后，有必要通过编辑 *php.ini* 文件来加载 MS SQL 扩展。

只需在配置文件中删除行 *extension=php_mssql.dll* 前面的分号注释字符即可生效。

在非 Windows PHP 中配置以使用 MS SQL 数据库稍微复杂一些，但仍然可行。有关设置说明，请参阅 **http://www.php.net/mssql**。

运行后，PHP 与 MS SQL Server 配合良好，且 PEAR::DB 实现非常完整。测试脚本对 MS SQL Server 完美运行，经测试的版本为 MS SQL Server 2000（版本 8.00.760 SP3）。

### Oracle 7/8/8i

`php_fsql.dll` and configure PHP via the `php.ini` file to use FrontBase. 通用的 PEAR::DB 测试脚本第一次尝试时运行没有任何问题。

考虑到我之前没有任何 FrontBase 使用经验，这非常令人鼓舞。如果您考虑在 PHP 应用中使用 FrontBase，可以获得开发许可证，以便在部署前先测试应用，而无需承担财务承诺。

### SQLite

SQLite 是一个有趣的数据库引擎，根据最近的在线资料，从 PHP 5 版本开始将默认随 PHP 一起发布。SQLite 是一个基于文件的数据库引擎，正如其名称所示，非常轻量级。DSN 规范类似于：

```
sqlite:///c:/temp/PEAR/sqlite_employees.dat
```

上述 DSN 在 Windows 上有效，但只需适当更新路径格式即可简单地适配到其他操作系统上。

在基于 Windows 的 PHP 上安装 SQLite 轻而易举。只需从 **http://www.php.net/sqlite** 下载可用的 `php_sqlite.dll` 文件，然后从 SQLite 网站 **http://www.sqlite.org/** 下载实际的 SQLite 引擎 DLL（`sqlite.dll`）。

将 `sqlite.dll` 文件放置在 Windows 的搜索路径中（如 `system32` 目录），然后将 `php_sqlite.dll` 复制到 PHP 扩展目录。然后通过在 `php.ini` 文件中添加 `extension=php_sqlite.dll` 来启用 SQLite。

测试脚本运行没有任何错误或警告。
然而，生成了一条通知：

```
Notice: Undefined index: mode in C:\\temp\\PEAR\\php-4.3.4-Win32\\pear\\DB\\sqlite.php on line 185
```

此警告基于这样一个事实：出于某种原因，SQLite 数据库对象期望解析后的 DSN 具有名为 *mode* 的成员，而该成员不存在。也许这将在 PEAR::DB 的未来版本中添加。无论如何，如果您在典型配置的环境中运行，此通知将不会显示。然而，如果您在类 Unix 操作系统上运行 SQLite，*mode* 值指定文件模式（例如 0644），您可能希望指定它。如果您这样做，则需要编辑 DB_sqlite 实现或使用基于数组的 DSN 并直接提供 *mode* 键。

从 PHP 的角度来看，PEAR::DB 中对 SQLite 的支持对于这样一个新数据库来说出人意料地完整。在受限的托管环境中或不需要完整数据库后端的情况下，使用 SQLite 可能更受青睐。SQLite 的开销非常小，且 SQL 语言支持非常完整。

### dBase

PEAR::DB 中对 dBase 的支持极其有限。示例代码无法与 dbase 配合使用，因为接口的真正支持非常少。在 PHP 网站上稍微查看后，甚至 dBase 本身也未得到完全支持：

不支持索引或备注字段。也不支持锁定，两个并发




## 结论

PEAR::DB 是一个功能强大的面向对象抽象层，由 PHP 核心开发团队成员支持和维护。PEAR::DB 是任何支持数据库的 PHP 应用的正确工具，无论其规模大小。使用 PEAR::DB 的主要原因是通过代码复用实现快速（或更快速）应用开发和应用可维护性。虽然 PEAR::DB 可以实现数据库可移植性，但大多数中大型应用将会依赖底层数据库，以至于很可能会使用特定于引擎的 SQL。

随着 PHP 的成熟，PEAR::DB 也将随之成熟。认真考虑应用长期可维护性的开发者，应该认真考虑将 PEAR::DB 作为其数据库抽象层。

## 附录 A：图表清单

### 表格

| 项目 | 页码 |
| --- | --- |
| 表 1：PEAR::DB 支持的数据库 | 19 |
| 表 2：数据库类的默认选项 | 20 |
| 表 3：DB 类方法 | 30 |
| 表 4：DSN 数组元素 | 36 |
| 表 5：代码清单 18 的结果（为本书重新格式化） | 46 |
| 表 6：query() 方法中使用的占位符 | 60 |
| 表 7：每个数据库后端在 getSpecialQuery 中支持的类型 | 107 |
| 表 8：DB_result 类方法 | 109 |
| 表 9：DB_storage 类方法 | 125 |

### 图

| 项目 | 页码 |
| --- | --- |
| 图 1：系统属性页面 | 4 |
| 图 2：环境变量对话框 | 5 |
| 图 3：将路径添加到 PEAR.BAT 文件 | 5 |
| 图 4：ErrorPopup 函数创建的弹出窗口 | 52 |
| 图 5：代码清单 58 的基于浏览器的输出 | 117 |
| 图 6：DB_storage 概览代码的输出 | 124 |

### 代码清单

| 项目 | 页码 |
| --- | --- |
| 代码清单 1：创建示例数据库的 MySQL 语句 | 10 |
| 代码清单 2：示例员工数据库的 SQL 查询 | 11 |
| 代码清单 3：过程式数据库访问 | 12 |
| 代码清单 4：PEAR::DB 数据库访问 | 13 |
| 代码清单 5：PEAR::DB 数据库访问（第二次尝试） | 16 |
| 代码清单 6：完整 DSN 格式 | 18 |
| 代码清单 7：DSN 格式的变体 | 18 |
| 代码清单 8：DB::connect() 示例 | 22 |
| 代码清单 9：使用序列 | 23 |
| 代码清单 10：自定义序列表名称格式 | 25 |
| 代码清单 11：使用 prepare() 和 execute() 概述 | 27 |
| 代码清单 12：使用 autoPrepare | 28 |
| 代码清单 13：DB::factory | 32 |
| 代码清单 14：DB::connect 的几个示例 | 34 |
| 代码清单 15：DB::assertExtension 示例 | 37 |
| 代码清单 16：DB_common::toString 示例 | 42 |
| 代码清单 17：DB_common::quote 示例 | 43 |
| 代码清单 18：DB_common::provides 示例 | 45 |
| 代码清单 19：DB_common::errorCode、DB_common::errorMessage、DB_common::errorNative() 示例 | 47 |
| 代码清单 20：使用 DB_Error | 52 |
| 代码清单 21：DB_common::setFetchMode - DB_FETCHMODE_ORDERED（默认） | 53 |
| 代码清单 22：DB_common::setFetchMode - DB_FETCHMODE_ASSOC | 55 |
| 代码清单 23：DB_common::setFetchMode - DB_FETCHMODE_OBJECT | 56 |
| 代码清单 24：DB_common::setFetchMode - 使用 object_class 参数的 DB_FETCHMODE_OBJECT | 58 |
| 代码清单 25：使用 prepare() -- 简单示例 | 61 |
| 代码清单 26：创建 uploadedfiles 表的 SQL 语句 | 62 |
| 代码清单 27：使用 '&' 占位符的 prepare() 方法 | 63 |
| 代码清单 28：使用 autoPrepare() - INSERT | 64 |
| 代码清单 29：使用 autoPrepare() - UPDATE | 65 |
| 代码清单 30：使用 autoExecute() | 67 |
| 代码清单 31：使用 buildManipSQL() | 68 |
| 代码清单 32：executeEmulateQuery() 示例 | 70 |
| 代码清单 33：使用 executeMultiple() | 71 |
| 代码清单 34：使用 query() | 73 |
| 代码清单 35：使用 SQL 限制 MySQL 查询... | 74 |

### 输出清单

| 项目 | 页码 |
| --- | --- |
| 输出 1：在无命令行参数的情况下运行 PEAR 命令 | 7 |
| 输出 2：PEAR list 的输出 | 7 |
| 输出 3：序列示例（代码清单 9）的结果 | 24 |
| 输出 4：序列示例第二次运行的结果 | 24 |
| 输出 5：DB::assertExtension 示例输出 | 37 |
| 输出 6：DB_common::toString 输出 | 42 |
| 输出 7：DB_common::quote 示例输出 | 44 |
| 输出 8：fetchMode 设为 DB_FETCHMODE_ORDERED 时的输出 | 54 |
| 输出 9：fetchMode 设为 DB_FETCHMODE_ASSOC 时的输出 | 55 |
| 输出 10：fetchMode 设为 DB_FETCHMODE_OBJECT 时的输出 | 56 |
| 输出 11：fetchMode 设为 DB_FETCHMODE_OBJECT 并设置了 object_class 时的输出 | 58 |
| 输出 12：使用 buildManipSQL() 的示例 | 68 |
| 输出 13：executeEmulateQuery() 示例的输出 | 70 |
| 输出 14：getRow() 方法的输出 | 79 |
| 输出 15：getCol() 方法的输出 | 81 |
| 输出 16：与代码清单 40 相关的 getAssoc() 输出 | 83 |
| 输出 17：与代码清单 41 相关的 getAssoc() 输出 | 84 |
| 输出 18：与代码清单 42 相关的 getAssoc() 输出 | 85 |
| 输出 19：与代码清单 43 相关的 getAssoc() 输出 | 86 |
| 输出 20：与代码清单 44 相关的 getAssoc() 输出 | 88 |
| 输出 21：与代码清单 45 相关的 getAssoc() 输出 | 89 |
| 输出 22：与代码清单 46 相关的 getAll() 输出 | 91 |
| 输出 23：与代码清单 47 相关的 getAll() 输出 | 93 |
| 输出 24：使用 commit() 的示例 | 96 |
| 输出 25：使用 rollback() 的示例 | 98 |
| 输出 26：在用户权限不足的 MySQL 数据库上执行 createSequence() 的输出 | 102 |
| 输出 27：tableInfo() 方法的输出 | 104 |
| 输出 28：与 getTables 示例（代码清单 54）相关的输出 | 106 |
| 输出 29：getListOf() 示例（代码清单 55）的输出 | 108 |
| 输出 30：代码清单 56 中 fetchRow() 的结果 | 112 |
| 输出 31：fetchInto 示例（代码清单 57）的结果 | 114 |
| 输出 32：tableInfo() 方法的 MODE 参数 | 120 |
| 输出 33：setUp() 示例的输出 | 126 |
| 输出 34：DB_storage::toString() 的输出 | 129 |
| 输出 35：使用 set() 和 get() 以及回调验证函数 | 133 |





- 多结果集 ........ 115
- 多字段键 ........ 10
- MySQL .................... 145

## N
- 原生数据库错误 .......... 46

## O
- ODBC.. 14, 15, 16, 17, 18, 43, 44, 141, 149, 150
- Oracle ... v, 14, 18, 23, 25, 149

## P
- 分页 ................ 76
- 密码 .................. 36
- pconnect .................. 44
- PEAR 包管理器 2, 6, 7
- pear.bat .................. 3, 5
- 持久连接 ... 20, 21, 22, 23, 25, 26, 33
- PHP 5 ..................... 69
- PHP 扩展 ....... 30, 36
- phptype ................... 36
- 端口 ...................... 36
- PostgreSQL ... 14, 18, 146
- prepare ................... 26, 44
- 协议 .................. 36

## Q
- 引号 .................... 43

## R
- REPLACE .................. 35
- REVOKE ................... 35

## S
- 模式 .................. 106
- 序列 ................. 101
- 序列 ................ 23
- 套接字 ................... 36
- SQLite ... 15, 19, 141, 148, 151, 152, 154
- stdClass 对象 .......... 57
- SyBase .......... 14, 18, 150

## T
- 表 .................. 106
- 事务 44, 45, 93, 94, 96

## U
- UNLOCK .................. 35
- UPDATE ............. 35, 100
- 用户名 ................. 36
- 用户 ................... 106

## V
- 视图 .................. 106

## W
- --without-pear .......... 2

