
| Rule Type | Value of $format Argument | Description |
|---|---|---|
| numeric | N/A | The value must be a number. |
| nopunctuation | N/A | The value must not contain punctuation characters. |
| nonzero | N/A | The value must be a number that doesn't begin with zero. |
| compare | $comparisonType | Compares two field values (pass a two-element array of element names as the first parameter to addRule()). Good for checking whether two password fields match. Allowed values for $comparisonType: "eq" or "==": Values must be the same (default setting) "neq" or "!=": Values must be different "gt" or ">": First value must be greater than the second "gte" or ">=": First value must be greater than or equal to the second "lt" or "<": First value must be less than the second "lte" or "<=": First value must be less than or equal to the second |
| callback | $functionName | Runs a callback function called $functionName to do the check. The function should expect the value to check as an argument and return true if the value passed the check, or false otherwise. |
| uploadedfile | N/A | The file must have been uploaded. (For file upload fields.) |
| maxfilesize | $max | The uploaded file must not exceed $max bytes in length. (For file upload fields.) |
| mimetype | $type | The uploaded file must be of MIME type $type. (For file upload fields.) |
| filename | $regex | The uploaded file's name must match the regular expression $regex. (For file upload fields.) |

For example, you could add a rule to check that the submitted username field is no longer than ten characters:

```
$form->addRule( "username", "Username must be no longer than 10 characters", 'maxlength', 10 );
```

## Try It Out A Registration Form using HTML_QuickForm

To show just how powerful and useful HTML_QuickForm is, in this example you rewrite the register.php book club registration script from Chapter 14, using HTML_QuickForm to handle the form display and validation.

Before you start, though, install an additional PEAR package called HTML_QuickForm_Renderer_Tablessless. By default, HTML_QuickForm outputs each form using an HTML table to hold the form fields and labels. HTML forms created without using tables are more flexible and can be easier to restyle. What's more, the tables-based forms produced by HTML_QuickForm aren't valid XHTML. HTML_QuickForm_Renderer_Tablessless is a renderer class that replaces the default HTML_QuickForm renderer and generates XHTML-compliant, tables-free form markup.

At the time of writing, HTML_QuickForm_Renderer_Tablessless is a beta package, which means it can't be installed using a default PEAR setup:

```
$ pear install --alldeps HTML_QuickForm_Renderer_Tablessless
Failed to download pear/HTML_QuickForm_Renderer_Tablessless within preferred
state "stable", latest release is version 0.6.1, stability "beta", use
"channel://pear.php.net/HTML_QuickForm_Renderer_Tablessless-0.6.1" to install
Cannot initialize 'channel://pear.php.net/HTML_QuickForm_Renderer_Tablessless',
invalid or missing package file
Package "channel://pear.php.net/HTML_QuickForm_Renderer_Tablessless" is not
valid
install failed
$
```

By the time you read this you may find that the package is no longer in beta, in which case you can install it in the normal way — that is, using pear install --alldeps HTML_QuickForm_Renderer_Tablessless. If the package is still in beta, you can install it by specifying the channel explicitly, as follows:

```
$ pear install --alldeps channel://pear.php.net/HTML_QuickForm_Renderer_
Tablessless-0.6.1
downloading HTML_QuickForm_Renderer_Tablessless-0.6.1.tgz ...
Starting to download HTML_QuickForm_Renderer_Tablessless-0.6.1.tgz (6,828
bytes)
......done: 6,828 bytes
install ok: channel://pear.php.net/HTML_QuickForm_Renderer_Tablessless-0.6.1
$
```

Now you're ready to modify the book club application code. First, copy the book_club folder (and its files) that you created in Chapter 14 to a new folder, book_club_2, in your document root. This will preserve your original application files.

Next, open the common.inc.php file inside the book_club_2 folder and modify the CSS in the displayPageHeader() function at the top of the file. This is necessary to make the CSS compatible with the markup produced by HTML_QuickForm. Replace the old displayPageHeader() function with the following:

```
function displayPageHeader( $pageTitle, $membersArea = false ) {
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title><?php echo $pageTitle?></title>
<link rel="stylesheet" type="text/css" href="<?php if ( $membersArea )
echo "../" ?>.common.css" />
<style type="text/css">
th { text-align: left; background-color: #bbb; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
.error { background: #d33; color: white; padding: 0.2em; margin: 0.2em 0 0.2em 0; font-size: 0.9em; }
fieldset { border: none; }
ol {list-style-type: none; }
input, select, textarea { float: none; margin: 1em 0 0 0; width: auto; }
div.element { float: right; width: 57%; }
div.element label { display: inline; float: none; }
</style>
</head>
<body>
<h1><?php echo $pageTitle?></h1>
<?php
}
```

Now, rewrite the register.php script in the book_club_2 folder to use HTML_QuickForm. Replace the old code in the script with the following new code:

```
<?php
require_once( "common.inc.php" );
require_once( "HTML/QuickForm.php" );
require_once( "HTML_QuickForm_Renderer_Tableless.php" );
$form = new HTML_QuickForm( "", "post", "register.php", "",
array( "style" => "width: 30em;", true );
$form->removeAttribute( "name" );
addElements( $form );
addRules( $form );
$form->setRequiredNote( "" );
if ( $form->isSubmitted() && $form->validate() ) {
    $form->process( "processForm" );
    displayThanks();
} else {
    displayPageHeader( "Sign up for the book club!" );
?>
<p>Thanks for choosing to join our book club.</p>
<p>To register, please fill in your details below and click Send Details.</p>
<p>Fields marked with an asterisk (*) are required.</p>
<?php
    $renderer = new HTML_QuickForm_Renderer_Tableless();
    $form->accept( $renderer );
    echo $renderer->toHtml();
    displayPageFooter();
}

function addElements( $form ) {
    $form->addElement( "text", "username", "Choose a username" );
    $password1 = $form->addElement( "password", "password1", "Choose a password" );
    $password1->setValue( "" );
    $password2 = $form->addElement( "password", "password2", "Retype password" );
    $password2->setValue( "" );
    $form->addElement( "text", "emailAddress", "Email address" );
    $form->addElement( "text", "firstName", "First name" );
    $form->addElement( "text", "lastName", "Last name" );
    $genderOptions = array();
    $genderOptions[] = HTML_QuickForm::createElement( "radio", null, null, "Male", "m" );
    $genderOptions[] = HTML_QuickForm::createElement( "radio", null, null, "Female", "f" );
    $form->addGroup( $genderOptions, "gender", "Your gender", "" );
    $member = new Member( array() );
    $form->addElement( "select", "favoriteGenre", "What's your favorite genre?", $member->getGenres() );
    $form->addElement( "textarea", "otherInterests", "What are your other interests?", array( "rows" => 4, "cols" => 50 ) );
    $buttons = array();
    $buttons[] = HTML_QuickForm::createElement( "submit", "submitButton", "Send Details" );
    $buttons[] = HTML_QuickForm::createElement( "reset", "resetButton", "Reset Form" );
    $form->addGroup( $buttons, null, null, "&nbsp;" );
}

function addRules( $form ) {
    $form->addRule( "username", "Please enter a username", "required" );
    $form->addRule( "username", "The username can contain only letters and digits", "alphanumeric" );
    $form->addRule( "password1", "Please enter a password", "required" );
    $form->addRule( "password1", "The password can contain only letters and
```