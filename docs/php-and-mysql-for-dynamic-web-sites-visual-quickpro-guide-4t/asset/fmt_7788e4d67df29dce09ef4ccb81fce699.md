
## PHP Contact Form Script

### Code Listing (email.php)

```php
18          $body = "Name: {$_POST['name']}\n\nComments: {$_POST['comments']}";

19

20          // Make it no longer than 70 characters long:
21          $body = wordwrap($body, 70);

22

23          // Send the email:
24          mail('your_email@example.com',
              'Contact Form Submission',
              $body, "From: {$_POST['email']}");

25

26          // Print a message:
27          echo '<p><em>Thank you for
              contacting me. I will reply some
              day.</em></p>';

28

29          // Clear $_POST (so that the form's not sticky):
30          $_POST = array();

31

32      } else {
33          echo '<p style="font-weight: bold;
              color: #C00">Please fill out the
              form completely.</p>';
34      }

35

36  } // End of main isset() IF.

37

38  // Create the HTML form:
39  ?>
40  <p>Please fill out this form to contact me.</p>
41  <form action="email.php" method="post">
42      <p>Name: <input type="text"
              name="name" size="30" maxlength="60"
              value="<?php if (isset($_POST['name']))
              echo $_POST['name']; ?>" /></p>
43      <p>Email Address: <input type="text"
              name="email" size="30" maxlength="80"
              value="<?php if (isset($_POST['email']))
              echo $_POST['email']; ?>" /></p>
44      <p>Comments: <textarea name="comments"
              rows="5" cols="30"><?php if (isset
              ($_POST['comments'])) echo $_POST
              ['comments']; ?></textarea></p>
45      <p><input type="submit" name="submit"
              value="Send!" /></p>
46  </form>
47  </body>
48  </html>
```

---

### Step-by-Step Explanation

#### 3. Create the body of the email

```php
$body = "Name: {$_POST['name']}\n\nComments: {$_POST['comments']}";
$body = wordwrap($body, 70);
```

The email’s body will start with the prompt **Name:**, followed by the name entered into the form. Then the same treatment is given to the comments. The `wordwrap()` function then formats the whole body so that each line is only 70 characters long.

#### 4. Send the email and print a message in the Web browser

```php
mail('your_email@example.com', 'Contact Form Submission', $body, "From: {$_POST['email']}");
echo '<p><em>Thank you for contacting me. I will reply some day.</em></p>';
```

Assuming the server is properly configured, this one line will send the email. You will need to change the *to* value to your actual email address. The *From* value will be the email address from the form. The subject will be a literal string.

There’s no easy way of confirming that the email was successfully sent, let alone received, but a generic message is printed.

#### 5. Clear the `$_POST` array

```php
$_POST = array();
```

In this example, the form will always be shown, even upon successful submission. The form will be sticky in case the user omitted something. However, if the mail was sent, there’s no need to show the values in the form again. To avoid that, the `$_POST` array can be cleared of its values using the `array()` function.

> The contact form will remember the user-supplied values in case it is not completely filled out.

#### 6. Complete the conditionals

```php
} else {
    echo '<p style="font-weight: bold; color: #C00">Please fill out the form completely.</p>';
}
} // End of main isset() IF.
```

The error message contains some inline CSS, so that it’s in red and made bold.

#### 7. Begin the form

```html
<p>Please fill out this form to contact me.</p>
<form action="email.php" method="post">
  <p>Name: <input type="text" name="name" size="30" maxlength="60" value="<?php if (isset($_POST['name'])) echo $_POST['name']; ?>" /></p>
  <p>Email Address: <input type="text" name="email" size="30" maxlength="80" value="<?php if (isset($_POST['email'])) echo $_POST['email']; ?>" /></p>
```

The form will submit back to this same page using the POST method. The first two inputs are of type text; both are made sticky by checking if the corresponding `$_POST` variable has a value. If so, that value is printed as the current value for that input. Because the `$_POST` array is cleared out in Step 5, `$_POST['name']` and the like will not be set when this form is viewed again, after its previous successful completion and submission.

#### 8. Complete the form

```html
  <p>Comments: <textarea name="comments" rows="5" cols="30"> <?php if (isset($_POST['comments'])) echo $_POST['comments']; ?></textarea></p>
  <p><input type="submit" name="submit" value="Send!" /></p>
</form>
```

The comments input is a `textarea`, which does not use a `value` attribute. Instead, to be made sticky, the value is printed between the opening and closing `textarea` tags.

#### 9. Complete the HTML page

```html
</body>
</html>
```

#### 10. Save and test

Save the file as `email.php`, place it in your Web directory, and test it in your Web browser.

> Successful completion and submission of the form.

#### 11. Check your email

Check your email to confirm that you received the message.

> The resulting email (from the data in the form).

If you don’t actually get the email, you’ll need to do some debugging work. With this example, you should confirm with your host (if using a hosted site) or yourself (if running PHP on your server), that there’s a working mail server installed. You should also test this using different email addresses (for both the *to* and *from* values). Also, watch that your spam filter isn’t eating up the message.

---

### Tips

#### `mail()` function optional argument

The `mail()` function takes an optional fifth argument, for additional parameters to be sent to the mail-sending application.

#### `mail()` return value

The `mail()` function returns a `1` or a `0` indicating the success of the function call. This is not the same thing as the email successfully being sent or received. Again, you cannot easily test for either using PHP.

#### Sending HTML emails or attachments

While it’s easy to send a simple message with the `mail()` function, sending HTML emails or emails with attachments involves more work. I discuss how you can do both in my book *PHP 5 Advanced: Visual QuickPro Guide* (Peachpit Press, 2007).

#### Spam prevention

Using a contact form that has PHP send an email is a great way to minimize the spam you receive. With this system, your actual email address is not visible in the Web browser, meaning it can’t be harvested by spambots.

---

## Handling File Uploads

[Chapters 2](#ch02.html#ch02), “[Programming with PHP](#ch02.html#ch02),” and [3](#ch03.html#ch03), “[Creating Dynamic Web Sites](#ch03.html#ch03),” go over the basics of handling HTML forms with PHP. For the most part, every type of form element can be handled the same in PHP, with one exception: file uploads. The process of uploading a file has two dimensions. First the HTML form must be displayed, with the proper code to allow for file uploads. Upon submission of the form, the server will first store the uploaded file in a temporary directory, so the next step is for the PHP script to copy the uploaded file to its final destination.

For this process to work, several things must be in place:

- PHP must run with the correct settings.
- A temporary storage directory must exist with the correct permissions.
- The final storage directory must exist with the correct permissions.

With this in mind, this next section will cover the server setup to allow for file uploads; then a PHP script will be created that actually does the uploading.

### Allowing for file uploads
