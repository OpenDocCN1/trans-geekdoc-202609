process is complete and the user can be congratulated for the successful completion of the form. Otherwise, the form is displayed again.

```
```php
<?php
$ok = false;
if (isset($_POST['Submit']) &&
    isset($_POST['multilistname'])) {
    if (is_array($_POST['multilistname'])) {
        for ($i=0; $i <
            count($_POST['multilistname']); $i++) {
            if ($_POST['multilistname'][$i] != '') {
                $ok = true;
                break;
            }
        }
    }
}

if ($ok) {
    echo '<h1>Thank you for filling out this
        form!</h1>';
} else {
?>
<form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
?>">
    <select name="multilistname[]"
        multiple="multiple" size="5">
    </select>
<br />
    <input type="submit" name="Submit" />
</form>
<?php
}
?>
```
```