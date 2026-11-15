```
</tr>
<?php
for ( $i = 1; $i <= 10; $i++ ) {
$oddEven = ( $i % 2 == 0 ) ? "Even" : "Odd";
switch ( $i ) {
case 2:
case 3:
case 5:
case 7:
$prime = "Yes";
break;
default:
$prime = "No";
break;
}
?>
<tr>
<td><?php echo $i?></td>
<td><?php echo $oddEven?></td>
<td><?php echo $prime?></td>
</tr>
<?php
}
?>
</table>
</body>
</html>
```

# Exercise 2 Solution

The trick here is to store two sets of pigeon coordinates representing the two pigeons, and then expand both the “flying” logic and the loop conditions to allow for both pigeons. For example, the first do . . . while loop should only exit once both pigeons are positioned more than half the map size away from the home base, and the second do...while loop should exit when both pigeons have flown home. Therefore the loop conditions and decisions within the script need to be a bit more complex:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Homing Pigeons Simulator</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
div.map { float: left; text-align: center; border: 1px solid #666;
background-color: #fcfcfc; margin: 3px; padding: 1em; }
span.home, span.pigeon { font-weight: bold; }
span.empty { color: #666; }
</style>
</head>
<body>
```