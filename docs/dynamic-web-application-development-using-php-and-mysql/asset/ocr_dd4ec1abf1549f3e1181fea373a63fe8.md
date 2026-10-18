validation and once again concerns the subject of whether the data you have is what you expected. Consider the following script:

```
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
```

The above script displays a form consisting of two elements: a textarea and a submit button. A user is free to type a message in the textarea which, once submitted, is displayed on the web page. This is illustrated in Figure 20.6, where the message ‘Isn’t PHP great?’ is displayed.

The problem comes when a user decides to enter a message which includes some (X)HTML elements. They are free to do this as (X)HTML is just text after all and this is known as (X)HTML injection. An example of this could be where a user enters ‘<h1>This is large!</h1>’ as the message. In this case, the user’s message is displayed as a level 1 heading. Worse than that, if a user enters only the first part of a multiple part element the whole display of the web page can be affected from that point onwards. Consider the message ‘<i>Hello, this is in italics’. The result of this displays the message in italic characters but also the text following the message. This is illustrated in Figure 20.7.

To overcome this vulnerability, you can use the PHP function htmlentities(). In its simplest form, it looks like this:

```
```text
htmlentities (string string)
```
```

The function translates ‘<’ characters into the character entity ‘&lt;’ and ‘>’ into the character entity ‘&gt;’. These are displayed as the characters ‘<’ and ‘>’ respectively in a browser but a browser does not recognize them as being the start and end of an (X)HTML element and therefore does not parse the (X)HTML element. The following script illustrates