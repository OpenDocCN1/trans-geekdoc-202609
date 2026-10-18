# FIGURE 20.2 Select menu with no null option

![](bbox=[0.09, 0.07, 0.79, 0.3])

However, an improvement to our script would be to include a null value for the select menu, such as ‘___’ as a default, for example:

```
<option>---</option>
```

We could then check that the user has selected a title other than this, for example:

```
if ($_POST["submit"] == "___")
    echo "<p>Please select a title.</p>";
```

This would provide a degree of confidence that the user has made an informed choice and not simply clicked submit as a default. The completed script now looks like this:

```
<h2>Please select your title:</h2>

<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><select name='strTitle'>
    <option>---</option>
    <option>Mr</option>
    <option>Miss</option>
    <option>Ms</option>
    <option>Mrs</option>
    <option>Dr</option>
</select></p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-10.php
if (isset($_POST["submit"]) ) {
    if ($_POST["submit"] == "___")
        echo "<p>Please select a title.</p>";
    else {
        $strTitle = $_POST["strTitle"];
        echo "<p>Your title is $strTitle</p>";
    }
}
?>
```