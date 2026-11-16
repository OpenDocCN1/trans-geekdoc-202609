

再次强调，这是一个相当简单的类，得益于继承的强大功能。你声明一个名为 name 的属性，这样更容易获取组织拥有的唯一名称（sname2 属性对组织未使用）。

要向 DataManager 类添加 getEmployer() 和 getEmployees() 函数，请将以下代码追加到 class.DataManager.php 文件末尾：

```
public static function getEmployer($individualID) {
    $sql = "SELECT \"organizationid\" FROM \"entityemployee\" . "
        "WHERE \"individualid\" = $individualID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(! ($res && pg_sql_num_rows($res))) {
        die("Failed getting employer info for individual $individualID");
    }

    $row = pg_sql_fetch_assoc($res);

    if($row) {
        return new Organization($row['organizationid']);
    } else {
        return null;
    }
}

public static function getEmployees($orgID) {
    $sql = "SELECT \"individualid\" FROM \"entityemployee\" . "
        "WHERE \"organizationid\" = $orgID";
    $res = pg_sql_query(DataManager::getConnection(), $sql);

    if(! ($res && pg_sql_num_rows($res))) {
        die("Failed getting employee info for org $orgID");
    }
    if(pg_sql_num_rows($res)) {
        $objs = array();
        while($row = pg_sql_fetch_assoc($res)) {
            $objs[] = new Individual($row['individualid']);
        }
        return $objs;
    } else {
        return array();
    }
}
```

这两个函数依赖于名为 entityemployee 的表的存在，如以下代码所示。该表将个人与雇佣他们的组织关联起来。例如，同一家公司的员工会有不同的个人 ID，但相同的组织 ID。

```
CREATE TABLE "entityemployee" (
    "individualid" int NOT NULL,
    "organizationid" int NOT NULL,
    CONSTRAINT "fk_entityemployee_individualid"
    FOREIGN KEY ("individualid") REFERENCES "entity"("entityid"),
    CONSTRAINT "fk_entityemployee_organizationid"
    FOREIGN KEY ("organizationid") REFERENCES "entity"("entityid")
);
```

还需要最后一个函数才能使整个系统工作 — DataManager 中用于列出数据库中所有实体的方法。它名为 getAllEntitiesAsObjects()，用于完成你对对象所需的所有工作。将此方法添加到 class.DataManager.php 中：

```
public static function getAllEntitiesAsObjects() {
$sql = "SELECT \"entityid\", \"type\" from \"entity\"";
$res = pg_sql_query(DataManager::getConnection(), $sql);
if(!$res) {
die("Failed getting all entities");
}
if(pg_sql_num_rows($res)) {
$objs = array();
while($row = pg_sql_fetch_assoc($res)) {
if($row['type'] == 'I') {
$objs[] = new Individual($row['entityid']);
} elseif ($row['type'] == 'O') {
$objs[] = new Organization($row['entityid']);
} else {
die("Unknown entity type {$row['type']} encountered!");
}
}
return $objs;
} else {
return array();
}
}
```

DataManager 使你能够枚举系统中的所有联系人。它检查 entity 表中 ctype 字段的值，以确定条目是 Individual 还是 Organization，然后实例化相应类型的对象并将其添加到函数返回的数组中。

## 使用系统

到现在，你可以看到 OOP 方法的真正威力。名为 test.php 的以下代码将显示数据库中所有联系人的视图，包括它们的所有联系信息：

```
<?php
require_once('class.DataManager.php'); //everything gets included by it
function println($data) {
print $data . "<br>\n";
}

$arContacts = DataManager::getAllEntitiesAsObjects();

foreach($arContacts as $objEntity) {

	if(get_class($objEntity) == 'Individual') {
		print "<h1>Individual - {$objEntity->__toString()}</h1>";
	} else {
		print "<h1>Organization - {$objEntity->__toString()}</h1>";
	}

	if($objEntity->getNumberOfEmails()) {
		//We have emails! Print a header
		print "<h2>Emails</h2>";

		for($x=0; $x < $objEntity->getNumberOfEmails(); $x++) {
			println({$objEntity->emails($x)->__toString()}); $x++
		}
	}

	if($objEntity->getNumberOfAddresses()) {
		//We have addresses!
		print "<h2>Addresses</h2>";

		for($x=0; $x < $objEntity->getNumberOfAddresses(); $x++) {
			println({$objEntity->addresses($x)->__toString()});
		}
	}

	if($objEntity->getNumberOfPhoneNumbers()) {
		//We have phone numbers!
		print "<h2>Phones</h2>";

		for($x=0; $x < $objEntity->getNumberOfPhoneNumbers(); $x++) {
			println({$objEntity->phonenumbers($x)->__toString()});
		}
	}

	print "<hr>\n";

} //End foreach

?>
```

你可以将数据输入自己的表中，因为这将帮助你弄清楚一切如何协同工作。你可能想尝试模仿图 3-8 所示的结果（通过在浏览器中导航到 test.php）。

![](img/a1b732997d9cb194dceec0570dc79710_86_0.png)

## 图 3-8：示例应用程序的结果

仅需 50 行代码（包括空行），你就可以显示系统中关于实体的几乎所有内容。这里未显示雇主和员工；再次，这是留给你尝试的练习。test.php 中调用 get_class 函数的那行代码会给你一些想法，帮助你弄清楚正在处理哪个类，从而知道是应该在 Individual 上调用 getEmployer()，还是在 Organization 上调用 getEmployees()。

## 总结

UML 图是规划复杂（甚至不太复杂）应用程序的必备工具。设计得当的图表能让你以纯文本无法实现的更清晰方式记录复杂系统。当你将类图作为常规软件开发流程的一部分时，更容易看出类和数据库表应如何设计。

充分利用 PHP6 中的 OO 特性，有助于快速开发应用程序，并建立一个更易于维护、提供更高灵活性和可扩展性、并减少实现业务需求所需代码总量的代码库。

通过将软件架构分为业务逻辑层（如 `Individual` 类）和数据访问层（如 `DataManager` 类），你可以轻松更改底层数据源、表结构或查询，而不会干扰应用程序的其余部分。负责实现业务逻辑的对象不会被数据访问机制所杂乱，后者的存在可能会混淆和模糊业务规则。

第 4 章探讨了思考软件架构的新方法，该方法提高了代码的可重用性和可维护性，并在设计类时提供了不同层次的抽象。

## 设计模式

在本书的前面章节中，你了解到对象可以通过继承从父对象派生。你还了解到对象可以包含对其他对象的引用（例如，DrumSet 对象持有 Drum 对象）。通常，从其他对象组合对象的技术被称为对象组合。

继承和对象组合都是设计面向对象（OO）软件的强大工具，允许各种各样的设计选择。当然，拥有众多选择并不总是使决策更容易。你会如何设计应用程序，使其易于维护和扩展？你会如何编写一个组件，让团队的其他成员能够通过简单的界面使用？编写软件时，你可以凭借经验、智慧、运气、大量含咖啡因的饮料，或以上因素的任何组合，独自解决某些问题。

你可能已经重复使用过自己的现有代码来解决问题。也许你有一个用于连接数据库的标准脚本。设计模式略有不同，因为它们不仅仅是关于重用代码；它们比这更抽象、更具普遍性。同一设计模式可能出现在完全不同类型的软件中。设计模式关乎重用组织和组合的理念，而不仅仅是重用相同的执行。了解模式后，你将能够识别它在哪里有用。然后你可以继续实现它，因为这是一个被认可的解决方案。

设计模式是解决特定问题的一种特定方式。在本书中，它代表对象或一组对象的结构方式，以及它们如何与模式中的其他对象协作和通信。每个模式都有一个描述性名称（例如 Observer 或 Observable），每个模式都有一个可以在类图中展示的特定设计。

初学模式时可能会感到困惑。如果这个初始描述似乎不够清晰，请不要担心。你将在本章中学习五种不同的模式，并基于前几章中看到的一些代码进行构建。

