
5 Since the user’s name and email have been included in `Reply-To` header, you could just send the value of `$_POST`['comments'] as the body text. However, that doesn’t demonstrate how to build a longer email message. Create the body for a plain text version like this:

```php
$text = "Name: {$_POST['name']}\\r\\n\\r\\n";  
$text .= "Email: {$_POST['email']}\\r\\n\\r\\n";  
$text .= "Comments: {$_POST['comments']}";
```

Again, this uses strings enclosed in double quotation marks so that the values of the variables are incorporated. The email specification requires each line to end with a carriage return and newline character. The `\r\n\r\n` at the end of the first two lines use escape sequences to insert the appropriate characters (see [Table 3.2](#ch03.html#ch03tab2) in [Lesson 3](#ch03.html#ch03)).

### ![Image](graphics/caution.jpg)**CAUTION!**

The second and third lines in the preceding code block use the combined concatenation operator (a period followed by an equals sign) to add more text to the variable. If you omit the period, each new line overwrites the previous one.

**6.** For such a simple feedback form, you probably wouldn’t want to send it as HTML email, but you build the message body in exactly the same way, adding the HTML tags to the string like this:

```php
$html = '<html><head><title>';  
$html .= $mail->getSubject();  
$html .= '</title></head><body>';  
$html .= "<p><strong>Name: </strong><a href='mailto: {$_POST['email']}'>{$_POST['name']}</a></p>";  
$html .= '<p><strong>Comments: </strong>' . nl2br($_POST['comments']) . '</p>';  
$html .= '</body></html>';
```

This creates the HTML for the email. The second line uses the `Zend_Mail` getSubject() method to retrieve the email’s subject line to go inside the `<title>` tags.

The user input is embedded in two paragraphs. In the first one, the user’s email is turned into a link for the name. In the second one, the value of `$_POST['comments']` is passed to the PHP `nl2br()` function, which converts newline characters into HTML `<br />` tags. You can’t use a function inside a string, so the string is built in three parts and joined together by the concatenation operator.

### ![Image](graphics/caution.jpg)**CAUTION!**

If you omit the closing PHP tag from process_comments.php, Dreamweaver interprets the HTML tags in this string as part of the page markup, preventing Design view from displaying the form.

**7** After building the message body, add the plain text and HTML versions to the email like this:

```php
$mail->setBodyText($text, 'UTF-8');  
$mail->setBodyHtml($html, 'UTF-8');
```

Adding the character set as the second argument is optional, but it’s a good idea to ensure that the input is handled correctly.

### ![Image](graphics/tip.jpg)**TIP:**

Not everyone likes HTML mail, and some people set their email program to reject it. When using `Zend_Mail`, you should always use setBodyText() to create a plain text version, even if you want most recipients to see the HTML version. If you send both HTML and plain text, recipients will see the message in their preferred format.

**8.** You’re now ready to send the email. The `send()` method returns a Boolean value indicating whether it succeeded. You can capture this value to preserve the user’s input and redisplay it in the form if the mail can’t be sent. Add the following code to the mail processing script:

```php
$success = $mail->send();  
if (!$success) {  
    $errors = TRUE;  
}
```

Normally, form fields are cleared when a form is submitted. You want this to happen if the email is sent successfully, but setting `$errors` to `TRUE` results in the Redisplay on Error server behavior code preserving the input. This gives the user the option to retry later without needing to fill in every field again.

**9.** Save process_comments.php, and switch to the source code in comments.php. Add the following mixture of PHP and HTML to display the results of submitting the form:

```html
<form id="form1" name="form1" method="post" action="">  
    <?php if (isset($success) && !$errors) { ?>  
        <p>Thank you. Your comments have been sent.</p>  
    <?php } elseif (isset($success) && $errors) { ?>  
        <p>Sorry, there was a problem. Please try later.</p>  
    <?php } ?>  
    <p>All fields are required</p>
```

The first conditional statement uses `isset()` to check whether $success exists. The variable is created only when the email is sent, which in turn can happen only if there are no errors. So, if `$success` exists, and $errors is `FALSE`, the mail must have been sent successfully. If, on the other hand, `$success` exists, but `$errors` is `TRUE`, it means an attempt was made to send the email, but it failed.

**10** Finally, the moment of truth. Save comments.php and load it into a browser. Fill in all the fields, and click Send Comments. If all your code is correct, you should receive an email in your inbox after a short while. As the following screen shot shows, setting the character set of the email to UTF-8 supports languages other than unaccented English.

![image](graphics/fig08_13.jpg)

You can compare your code with lesson08/completed/comments.php and lesson08/completed/scripts/process_comments.php.

Troubleshooting email problems is notoriously difficult. Emails normally travel around the Internet in seconds. Sometimes, they take several hours or never arrive at all. This can happen for a variety of reasons:

• Incorrect settings on the mail server

• Rejection by a mail server

• Network problems

• System failure

• Overaggressive spam filtering

If the problem lies with your mail connector script, the processing script should throw an exception. Analyze the message. The most likely cause is that you have used the wrong authentication type or that your login details are incorrect.

If submitting the form doesn’t result in an exception being thrown, try using different email addresses.

If email still doesn’t arrive, amend your mail connector script to use `Zend_Mail_Transport_Sendmail`, as described in “Setting the default transport for `Zend_Mail`,” and upload all the files to your remote server. It should work when you test it from there.

### Processing Other Form Elements

The simple feedback form in comments.php uses only text input fields and a text area. Other form elements need to be handled slightly differently. The form in lesson08/start/inquiry.php contains all types of input elements. In addition to the text input fields and text area, it contains a checkbox group, a radio button group, a single-choice `<select>` menu, and a multiple-choice `<select>` list.

![image](graphics/fig08_14.jpg)

As you saw in previous lessons, the values of form elements are passed through the `$_POST` or `$_GET` array depending on which method was used to submit the form. In the absence of a form being submitted or a query string being appended to the URL, the `$_POST` and `$_GET` arrays exist but contain no elements. Because PHP treats an empty array as `FALSE`, you can use `if ($_POST)` to test whether a form has been submitted by the `POST` method. When you submit a form, elements are created in the `$_POST` array for the submit button and each text field or text area. Even if nothing is entered in the fields, the array elements exist, so the `$_POST` array—as opposed to individual elements—is no longer empty; therefore, PHP implicitly treats it as `TRUE`.

Checkboxes, radio button groups, and multiple-choice `<select>` lists behave differently. The following exercise illustrates what happens when you include them in a form:

**1** Copy lesson08/start/inquiry.php to lesson08/workfiles, and switch to Code view.

**2.** Add the following code between the closing `</form>` and `</body>` tags:

```php
<?php if ($_POST) {  
    print_r($_POST);  
} ?>
```

This checks if the form has been submitted. If it has, `print_r()` displays the contents of the `$_POST` array. The `<pre>` tags make the output easier to read.
