# Chapter 9

```
if (mysql_num_rows($result) > 0) {
While ($row = mysql_fetch_assoc($result)) {
  Enemies[$row['id']] = 'selected';
}
}
?
```

```
<html>
<head>
<title>Character Editor</title>
</head>
<body>
<img src="CBA_Tiny.gif" align='left' hspace='10'>
<h1>Comic Book<br />/Appreciation</h1><br />
<h3>?php echo $subhead;??>
```

```
<form action='char_transact.php' name='theform' method='post'>
<table border='0' padding='15' bgcolor='?php echo $tablebg;?>
<tr>
<td>Character Name:</td>
<input type='text' name='alias' size='41' value='?php echo $ch['alias'];?'></td>
</tr>
<tr>
<td>Real Name:</td>
<input type='text' name='name' size='41' value='?php echo $ch['name'];?'></td>
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
```

```
<tr>
<td>Lair Location:<br /><font size=2 color='#990000'>
(address,<br />city, state, zip)</font></td>
</tr>
```

258