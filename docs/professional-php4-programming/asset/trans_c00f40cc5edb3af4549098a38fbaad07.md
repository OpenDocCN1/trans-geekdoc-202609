
{
    // Revoke a privilege from the user
    global $sql;

    // Make sure user has this privilege:
    if (!$this->hasPrivilege($iPrivilegeID)) return;

    $sUsername = $this->getUsername();
    $sql->query("DELETE from UserPrivilege WHERE
                privilegeid=$iPrivilegeID AND
                username='$sUsername'");
}

最后一步是从用户的权限数组中移除该权限：

```php
$iIndex = array_search($iPrivilegeID, $this->privileges);
unset($this->privileges[$iIndex]);

}
```

hasPrivilege() 用于检查用户是否拥有某项权限：

```php
function hasPrivilege($iPrivilegeID)
{
    // Determine whether user has specified privilege

    // Initialize privileges if necessary:
    if (!is_array($this->privileges)) $this->populatePrivileges();

    return in_array($iPrivilegeID, $this->privileges);
}
```

create()、update() 和 delete() 是非常简单的函数，其功能与对应的 Privilege 类方法非常相似：

```php
function create()
{
    // Add new user to database

    global $sql;

    $sUserName = $this->getUsername();
    $sFullName = $this->getFullname();

    $sql->query("INSERT INTO User VALUES ('$sUserName', '$sFullName')");
}

function update()
{
    // Update user in database

    global $sql;

    $sUserName = $this->getUsername();
    $sFullName = $this->getFullname();

    $sql->query("UPDATE User SET fullname='$sFullName'
                     WHERE username='$sUserName' ");
}

function delete()
{
    // Remove the user from the database

    global $sql;

    $sUserName = $this->getUsername();

    // First remove from UserPrivilege
    $sql->query("DELETE FROM UserPrivilege
                   WHERE username='$sUserName' ");

    // Next remove from Privilege
    $sql->query("DELETE FROM User
                   WHERE username='$sUserName' ");

    $this->userExists = 0;
}
```

最后，我们有用于 User 属性的 getXxx() 和 setXxx() 方法：

```php
function getUsername()
{
    // Returns the property

    return $this->username;
}

function setUsername($sVal)
{
    // Set the property

    if (!ereg("^[a-zA-Z0-9_]{5,10}$", $sVal)) return 0;
    $this->username = $sVal;
    return 1;
}

function getFullname()
{
    // Returns the property

    return $this->fullname;
}
```

只有当用户名包含字母数字字符或下划线，且长度在 5 到 10 个字符之间（包含首尾）时才有效（有关正则表达式的详细信息，参见第 7 章）：

```php
function setFullname($sVal)
{
    // Set the property

    if (strlen($sVal) > 50) return 0;
    $this->fullname = $sVal;
    return 1;
}
}
?>
```

## 测试类

编写脚本来测试你开发的类总是很有帮助。测试脚本可以让你隔离类中的问题，这些问题在整个应用程序的上下文中可能更难识别。下面的简单程序表明我们的代码中没有解析错误，并且这些类基本上按预期工作。它还能让我们了解使用所创建的类是什么感觉：

```php
<?php
// test.userpriv.php

require_once("DB.php");
require_once("priv.classes.inc");

$sql = new DB("localhost", "", "", "userprivilege");
$sql->open();
```

首先我们将测试用户创建：

```php
$oUser = new User();
$oUser->setUsername("scollo");
$oUser->setFullname("Christopher Scollo");
$oUser->create();
```

现在我们测试权限创建：

```php
$oPriv = new Privilege();
$oPriv->setDescription("stay out late");
$oPriv->create();
```

让我们尝试为我们的用户分配一个权限：

```php
$oUser->addPrivilege($oPriv->getPriv_id());
```

与其从头创建用户，我们现在将测试从数据库创建用户：

```php
unset($oUser);
unset($oPriv);
$oUser = new User("scollo");
$oPriv = new Privilege(1);
```

稍微输出一点内容以证明权限已被分配：

```php
if ($oUser->hasPrivilege($oPriv->getPriv_id())) {
    echo($oUser->getFullname() . " may " . $oPriv->getDescription()
    . "<br />");
} else {
    echo($oUser->getFullname() . " may not " . $oPriv->getDescription()
    . "<br />");
}
```

最后，我们将测试对象删除：

```php
$oUser->delete();
$oPriv->delete();
?>
```

然后我们将这段代码保存为名为 test.userpriv.php 的文件，并在浏览器中调用它：

![](img/9cf7789dba9b16ef3f8576d5aea89186_956_0.png)

## privilege.php

privilege.php 程序使用户能够在系统中添加、编辑和删除权限：

```php
<?php
require("DB.php");
require("priv.classes.inc");

$sql = new DB("localhost", "", "", "userprivilege");
$sql->open();
```

第一个方法 displaySelection() 显示可编辑的权限列表，以及一些用于操作它们的按钮：

在这里，我们遍历 privileges 数组，并将每个元素作为 `<option>` 元素添加到 `<select>` 列表中：

```php
function displaySelection($aPrivileges)
{
    // Display the list of choices

    echo("<?xml version=\"1.0\"?>\n");

?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Privilege</title>
</head>
<body>
<form method="post" action="privilege.php">
<select name="priv_id">
<?php
foreach ($aPrivileges as $iPrivID => $sDescription) {
    echo (
        "<option value=\"$iPrivID\">" .
        stripslashes(htmlspecialchars($sDescription)) .
        "</option>\n"
    );
}
?>
</select>
<br />
<br />
<input type="submit" name="action" value="Add New" />
<input type="submit" name="action" value="Change Privilege" />
<input type="submit" name="action" value="Exit" />
</form>
</body>
</html>
<?php
}
```

displayDetails() 向用户显示所选权限的描述：

```php
function displayDetails($oPriv)
{
    // Generate page for selected privilege

    echo("<?xml version=\"1.0\"?>\n");

?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Privilege</title>
</head>
<body>
<form method="post" action="privilege.php">
```

由于我们不需要查看权限ID的值（而且也不应该能够更改它），我们将使用隐藏字段来传递权限ID及其描述：

```html
<input type="hidden" name="priv_id"
       value="<?php echo($oPriv->getPriv_id()); ?>" />
<h3>Description:</h3>
<input
       type="text"
       name="description"
       value="<?php echo(stripslashes(htmlspecialchars(
                      $oPriv->getDescription()))); ?>"
       size="50"
       maxlength="50"
       />
<br />
<br />
<input type="submit" name="action" value="Save" />
<input type="submit" name="action" value="Delete" />
<input type="submit" name="action" value="Cancel" />
</form>
</body>
</html>
```

```php
<?php
}
```

getPrivileges() 允许我们获取所有当前的权限ID。现在我们不关心描述，因为它们不是主键：

```php
function getPrivileges()
{
    // Returns an array of all privileges

    global $sql;

    $aRet = array();

    $sql->query("SELECT * FROM Privilege ORDER BY priv_id");

    while ($row = $sql->fetchObject()) {
        $aRet[(int)$row->priv_id] = $row->description;
    }
    return $aRet;
}
```

validate() 检查提交的表单数据是否有效，并根据结果创建一个新的 Privilege 对象。如果提供了ID且不存在具有该ID的 Privilege，则会创建一个具有该ID的新 Privilege。如果未提供ID，则使用一个空白的 Privilege：

```php
function validate()
{
    // Validate form data and set the global priv object

    global $Priv_id, $description, $oPriv;

    if ($priv_id) {
        // Make sure it's a valid PrivID
        $oPriv = new Privilege((int)$priv_id);
        if (!$oPriv->privilegeExists) return 0;
    } else {
        $priv_id = 0;
        $oPriv = new Privilege();
    }
    return 1;
}
```

save() 在检查要保存的权限是否存在之前，先设置权限的描述。如果存在，save() 将尝试在数据库中更新它。如果不存在，save() 将尝试创建一个全新的数据库条目：

```php
function save()
{
    // Save the selected privilege

    global $oPriv, $description;

    $oPriv->setDescription(addslashes($description));
    if ($oPriv->privilegeExists) {
        if (!$oPriv->update()) return 0;
    } else {
        if (!$oPriv->create()) return 0;
    }
    return 1;
}
```

delete() 移除指定的权限：

```php
function delete($oPriv)
{
    // Remove the selected privilege
```
