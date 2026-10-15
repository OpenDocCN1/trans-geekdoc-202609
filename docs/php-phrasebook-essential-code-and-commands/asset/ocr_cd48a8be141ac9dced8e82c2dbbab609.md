NOTE
When you submit the form using the keyboard (for example, with the Enter key), both coordinates are 0.

# Checking Mandatory Fields

```
if (isset($_POST['Submit']) &&
    isset($_POST['textfieldname']) &&
    trim($_POST['textfieldname']) != '')
```

When validating a form, most of the time the emphasis is on mandatory fields. You can check if they contain values in two ways:

+   - Check whether the fields exist in $_GET/$_POST
+     ```
+     if (!isset($_GET['fieldname'])) {
+       // Error!
+     }
+     ```
+   - Check whether the values in $_GET/$_POST contain information other than whitespace
+     ```
+     if (trim($_GET['fieldname']) == '') {
+       // Error!
+     }
+     ```

It is very important that you combine both techniques. You always have to check for a field's existence using isset() to avoid error messages when trying to access array values that do not exist. But you always have to check whether there is something within the field apart from whitespace because text fields are always submitted. In addition, when empty, isset() always returns true independent of the field's value.