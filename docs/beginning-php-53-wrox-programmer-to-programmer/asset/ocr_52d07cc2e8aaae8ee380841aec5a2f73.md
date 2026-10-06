# Chapter 10: Preserving State With Query Strings

```
$firstName = "John";
$age = "34";
$queryString = "firstName=$firstName&amp;age=$age";
echo '<a href="moreinfo.php?'.$queryString.'>Find more info on
this person</a>";';"
```

This code generates the following markup:

```
<p><a href="moreinfo.php?firstName=John&amp;age=34">Find out info on
this person</a></p>
```

If the user clicks this link, moreinfo.php is run, and the query string
(firstName=John&age=34) is passed to the moreinfo.php script. Data has been transmitted from one
execution to the next.

Note that the ampersand (&) character needs to be encoded as &amp;

One thing to watch out for is the type of characters that you insert into the field names and values in
y query string. A query strings only allows the following characters to be used
within field names and values: letters, numbers, and the symbols -, _, .(period), !, *, ' (single quote),
and ).

So what do you need to transmit other characters, such as spaces, curly braces, or ?nThe answer is that you should use urlEncoding. This is a scheme that encodes reserved characters
as hexadecimal values preceded by a percent (%) symbol, with the exception of space characters, which
are encoded as plus (+) signs. (Characters that don't need to be encoded, as letters and numbers,
are sent as they are).

As happens, PHP gives you a function called urlencode() that can encode any string using URL
encoding. Simply pass a string to encode, and it returns the encoded string. So you can use
urlencode() to encode any data that may contain reserved characters. Here's an example:

```
$firstName = "John";
$homePage = "http://www.example.com/";
$favoriteSport = "Ice Hockey";
$queryString = "firstName=$firstName&amp;homePage=".urlencode($homePage)."&amp;favoriteSport=".urlencode($favoriteSport);
echo '<p><a href="moreinfo.php?'.$queryString.'>Find more info on
this person</a>";';"
```

This code outputs the following markup:

```
<p><a href="moreinfo.php?firstName=John&homePage=http%3A%2F%2Fwww.example.com%2F&amp;favoriteSport=Ice-Hockey">Find out info on this person</a></p>
```

If you ever need to decode a URL-encoded string you can use the corresponding urldecode() function. See http://www.php.net/urldecode for details.