use just \n. The Macintosh uses just \r. Go figure. But the truth is, browsers don't really care because they treat all whitespace (including linefeeds) as a single space. So I just always use \n.

# Embedding variables (and printing them, too)

If you're using the heredoc style strings or the double-quote style strings, you can use a cool technique for embedding your variables right in the strings. Why would you do that? Take a look at the following code:

```
```php
<?php
 $myname = "me";
 print "Hello, $myname! It's a fine name and my name
 too!";
 ?>
```
```

This code results in the following HTML:

Hello, me! It's a fine name and my name too!

This output is just as if you printed "Hello," and then the value stored in $myname, and then "! It's a fine name and my name too!".

The PHP processor doesn't always know exactly where the variable name ends, resulting in confusion. Look at these two lines:

```
```php
$word = "apple";
print "$words are my favorite food";
```
```

The PHP processor doesn't know that the variable you're attempting to use in the string is $word. Instead, it looks for a variable called $words. To fix this, you can surround the variable name with braces, like so:

```
```php
$word = "apple";
print "{$word}s are my favorite food";
```
```

Or you can put the dollar sign outside the braces and just surround the name itself with braces, as in ${word}.

# Concatenating and squishing together strings

Concatenation is one of those words that no one outside the computer world seems to know, yet each person inside the computer world, after learning what it is, uses the technique almost daily. If you're new to concatenation, you can be sure to start using it at the beginning of your day, just after your morning cup of coffee.