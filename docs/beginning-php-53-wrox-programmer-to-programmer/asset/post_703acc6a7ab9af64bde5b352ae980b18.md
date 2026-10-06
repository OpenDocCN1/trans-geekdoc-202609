
# Part III: Using PHP Practice

## Adding More Common Code

Because your members' pages are in a subfolder inside your book club folder, you need to modify the displayHeader() function inside common.php to change the URL of the common.css style when called from a page within the members' area. Change the first line of the function to:

```php
function displayHeader($pageTitle, $membersArea = false ) {
```

Now, within the function, change the line that this shows:

```php
<link rel="stylesheet" type="text/css" href="<?php if ($membersArea) echo "../common.css"; ?>" />
```

This adds an extra "../" to the common.css URL if a second argument is passed to the function.

Next, add a function to check if a member is logged in. This will be called from every page in the members' area. If a user who isn't logged in attempts to access a page in the members' area, you want to redirect them to the login page. Add the following checkLogin() function after the setLocation() function in your common.php file:

```php
function checkLogin() {
    session_start();
    if (!$_SESSION["member"] || $_SESSION["member"] != Member::getMember(
$_SESSION["member"]->getValue("id"))) {
        $_SESSION["member"] = '';
        header('Location: login.php');
        exit;
    } else {
        $logEntry = new LogEntry(array (
            "memberId" => $_SESSION["member"]->getValue("id"),
            "pageUrl" => basename($_SERVER["PHP_SELF"])
        ));
        $logEntry->record();
    }
}
```

This makes sure a PHP session is active with session_start(), then checks to see if there's a Member object stored in the member element of the $_SESSION superglobal array; this indicates that a member is logged in, as you see in the next section. If a Member was found, it is reloaded from the database by Member::getMember(). This not only ensures the data is in the current, but also makes the currently logged-in member does exist in the members table (if the member was deleted while they were logged in, they shouldn't be allowed to continue using the system).

If the $_SESSION_element was not found, or the Member object it contained no longer exists in the database, the $_SESSION_element is cleared (to save having to look the member up again), the user is redirected to the login page using the PHP header() function, and the application is exiting without browser. The PHP exit command (prevents any of the header content from being sent). If the Member object was found, the page is viewed by creating a new LogEntry object, populating it with the logged-in member's ID and the current page URL, and calling the object's record() method.

## Chapter 14: Manipulating MySQL Data with PHP

The page URL is retrieved from the "PHP_SELF" element in the $_SERVER superglobal:

```php
"pageUrl" => basename($_SERVER["PHP_SELF"])
```

$_SERVER is another useful superglobal, similar to the ones encountered in Chapters 7 and 9. It stores various values related to the Web server and script environment. The "PHP_SELF" element stores the URL of the current page relative to the top level of the server. For example, if a PHP script at http://www.example.com/myscripts/script.php is viewed, $_SERVER["PHP_SELF"] is set to /myscripts/script.php. For the purposes of this application, you only want to store the filename of the page — for example, diary.php — so use PHP's basename() function to remove the path of the URL.

You looked at sessions in Chapter 10, and you look at the $_SERVER superglobal in more detail in Chapter 16.

## Writing the Login Page Script

Now you've updated your classes and code, you're ready to create the script to display and handle the member login page. First, create a members folder within your book_club folder; this folder will hold not only the login script, but also the protected pages of members area. With this members folder, create the following script and call it login.php:

```php
<?php
require_once "../common.inc.php";
session_start();

if ( isset($_POST['action']) && $_POST['action']) == "login" ) {
    processForm();
} else {
    displayForm(array(), array(), new Member(array()) );
}

function displayForm($errorMessages, $missingFields, $member) {
    displayHeader("Login to the book club members' area", true);
}

if ($errorMessages) {
    foreach ($errorMessages as $errorMessage) {
        echo $errorMessage;
    }
} else {
    <p>To access the members' area, please enter your username and password below click Login.</p>
}
?>
<form action="login.php" method="post" style="margin-bottom: 50px">
    <div style="width:300px">
        <input type="hidden" name="action" value="login" />
    </div>
    <label for="username"><?php validateField("username", $missingFields); ?>Username</label>
```

<input type="text" name="$username" id="username" value="<?php
echo $getValueEncoded( '$username' ) ?> />

<label for="password"><?php if ( $missingFields ) echo 'class="error"'; ?>password</label>
<input type="password" name="$password" id="password" value="" />

<div style="color: blue;">
<input type="submit" name="$submitButton" id="submitButton" />
</div>
</div>
</form>

<?php
displayPageFooter();
}

function processForm() {
  $requiredFields = array( 'username', 'password' );
  $missingFields = array();
  $errorMessages = array();

  $member = new Member(
    'username' => isset( $_POST['$username'] ) ? preg_replace( "/[^\\-a-zA-Z0-9]\\/", "", $_POST['$username'] ) : "",
    'password' => isset( $_POST['$password'] ) ? preg_replace( "/[^\\-a-zA-Z0-9]\\/", "", $_POST['$password'] ) : ""
  );

  foreach ( $requiredFields as $requiredField ) {
    if ( !$member->getValue( $requiredField ) ) {
      $missingFields[] = $requiredField;
    }
  }

  if ( $missingFields ) {
    $errorMessages[] = '<p class="error">There are missing fields in the form you submitted. Please complete the fields highlighted below and click Login to resend the form.</p>';
  } elseif ( $loggedInMember = $member->authenticate() ) {
    $errorMessages[] = '<p class="error">Sorry, we could not log you in with those details. Please check your username and password, and try again.</p>';
  }

  if ( $errorMessages ) {
    displayForm( $errorMessages, $missingFields, $member );
  } else {
    $_SESSION["member"] = $loggedInMember;
    displayThanks();
  }
}

function displayThanks() {

```php
displayHeader( "Thanks for logging in!", true);
?>
<p>Thank for logging in. Please proceed to the <a href="index.php?members">members area</a></p>
<?php
displayFooter();
?>
```

The structure of this script is similar to the register.php script you created earlier. If the form was submitted, processForm() is called; otherwise, displayForm() is called. displayForm() displays the login form, which contains username and password fields, as well as a Login Button. Any error message is displayed at the top of the form, and any fields are highlighted in red.

processForm() checks the submitted login details and, if valid, logs the in. First it creates a new Member object populated with the supplied username and password (filtered to remove any invalid characters). If either field failed, an error message is generated. The script validates the entered username and password by calling the Member object's authenticate() method:

```php
else if (!$loggedInMember = $member->authenticate()) {
```

Remember that this method returns a Member object representing the logged-in member if the username and password match; otherwise it returns nothing. So if $loggedInMember is false, the login failed and an error message is generated:

```php
$errorMessages[] = <p class="error">Sorry, we could not log you in with those details. Please check your username and password, and try again.</p>
```

If any error messages were generated, the form is redisplayed. Otherwise, all well so, the logged-in Member object is stored in the session, and a thank-you message is displayed:

```php
if ($errorMessages) {
    displayForm( $errorMessages, $missingFields, $member);
} else {
    $_SESSION["member"] = $loggedInMember;
    displayThanks();
}
```

By storing a Member object representing the logged-in member in the $_SESSION array, all scripts in the application can easily test if a member is currently logged in, and identify the logged-in member, simply by looking in the session data.

The final function, displayThanks(), thanks the member for logging in and provides them with a link to take them to the main page of the members' area, index.php.
