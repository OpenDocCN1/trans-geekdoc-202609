
When you use `fetchAll()`, the results are always stored as a multidimensional array with a subarray for each row—even if there’s only one row. You normally access the results of `fetchAll()` with a `foreach` loop like this:

foreach ($result as $row) {  

  // handle each row  

}

Inside the loop, you access each field by its column `name` like this: $row[‘user_id’].

If you don’t use a loop, you need to specify the subarray number (counting from 0) like this: `$result[0][‘user_id’]`.

**4** If the email isn’t in the database, the `fetchRow()` method returns `FALSE`. So, if there’s no result, you need to set `$errors` to `TRUE`. Otherwise, you can carry on with the reset request. Add the highlighted code *inside* the conditional statement you created in the previous step:

  $result = $dbRead->fetchRow($sql);  

  **if (!$result) {**  

**    $errors = TRUE;**      

**  } else {**    

**    // update database and send mail**      

**  }**    

}

**5.** If the email exists in the database, you need to create a security token and update the user’s record to store it in the database. Insert the following code inside the `else` block:

$token = md5(uniqid(mt\_rand(), TRUE));  

$data = array('token' => $token);  

$dbWrite->update('users', $data, "user\_id = {$result\['user\_id'\]}");

The first line of new code uses a typical PHP shortcut by passing functions as arguments to other functions. The `uniqid()` function generates a unique ID based on the current time. It takes two optional arguments designed to randomize the value. The first of these is `mt_rand()`, which generates a random number. Finally, `uniqid()` is wrapped in md5(), an encryption function that produces a 32-character hexadecimal string. Don’t worry if you find the details confusing. Just accept that the value assigned to `$token` should be impossible for anyone to guess.

The second line creates an associative array that assigns $token to the `name` of the database column where it’s to be stored.

The third line uses the `$dbWrite` database object with read/write privileges to update the user’s record. The third argument uses the `user_id` primary key from the database result to identify the record to be updated. Because `$result[‘user_id’]` is an array element, you need to wrap it in curly braces to incorporate it into the double-quoted string. The value contained in `$result[‘user_id’]` is the record’s primary key, which is an automatically incremented integer, so it’s safe to use directly in the third argument. Also, because it’s a number, the value doesn’t need to be in quotation marks.

The second line creates an associative array that assigns $token to the `name` of the database column where it’s to be stored.

The third line uses the `$dbWrite` database object with read/write privileges to update the user’s record. The third argument uses the `user_id` primary key from the database result to identify the record to be updated. Because `$result[‘user_id’]` is an array element, you need to wrap it in curly braces to incorporate it into the double-quoted string. The value contained in `$result[‘user_id’]` is the record’s primary key, which is an automatically incremented integer, so it’s safe to use directly in the third argument. Also, because it’s a number, the value doesn’t need to be in quotation marks.

**6** Now, you need to send an email to the user with a link to the password reset page. Add the following script inside the `else` block, using your own email address in the setFrom() method:

$mail = new Zend\_Mail('UTF-8');  

$mail->addTo($result\['email'\], "{$result\['first\_name'\]} {$result\['family\_name'\]}");  

$mail->setSubject('Instructions for resetting your password');  

$mail->setFrom('webmaster@example.com', 'DW CS5 with PHP');  

$link = "http://phpcs5/lesson08/workfiles/reset.php?id={$result\['user\_id'\]}&token=$token";  

$message = "Use the following link to reset your password. This link can be used once only. $link";  

$mail->setBodyText($message, 'UTF-8');  

$mail->send();

Creating and sending an email was covered in detail earlier in this lesson, so this code should be easy to understand.

The values from the database result are used to set the recipient’s address by passing the email address as the first argument to `addTo()` and enclosing the `first_name` and `family_name` values in a double-quoted string as the second argument. This personalizes the address with the recipient’s real name—or at least the one registered in the system.

The `$link` variable contains the URL of the password reset page with a query string that contains the user’s primary key and the security token. The `$link` variable is then incorporated in the $message string and passed to `setBodyText()`. This sends a plain text message only.

**7.** Save request_reset.php, and copy forgotten.php from lesson08/start to lesson08/workfiles. The code in forgotten.php contains two conditional statements that control the HTML displayed onscreen.

Use `require_once()` above the `DOCTYPE` declaration to include scripts/request_reset.php, and load forgotten.php into a browser. You should see the reset request form.

![Image](graphics/fig08_24.jpg)

**8** Test the page by typing a false email address into the text field and clicking Submit. You should see an error message displayed below the form.

![Image](graphics/fig08_25.jpg)

**9.** Type your own email address in the field, and submit the form. Assuming that your address is registered in the database, the form should disappear, and you are presented with the following message:

![Image](graphics/fig08_26.jpg)

The different messages are controlled by the conditional statements in forgotten.php. An `if… else` statement uses the value of `$result` to determine whether to show the form or the message in the preceding screen shot. The error message is controlled by the value of `$errors`.

**10** If the gods of cyberspace are smiling on you, you should receive an email similar to this:

![image](graphics/fig08_27.jpg)

You’re ready to move on to the script that resets the password. You can compare your code with lesson08/completed/scripts/request_reset.php.

If you see the success message in step 9 but don’t receive an email, the most likely causes are network problems or the email being rejected by the mail server. Using a dummy address in the `setFrom()` method is a common cause of rejection, because the email is perceived as spam.

### Building the password reset script

The script that resets a user’s password needs to perform a couple of checks before updating the record in the database. First, it needs to verify the `user_id` and security token. If they don’t match, there’s no point in going any further. If they’re OK, the next task is to validate the new password, using the same technique as in [Lesson 7](#ch07.html#ch07). If the password is acceptable, the script can finally update the user’s record. The following illustration outlines the decision chain.

![Image](graphics/fig08_28.jpg)

Again, there’s a lot going on, but the final script is just 45 lines.

**1** Copy lesson08/start/reset.php to lesson08/workfiles, and examine the code in Split view. In Design view, you can see there are three blocks of HTML: confirmation that the password has been reset, an error message, and a form with two password fields. The Display Error Message server behavior has been applied to `<span>` tags next to the password fields. As in forgotten.php, a series of conditional statements controls what is displayed.

**2.** Copy lesson08/start/scripts/reset_password.php to lesson08/workfiles/scripts. This contains the following basic code:

session_start();  

$_SESSION['nomatch'] = TRUE;  

$errors = array();  

$success = FALSE;  

require_once('library.php');  

try {  

} catch (Exception $e) {  

  echo $e->getMessage();  

}

The script needs to keep track of the user’s identity to update the correct record in the database. You could store the details in hidden form fields, but it’s more secure to use session variables, which remain on the server. So, the script initiates a session with `session_start()` and creates a session variable called `$_SESSION['nomatch']`, which is set to `TRUE`. `$_SESSION['nomatch'], $errors`, and `$success` control what is displayed in reset.php.

The script needs to access the database each time the page loads, so library.php is included right away.

**3.** Switch back to reset.php and include scripts/reset_password.php using `require_once()` above the `DOCTYPE` declaration.

**4.** Locate the opening `<form>` tag (around line 21). It currently looks like this:

```
<form id="form1" name="form1" method="post" action="">
```

