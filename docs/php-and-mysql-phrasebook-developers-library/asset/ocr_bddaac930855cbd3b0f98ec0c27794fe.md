The return values of those validations may be a bit surprising, but they are aligning with the return valid of the other filters: The validated (in this case, unchanged) data is returned. If a validation fails, however, the functions return false. So, after validating the input or the variable, you either have good data or no data.

# Writing All Form Data into a File

```
```php
<?php
if (isset($_POST['Submit']) &&
    isset($_POST['fieldname']) &&
    trim($_POST['fieldname']) != '') {
    echo '<h1>Thank you for filling out this form!</h1>';
    $data = '';
    $data = @file_get_contents('formdata.txt');
    if ($data != '') {
        $data = unserialize($data);
    }
    $data[] = $_POST;
    file_put_contents('formdata.txt',
        serialize($data));
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
...
</form>
<?php
}
?>
```
```