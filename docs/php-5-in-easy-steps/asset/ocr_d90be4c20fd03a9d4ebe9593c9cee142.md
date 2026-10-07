# # Displaying submitted values

When HTML form data is submitted with the "post" method, PHP adds each submitted key-value pair to its special $_POST[] array. Any submitted value can be referenced by adding its key (input name) within the square brackets. For instance, the color value in this example can be referenced by $_POST['color'].

Surround the keys with single quotes to differentiate them from text strings, which are double quotes.

![](bbox=[0.035, 0.175, 0.12, 0.255])

The PHP script below begins by assigning each submitted value to a variable, named as it key. The script checks for null values, to ensure input, then uses the values in generated output.

```
<<head><title>Your submission</title></head>
<body><img src="foodn.jpg" width="368" height="54">
<?php
$username = $_POST['username']; //assign value
$color = $_POST['color']; //assign value
$dish = $_POST['dish']; //assign value

if ($username != null) {
    echo("Thanks for your selection $username<hr>");
    if ($color != null) && ($dish != null) {
        $msg = "You really enjoy $dish<br>";
        $msg = "- especially with a nice $color wine";
        echo ($msg);
    }
}
</body></html>
```

![](bbox=[0.185, 0.36, 0.285, 0.45])

The first statement block will be executed only if the user has entered a username value. The second statement block will be executed only if the user has entered both a color and a dish value.

![](bbox=[0.035, 0.475, 0.12, 0.565])

If for some reason the submission method is unknown the values can be referenced from the special $_REQUEST[] array in the same way as with $_POST[].

![](bbox=[0.035, 0.735, 0.12, 0.825])

| Your submission |
| Edit | View | Favorites | Tools | Help |
| Address Mike&color=white&dish=BeefStifado+with+Greek | Go |
| Thanks for your selection Mike |
| You really enjoy Beef Stifado with Greek salad - especially with a nice white wine |
| Done 
 Local intranet |

6. Generating dynamic content | 99