```
if (getFormDataPOST('listname') == 'php5.4') {
    echo ' selected="selected"';
}
?>PHP 5.4</option>
</select>
```

# Preselecting Multiple Selection Lists

```
<select name="multilistname[]" multiple="multiple" size="3">
<option value="php52"><?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php52',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 5.2</option>
<option value="php53"><?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php53',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 5.3</option>
<option value="php54"><?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php54',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 5.4</option>
</select>
```