# Checking Selection Lists

```
isset($_POST['listname']) &&
$_POST['listname'] != ''
```

When it comes to validating a selection list, the approach depends on the type of list:

+   - If it is a list in which only one element may be selected, the list is considered to be filled out incorrectly if
+   - No option in the list is selected
+   - The selected option has an empty string as a value
+   - If it is a list in which multiple elements may be selected, the list is considered to be filled out incorrectly if
+   - No option in the list is selected
+   - All selected options have an empty string as a value

Options with empty strings as values come into play if the list contains functionless dummy entries that have captions such as “Please choose from list.” These list options must not receive a value other than "", so that the validation algorithm can distinguish these entries from reasonable ones.

The listing at the beginning of this phrase validates a single selection list—again including PHP code to pre-fill the list.

```
<?php
if (isset($_POST['Submit']) &&
    isset($_POST['listname']) &&
    $_POST['listname'] != '') {
echo '<h1>Thank you for filling out this
```