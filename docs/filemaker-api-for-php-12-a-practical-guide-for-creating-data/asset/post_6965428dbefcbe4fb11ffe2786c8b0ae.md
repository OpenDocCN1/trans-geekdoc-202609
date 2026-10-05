
seconds (since Unix Epoch on January 1, 1970).

```
$today = date('U', strtotime($record->getField('Date')));
$date = date('U', strtotime($record->getField('Date2')));
If($today <= $date) {
    echo $today . "<" . $date;
} else {
    echo $today . ">" . $date;
}
?>
<body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_286_0.png)

Figure 7-100: Five different methods to compare dates.

# Lesson 36: Display HTML/CSS Using PHP

**Objective:** In this lesson you will learn how to display HTML/CSS stored in a field. For those of you publishing data to the web using PHP you'll eventually run across the need to display HTML or CSS content stored in a field. For example, maybe you have a shopping cart with all the card stored in your product table, as our product Pay eCommerce Pro, or maybe you want to allow your users to type in stylized text and have it display on the web correctly without the users needing to know anything about HTML or CSS tags.

**Difficulty:** Easy

**Sample Files:**
PHPFiles/Advanced/Lesson36/DisplayHTMLCSSUsingPHP.php
PHPFiles/Advanced/Lesson36/DisplayHTMLCSSUsingPHP.fmp12

> This lesson uses a separate database file to demonstrate the lesson. Please upload the DisplayHTMLCSSUsingPHP.fmp12 database file to your server.

**Page Navigation:**

- - List

**FileMaker API Methods:**
newFindAllCommand()
execute()
getFirstRecord()
getField()

**Code:**

Start by connecting to the database.

```html
<body>
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'DisplayHTMLCSSUsingPHP');
$fm->setProperty('hostspec', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>
</body>
```

Scroll down to the bottom of the code where it starts with the following code:

```
echo '<td>' . html_entity_decode($record->getField('Text')) . '</td>';
```

| html_entity_decode(string): Convert all HTML entities to their applicable characters. | http://us.php.net/manual/function.html-entity-decode |

What you notice is the use of the PHP function html_entity_decode(). What this function is to convert all the HTML entities to their applicable characters and display the HTML and CSS from the Text field as expected. If you were to omit this function using the normal FileMaker API for PHP code you would get the contents of the field

field "as is", without any HTML or CSS formatting. Means the HTML and CSS tags show up as raw text. You can see the difference on the sample web page in your browser when you compare it against the content in the database.

```php
echo '<td>' . $record->getField('Text') . '</td>';
```

The FileMaker API also has the getFieldUnencoded() function that will return the unencoded field contents. It does not have, however, special characters to HTML entities.

```php
echo '<td>' . $record->getFieldUnencoded('Text') . '</td>';
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_288_0.png)

You may find the following functions useful when you need to encode/decode special characters using PHP and FileMaker.

- html_entity_decode() — Convert all HTML entities to their applicable characters http://us3.php.net/manual/en/function.html-entity-decode.php
- htmlentities() — Convert all applicable characters to HTML entities http://www.php.net/manual/en/function.htmlentities.php
- htmlspecialchars() — Convert special characters to HTML entities http://www.php.net/manual/en/function.htmlspecialchars.php
- htmlspecialchars_decode() — Convert special HTML entities back to characters http://www.php.net/manual/en/function.htmlspecialchars-decode.php

All PHP String Functions http://www.php.net/manual/en/ref/strings.php

# Lesson 36: Display HTML Using PHP

| Decoded | Raw Text |
|---|---|
| This is plain text will display when entered into the field. | This is plain text will display when entered into the field. |
| Notice that formatting you apply inside FileMaker does not translate to a PHP web page | Notice that formatting you apply inside FileMaker does not translate to a PHP web page. |
| Here is how to format data in a field for the web the next record and | This is how to format data in a field for the web the next record and |

DisplayHTMLUsingPHP sample web page
If you want to include HTML tags for likes or CSS styles you use the PHP method `html_entity_decode()`

Unencoded Text
This is plain text will display when entered into the field. Notice that formatting you apply inside FileMaker does not translate over a PHP web page. Here is how to format data in a field for the web the next record.

DisplayHTMLUsingPHP sample web page
If you want to include HTML tags for likes or CSS styles you use the PHP method `html_entity_decode()`

A nice feature of FileMaker is that you can provide a CSS script to convert the CSS for your users. You can also use a calculation, which will allow them have easily easily while while use the calculation for your web page to ensure the formatting displays as expected.

```
<span>&lt;* if you want to include <span>&lt;HTML&gt;</span>&lt;SPAN&gt;</span> tags for likes like forms or CSS styles you want to use the method <span>&lt;SPAN&gt; style="font-size:14px;font-weight:bold;"&gt;html_entity_decode(Text)&lt;/SPAN&gt;</span> It is fairly accurate in it uses a script to convert the CSS for your users.
```

For those who don't want to read the HTML-CSS code if you want to include HTML tags for likes forms or CSS styles you have to use the method
A nice feature of FileMaker is that you can provide a CSS script to convert the CSS for your users. You can also use a calculation, which will allow them to have easily readable while you use the calculation on your web page to ensure the formatting displays as expected.

If you want to include HTML tags for likes forms or CSS styles you have to use the PHP method `html_entity_decode()`. A nice feature of FileMaker is that you can provide a CSS script to convert the CSS for your users. You can also use a calculation, which will allow them to have easily readable while you use the calculation on your web page to ensure the formatting displays as expected.

For those who don't want to read the HTML-CSS code if you want to include HTML tags for likes forms or CSS styles you have to use the method

If you want to include HTML tags for likes forms or CSS styles you have to use the PHP method `html_entity_decode()`. A nice feature of FileMaker is that you can provide a CSS script to convert the CSS for your users. You can also use a calculation, which will allow them to have easily readable while you use the calculation on your web page to ensure the formatting displays as expected.

Figure 7-101: Compare the methods to display HTML/CSS in. (Wait, text says "display HTML/CSS in.")

![](img/5a2c5fda68d42e5d65f51850276e49ec_289_0.png)
