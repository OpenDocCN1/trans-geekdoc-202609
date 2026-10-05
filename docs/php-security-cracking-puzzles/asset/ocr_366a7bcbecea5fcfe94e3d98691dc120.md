```
fwrite($fd,$str);
close($fd);
...
?>
```

As you can see in Listing II.7.3, the $_POST['pass'] is processed by the md5() function before it is saved in the file.

Now, when passwords are encrypted, the user authorization system (Listings II.7.1 and II.7.2) must be modified. A block in Listing II.7.1 must be modified as shown in Listing II.7.4 in bold.

# Listing II.7.4. The modified user registration code

```
<?php
if(md5($_POST['pass']) != $temp['password'][$index])
{
    exit("Wrong password!");
}
// If the correct password is entered,
// and displaying the form for editing data
include "2.php"; // The handler of the second HTML form
?>
<table>
<form method="post">
<input type="hidden" name="name"
value='<?php htmlspecialchars($temp['name'][$index]); ?>'>
<input type="hidden" name="pass"
value='<?php htmlspecialchars($_POST[pass]); ?>'>
<input type="hidden" name="edit" value=edit
<tr>
<td>Password:</td>
<td><input type="password" name="passw"
value='<?php htmlspecialchars($_POST[pass]); ?>'></td>
</tr>
<tr>
<td>Password:</td>
<td><input type="password" name="pass again"
value='<?php htmlspecialchars($_POST[pass]); ?>'></td>
</tr>
```