# Chapter 9

```
bad_id = $cid;
$result = mysql_query($sql) or die(mysql_error());

if ($enemies != '') {
$val = '*';
foreach ($enemies as $key => $id) {
$val[] = '*($cid', '$$id');
}
$values = implode(',', $val);
if ($align == 'good') {
$cols = '(good_id, bad_id)';
} else {
$cols = '(*bad_id, good_id)';
}
$sql = 'INSERT IGNORE INTO char_code_bad_link SET $cols\nVALUES ($values)';
$result = mysql_query($sql) or die(mysql_error());
}

$redirect = 'charlist.php';
break;

case "Delete Powers":
if ($powers != '') {
$powerlist = implode(',', $powers);

$sql = 'DELETE FROM char_power WHERE id IN ($powerlist*)';
$result = mysql_query($sql) or die(mysql_error());
}

$sql = 'DELETE FROM char_power_link\nWHERE power_id IN ($powerlist*)';
$result = mysql_query($sql) or die(mysql_error());
}

$redirect = 'poweredit.php';
break;

case "Add Power":
if ($newpower != '') {
$sql = 'INSERT IGNORE INTO char_power (id, power)\nVALUES (NULL, '$newpower*)';
$result = mysql_query($sql) or die(mysql_error());
}

$redirect = 'poweredit.php';
break;

default:

$redirect = 'charlist.php';
break;
}
header("Location: $redirect");
?
```

262