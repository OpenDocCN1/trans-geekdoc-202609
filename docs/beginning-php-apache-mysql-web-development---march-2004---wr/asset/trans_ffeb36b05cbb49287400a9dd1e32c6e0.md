

# 构建数据库

```php
if ($char == '' || $is_numeric($char)) $char='0';
$subtype = 'Create';
$subhead = 'Please enter data and click $subtype
Character.*';
$tablebg = '#EEEEFF';
```

```php
$conn = mysqli_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die('Could not connect to MySQL database. ' . mysqli_error());
mysqli_select_db($SQL_DB, $conn);
```

```php
$sql = 'SELECT id, power FROM char_power';
$result = mysqli_query($sql);
if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        Sparlist[$row['id']] = $row['power'];
    }
}
```

```php
$sql = 'SELECT id, alias FROM char_main WHERE id != $char*';
$result = mysqli_query($sql) or die(mysqli_error());
if (mysqli_num_rows($result) > 0) {
    $row = mysqli_fetch_assoc($result);
    $charlist[$row['id']] = $row['alias'];
}
```

```php
if ($char == '0') {
    $sql = 'SELECT c.alias, c.real_name AS name, c.align, 1.lair_addr
AS address, z.city, z.state, z.id ZIP FROM char_main c,
char_lair_1, char_zipcode WHERE z.id = 1.zip_id AND
c.id = 1 AND c.id = $char*';
    $result = mysqli_query($sql) or die(mysqli_error());
    $ch = mysqli_fetch_assoc($result);
}
```

```php
if (is_array($ch)) {
    $subtype = 'Update';
    $tablebg = '#EEEEFF'; 
    // ... logic truncated in OCR ...
}
```

```php
$sql = 'SELECT p.id FROM char_main c JOIN char_power p
JOIN pk_power ON c.id = p.char_id
AND p.id = c.id = $char';
$result = mysqli_query($sql) or die(mysqli_error());
if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        $powers[$row['id']] = 'selected';
    }
}
```

```php
// 获取角色敌人的列表
$sql = 'SELECT n.id FROM char_main c JOIN char_good_bad_link gb
JOIN char_main n ON (c.id = gb.good_id AND n.id = gb.bad_id)
OR (n.id = gb.good_id AND c.id = gb.bad_id) WHERE
c.id = $char*';
$result = mysqli_query($sql) or die(mysqli_error());
```

# 第 9 章

```php
if (mysql_num_rows($result) > 0) {
    while ($row = mysql_fetch_assoc($result)) {
        Enemies[$row['id']] = 'selected';
    }
}
?>
```

```html
<html>
<head>
<title>角色编辑器</title>
</head>
<body>
<img src="CBA_Tiny.gif" align='left' hspace='10'>
<h1>漫画书<br />/ 赏析</h1><br />
<h3><?php echo $subhead; ?></h3>
```

```html
<form action='char_transact.php' name='theform' method='post'>
<table border='0' padding='15' bgcolor='<?php echo $tablebg;?>'>
    <tr>>
    <tr>
        <td>角色名称：</td>
        <td><input type='text' name='alias' size='41' value='<?php echo $ch['alias'];?>'></</td>>
    </tr>
    <tr>
        <td>真实姓名：</td>
        <td><input type='text' name='name' size='41' value='<?php echo $ch['name'];?>'></</td>>
    </tr>
    <tr>
        <td>能力：<br /><font size=2 color='#990000'>
        (按住 Ctrl 点击以选择 <select multiple<br />能力)</font></td>
    </tr>
    <tr>
        <td><select multiple='multiple' name='powers[]' size='4'>
        <?php
        foreach ($pwrlist as $key => $value) {
            echo "<option value='$key'> $powers[$key]\n";
        }
        ?>
        </select></</td>>
    </tr>
    <tr>
        <td>巢穴位置：<br /><font size=2 color='#990000'>
        (地址，<br />城市，州，邮政编码)</font></td>
    </tr>
    <tr>
        <td></td>
        <td>
            <input type='text' name='address' size='41' value='<?php echo $ch['address'];?>'><br />
            <input type='text' name='city' value='<?php echo $ch['city'];?>?>
            <input type='text' name='state' size='2' value='<?php echo $ch['state'];?>?>
            <input type='text' name='zip' size='10' value='<?php echo $ch['zip'];?>?>
        </td>
    </tr>
    <tr>
        <td>阵营：</td>
        <td>
            <input type='radio' name='align' value='good' <?php echo($ch['align']=='good' ? 'checked' : ''); ?><br />
            <input type='radio' name='align' value='evil' <?php echo($ch['align']=='evil' ? 'checked' : ''); ?>>
        </td>
    </tr>
<?php if (is_array($charlist)) { ?>
    <tr>
        <td>敌人：<br /><font size=2 color='#99000'>
        (按住 Ctrl 点击以选择多个 <br />敌人)</font></td>
        <td>
            <select multiple='' name='enemies[]' size='4'>
            <?php
            foreach ($charlist as $key => $value) {
                echo '<option value='.$key.'>'.$value.'</option>';
            }
            ?>
            </select>
        </td>
    </tr>
<?php } ?>
    <tr>
        <td colspan='2'>
            <input type='submit' name='action' value='<?php echo $subtype;?> 角色'>
            <input type='reset'>
            <?php if ($subtype == 'Update') { ?>
                &nbsp;&nbsp;&nbsp;&nbsp;
                <input type='submit' name='action' value='删除角色'>
            <?php } ?>
        </td>
    </tr>
</table>
```

```html
<input type='hidden' name='cid' value='<?php echo $char;?>'>
</form>
<a href='charlist.php'>返回首页</a>
</body>
</html>
```

# 构建数据库（注意：此部分的 OCR 内容似乎是重复或碎片化的；后续逻辑遵循了所提供的 PHP 代码。）

4. 好的，现在有了。这段代码最长，但它包含了 SQL 语句。看起来不太妙。但如果你想从网站下载这段代码，就尽管去。把它看作是你的礼物。输入后，将其保存为 `char_transact.php`。

```php
<?php
require('config.php');
foreach($_POST as $key => $value) {
    $key = $value;
}

$conn = mysqli_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die('Could not connect to MySQL database. ' . mysqli_error());
mysqli_select_db($DB, $conn);

switch ($action) {
    case "Create":
        $sql = "INSERT IGNORE INTO char_zipcode (id, city, state) VALUES ('$zip', '$city', '$state')";
        $result = mysqli_query($sql) or die(mysqli_error());

        $sql = "INSERT IGNORE INTO char_lair (id, zip_id, lair_addr) VALUES ('$zip', '$address')";
        $result = mysqli_query($sql) or die(mysqli_error());
        if ($result) $lairid = mysqli_insert_id($conn);

        $sql = "INSERT IGNORE INTO char_main (id, lair_id, alias, name) VALUES ('$lairid', '$alias', '$name')";
        $result = mysqli_query($sql) or die(mysqli_error());
        if ($result) $charid = mysqli_insert_id($conn);

        if ($enemies != '') {
            $val = "";
            foreach ($enemies as $key => $sid) {
                $val[] = '$charid', '$sid';
            }
            $values = implode(',', $val);
            $sql = "INSERT IGNORE INTO char_power_link (char_id, power_id) VALUES $values";
            $result = mysqli_query($sql) or die(mysqli_error());
        }
    }
?>
```

# 构建数据库（继续）

```php
$values = implode(',', $val);
if ($align == 'good') {
    $cols = '(good_id, bad_id)';
} else {
    $cols = '(bad_id, good_id)';
}
$sql = 'INSERT IGNORE INTO char_good_bad_link $cols VALUES $values';
$result = mysqli_query($sql) or die(mysqli_error());
}

$redirect = 'charlist.php';
break;

case "Delete Character":
    $sql = "DELETE FROM char_main, char_lair USING char_main m, char_lair l WHERE m.lair_id = l.id AND m.id = $cid";
    $result = mysqli_query($sql) or die(mysqli_error());

    $sql = "DELETE FROM char_power_link WHERE char_id = $cid";
    $result = mysqli_query($sql) or die(mysqli_error());

    $sql = "DELETE FROM char_good_bad_link WHERE good_id = $cid OR bad_id = $cid";
    $result = mysqli_query($sql) or die(mysqli_error());

$redirect = 'charlist.php';
break;

case "Update Character":
    $sql = "INSERT IGNORE INTO char_zipcode (id, city, state) VALUES ('$zip', '$city', '$state')";
    $result = mysqli_query($sql) or die(mysqli_error());

    $sql = "UPDATE char_lair l, char_main m SET l.zip_id='$zip', l.lair_addr='$address', m.alias='$alias', real_name='$name', align='$align' WHERE m.id = $cid AND m.lair_id = l.id";
    $result = mysqli_query($sql) or die(mysqli_error());

    $sql = "DELETE FROM char_power_link WHERE char_id = $cid";
    $result = mysqli_query($sql) or die(mysqli_error());

    if ($powers != '') {
        $val = '';
        foreach ($powers as $key => $id) {
            $val[] = '$charid', '$id';
        }
        $values = implode(',', $val);
        $sql = "INSERT IGNORE INTO char_power_link (char_id, power_id) VALUES $values";
        $result = mysqli_query($sql) or die(mysqli_error());
    }
}
```
