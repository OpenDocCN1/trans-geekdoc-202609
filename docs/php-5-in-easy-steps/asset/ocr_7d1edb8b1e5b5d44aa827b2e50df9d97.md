# String manipulation

This example demonstrates how strings can be manipulated using some of PHP’s string functions. The function name is sent to the server, when the form is submitted, as the value associated with the key "fcn".

![](bbox=[0.183, 0.198, 0.263, 0.283])

```
<html><head><title>String Manipulation</title> </head>
<body>
<form action="strings.php" method="post">
<b>Enter some text here:</b> <br>
<textarea name="txt" rows="3" cols="45"></textarea>
<input type="radio" name="fcn" value="strlen">
Find the text length
<input type="radio" name="fcn" value="strrev">
Reverse the text<br>
<input type="radio" name="fcn" value="strrtoupper">
Change to all uppercase
<input type="radio" name="fcn" value="strtolower">
Change to all lowercase<br>
<input type="radio" name="fcn" value="ucwords">
Make the first letter of all words uppercase <hr>
<input type="submit" value="Manipulate">
</form>
</body>
</html>
```

strings.html

The string to be manipulated in this example is the text input content of the textarea, which is sent to the server with the "txt" key.

![](bbox=[0.073, 0.483, 0.143, 0.545])

| String Manipulation |
| File Edit View Favorites Tools Help |
| Address http://localhost/strings.html Go |
| Enter some text here: |
| PHP is fantastic - and so easy to learn! |
| ○ Find the text length ○ Reverse the text |
| ○ Change to all uppercase Change to all lowercase |
| ○ Make the first letter of all words uppercase |
| Manipulate |
| Done Local intranet |