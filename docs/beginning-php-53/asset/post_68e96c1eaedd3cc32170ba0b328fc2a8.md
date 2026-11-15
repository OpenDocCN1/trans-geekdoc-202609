
```php
function displayForm( $missingFields ) {
?>
<h1>Membership Form</h1>

<?php if ( $missingFields ) { ?>
<p class="error">There were some problems with the form you submitted.
Please complete the fields highlighted below and click Send Details to
resend the form.</p>
<?php } else { ?>
<p>Thanks for choosing to join The Widget Club. To register, please
fill in your details below and click Send Details. Fields marked with an
asterisk (*) are required.</p>
<?php } ?>

<form action="registration.php" method="post">
<div style="width: 30em;">

<label for="firstName"<?php validateField( "firstName",
$missingFields ) ?>>First name *</label>
<input type="text" name="firstName" id="firstName"
value="<?php setValue( "firstName" ) ?>" />

<label for="lastName"<?php validateField( "lastName",
$missingFields ) ?>>Last name *</label>
<input type="text" name="lastName" id="lastName" value=
"<?php setValue( "lastName" ) ?>" />

<label for="password1"<?php if ( $missingFields ) echo
' class="error" ?>>>Choose a password *</label>
<input type="password" name="password1" id="password1" value="" />
<label for="password2"<?php if ( $missingFields ) echo
' class="error" ?>>>Retype password *</label>
<input type="password" name="password2" id="password2" value="" />

<label><?php validateField( "gender", $missingFields ) ?>>Your
gender: *</label>
<label for="genderMale">Male</label>
<input type="radio" name="gender" id="genderMale" value=
"M"<?php setChecked( "gender", "M" )?> />
<label for="genderFemale">Female</label>
<input type="radio" name="gender" id="genderFemale" value=
"F"<?php setChecked( "gender", "F" )?> />

<label for="favoriteWidget">What's your favorite widget? </label>
<select name="favoriteWidget" id="favoriteWidget" size="1">
<option value="superWidget"<?php setSelected( "favoriteWidget",
"superWidget" ) ?>>The SuperWidget</option>
```

```php
<option value="megaWidget"<?php setSelected( "favoriteWidget",
"megaWidget" ) ?>>The MegaWidget</option>
<option value="wonderWidget"<?php setSelected( "favoriteWidget",
"wonderWidget" ) ?>>The WonderWidget</option>
</select>

<label for="newsletter">Do you want to receive our newsletter?
</label>
<input type="checkbox" name="newsletter" id="newsletter" value="yes"
<?php setChecked( "newsletter", "yes" ) ?> />

<label for="comments">Any comments?</label>
<textarea name="comments" id="comments" rows="4" cols="50"><?php
setValue( "comments" ) ?></textarea>

<div style="clear: both;">
<input type="submit" name="submitButton" id="submitButton" value=
"Send Details" />
<input type="reset" name="resetButton" id="resetButton"
value="Reset Form" style="margin-right: 20px;" />
</div>

</div>
</form>
<?php
}
?>
function displayThanks( ) {
?>
<h1>Thank You</h1>
<p>Thank you, your application has been received.</p>
<?php
}
?>
</body>
</html>
```

Now browse the script's URL in your Web browser. You'll see a blank registration form. Try submitting an empty form by clicking Send Details. You should see an error message, with the missing required fields highlighted. If you fill in some values and resubmit, the script keeps checking to see if you've filled in the required fields. If not, it redisplays the form, including any data you've already entered, and highlights the missing fields, as shown in Figure 9-7.

Finally, try filling in all the required fields and clicking Send Details again. This time, you should see the thank-you message.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_283_0.png)

Figure 9-7

## How It Works

The script kicks off with the standard XHTML page header. It includes an additional CSS class for the red error boxes:

```html
<style type="text/css">
.error { background: #d33; color: white; padding: 0.2em; }
</style>
```

Next, the script checks to see if the form has been submitted. It does this by looking for the existence of the submitButton field. If present, it means that the Send Details button has been clicked and the form received, and the script calls a processForm() function to handle the form data. However, if the form hasn't been displayed, it calls displayForm() to display the blank form, passing in an empty array (more on this in a moment):

```php
if ( isset( $_POST["submitButton"] ) ) {
    processForm();
} else {
    displayForm( array() );
}
```

Next the script defines some helper functions. validateField() is used within the form to display a red error box around a form field label if the required field hasn’t been filled in. It’s passed a field name, and a list of all the required fields that weren’t filled in. If the field name is within the list, it displays the markup for the error box:

```php
function validateField( $fieldName, $missingFields ) {
    if ( in_array( $fieldName, $missingFields ) ) {
        echo ' class="error"';
    }
}
```

setValue() is used to prefill the text input fields and text area field in the form. It expects to be passed a field name. It then looks up the field name in the $_POST superglobal array and, if found, it outputs the field’s value:

```php
function setValue( $fieldName ) {
    if ( isset( $_POST[$fieldName] ) ) {
        echo $_POST[$fieldName];
    }
}
```

setChecked() is used to preselect checkboxes and radio buttons by inserting a checked attribute into the element tag. Similarly, setSelected() is used to preselect an option in a select list via the selected attribute. Both functions look for the supplied field name in the $_POST array and, if the field is found and its value matches the supplied field value, the control is preselected:

```php
function setChecked( $fieldName, $fieldValue ) {
    if ( isset( $_POST[$fieldName] ) && $_POST[$fieldName] == $fieldValue ) {
        echo ' checked="checked"';
    }
}
```

```php
function setSelected( $fieldName, $fieldValue ) {
    if ( isset( $_POST[$fieldName] ) && $_POST[$fieldName] == $fieldValue ) {
        echo ' selected="selected"';
    }
}
```

Next comes the form handling function, processForm(). This sets up an array of required field names, and also initializes an array to hold the required fields that weren’t filled in:

```php
function processForm() {
    $requiredFields = array( "firstName", "lastName", "password1", "password2",
                             "gender" );
    $missingFields = array();
}
```

Now the function loops through the required field names and looks for each field name in the `$_POST` array. If the field name doesn't exist, or if it does exist but its value is empty, the field name is added to the `$missingFields` array:

```php
foreach ( $requiredFields as $requiredField ) {
    if ( !isset( $_POST[$requiredField] ) or !$_POST[$requiredField] ) {
        $missingFields[] = $requiredField;
    }
}
```

If missing fields were found, the function calls the `displayForm()` function to redisplay the form, passing in the array of missing field names so that `displayForm()` can highlight the appropriate fields. Otherwise, `displayThanks()` is called to thank the user:

```php
if ( $missingFields ) {
    displayForm( $missingFields );
} else {
    displayThanks();
}
```

The `displayForm()` function itself displays the HTML form to the user. It expects an array of any missing required field names. If this array is empty, the form is presumably being displayed for the first time, so `displayForm()` shows a welcome message. However, if there are elements in the array, the form is being redisplayed because there were errors, so the function shows an appropriate error message:

```php
function displayForm( $missingFields ) {
?>
<h1>Membership Form</h1>

<?php if ( $missingFields ) { ?>
<p class="error">There were some problems with the form you submitted.
Please complete the fields highlighted below and click Send Details to resend
the form.</p>
<?php } else { ?>
<p>Thanks for choosing to join The Widget Club. To register, please fill
in your details below and click Send Details. Fields marked with an asterisk
(*) are required.</p>
<?php } ?>
```

Next, the form itself is displayed. The form uses the post method, and its `action` attribute points back to the script's URL:

```html
<form action="registration.php" method="post">
```

Then each form control is created using HTML markup. Notice how the `validateField()`, `setValue()`, `setChecked()`, and `setSelected()` functions are called throughout the markup in order to insert appropriate attributes into the elements.

With the password fields, it's unwise to redisplay a user's password in the page because the password can easily be read by viewing the HTML source. Therefore, the two password fields are always
