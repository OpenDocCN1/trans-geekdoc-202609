# Chapter 5

```
<td bgcolor="#ffffff*>
<INPUT type="radio" name="type" value="Movie" CHECKED>
Movie<BR>
<INPUT type="radio" name="type" value="Actor*>
Actor<BR>
<INPUT type="radio" name="type" value="Director*>
Director<BR>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" width="50%*>
Display Debug info
</td>
<td bgcolor="#ffffff" width="50%*>
<INPUT type="checkbox" name="Debug" CHECKED>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" colspan="2" align="center*>
<INPUT type="SUBMIT" name="Submit" value="Search*>
<INPUT type="SUBMIT" name="Submit" value="Add*>
</td>
</tr>
</table>
</form>
</body>
</html>
```

2. Create another file named formprocess3.php and edit it to the following code:

```
<?php
if ($_POST['type'] == "Movie" && $_POST['Movie'] == "*") {
  header("Location:form3.php");
}
$title = $_POST['Submit']" . "*" . $_POST['type']" : "*" . $_POST['Name']";
<html>
<head>
<TITLE><?php echo $title?></TITLE>
</head>
<body>
<?php
if ($_POST['Debug'] == "on") {
<PRE>
<?php
print_r($_POST);
?>
</PRE>
<?php
$name = $_POST['Name'];
$name[0] = strtoupper($name[0]);
```

146