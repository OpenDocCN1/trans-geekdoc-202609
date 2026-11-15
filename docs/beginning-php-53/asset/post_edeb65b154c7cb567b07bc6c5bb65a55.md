
## Chapter 16

## Exercise 1 Solution

To write a function that calculates the number of weekdays in a given month, you can use the following approach:

- 1. Calculate the total number of days in the month.
- 2. Loop through each day and test whether it is a weekday. If so, increment a counter.
- 3. Return the counter value.

Here is a possible solution:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Number of weekdays in a month</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Number of weekdays in a month</h1>
<?php
function weekdaysInMonth( $year, $month ) {
$date = mktime( 0, 0, 0, $month, 1, $year );
$daysInMonth = idate( "t", $date );
$weekdays = 0;
for ( $d = 1; $d <= $daysInMonth; $d++ ) {
$date = mktime( 0, 0, 0, $month, $d, $year );
$dayOfWeek = idate( "w", $date );
if ( $dayOfWeek != 0 && $dayOfWeek != 6 ) $weekdays++;
}
return $weekdays;
}
$weekdays = weekdaysInMonth( 1997, 3 );
echo "<p>March 1997 contained $weekdays weekdays.</p>";
?>
</body>
</html>
```

## Exercise 2 Solution

It's easy to modify the contact form script to allow the visitor to email any recipient. All you need to do is add in a field for the recipient's email address, then pass that email address to the `mail()` function. For the carbon-copy recipient, you can add an optional field for the CC email address. Then, if the field was filled in, you can add an appropriate `Cc:` header to the message.

Here's a version of the `contact.php` script incorporating these changes (changed lines are highlighted):

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Send an Email Message</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
.error { background: #d33; color: white; padding: 0.2em; margin: 0.2em 0 0.2em 0;
font-size: 0.9em; }
fieldset { border: none; padding: 0; }
ol {list-style-type: none; padding: 0; margin: 0; }
input, select, textarea { float: none; margin: 1em 0 0; width: auto; }
div.element { float: right; width: 57%; }
div.element label { display: inline; float: none; }
select { margin-right: 0.5em; }
span.required { display: none; }
</style>
</head>
<body>
<h1>Send an Email Message</h1>
<?php
require_once ( "HTML/QuickForm.php" );
require_once ( "HTML/QuickForm/Renderer/Tableless.php" );
$form = new HTML_QuickForm( "form", "post", "exercise2.php", "", array( "style" =>
"width: 30em;" ), true );
$form->removeAttribute( "name" );
$form->setRequiredNote( "" );
$form->addElement( "text", "firstName", "First name" );
$form->addElement( "text", "lastName", "Last name" );
$form->addElement( "text", "emailAddress", "Email address" );
$form->addElement( "text", "toEmailAddress", "To" );
$form->addElement( "text", "ccEmailaddress", "CC (optional)" );
$form->addElement( "text", "subject", "Message subject" );
$form->addElement( "textarea", "message", "Message", array( "rows" => 10, "cols" =>
50 ) );
$form->addElement( "submit", "sendButton", "Send Message" );
$form->addRule( "firstName", "Please enter your first name", "required" );
$form->addRule( "firstName", "The First Name field can contain only letters,
 digits, spaces, apostrophes, and hyphens", "regex", "/^[ \'\\.-a-zA-Z0-9-+$/" );
$form->addRule( "lastName", "Please enter your last name", "required" );
$form->addRule( "lastName", "The Last Name field can contain only letters, digits,
 spaces, apostrophes, and hyphens", "regex", "/^[ \'\\.-a-zA-Z0-9-+$/" );
$form->addRule( "emailAddress", "Please enter an email address", "required" );
$form->addRule( "emailAddress", "Please enter a valid email address", "email" );
$form->addRule( "toEmailAddress", "Please enter an email address", "required" );
$form->addRule( "toEmailAddress", "Please enter a valid email address", "email" );
$form->addRule( "toEmailAddress", "Please enter a valid email address", "email" );
$form->addRule( "ccEmailAddress", "Please enter a valid email address", "email" );
$form->addRule( "subject", "Please enter a message subject", "required" );
$form->addRule( "subject", "Your subject can contain only letters, digits, spaces,
 apostrophes, commas, periods, and hyphens", "regex", "/^[ \'\\.,\\-a-zA-Z0-9-+$/" );
$form->addRule( "message", "Please enter your message", "required" );
if ( $form->isSubmitted() and $form->validate() ) {
 $form->process( "sendMessage" );
} else {
echo "<p>Please fill in all the fields below ( CC field is optional), then click
 Send Message to send your email.</p>";
$renderer = new HTML_QuickForm_Renderer_Tableless();
$form->accept( $renderer );
echo $renderer->toHtml();
}
function sendMessage( $values ) {
$headers = "From: ". $values['firstName'] . " ". $values['lastName'] . " <".
 $values['emailAddress'] . " >\r\n";
if ( $values["ccEmailAddress"] ) $headers .= "Cc: ". $values["ccEmailAddress"] .
 "\r\n";
if ( mail( $values["toEmailAddress"], $values["subject"], $values["message"],
 $headers ) ) {
echo "<p>Your message has been sent.</p>";
} else {
echo '<p>Sorry, your message could not be sent.</p>';
echo '<p>Please <a href="javascript:history.go(-1)">go back</a> to the form,
 check the fields and try again.</p>';
}
}
?>
</body>
</html>
```

## Chapter 17

## Exercise 1 Solution

The only trick to successfully complete this exercise is to remember that the top-left corner of an image is (0,0). This means that you must remember to subtract 1 from the width and height of the image to get the rightmost position and bottommost position of the image, respectively. Here's the code to draw the black border:

```php
<?php
$myImage = imagecreatefromjpeg( "hook.jpg" );
$black = imagecolorallocate( $myImage, 0, 0, 0 );
$width = imagesx( $myImage );
$height = imagesy( $myImage );
imagerectangle( $myImage, 0, 0, $width-1, $height-1, $black );
header( "Content-type: image/jpeg" );
imagejpeg( $myImage );
imagedestroy( $myImage );
?>
```

If your script was similar to this one, your output should include a nice clean border around the image, like the one shown in Figure A-1.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_745_0.png)

Figure A-1

## Exercise 2 Solution

There are two obvious ways that you can graphically display disk space. The quickest and easiest way is to create a simple horizontal scale: a rectangular shape that is made up of two blocks of color, one color representing the used space on the disk and the other representing the free space. This gives you a nice quick overview of your disk usage. The code for doing this follows.

It's always good practice to store the width and height of your images in variables within the script. Then if you want to change the size of the image you can do so easily at the beginning of the script and any calculations you do with the image width and height are automatically updated.

```php
<?php
$iWidth = 500;
$iHeight = 50;
$myImage = imagecreate( $iWidth, $iHeight );
$white = imagecolorallocate( $myImage, 255, 255, 255 );
$black = imagecolorallocate( $myImage, 0, 0, 0 );
$red = imagecolorallocate( $myImage, 255, 0, 0 );
$green = imagecolorallocate( $myImage, 0, 255, 0 );
$diskTotal = disk_total_space( "/" );
$diskFree = disk_free_space( "/" );
imagerectangle( $myImage, 0, 0, $iWidth - 1, $iHeight - 1, $black );
```
