# Prefilling Text Fields and Password Fields

```
<?php
    require_once 'stripFormSlashes.inc.php';
    require_once 'getFormData.inc.php';
?>
...
<input type="text" name="textfieldname"
    value="<?php
        echo
    htmlspecialchars(getFormDataPOST('textfieldname'));
    ?>" />
```

*Prefilling Text Fields (text-cookie.php; excerpt)*

# Prefilling Multiline Text Fields

```
<textarea cols="40" rows="5"
name="areafieldname"><?php
    echo (isset($_POST['areafieldname'])) ?
    htmlspecialchars($_POST['areafieldname']) : '';
?></textarea>
```

With multiline text fields, almost the same approach as with single-line text fields and password fields can be used. The only difference is the location where to put the prefill value: It belongs between <textarea> and </textarea>, as shown in the code.

```
<?php
    require_once 'stripFormSlashes.inc.php';
?>
...
<textarea cols="40" rows="5"
name="areafieldname"><?php
    echo (isset($_POST['areafieldname'])) ?
    htmlspecialchars($_POST['areafieldname']) : '';
?></textarea>
```