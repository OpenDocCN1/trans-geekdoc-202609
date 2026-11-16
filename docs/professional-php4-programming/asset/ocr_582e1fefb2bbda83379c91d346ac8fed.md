```
```php
<?php
/* Some German Special Characters */
$string = 'ä ü ö';

echo(ucwords($string)); // Gives you 'ä ü ö'

setlocale("LC_ALL", 'de_DE'); // here we are setting the German locale
echo(ucwords($string)); // Gives you 'Ä Ü Ö'
?>
```
```

# # Local Time and Dates

PHP has some functions that can be used to produce information about time and date in a format that is local to the user.

Firstly, use setlocale() to indicate the locale to be used. The syntax used is:

```
`string setlocale(mixed category, string locale)`
```

category is used to define the scope of the locale change. It can take the following values:

| Category Specifier | Scope of Locale Change |
|---|---|
| LC_ALL | For all of the below |
| LC_COLLATE | For string comparison |
| LC_CTYPE | For character classification and conversion, that is, strtoupper() |
| LC_MONETARY | For currency conversion |
| LC_NUMERIC | For decimal separator |
| LC_TIME | For date and time formatting with strftime() |

The LC_TIME category enables locale-specific formatting of time and dates.

What we should use for the locale setting is somewhat implementation specific. We can use a string of the type cc_RR where cc is the country-code for your country, as defined in the ISO 639 standard, and RR is the region (which is not the same as the country-code).

Some base languages are used in many different parts of the world, so it's necessary to append the specified region. English is a good example. Its ubiquity means that we can have locales installed on our system for Australia, Botswana, Canada, Denmark, Britain, Hong Kong, Ireland, India, New Zealand, Philippines, Singapore, the USA, South Africa, and Zimbabwe.

Normally there's also a file that defines some aliases for the languages, so that we can use either danish, dansk, or da_DK to specify the Danish locale. Locale aliases are case-insensitive, so we could also write Danish, DANISH, or DaNiSh. The locale is case-sensitive otherwise, so it should be specified as da_DK and not as da_dk.