
$errors\['first_name'\] = 'Required field, no numbers';  
}  
if (!$val->isValid($_POST\['surname''])) {  
$errors\['surname'\] = 'Required field, no numbers';  
}  
} catch (Exception $e) {  
}  
2. The next input field to validate is `username`. A username should consist of letters and numbers only, and should be 6–15 characters long. This requires two tests, so you need to create a `Zend_Validate` object, and chain the validators. You don’t need the existing validator, so you can overwrite it.  
Add the following code immediately after the code you entered in the previous step (and still inside the `try` block):  
$val = new Zend\_Validate();  
$length = new Zend\_Validate\_StringLength(6,15);  
$val->addValidator($length);  
$val->addValidator(new Zend\_Validate\_Alnum());  
if (!$val->isValid($_POST\['username''])) {  
$errors\['username'\] = 'Use 6-15 letters or numbers only';  
}  
This starts by creating a generic `Zend_Validate` object ready for chaining. Next, a `StringLength` validator—with a minimum of 6 characters and a maximum of 15—is created and assigned to `$length`.  
In the third line, the `addValidator()` method chains `$length` to `$val`.  
Then the `Alnum` validator is chained to it. By not passing an argument to `Alnum`, no whitespaces are allowed.  
Why use different ways of chaining the validators? Surely the `StringLength` validator could have been passed directly as an argument to `addValidator()` in the same way as `Alnum,` right? It could, but the password field needs to be a minimum of 8 characters. Assigning the `StringLength` validator to its own variable lets you change the minimum value ready for reuse.  
**3.** On the line immediately after the code you just inserted, type **$length->**. As soon as you type the `->` operator, Dreamweaver code hints display the methods available to a `StringLength` validator. Type **s**. The code hints display a number of methods that begin with “set.”  
![Image](graphics/fig07_15.jpg)  
**4.** Use your arrow keys to scroll down to `setMin($min)` and press Enter/Return or double-click. Set the value to **8**, and type a closing parenthesis and semicolon. The finished line should look like this:  
$length->setMin(8);  
This resets the minimum number of characters required by the `StringLength` validator to 8. The maximum remains unchanged at 15.  
### ![Image](graphics/tip.jpg)**TIP:**  
Many ZF classes have methods that begin with “get” and “set” to find out or change the values of an object’s properties.  
**5.** Now that you have changed the minimum required by the `StringLength` validator, you can create the validation test for the `password` input field. It’s almost exactly the same as for `username`. Add this immediately after the line you just entered:  
$val = new Zend\_Validate();  
$val->addValidator($length);  
$val->addValidator(new Zend\_Validate\_Alnum());  
if (!$val->isValid($_POST\['password''])) {  
$errors\['username'\] = 'Use 8-15 letters or numbers only';  
}  
This allows any combination of letters and numbers. For a more robust password, use the `Regex` validator. There’s a regex for a strong password that requires a mixture of uppercase and lowercase characters and numbers at [http://imar.spaanjaars.com/QuickDocId.aspx?quickdoc=297](http://imar.spaanjaars.com/QuickDocId.aspx?quickdoc=297). In the comments on the same page, there’s an even stronger one that requires at least one special character.  
**6** To check that both password values are identical, use the `Identical` validator. This code goes immediately after the code in the preceding step:  
$val = new Zend\_Validate\_Identical($_POST\['password']);  
if (!$val->isValid($_POST\['conf_password''])) {  
$errors\['conf_password'\] = "Passwords don't match";  
}  
You want to check that `$_POST[‘conf_password’]` is identical to `$_POST[‘password’]`, so `$_POST[‘password’]` is passed as the argument to the `Identical` validator.  
### ![Image](graphics/caution.jpg)**CAUTION!**  
The error message contains an apostrophe, so the string needs to be enclosed in double quotation marks.  
**7.** The final test is for the email. Add this after code in the previous step:  
$val = new Zend\_Validate\_EmailAddress();  
if (!$val->isValid($_POST\['email''])) {  
$errors\['email'\] = 'Use a valid email address';  
}  
**8.** Save user_registration.php. You’ll come back to it later to add the code that inserts the user’s details in the database. If you want to check your code so far, compare it with lesson07/completed/scripts/user_registration02.php.  
#### **Preserving input when validation fails**  
Ever submitted an online form only to be told there’s an error, and all your input has been wiped out? Not much fun is it? Good validation and form design preserves the user’s input if there’s an error. It’s quite simple to do. The input is stored in the `$_POST` or `$_GET` array, depending on the method used to submit the form (most of the time, it’s `POST`). All that’s necessary is to assign the appropriate element of the `$_POST` or `$_GET` array to the `value` attribute of the input field.  
**1.** In add_user.php, locate the first `<input>` tag in Code view. It looks like this:  
<input type=”text” name=”first_name” id=”first_name” />  
**2.** The `<input>` tag doesn’t have a `value` attribute, so you need to add one, and use PHP to assign its content like this:  
<input type=”text” name=”first_name” id=”first_name”  
**value=”<?php if ($\_POST && $errors) {**  
  **echo htmlentities($\_POST\['first_name'\], ENT\_COMPAT, 'UTF-8');**  
**}?>”** />  
The PHP code block inside the quotation marks of the `value` attribute is controlled by a conditional statement that checks the `$_POST` and `$errors` arrays. The `$_POST` array is empty unless a form has been submitted, so the code inside the curly braces is ignored when the page first loads.  
The `$errors` array is declared at the top of user_registration.php, so it always exists, but elements get added to it only if the validation script finds any problems with the user input. Consequently, `$errors` will equate to `TRUE` only if the form has been submitted and at least one error has been found.  
If both tests equate to `TRUE`, the code passes `$_POST[‘first_name’]` to a function called `htmlentities()` and uses `echo` to display the result. You could use `echo` on its own, but displaying raw user input in a web page is a security risk. The `htmlentities()` function sanitizes the input by converting characters that have a special meaning in HTML into HTML entities. For example, the angle brackets in `<script>` are converted to `&lt;` and `&gt;`, which prevent an unauthorized script from running in your web page.  
Often, `htmlentities()` takes just one argument—the string you want to convert. The second and third arguments have been added because `htmlentities()` uses Latin1 (iso-8859-1) as its default encoding. `ENT_COMPAT` is a constant that specifies preserving single quotation marks and converting only double ones. The third argument specifies UTF-8 (Unicode) as the encoding. This preserves accented or nonalphabetic characters.  
**3.** Save add_user.php, type anything in the “First name” field, and submit the form. The validation script detects errors in the other fields, so `$_POST` and `$errors` are no longer empty arrays. The value you entered is redisplayed.  
You can compare your code with lesson07/completed/add_user02.php.  
#### **Dealing with unwanted backslashes**  
In add_user.php, test the “First name” field with a name that contains an apostrophe, such as **O’Toole**. If magic quotes (see [Lesson 2](#ch02.html#ch02)) are turned on, the apostrophe is preceded by a backslash like this when it’s redisplayed:  
![Image](graphics/fig07_16.jpg)
