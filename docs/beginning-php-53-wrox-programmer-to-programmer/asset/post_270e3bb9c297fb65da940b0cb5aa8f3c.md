
# Part III: Using PHP in Practice

On Windows you can use Windows Explorer to set permissions on the photos folder. Now try running your script in your browser. You should see the form shown in Figure 9-10. Enter your name and choose a JPEG photo to upload, then click Send Photo. You should see a thank-you message along with your uploaded photo, as in Figure 9-11.

![](img/ede05b7b77968b82cbd9a513122fb183_299_0.png)

Figure 9-10

![](img/ede05b7b77968b82cbd9a513122fb183_299_1.png)

Figure 9-11

# Chapter 9: Handling HTML Forms with PHP

### How It Works
The script first checks to see if the form has been submitted by looking for the existence of the sendPhoto submit button field. If the form was submitted, processForm() is called to handle the form; otherwise the form is displayed with displayForm():

```php
if ( isset(\$_POST["sendPhoto"]) ) {
    processForm();
} else {
    displayForm();
}
```

processForm() handles the uploaded file (if any). First it checks to make sure a file was uploaded, and that it uploaded without error:

```php
if ( isset(\$_FILES["photo"]) and \$_FILES["photo"]["error"] == UPLOAD_ERR_OK ) {
```

If the uploaded file is not a JPEG format, the function returns:

```php
if ( \$_FILES["photo"]["type"] != "image/jpeg" ) {
    echo <p>JPEG photos only, thanks!</p>;
}
```

The function then opts to move the file from the temp folder to the photos folder, displaying an error message if there was a problem. If all goes well, the thank-you page is displayed:

```php
else if (!move_uploaded_file(\$_FILES["photo"]["tmp_name"], "photos/" . basename(\$_FILES["photo"]["name"])) ) {
    echo <p>Sorry, there was a problem uploading that photo.</p>;
} else {
    displayThanks();
}
```

Note the use of the basename() function(). This takes a file path and extracts the filename portion of the path. not just the full path of the file when it's uploaded — so the script uses basename() to make that only the filename is used for the file in the photos folder. Furthermore, this prevents inserting malicious characters (for example, "../") into the filename.

The function also displays an error message if no photo was uploaded, or if PHP reported an error in the \$_FILES array:

```php
else { switch(\$_FILES["photo"]["error"]) {
    case UPLOAD_ERR_INI_SIZE:
        $message = "The photo is larger than the server allows.";
        break;
    case UPLOAD_ERR_FORM_SIZE:
        $message = "The photo is larger than the script allows.";
        break;
}
```

```php
case UPLOAD_ERR_NO_FILE:
$message = "No file was uploaded. Make sure you choose a file to upload.";
  break;
  default:
    $message = "Please contact your server administrator for help";
    echo "<p>Sorry, there was a problem uploading that photo. $message</p>";
}
```

The displayForm() function simply displays the file upload form, with a text field for the visitor’s name and a file select field to allow a file to be uploaded. Finally, the displayThanks() function thanks the user, displaying the user’s name (if supplied) and his photo.

# Redirecting after a Form Submission

Before leaving the topic of form handling in PHP, it’s worth mentioning the concept of URL redirection. Though not directly related to forms, redirection is often used within form handling code.

Normally when you run a PHP script — whether by typing its URL, following a link, or submitting a form — the script does its thing, some sorts of response to a Web Page, and exits.

However, by sending a special HTTP header to the browser from the PHP script, you can cause the browser to jump to a new URL after the script has run. This is commonly used within a handler script to redirect the users to a thank-you page after they’ve submitted the form. This means you can keep your thank-you page separate from your PHP script, which makes the page easier to edit and update.

Another good thing about redirecting to a new URL after a form has been submitted is that it prevents users from accidentally resubmitting the form by clicking their Reload or Refresh button. Instead, all that happens is they reload the page they were redirected to.

Redirection is as simple as outputting a Location: HTTP header, including the URL you want to redirect to in PHP using the built-in header() function. Here’s how to redirect to a page called thanks.html:

```php
header("Location: thanks.html");
```

The only thing to watch out for is that you don’t output anything else to the browser — via echo() or print(), or by including HTML markup outside the <?php ... ?> tags — before calling header(). This is because the moment you send content to the browser, the PHP engine automatically sends the default HTTP headers — which won’t include your Location: header — and you can send headers only once per request.

# Chapter 9: Handling HTML Forms with PHP

Here's a quick example of a form handler script that redirects to a thank-you page:

```php
<?php

if (isset($_POST['submitButton'])) {
    // (deal with the submitted fields here)
    header("Location: thanks.html");
    exit;
} else {
    displayForm();
}

function displayForm() {
?>
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/html1/html1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
    <title>Membership Form</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>

<h1>Membership Form</h1>

<form action="form_handler_redirect.php" method="post">
    <div style="width:30cm;">
        <label for="firstName">First name</label>
        <input type="text" name="firstName" id="firstName" value="" />
        <label for="lastName">Last name</label>
        <input type="text" name="lastName" id="lastName" value="" />
        <div style="clear: both;">
            <input type="submit" name="submitButton" id="submitButton" value="Send Details"
        </div>
    </div>
</form>
</body>
</html>
<?php
```

Notice that the script doesn't output anything to the browser until either the header() function is called, or the membership form is displayed. Also notice that the script terminates with the exit statement after calling header().

# Summary

This chapter has shown you how to deal with Web forms within your PHP scripts. You learned:

- To create Web forms, including all different types of controls you can place in a form
- All about the $_GET, $_POST, and $_REQUEST superglobals, and how your scripts can use them to capture data sent by a user
- Some of the security issues surrounding forms, and how to mitigate them
- How to deal with empty form fields
- How to get the PHP engine to recognize multi-value fields, and how to read the data fields send
- How to generate Web forms from your PHP scripts. This allows you to add more interactivity and flexibility to your forms. You worked through an example of such an interactive form
- The concept of hidden form fields and how to use them to store data between page requests. You used this technique to create a three-stage registration form
- How to handle files uploaded via Web forms, using the $_FILES superglobal to redirect browser after a form submission to display a thank-you page and avoid issues with page reloads

# Exercises

- Write a simple number-guessing game in PHP. The script should “think” of a random number between 1 and 100, then give the user five chances to guess the number. For each guess, the script should report whether the guessed number was too low, high, or correct. (Hint: Use rand(1, 100) to generate a random number between 1 and 100.)
- Create a script that displays a form allowing the user to select one of three Amazon stores — amazon.com, amazon.ca, and amazon.co.uk — and then jumps to the relevant store based on the user’s choice.
