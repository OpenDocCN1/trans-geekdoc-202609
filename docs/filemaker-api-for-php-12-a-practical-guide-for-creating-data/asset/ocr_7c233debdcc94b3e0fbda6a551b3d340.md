field "as is", without any HTML or CSS formatting. Means the HTML and CSS tags show up as raw text. You can see the difference on the sample web page in your browser when you compare it against the content in the database.

echo '<td> $record->getField('Text') . '</td>';

The FileMaker API also has the getFieldUnencoded() function that will return the unencoded field contents. It does not have, however, special characters to HTML entities.

echo '<td> $record->getFieldUnencoded('Text') . '</td>';

![](bbox=[0.095, 0.241, 0.636, 0.303])

You may find the following functions useful when you need to encode/decode special characters using PHP and FileMaker.

+   - html_entity_decode() — Convert all HTML entities to their applicable characters http://us3.php.net/manual/en/function.html-entity-decode.php
- htmlentities() — Convert all applicable characters to HTML entities http://www.php.net/manual/en/function.htmlentities.php
- htmlspecialchars() — Convert special characters to HTML entities http://www.php.net/manual/en/function.htmlspecialchars.php
- htmlspecialchars_decode() — Convert special HTML entities back to characters http://www.php.net/manual/en/function.htmlspecialchars-decode.php

All PHP String Functionsnhttp://www.php.net/manual/en/ref/strings.php