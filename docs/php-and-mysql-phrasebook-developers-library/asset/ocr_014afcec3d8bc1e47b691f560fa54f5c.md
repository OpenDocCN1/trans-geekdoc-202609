selection in a cookie, using the include file getFormData.inc.php, as shown in the following code:

```
<?php
    require_once 'getFormData.inc.php';
?>
...
<input type="radio" name="groupname" value="php52"
<?php
    if (getFormDataPOST('groupname') == 'php52') {
        echo 'checked="checked" ';
    }
?>/>PHP 5.2
<input type="radio" name="groupname" value="php53"
<?php
    if (getFormDataPOST('groupname') == 'php53') {
        echo 'checked="checked" ';
    }
?>/>PHP 53
<input type="radio" name="groupname" value="php54"
<?php
    if (getFormDataPOST('groupname') == 'php54') {
        echo 'checked="checked" ';
    }
?>/>PHP 5.4
```

# Preselecting Check Boxes

```
<input type="checkbox" name="boxname" value="yes"
<?php
    if (isset($_POST['boxname']) && $_POST['boxname']
    == 'yes') {
        echo 'checked="checked" ';
    }
?>/>I agree. ...
```