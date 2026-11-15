The page URL is retrieved from the "PHP_SELF" element in the $_SERVER superglobal array:

```
"pageUrl" => basename( $_SERVER["PHP_SELF"] )
```

$_SERVER is another useful superglobal, similar to the ones you encountered in Chapters 7 and 9. It stores various values related to the Web server and script environment. The "PHP_SELF" element stores the URL of the current page relative to the top level of the Web site. For example, if a PHP script at http://www.example.com/myscripts/script.php is viewed, $_SERVER[ "PHP_SELF" ] is set to /myscripts/script.php. For the purposes of this application, you only want to store the filename of the page — for example, diary.php — so you use PHP's basename() function to remove the path portion of the URL.

You looked at sessions in Chapter 10, and you look at the $_SERVER superglobal in more detail in Chapter 16.

# Writing the Login Page Script

Now that you've updated your classes and common code, you're ready to create the script to display and handle the member login page. First, create a members folder within your book_club folder; this folder will hold not only the login script, but also the protected pages of the members' area. Within this members folder, create the following script and call it login.php:

```
<?php
require_once( "../common.inc.php" );
session_start();

if ( isset( $_POST["action"] ) and $_POST["action"] == "login" ) {
    processForm();
} else {
    displayForm( array(), array(), new Member( array() ) );
}

function displayForm( $errorMessages, $missingFields, $member ) {
    displayPageHeader( "Login to the book club members' area", true );

    if ( $errorMessages ) {
        foreach ( $errorMessages as $errorMessage ) {
            echo $errorMessage;
        }
    } else {
?>
<p>To access the members' area, pleas enter your username and password
below then click Login.</p>
<?php } ?>

<form action="login.php" method="post" style="margin-bottom: 50px;">
    <div style="width: 30em;">
        <input type="hidden" name="action" value="login" />

        <label for="username"><?php validateField( "username", $missingFields )
        ?>>Username</label>
```