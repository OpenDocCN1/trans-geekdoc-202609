

protected $DateAccountCreated;
protected $TimeAccountCreated;

protected function DefineTableName() {
    return("system_user");
}

protected function DefineRelationMap() {
    return(array(
        "id" => "ID",
        "first_name" => "FirstName",
        "last_name" => "LastName",
        "username" => "Username",
        "md5_pw" => "Password",
        "email_address" => "EmailAddress",
        "date_last_login" => "DateLastLogin",
        "time_last_login" => "TimeLastLogin",
        "date_account_created" => "DateAccountCreated",
        "time_account_created" => "TimeAccountCreated"));
}

?>

这一切都很好，但你还必须向自己证明，你的用户对象的第三个版本与第二个版本的工作方式完全相同——至少就其对外界的接口而言。这个全功能示例展示了创建、读取、更新和删除。

```php
<?php
require("pdofactory.phpm");
require("databoundobject.phpm");
require("userv3.phpm");

print "Running...<br />";

$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::GetPDO($strDSN, "chapterseven", "chapterseven",
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

$id = $objUser->getID();

print "ID in database is " . $id . "<br />";

print "Destroying object...<br />";
unset($objUser);

print "Recreating object from ID $id<br />";
$objUser = new User($objPDO, $id);

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";

print "Committing a change.... Steve will become Steven, Nowicki will become Nowickcow<br />";
$objUser->setFirstName("Steven");
$objUser->setLastName("Nowickcow");
print "Saving...<br />";
$objUser->Save();

?>
```

试一下，确保将其保存到与所需类相同的目录中。你应该会看到类似于以下的输出：

```
Running...
First name is Steve
Last name is Nowicki
Saving...
ID in database is 167
Destroying object...
Recreating object from ID 167
First name is Steve
Last name is Nowicki
Committing a change.... Steve will become Steven, Nowicki will become Nowickcow
Saving...
```

正如你所见，新形成的轻量级 User 类与你的第二个版本的工作方式完全相同，但它小得多，更易于移植，并且不会受到前面章节中指出的相同问题的影响，你将在后续讨论中亲自验证这一点。

## 了解其工作原理

由于代码之间有大量相似之处，希望快速浏览一遍不会显得太令人生畏。

首先，请注意该类被声明为抽象类：

```
abstract class DataBoundObject {
```

这告诉 PHP 期望有一个或多个抽象方法——这些方法将在父类中定义但不实现。这使你可以规定这些方法的参数数量和顺序，并强制要求任何扩展该抽象类的子类都必须实现这些方法。

接下来，你会看到声明了一些受保护的成员变量：

```
protected $ID;
protected $objPDO;
protected $strTableName;
protected $arRelationMap;
protected $blForDeletion;
protected $blIsLoaded;
protected $arModifiedRelations;
```

这些非类特定的变量将对象与底层关系数据库关联。请注意新增了一个保存数据库表名的变量，以及一个关联数组，用于指示子对象生命周期内哪些字段已被修改。

此外，成员变量被声明为受保护。这意味着，虽然在类外部不可公开访问，但它们可供父类的子类访问。

定义了两个抽象方法：

```
abstract protected function DefineTableName();
abstract protected function DefineRelationMap();
```

这些方法必须在子类中实现，其任务仅仅是设置表名和关系映射。

构造函数实际上会调用这两个方法，并（理所当然地）假设子类已实现它们：

```
public function __construct(PDO $objPDO, $id = NULL) {
    $this->strTableName = $this->DefineTableName();
    $this->arRelationMap = $this->DefineRelationMap();
    $this->objPDO = $objPDO;
    $this->blIsLoaded = false;
    if (isset($id)) {
        $this->ID = $id;
    };
    $this->arModifiedRelations = array();
};
```

你会注意到，构造函数与之前一样，接受一个 PDO 实例以及可选的标识符，该标识符表明相关实体已存在于数据库中。构造函数还将“加载”状态设置为 false，表示尚未从底层数据库读取任何数据。修改关系数组也会被重置。

新的 Load() 方法借用了之前位于构造函数中的代码，这些代码用于在实例化类时传入标识符的情况下，用数据库中的数据填充对象。通过将此类代码放入单独的方法中，它不再在实例化时自动调用。

```
public function Load() {
    if (isset($this->ID)) {
    $strQuery = "SELECT ";
    foreach ($this->arRelationMap as $key => $value) {
    $strQuery .= "\"" . $key . "\",";
    }
    $strQuery = substr($strQuery, 0, strlen($strQuery)-1);
    $strQuery .= " FROM " . $this->strTableName . " WHERE
    \"id\" = :eid";
    $objStatement = $this->objPDO->prepare($strQuery);
    $objStatement->bindParam(':eid', $this->ID,
    PDO::PARAM_INT);
    $objStatement->execute();
    $arRow = $objStatement->fetch(PDO::FETCH_ASSOC);
    foreach ($arRow as $key => $value) {
    $strMember = $this->arRelationMap[$key];
    if (property_exists($this, $strMember)) {
    if (is_numeric($value)) {
    eval('$this->' . $strMember .
    ' = ' . $value . ';');
    } else {
    eval('$this->' . $strMember .
    ' = "' . $value . '"');
    }
    }
    };
    $this->blIsLoaded = true;
    }
}
```

加载完成后，“bIsLoaded”标志将被设置为 true。这样可以防止类在子对象的剩余生命周期内不必要地调用 Load() 方法。

Save() 方法与原始数据启用的 User 类几乎保持不变。唯一的关键区别在于测试给定属性是否已被修改：

```
if (array_key_exists($value, $this->arModifiedRelations)) {
    $strQuery .= "" . $key . " = :$value, ";
}
```

这样一来，如果某个字段未被修改，则它不会包含在生成的 UPDATE 或 INSERT 语句中。当然，在填充预处理语句参数时也会应用相同的测试：

```
if (array_key_exists($value, $this->arModifiedRelations)) {
if ((is_int($actualVal)) || ($actualVal == NULL)) {
$objStatement->bindValue(':'.$value, $actualVal, PDO::PARAM_INT);
} else {
$objStatement->bindValue(':'.$value, $actualVal, PDO::PARAM_STR);
};
};
```

以这种方式进行两次测试非常重要；如果你尝试将值绑定到不存在的参数，PDO 会严格报错：

标记删除的方法、析构函数和 __call() 重载方法均与原始 User 类保持不变。

两个访问器方法已略作调整：

```
private function SetAccessor($strMember, $strNewValue) {
    if (property_exists($this, $strMember)) {
        if (is_numeric($strNewValue)) {
            eval('$this->' . $strMember . ' = ' .
            $strNewValue . ';');
        } else {
            eval('$this->' . $strMember . ' = "' .
            $strNewValue . '"');
        };
        $this->arModifiedRelations[$strMember] = "1";
    } else {
        return(false);
    };
}
```

请注意，修改关系映射现已调整，以指示相关关系已被修改。Save() 将使用这些数据，根据需要构建更简洁的 UPDATE 或 INSERT 语句：

```
private function GetAccessor($strMember) {
    if ($this->blIsLoaded != true) {
        $this->Load();
    }
    if (property_exists($this, $strMember)) {
        eval('$strRetVal = $this->' . $strMember . ';');
        return($strRetVal);
    } else {
        return(false);
    };
}
```

最后，正如你从前面的代码中所见，'get' 访问器也进行了一小处修改。类会被测试以确定“加载”标志是否设置为 true。如果不是，则在尝试求值并返回属性之前会先调用 Load() 方法。

那这个类本身呢？如 userv3.phpm 中的代码所示，它已变得更小了。首先请注意，它继承自 DataBoundObject：

```
class User extends DataBoundObject {
```

因此，你的应用程序必须确保不仅为该类本身存在 require() 语句，同样重要的是，也要为 DataBoundObject 类存在 require() 语句。

