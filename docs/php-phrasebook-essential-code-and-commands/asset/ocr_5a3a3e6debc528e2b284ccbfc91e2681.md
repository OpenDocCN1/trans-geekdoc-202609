```
if (getFormDataPOST('listname') == 'php3') {
    echo ' selected="selected"';
}
?>>PHP 3</option>
<option value="php4"><?php
if (getFormDataPOST('listname') == 'php4') {
    echo ' selected="selected"';
}
?>>PHP 4</option>
<option value="php5"><?php
if (getFormDataPOST('listname') == 'php5') {
    echo ' selected="selected"';
}
?>>PHP 5</option>
</select>
```

*Prefilling Selection Lists (select-cookie.php; excerpt)*

# Preselecting Multiple Selection Lists

```
if (isset($_POST['multilistname']) &&
in_array('php4', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
```

When it comes to prefilling form elements, multiple selection lists are the most difficult ones to implement. This is because in $_GET or $_POST, you have an array of chosen options; so you cannot just compare strings, but you have to search for the specified value in the array. Luckily, PHP offers something suitable in the form of the in_array() function. So, the effort required is not much more than with the other form elements: If the current value is in $_GET/$_POST, print out the selected attribute.