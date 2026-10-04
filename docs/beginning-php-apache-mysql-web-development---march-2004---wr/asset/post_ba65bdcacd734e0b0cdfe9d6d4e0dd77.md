
# Building Databases

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
// get list of character's enemies
$sql = 'SELECT n.id FROM char_main c JOIN char_good_bad_link gb
JOIN char_main n ON (c.id = gb.good_id AND n.id = gb.bad_id)
OR (n.id = gb.good_id AND c.id = gb.bad_id) WHERE
c.id = $char*';
$result = mysqli_query($sql) or die(mysqli_error());
```

# Chapter 9

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
<title>Character Editor</title>
</head>
<body>
<img src="CBA_Tiny.gif" align='left' hspace='10'>
<h1>Comic Book<br />/Appreciation</h1><br />
<h3><?php echo $subhead; ?></h3>
```

```html
<form action='char_transact.php' name='theform' method='post'>
<table border='0' padding='15' bgcolor='<?php echo $tablebg;?>'>
    <tr>
        <td>Character Name:</td>
        <td><input type='text' name='alias' size='41' value='<?php echo $ch['alias'];?>'></td>
    </tr>
    <tr>
        <td>Real Name:</td>
        <td><input type='text' name='name' size='41' value='<?php echo $ch['name'];?>'></td>
    </tr>
    <tr>
        <td>Powers:<br /><font size=2 color='#990000'>
        (Ctrl-click to pick <select multiple<br />powers)</font></td>
    </tr>
    <tr>
        <td><select multiple='multiple' name='powers[]' size='4'>
        <?php
        foreach ($pwrlist as $key => $value) {
            echo "<option value='$key'> $powers[$key]\n";
        }
        ?>
        </select></td>
    </tr>
    <tr>
        <td>Lair Location:<br /><font size=2 color='#990000'>
        (address,<br />city, state, zip)</font></td>
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
        <td>Alignment:</td>
        <td>
            <input type='radio' name='align' value='good' <?php echo($ch['align']=='good' ? checked='checked' : ''); ?><br />
            <input type='radio' name='align' value='evil' <?php echo($ch['align']=='evil' ? checked='checked' : ''); ?>>
        </td>
    </tr>
<?php if (is_array($charlist)) { ?>
    <tr>
        <td>Enemies:<br /><font size=2 color='#990000'>
        (Ctrl-click to or/select multiple <br />enemies)</font></td>
        <td>
            <select multiple='' name='enemies[]' size='4'>
            <?php
            foreach ($charlist as $key => $value) {
                echo '<option value=''.$key.'">'.$enemies[$key].'.$value.'</option>\n';
            }
            ?>
            </select>
        </td>
    </tr>
<?php } ?>
    <tr>
        <td colspan='2'>
            <input type='submit' name='action' value='<?php echo $subtype;?> Character'>
            <input type='reset'>
            <?php if ($subtype == 'Update') { ?>
                &nbsp;&nbsp;&nbsp;&nbsp;
                <input type='submit' name='action' value='Delete Character'>
            <?php } ?>
        </td>
    </tr>
</table>
```

```html
<input type='hidden' name='cid' value='<?php echo $char;?>'>
</form>
<a href='charlist.php'>Return to Home Page</a>
</body>
</html>
```

# Building Databases (Note: OCR content for this section appears to be repetitive or fragmented in the source; the following logic follows the reconstructed flow of the PHP code provided.)

4. Okay, only more now. This code is the longest, but it contains a list of SQL statements. It is not bad as it looks. But if you want to download this code from the site, go ahead, be guilt-free. Consider it a gift to you. If you are typing it, you know the drill. After entering it, save this as char_transact.php.

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

# Building Databases (Continued)

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

    $sql = "DELETE FROM char_good_bad_link WHERE good_id = $cid OR bad_id = $cid";
    $result = mysqli_query($sql) or die(mysqli_error());
}

$redirect = 'charlist.php';
break;
```