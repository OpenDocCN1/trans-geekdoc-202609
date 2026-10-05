# Chapter II.2: Regular Expressions 131

```
echo $text;
function replace_text($matches)
{
  return substr($matches[0], 1).strtolower(substr($matches[0], 1));
}
```

The regular expression [A-Z]{2,} searches for all words with two or more uppercase letters in a row. These words are replaced with the result returned by the replace_text() callback function. The function's parameter is an array of the matched strings, the first element in array elements containing the matches for successive parenthesized parts of the regular expression. The function leaves the first letter of each matched string unchanged and changes to lowercase the remaining letters with the help of strtolower() function.

PHP has a special function for converting the first letter of a word to uppercase and the rest into lowercase: ucfirst(). However, in most cases, it does not work properly with national language characters; therefore, for fail-safe operation on all servers the solution presented in Listing II.2.10 is preferable.

![](bbox=[0.075, 0.465, 0.143, 0.535])

# II.2.10. Splitting Long Strings

Long strings, like the problem in Section II.2.8, are amenable to the preg_replace_callback() function using a custom callback function (Listing II.2.11).

# II.2.11. Splitting a long string

```
<?php
$text = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAaaaaaaaaaa";

$text = preg_replace_callback(
  "!(\w{25,})|",
  "split_text",
  $text
);

function split_text($matches)
{
```