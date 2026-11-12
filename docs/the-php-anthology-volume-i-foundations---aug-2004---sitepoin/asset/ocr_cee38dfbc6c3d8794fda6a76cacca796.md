```
// labelled "Enter your name"
$form->addElement('text', 'firstName', 'Enter your name');

// Add a submit button called submit with "Send" as the text
// for the button
$form->addElement('submit', 'submit', 'Send');

// If the form is submitted...
if (isset($_POST['submit'])) {
    // Display the submitted value "firstName"
    echo 'Hello ' . $form->getSubmitValue('firstName');
} else { // If not submitted, display the form
    $form->display();
}
?>
```

This displays a simple form in which users can enter their names.

Here’s the nicely formatted HTML it generates:

```
<table border="0">
    <form action="/sitepoint/WebPageElements/3.php" method="POST"
    name="quickForm1" target="_self">
    <tr>
        <td align="right" valign="top"><b>Enter your name</b></td>
        <td nowrap="nowrap" valign="top" align="left"><input
        name="firstName" type="text" /></td>
    </tr>
    <tr>
        <td align="right" valign="top"><b></b></td>
        <td nowrap="nowrap" valign="top" align="left"><input
        name="submit" value="Send" type="submit" /></td>
    </tr>
    </form>
</table>
```

In this case, we used the native $_POST variable to determine whether the form
had been submitted. But we don’t have to do it this way. If we apply QuickForm’s
validation functionality, we can use its validate method to check whether the
form has been submitted, and ensure it has been validated correctly, in a single
blow.

Here’s the same form; this time, it uses JavaScript in PHP to check that the name
was entered, and falls back on PHP validation should JavaScript be disabled: