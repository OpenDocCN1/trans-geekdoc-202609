
```php
digits", "alphanumeric" );
$form->addRule( "password2", "Please retype your password", "required" );
$form->addRule( "password2", "The password can contain only letters and digits", "alphanumeric" );
$form->addRule( array( "password1", "password2" ), "Please make sure you enter your password correctly in both password fields.", "compare" );
$form->addRule( "emailAddress", "Please enter an email address", "required" );
$form->addRule( "emailAddress", "Please enter a valid email address", "email" );
$form->addRule( "firstName", "Please enter your first name", "required" );
$form->addRule( "firstName", "The First Name field can contain only letters, digits, spaces, apostrophes, and hyphens", "regex", "/^[ \\\\-a-zA-Z0-9]+$/" );
$form->addRule( "lastName", "Please enter your last name", "required" );
$form->addRule( "lastName", "The Last Name field can contain only letters, digits, spaces, apostrophes, and hyphens", "regex", "/^[ \\\\-a-zA-Z0-9]+$/" );
$form->addRule( "gender", "Please select your gender", "required" );
$form->addRule( "gender", "The Gender field can contain only 'm' or 'f'", "regex", "/^[mf]$/" );
$member = new Member( array() );
$form->addRule( "favoriteGenre", "The Favorite Genre field can contain only allowed genre values", "regex", "/^(". implode( "|", array_keys( $member->getGenres() ) ). ")$/i" );
$form->addRule( "otherInterests", "The Other Interests field can contain only letters, digits, spaces, apostrophes, commas, periods, and hyphens", "regex", "/^[ \\\\.\\-a-zA-Z0-9]+$/" );
$form->addRule( "username", "A member with that username already exists in the database. Please choose another username.", "callback", "checkDuplicateUsername" );
$form->addRule( "emailAddress", "A member with that email address already exists in the database. Please choose another email address, or contact the webmaster to retrieve your password.", "callback", "checkDuplicateEmailAddress" );
}

function checkDuplicateUsername( $value ) {
return !(boolean) Member::getByUsername( $value );
}

function checkDuplicateEmailAddress( $value ) {
return !(boolean) Member::getByEmailAddress( $value );
}

function processForm( $values ) {
$values["password"] = $values["password1"];
$values["joinDate"] = date( "Y-m-d" );
$member = new Member( $values );
$member->insert();
}
function displayThanks() {
    displayPageHeader( "Thanks for registering!" );
?>
<p>Thank you, you are now a registered member of the book club.</p>
<?php
    displayPageFooter();
}
?>
```

Test the register.php script by opening its URL in your Web browser. You can see from Figure 15-3 that the form looks and behaves much like the form in Chapter 14. The main difference is that validation errors are displayed directly above the form fields, rather than at the top of the form.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_503_0.png)

Figure 15-3

## How It Works

You can see that the structure of this register.php script is quite different than that of the Chapter 14 version. First of all, the script includes the common code file, along with the two PEAR packages, HTML_QuickForm and HTML_QuickForm_Renderer_Tagless.

It then creates a new HTML_QuickForm object with an empty name attribute, a method="post" attribute, an action attribute that points the form back to the script (register.php), an empty target attribute, no additional attributes, and the $trackSubmit property set to true so that the script knows when the form data has been submitted. Once the HTML_QuickForm object has been created, its empty name attribute is removed completely from the form element (this is to ensure that the page is fully XHTML 1.0 compliant).

```php
$form = new HTML_QuickForm( "", "post", "register.php", "", array( "style" => "width: 30em;" ), true );
$form->removeAttribute( "name" );
```

Now the script calls two functions, addElements() and addRules(), that add several elements and validation rules to the $form object (you see how these work in a moment). It also calls the object's setRequiredNote() method to remove the default "** denotes required field" message; this is because the script already displays its own, similar message in the Web page:

```php
addElements( $form );
addRules( $form );
$form->setRequiredNote( "" );
```

The main decision-making logic of the script follows. If the form was submitted, and it passes validation, it is processed by calling the $form object's process() method, passing in the name of the function that will handle the form data (processForm()). Then a thank-you message is displayed:

```php
if ( $form->isSubmitted() && $form->validate() ) {
$form->process( "processForm" );
displayThanks();
}
```

If the form was not submitted, or it was submitted but didn't validate, the form is displayed. To do this, the script first displays the page header by calling the displayPageHeader() function in the common.inc.php file. Next, it creates a new HTML_QuickForm_Renderer_Tabless renderer object, sets the $form object's renderer to this object by calling the $form object's accept() method, and outputs the form by calling the toHtml() method of the renderer object, sending the returned markup to the browser. Finally, it outputs the page footer by calling displayPageFooter():

```php
} else {
displayPageHeader( "Sign up for the book club!" );
?>
<p>Thanks for choosing to join our book club.</p>
<p>To register, please fill in your details below and click Send Details.</p>
<p>Fields marked with an asterisk (*) are required.</p>
<?php
$renderer = new HTML_QuickForm_Renderer_Tabless();
$form->accept( $renderer );
echo $renderer->toHtml();
displayPageFooter();
}
```

Next comes the addElements() function to add the various form fields and controls to the $form object. If you've read the previous few sections, most of this code should be self-explanatory. A couple of the controls warrant special attention though. The two gender radio buttons are created with empty field names and labels, and the script specifies text ( " Male" and " Female") to appear after each button, as well as values for the fields ( "m" and "f"). The two buttons are then added to an array:

```php
$genderOptions = array();
$genderOptions[] = HTML_QuickForm::createElement( "radio", null, null, " Male", "m" );
$genderOptions[] = HTML_QuickForm::createElement( "radio", null, null, " Female", "f" );
```

This array of buttons is then used to create an element group with a name of "gender" and a label of "Your gender". HTML_QuickForm then sets each radio button's field name to the group name of "gender":

```php
$form->addGroup( $genderOptions, "gender", "Your gender", " " );
```

To create the favoriteGenre select field, the script calls the Member::getGenres() method to get the associative array of genre names and values to pass to addElement(). The script needs to create a temporary $member object in order to call Member::getGenres(), because getGenres() isn't a static method:

```php
$member = new Member( array() );
$form->addElement( "select", "favoriteGenre", "What's your favorite genre?", $member->getGenres() );
```

The addRules() function uses the $form object's addRule() method to add validation rules to most of the fields in the form. All required fields are checked against the required rule, and the alphanumeric rule is used on the username and both password fields to make sure they contain only letters and/or digits. In addition, the compare rule is used to check that both password fields contain the same value:

```php
$form->addRule( array( "password1", "password2" ), "Please make sure you enter your password correctly in both password fields.", "compare" );
```

The emailAddress field is, of course, checked using the email rule. The remaining fields — firstName, lastName, gender, favoriteGenre, and otherInterests — are checked against various regular expressions using the regex rule.

Of interest is the code for the favoriteGenre field. This creates a temporary $member object and calls its getGenres() method to retrieve the associative array of allowed genres. It then extracts the genre values with PHP's array_keys() function (which returns an indexed array containing all the keys in a given array), and uses the implode() function to turn the resulting array into a string of |-separated alternative values for plugging into the regular expression:

```php
$member = new Member( array() );
$form->addRule( "favoriteGenre", "The Favorite Genre field can contain only allowed genre values", "regex", "/^(". implode( "|", array_keys( $member->getGenres() ) ). ")$/" );
```
