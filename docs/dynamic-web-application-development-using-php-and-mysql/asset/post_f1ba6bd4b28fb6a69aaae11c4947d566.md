
## FIGURE 20.2 Select menu with no null option

![](img/b2471264f405d17994ef173e4b9cec92_616_0.png)

However, an improvement to our script would be to include a null value for the select menu, such as ‘___’ as a default, for example:

```
<option>---</option>
```

We could then check that the user has selected a title other than this, for example:

```
if ($_POST["submit"] == "___")
    echo "<p>Please select a title.</p>";
```

This would provide a degree of confidence that the user has made an informed choice and not simply clicked submit as a default. The completed script now looks like this:

```
<h2>Please select your title:</h2>

<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><select name='strTitle'>
    <option>---</option>
    <option>Mr</option>
    <option>Miss</option>
    <option>Ms</option>
    <option>Mrs</option>
    <option>Dr</option>
</select></p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-10.php
if (isset($_POST["submit"]) ) {
    if ($_POST["submit"] == "___")
        echo "<p>Please select a title.</p>";
    else {
        $strTitle = $_POST["strTitle"];
        echo "<p>Your title is $strTitle</p>";
    }
}
?>
```

## FIGURE 20.3 Select menu with null option

![](img/b2471264f405d17994ef173e4b9cec92_617_0.png)

Figure 20.3 illustrates the revised form menu.

Other form elements allow the user more freedom in the data they can input and these include the text, password and textbox elements. The following script illustrates a simple login form consisting of three form elements, a username input field, a password input field and a submit button:

```php
<h2>Please login:</h2>

<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>
<label for="intUsername">Username: </label>
<input type="text" name="intUsername" id="intUsername"/>
</p><p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/>
</p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-11.php

if (isset($_POST["submit"])) {
    $intUsername = $_POST["intUsername"];
    $strPassword = $_POST["strPassword"];
    echo "<p>Username: $intUsername Password: $strPassword</p>";
}
?>
```

At the moment all the script does is to display the values of intUsername and strPassword and performs no error checking. This is fine if the users always obey the rules which are:

- A username must be an 8-digit number beginning with the number 5 and containing no non-numeric characters.

```php
// File: example20-12.php

if (isset($_POST["submit"])) {
    $intUsername = $_POST["intUsername"];
    $strPassword = $_POST["strPassword"];

    $intErrorCount = 0;

    if (strlen($intUsername) < 8) {
        echo "<p>Username less than 8 characters</p>";
        $intErrorCount++;
    }
    if (strlen($strPassword) < 6) {
        echo "<p>Password less than 6 characters</p>";
        $intErrorCount++;
    }

    if ($intUsername{0} != "5") {
        echo "<p>Username doesn't start with a 5</p>";
        $intErrorCount++;
    }
    if (!is_numeric($intUsername) ) {
        echo "<p>Username needs to consist of only numbers</p>";
        $intErrorCount++;
    }

    if ($intErrorCount == 0)
        echo "<p>Username: $intUsername Password: $strPassword and all is well.</p>";
}
```

Figure 20.4 illustrates the output from the script.

## FIGURE 20.4 Form field detecting errors

![](img/b2471264f405d17994ef173e4b9cec92_619_0.png)

One other check we may need to implement is where the value of a data item in one form field affects the validation criteria of another. Consider the following script:

```html
<h2>Please select your title:</h2>
<form action="<?php echo $_SERVER["PHP_SELF"]; ?>" method='post'>
<p>
<label for="strTitle">Title: </label>
<select name='strTitle' id='strTitle'>
    <option>Mr</option>
    <option>Miss</option>
    <option>Ms</option>
    <option>Mrs</option>
    <option>Dr</option>
    <option>Other</option>
</select>
<label for="strOther">Other: </label>
<input type="text" name="strOther" id="strOther"/>
</p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-13.php

if (isset($_POST["submit"])) {
    echo "<p>Your title is $strTitle</p>";
}
?>
```

The above script implements a simple form consisting of three elements: a select menu, a text field and a submit button. The select menu allows a user to select their title from the menu. What we would like to include is some script which detects if the option ‘Other’ is chosen and subsequently set the $strTitle variable to contain the value entered in the $strOther text field. A further check is required that the length of the data in the $strOther field is a minimum of two characters. Here is the additional script:

```php
if ($strTitle == "Other") {
    $strTitle = $strOther;
}

if (strlen($strTitle) < 2)
    echo "<p>Title must be greater than two characters</p>";
```

The completed script with the above validation checks incorporated is as follows:

```html
<h2>Please select your title:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>
<label for="strTitle">Title: </label>
<select name='strTitle' id='strTitle'>
    <option>Mr</option>
    <option>Miss</option>
    <option>Ms</option>
    <option>Mrs</option>
    <option>Dr</option>
    <option>Other</option>
</select>
<label for="strOther">Other: </label>
<input type="text" name="strOther" id="strOther"/>
</p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-14.php

if (isset($_POST["submit"])) {
    $strTitle = $_POST["strTitle"];
    $strOther = $_POST["strOther"];

    if ($strTitle == "Other") {
        $strTitle = $strOther;
    }

    if (strlen($strTitle) < 2)
        echo "<p>Title must be greater than two characters</p>";
    else
        echo "<p>Your title is $strTitle.</p>";
}
?>
```

Figure 20.5 illustrates the output from the script.

## FIGURE 20.5 Cross-field validation

![](img/b2471264f405d17994ef173e4b9cec92_621_0.png)

## 20.3 Countering malicious data injection

### Escaping HTML elements in text fields

Another security breach which can be overcome is that of injecting HTML elements into form text, password and textarea fields. This is closely related to the issue of form data validation and once again concerns the subject of whether the data you have is what you expected. Consider the following script:

```php
<h2>Please enter your message:</h2>
<form action="<?php echo $_SERVER["PHP_SELF"]; ?>" method='post'>
<p>
<label for="strMessage">Message: </label>
<textarea name="strMessage" id="strMessage"></textarea>
</p>
<p><input type='submit' name='submit1'/></p>
</form>
<?php
// File: example20-15.php

if (isset($_POST["submit"])) {
    $strMessage = $_POST["strMessage"];

    echo "<p>Your message is $strMessage.</p>";
}
echo "<p>This is some text further down the web page.</p>";
?>
```

The above script displays a form consisting of two elements: a textarea and a submit button. A user is free to type a message in the textarea which, once submitted, is displayed on the web page. This is illustrated in Figure 20.6, where the message ‘Isn’t PHP great?’ is displayed.

The problem comes when a user decides to enter a message which includes some (X)HTML elements. They are free to do this as (X)HTML is just text after all and this is known as (X)HTML injection. An example of this could be where a user enters ‘<h1>This is large!</h1>’ as the message. In this case, the user’s message is displayed as a level 1 heading. Worse than that, if a user enters only the first part of a multiple part element the whole display of the web page can be affected from that point onwards. Consider the message ‘<i>Hello, this is in italics’. The result of this displays the message in italic characters but also the text following the message. This is illustrated in Figure 20.7.

To overcome this vulnerability, you can use the PHP function htmlentities(). In its simplest form, it looks like this:

```text
htmlentities (string string)
```

The function translates ‘<’ characters into the character entity ‘&lt;’ and ‘>’ into the character entity ‘&gt;’. These are displayed as the characters ‘<’ and ‘>’ respectively in a browser but a browser does not recognize them as being the start and end of an (X)HTML element and therefore does not parse the (X)HTML element. The following script illustrates
