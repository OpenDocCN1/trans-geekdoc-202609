
```bash
echo -e 'a\nb\nc\næ\nø\nå' | grep '[[:alnum:]]'
a
b
c
export LC_ALL=da_DK
echo -e 'a\nb\nc\næ\nø\nå' | grep '[[:alnum:]]'
a
b
c
æ
ø
å
```

If you really need to match the special characters based on the locale, you could use grep like this from within a PHP script:

```php
exec("echo("input") | grep 'pattern'", $output)
```

This will execute the command line given as the first argument, and save the output into the array $output. If you use this, you should be very careful not to execute strings coming from users, as this would be a serious security problem.

We can't rely on PHP to match the characters, so we use PHP to match the characters we do not want. In our example, we want to eliminate the empty spaces. So, instead of matching the characters in the words, we can get the wanted result by matching the characters that aren't blanks. The regular expression then looks like this:

```php
ereg( '([^[:blank:]]+)([:blank:]+' .
([^[:blank:]]+)([:blank:]+' .
([^[:blank:]]+)', $string, $regs);
```

This will match strings containing special characters, but it also matches numbers, which should be filtered like this:

```php
ereg( '([^[:blank:][:digit:]]+)([:blank:]+' .
([^[:blank:][:digit:]]+)([:blank:]+' .
([^[:blank:][:digit:]]+)', $string, $regs);
```

The filter can be expanded as necessary.

For more example code, refer to Chapter 7. To obtain a complete list of all the character classes, read the regex(7) manual page on any UNIX or Linux system.

## Capitalization

If the code relies on the built-in functions in PHP to capitalize strings, then use setlocale() first. Otherwise, PHP won't recognize special characters (æ, ø, å) as being part of the character set, and thus it won't convert them to uppercase:

```php
<?php
/* Some German Special Characters */
$string = 'ä ü ö';

echo(ucwords($string)); // Gives you 'ä ü ö'

setlocale("LC_ALL", 'de_DE'); // here we are setting the German locale
echo(ucwords($string)); // Gives you 'Ä Ü Ö'
?>
```

## Local Time and Dates

PHP has some functions that can be used to produce information about time and date in a format that is local to the user.

Firstly, use setlocale() to indicate the locale to be used. The syntax used is:

```
string setlocale(mixed category, string locale)
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

Start by trying to use the English name for your country, and if that doesn't work, then try using the cc_RR format. If it still doesn't work, then ask the administrator of the server whether or not the locale is installed, most likely at /usr/share/i18n/locales/.

The function strftime() is used to format a timestamp, like date(), but in a local language. It works by using a format string and an optional timestamp. If there is no timestamp supplied, the current time displayed on the computer is used. strftime() is used in combination with setlocale() like this:

```
setlocale("LC_TIME", $locale);
echo(strftime("%c"));
```

Here we used the %c format-specifier, which formats the preferred date and time representation for the current locale. The %c format-specifier creates a rather long string; therefore it's customary to get the format string itself from the locale. So in countries where the people are accustomed to using the day/month/year format, the format string should be specified as %d/%m-%y, whereas the format string should be %m/%d/%Y in other countries.

In this situation, it might not even be necessary to use strftime(), as the date() function could probably do the job. Only use strftime() if you want to include things like the name of the day or the current month.

The following is a list of format-specifiers used by the strftime() function:

| Specifier | Description |
|---|---|
| %a | The weekday name abbreviation string according to the currently enabled locale |
| %A | The full weekday name string according to the currently enabled locale |
| %b | The month abbreviation string according to the currently enabled locale |
| %B | The full month name string according to the currently enabled locale |
| %c | The date and time representation contained in the currently enabled locale |
| %C | Number indicating centuries (year divided by 100 and truncated to an integer, range from 00 to 99) |
| %d | The day of the month as a two-digit decimal number (range 01 to 31) |
| %D | Same as %m/%d/%y |
| %e | The day of the month as a decimal number: a single digit is preceded by a space (range ' 1' to '31') |
| %h | Same as %b |
| %H | Time by the hour as a decimal number using a 24-hour clock (range 00 to 23) |
| %I | Time by the hour as a decimal number using a 12-hour clock (range 01 to 12) |
| %j | Day of the year as a decimal number (range 001 to 366) |
| %m | Month as a decimal number (range 01 to 12) |
| %M | Minute as a decimal number |
| %n | The good old new line character |
| %p | Either "am" or "pm" according to the given time value, or the corresponding strings for the current locale |
| %r | Time in a.m. and p.m. notation |
| %R | Time in 24 hour notation |
| %S | Second as a decimal number |
| %t | Tab character |
| %T | Current time, equal to %H:%M:%S |
| %u | Weekday as a decimal number [1,7], with 1 representing Monday |
| %U | Week number of the current year as a decimal number, starting with the first Sunday as the first day of the first week |
| %V | The ISO 8601:1988 week number of the current year as a decimal number, range 01 to 53, where week 1 is the first week that has at least 4 days in the current year, and with Monday as the first day of the week. |
| %W | Week number of the current year as a decimal number, starting with the first Monday as the first day of the first week |
| %w | Day of the week as a decimal, Sunday being 0 |
| %x | Preferred date representation for the current locale without the time |
| %X | Preferred time representation for the current locale without the date |
| %y | Year as a decimal number without a century (range 00 to 99) |
| %Y | Year as a decimal number including the century |
| %Z | Time zone or name or abbreviation |
| %% | A literal "%" character |

Not all specifiers may be supported by your C Library, in which case they will not be supported by PHP's `strftime()`.

## Information Retrieval with localeconv()

localeconv() was added in PHP version 4.0.5, and it provides information about the formatting of strings representing monetary values. It doesn't do the formatting itself, but provides a way to learn the rules of a particular locale.

localeconv() returns an associative array with some standard elements like decimal_point, thousands_sep, and so on. For the full function description, have a look at the online documentation. You can then use these elements when you format your strings. number_format() is a suitable function to use:

```php
<?php
$amount = 123456.123;

setlocale("LC_ALL", 'en_US');
$locale_info = localeconv();

echo (number_format($amount,
    $locale_info['frac_digits'],
    $locale_info['mon_decimal_point'],
    $locale_info['mon_thousands_sep']));

setlocale("LC_ALL", 'da_DK');
$locale_info = localeconv();

echo (number_format($amount,
    $locale_info['frac_digits'],
    $locale_info['mon_decimal_point'],
    $locale_info['mon_thousands_sep']));

?>
```

The first echo statement gives us 123,456.12, and the second gives us 123.456,12. It's fairly straightforward to use localeconv() for simple tasks, but it gets more complicated if we need to take into account all the information it presents us with.

We will see a great deal of information about currency symbol order and displaying currency amounts. The following function will also tell us whether or not there should be a space between the two parts of the currency display. The function uses this information to return a formatted string:

```php
function localef($amount)
{
    //Export the values returned by localeconv into the local scope
    extract(localeconv());
```

The function starts by formatting a number with number_format(). This function uses the absolute value of $amount, so we strip the minus sign. We need to be sure of the absolute value of $amount, since the locale might provide its own signs instead of the standard + and -. This function changes $sign to the correct sign:

```
// Start by formatting the unsigned number
$number = number_format(abs($amount),
    $frac_digits,
    $mon_decimal_point,
    $mon_thousands_sep);
```
