This example replaces all occurrences of hamburger, bacon, and bucket o'grease in $string with Atkins-friendly foods.

You can even provide two arrays of the same size as your search-and-replace arguments, and str_replace() replaces an item in the search array with the replacement item with the same index:

```
```php
$ugly_words = array("hamburger", "bacon", "bucket o'grease");
$replacements = array("carrot", "broccoli", "2% milk");
$string = str_replace($ugly_words, $replacements, $string);
```
```

This replaces all instances of hamburger with carrot, all instances of bacon with broccoli, and all instances of bucket o'grease with 2% milk.

# What Can Go Wrong?

One problem with str_replace() is that it replaces everything that matches the pattern you gave it, no matter where it is in the string. If you replace off with on, you will discover that your officials are now onicials and your coffins are now conins.

Thus, while str_replace() is invaluable for stripping unwanted words from small-scale strings, you'll need regular expressions for more complex tasks. (See “#39: Regular Expressions” on page 69.)

# #38: Finding and Fixing Misspelled Words with pspell

Anyone who’s used Google has misspelled a word in a search, for example, alternative music. And Google always helpfully comes back with Did you mean alternative music?

If you have a search function on your site, the ability to suggest misspelled words when no results (or not enough results) are found is an extremely helpful feature, especially since a customer’s lack of spelling ability might cost you a sale. Fortunately, there’s a PHP module called pspell, which allows you to check a word’s spelling and suggest a replacement from pspell’s default dictionary. If you like, you can even create a custom dictionary. To start with, though, you’ll need to make sure that your PHP has the pspell library installed. Try this test script:

```
```php
<?php
$dict_config = pspell_config_create('en', 'american');
?>
```
```

If you get an error, you don’t have the pspell library installed. Flip back to “#18: Adding Extensions to PHP” on page 27 to see how to do this.