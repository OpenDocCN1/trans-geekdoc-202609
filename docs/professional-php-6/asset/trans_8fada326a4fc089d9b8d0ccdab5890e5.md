

}
public function __call($strFunction, $arArguments) {
    $strMethodType = substr($strFunction, 0, 3);
    $strMethodMember = substr($strFunction, 3);
    switch ($strMethodType) {
        case "set":
            return($this->SetAccessor
            ($strMethodMember, $arArguments[0]));
            break;
        case "get":
            return($this->GetAccessor($strMethodMember));
    };
    return(false);
}

private function SetAccessor($strMember, $strNewValue) {
    if (property_exists($this, $strMember)) {
        if (is_numeric($strNewValue)) {
            eval('$this->' . $strMember .
            ' = ' . $strNewValue . ';');
        } else {
            eval('$this->' . $strMember .
            ' = "' . $strNewValue . '";');
        }
    } else {
        return(false);
    }
}

private function GetAccessor($strMember) {
    if (property_exists($this, $strMember)) {
        eval('$strRetVal = $this->' . $strMember . ';');
        return($strRetVal);
    } else {
        return(false);
    }
}
?>

## 确保满足要求

前面这段代码相当令人生畏，也是你迄今为止在这本书中遇到的最长的一段代码。不用担心；你将在接下来的章节中更详细地了解它的工作原理。现在，重要的是先尝试运行它，以确保它满足你之前草拟的所有要求——即 CRUD（创建、读取、更新和删除）。

## 创建

尝试运行以下代码。要使其正常工作，你需要 user2.php（之前创建）和 pdoFactory.php（在第 6 章中找到）。

```
<?php

require("user2.php");
require("pdoFactory.php");

print "Running...<br />";

$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO);

$objUser->setFirstName("Steve");
$objUser->setLastName("Nowicki");
$objUser->setDateAccountCreated(date("Y-m-d"));

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";

print "Saving...<br />";

$objUser->Save();

print "ID in database is " . $objUser->getID() . "<br />";

?>
```

希望你看到以下输出：

```
Running...
First name is Steve
Last name is Nowicki
Saving...
ID in database is 1
```

同时查看数据库。你应该能看到以下条目：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
----------------+------------+---------------------
Steve | Nowicki | 2008-05-26
(1 row)
```

请注意，你没有指定每一列，但这没关系。因为其他列没有 NOT NULL 约束，它们实际上是可选的，并且被留空。

## 读取

下面是一段更简单的代码，它使用了你刚刚插入的记录：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
    array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
print "First name is " . $objUser->getFirstName() . "<br />";
?>
```

输出应正是你所期望的：

正在运行...
名是 Steve

通过向对象传递 ID '1'，它会自动用该 ID 表示的表中的数据填充——在这里，就是你的好朋友 Steve。

## 更新

这里是另一段你可以尝试的代码，演示如何在数据库中更新 Steve 的条目：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
    array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
$objUser->setFirstName("Steven");
$objUser->Save();
?>
```

试试看。你不会看到太多有趣的输出，但你应该能看到底层数据库表已被更新，Steve 现在被称为 Steven，如下所示：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
------------+-----------+---------------------
 Steven     | Nowicki   | 2008-05-26
(1 row)
```

在此会话中，你可以进行多次更新——更新一列、所有列，或介于两者之间的任何内容。

## 删除

在你了解底层类的工作原理之前，这里还有一段最后的代码供你尝试：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
 array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
$objUser->MarkForDeletion();
?>
```

在浏览器中运行此代码。同样，你不会看到太多有趣的输出，但你应该能观察到在底层数据库中，Steve 已彻底消失：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
------------+-----------+---------------------
(0 rows)
```

练习到此为止。现在是学习一些理论的时候了。

## 了解其工作原理

希望你现在已经向自己证明了该类可以正常工作并且工作良好。这是一段大量的代码，但使用该类的代码却很小且轻量。在 PHP 最佳实践中，这一点至关重要：将内容保存在可重用的类中，并将复杂性隔离在常规应用程序逻辑之外。

以下讨论假设你了解本章前面介绍的类的第一个版本在实际中是如何工作的。如果那部分说不清楚，那么在继续之前，最好先回顾一下相关材料。

## 新成员变量

你应该注意，以下成员变量已添加到类中：

```
private $ID;
private $objPDO;
private $strTableName;
private $arRelationMap;
private $blForDeletion;
```

所有这些成员变量都声明为私有，因为它们不应该在类本身之外被访问或修改。

成员变量 $ID 顾名思义，存储分配给数据库表中行的唯一标识符。在整个类中，假设它是数字，会自动递增，并且在表中名为 'id'。如果不是，那么根据需要调整该类应该足够容易。

PDO 对象的实例存储在 $objPDO 中。它在构造函数中首次传入，并在整个类生命周期内作为成员变量保留。在你自己的应用程序中，你可能希望使用 PDOFactory 类生成 PDO 对象的单例实例，以避免对同一 DSN 进行冗余的多次连接。然后，在实例化业务类时，可以将该实例传递给它们。

由于表名不能从类名推断（例如，在此例中，类名是 'User'，但表名为 'system_user'），因此有必要使用一个成员变量专门用于存储相应数据库表的名称。这在构造函数中被不可分割地设置。

一个关联数组 $arRelationMap 用于将表名（作为数组键）映射到成员变量名（作为数组值）。成员变量名存储时不带前面的美元符号。同样，这在构造函数中设置。

最后，一个简单的布尔标志用于指示对象是否已被标记为永久销毁。当设置为 true 时，类的析构函数将在底层数据库中调用物理删除。当然，在实际中，企业级应用程序很少要求永久销毁业务记录（例如出于采用《萨班斯-奥克斯利法案》等原因）。但是，你可以决定更改析构函数中的行为——例如，在记录上设置“禁用”标志，或以其他方式禁止其将来包含在常规选择中。

## 构造函数

添加标准构造函数，可在实例化类的对象时自动执行多个操作。

