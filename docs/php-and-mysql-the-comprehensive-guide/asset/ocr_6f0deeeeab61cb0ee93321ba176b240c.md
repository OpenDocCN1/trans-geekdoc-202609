```
```php
$id_POST = $_POST["id"] ?? "";

if ($id_GET != "" && $id_POST == "") {
?>
<form method="post">
<input type="hidden" name="id"
value="<?php echo htmlspecialchars($id_GET); ?> />
<input type="submit" value="Confirm deletion" />
</form>
<?php
}

if ($id_GET != "" && $id_POST != "") {
    delete_entry($id_POST); //yet to be implemented ;-)
    echo "<b>Entry deleted!</b>";
}
?>
</body>
</html>
```
```

# Listing 32.5 A (Lousy) Approach to Deleting Data ("delete.php")

![](bbox=[0.15, 0.49, 0.78, 0.59])

# Figure 32.5 First the User Confirms the Deletion ...

![](bbox=[0.15, 0.64, 0.78, 0.76])

# Figure 32.6 ... and Only Then Does the Web Server Execute It

The approach is not only bad, but also fatal, because user data is also used here without being checked. Just because POST data cannot be transmitted so easily and conveniently in the URL does not mean that it is not possible to forge the HTTP request. In this case, there is even a very simple way to trick the delete.php script: