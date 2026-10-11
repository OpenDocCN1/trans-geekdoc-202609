
<!DOCTYPE html>
<html>
<head>
<title>Instructor Sign Up </title>
</head>
<body>
<h2>Instructor Sign Up </h2>
<form method="get" action="" name="form1">
<table>
<tr>
<th style='text-align:left;'><label>Email Address</label></th>
<td>:&emsp;</td>
<td><input type="email" name="txtemail" size="30" placeholder="Your Email Address"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Name</label></th>
<td>:&emsp;</td>
<td><input type="text" name="txtname" size="30" placeholder="Your Name"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Qualification</label></th>
<td>:&emsp;</td>
<td><input type="text" name="txtqualification" size="30" placeholder="Your Qualification"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Country </label></th>
<td>:&emsp;</td>
<td><select name="txtcountry">
<option value="">Choose a country from the list</option>
<option value="India">India</option>
<option value="France">France</option>
<option value="Japan">Japan</option>
<option value="Canada">Canada</option>
</select></td>
</tr>
<tr></tr>
<tr>
<th></th><td></td><td><p><input type="submit" name="signup" value="Sign Up"></p></td>
</tr>
</table>
</form>
<hr></body>
</html>

I assume that you have some idea / understanding on HTML forms.

I have just randomly used some country names!

Let me explain what the code snippet is about:

We have 4 fields - instructor email id, instructor name, instructor qualification, instructor country. We try getting inputs using these 4 fields. If the form’s action is empty, all the data is submitted to the same page. Right now, we are not saving this data anywhere. We just pass the data and print them in the same page using superglobal variables.

On execution, you should see like this (if you have coded as above):

![4-3-2](Images/image00235.jpeg)

You can design the form as you like. But for learning purpose, don't change any element's name. We have these names in this form: `form1`, `txtemail`, `txtname`, `txtqualification`, `txtcountry`, `signup`. Make sure the spellings are right. Because, these names are going to play a big role.

Since the method we used here is get, we can collect those data using `$_REQUEST` or `$_GET` variables!

Code the following in the beginning of `instructor_signup.php` file:

```php
<?php
if(isset($_GET['signup'])){
  echo "<br>You have clicked Sign up";
}
?>
```

We will check if the form is submitted. What to do?

*   Add this code to the php file.
*   Execute the file
*   Click Sign up button in the page

![4-3-3](Images/image00236.jpeg)

If you get this message displayed on top, your form is submitted.

`if(isset($_GET['signup']))` explanation:

*   `$_GET['signup']` will get the value 1 if the button named `signup` is clicked.
*   `isset()` will check if `$_GET['signup']` has a value. If the button is not clicked, `$_GET['signup']` will not have value, making `isset()` to false. When it is clicked, `isset()` return true.
*   when you pass `isset($_GET['signup'])` inside `if()` statement, the condition is evaluated to be true and the statement block is executed. If condition evaluates to false, the statement block does not get executed.

Example: when you executed the page, you did not get the message, only when you clicked the button, you got this message.

Can you see the URL? When you use the `$_GET` method, all your values will be explicitly shown in the URL along with name parameters.

Now we will just get all these values in variables and print the same.

Add this code in the beginning: (Instead of only echo statement, we add few more lines).

```php
<?php
if(isset($_GET['signup'])){
   echo "<br>You have clicked Sign up";
   $email = $_REQUEST['txtemail'];
   $name = $_GET['txtname'];
   $qualification = $_GET["txtqualification"];
   $country = $_GET['txtcountry'];
}
?>
```

Unless needed, we can use single or double quotes.

We shall print the details below the form. See where your form ends with `</form>`. Place the code snippet below `<hr>` tag:

```php
<?php
if(isset($email)){
  echo "<br>Email - ".$email;
}
if(isset($name)){
  echo "<br>Name - ".$name;
}
if(isset($qualification)){
  echo "<br>Qualification - ".$qualification;
}
if(isset($country)){
  echo "<br>Country - ".$country;
}
?>
```

The reason for using `isset()` for every php variable is simple - if you don’t use, when you execute, php will search for those variables and display error if not found. Do you want to check? You can!

After adding code, make sure you don't refresh the URL with the parameters.

Execute `http://localhost/onlinecourse/instructor_signup.php`

After execution, give some input in those fields and click Sign up button:

![4-3-4](Images/image00237.jpeg)

Can you understand what it does? Also, make a note on the URL parameters!

Do you want your form data to be safe?

Very simple, you need to do 2 things:

*   change form method="post"
*   Change all your `$_GET[]` to `$_POST[]` variables. You can change / leave `$_REQUEST[]`

Let me give the code:

```php
<?php
if(isset($_POST['signup'])){
    echo "<br>You have clicked Sign up";
    $email = $_REQUEST['txtemail'];
    $name = $_POST['txtname'];
    $qualification = $_POST["txtqualification"];
    $country = $_POST['txtcountry'];
}
?>

<form method="post" action="" name="form1">
```

Execute `http://localhost/onlinecourse/instructor_signup.php`

![4-3-5](Images/image00238.jpeg)

See how clean your URL is!

When you are not sure whether your form is sent by get or post method, you can retrieve the form variables using `$_REQUEST`!

Let us have an idea on **GET vs POST:**

Both GET and POST create an array like: array( key1 => value1, key2 => value2, key3 => value3, ...). This array holds key/value pairs, where keys are the names of the form controls and values are the input data from the user.

You can access them from any function, class or file without having to do anything special. They are accessible globally.

*   `$_GET` is an array of variables passed to the current script via the URL parameters.
*   `$_POST` is an array of variables passed to the current script via the HTTP POST method.

### When to use GET?

Information sent from a form with the GET method is visible to everyone (all variable names and values are displayed in the URL).

*   GET has limits on the amount of information to send.
*   The limitation is about 2000 characters.
*   However, because the variables are displayed in the URL, it is possible to bookmark the page. This can be useful in some cases.
*   GET may be used for sending non-sensitive data.
*   GET should NEVER be used for sending passwords or other sensitive information!

### When to use POST?

Information sent from a form with the POST method is invisible to others (all names/values are embedded within the body of the HTTP request)

*   It has no limits on the amount of information to send.
*   Moreover POST supports advanced functionality such as support for multi-part binary input while uploading files to server.
*   However, because the variables are not displayed in the URL, it is not possible to bookmark the page.
*   Developers prefer POST for sending form data.

---

### 4.4 Form Validation

---

We will learn how to process forms with security in this section. Proper Validation of form data is important to protect your data from hackers and spammers!

Examples on validation:

These 2 validation rules are as per our instructor form signup.

*   if you provide a name in text field, it should contain letters and whitespace.
*   if you provide an email address in email field, it must be valid with @ and domain name.
*   we can also mention a field as mandatory or optional using required attribute in html input element.

**How do we validate the form designed in the previous section?**

We will follow some steps here:
