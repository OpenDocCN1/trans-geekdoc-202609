Although some Web sites pretend to group check boxes like radio buttons, this is technically not true. Every check box stands on its own; therefore, they all should have different names; it would not make sense to give them identical names. Then each check box can be treated individually: Check for the associated value attribute, and then print out the checked HTML attribute you find a match.

When using cookie data (if available), the code changes slightly:

```
<?php
require_once 'getFormData.inc.php';
?>
...
<input type="checkbox" name="boxname" value="yes"
<?php
if (getFormDataPOST('boxname') == 'yes') {
    echo 'checked="checked" ';
}
?>/>I agree.
```

# Preselecting Selection Lists

```
<select name="listname">
<option value="php52"><?php
if (isset($_POST['listname']) && $_POST['listname'] == 'php52') {
    echo ' selected="selected"';
}
?>>PHP 5.2</option>
<option value="php53"><?php
if (isset($_POST['listname']) && $_POST['listname'] == 'php53') {
```