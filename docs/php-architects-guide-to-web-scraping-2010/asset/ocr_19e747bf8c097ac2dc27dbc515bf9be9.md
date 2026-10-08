+   - u: Forces pattern strings to be treated as UTF-8 encoded strings.

The example below matches because the *i* modifier is used, which means that the pattern matches '`a`' and '`A`'.

```
```php
<?php
$matches = (preg_match('/a/i', 'A') == 1);
?>
```

# ## Wrap-Up

This chapter has covered the most essential aspects of regular expressions that apply to validation of scraped data. There are more advanced aspects of regular expressions that may be useful in other areas. Further review of the PCRE section of the PHP manual is encouraged.

+   - For pattern modifiers, see [http://php.net/manual/en/reference.pcre.pattern.modifiers.php](http://php.net/manual/en/reference.pcre.pattern.modifiers.php).
- For pattern syntax, see [http://php.net/manual/en/reference.pcre.pattern.syntax.php](http://php.net/manual/en/reference.pcre.pattern.syntax.php).
- For an excellent book on regular expressions, see “Mastering Regular Expressions,” ISBN 0596528124.