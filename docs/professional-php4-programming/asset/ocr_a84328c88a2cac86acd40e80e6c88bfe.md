```
```php
if (isset($strings[$string])) {
    return $strings[$string];
} else {
    return $string;
}

function gettext($string)
{
    return _($string);
}
```
```

This works thanks to PHP's wonderful arrays that allow you to use strings as the keys. The changes to our program are small but powerful:

```
```php
function outNumFiles($count)
{
    if ($count <= 0) {
        print(_("No files."));
    } elseif ($count == 1) {
        print(_("1 file."));
    } else {
        printf(_("%s files."), $count);
    }
}
```
```

The program still speaks English, but it's now easy to change the language as all the hard-coded strings have been replaced with calls to _(). We've been careful not to assume too much about the language that's going to use the function.

When internationalizing programs, it's always important to remember languages that deal with numbers in unfamiliar ways. If you can write your output routines in a style that permits coverage of these languages, then you eliminate the burden on the localization expert, because they won't have to write the code. We use the sprintf() function to format the output string in the else part when we're dealing with many files.

To change the language in the Gettext-version you should go through the steps explained earlier in the section GNU Gettext. In the other version, all you have to do to change the language is to include a file that holds a different definition of $strings – different from the previous definition which was null. If we want to localize our script for Danish, the $strings array would look like this:

```
```php
$strings = array(
    'No files.' => 'Ingen filer.',
    '1 file.' => '1 fil.',
    '%s files.' => '%s filer.');
```
```

Save this code in a separate file which is included in the file that contains the code for outNumFiles(). The Danish translation works perfectly, but it only works because the grammatical structure of Danish and English are quite similar. Here, we're having an exact mapping from each English word to a Danish word. We could illustrate this with an array: