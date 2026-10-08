
# Using the Calendar Functions

PHP has a set of functions that enable you to convert between different calendar systems.
The main calendars you will work with are the Gregorian, Julian, and Julian Day Count.

Most Western countries currently use the Gregorian calendar. The Gregorian date October 15, 1582, is equivalent to October 5, 1582, in the Julian calendar. Prior to that date, the Julian calendar was widely used. Different countries converted to the Gregorian calendar at different times and some not until in the twentieth century.

Although you may have heard of these calendars, you might not have heard of the Julian Day Count (JD). It is similar in many ways to a Unix timestamp. It is a count of the number of days since a date around 400 BC. In itself, it is not particularly useful, but it is useful for converting formats. To convert from one format to another, you first convert to Julian Day Count and then to the desired output calendar.

To use these functions in Unix, you first need to compile the calendar extension into PHP with `--calendar`. These functions are built into the Windows installs.

To give you a taste for these functions, consider the prototypes for the functions you would use to convert from Gregorian to the Julian calendar:

```
int gregorianjd(int month, int day, int year)
string jdtojulian(int julianday)
```

To convert a date, you would need both of these functions:

```php
$jd = gregorianjd(9, 18, 1582);
echo jdtojulian($jd);
```

This call echoes the Julian date in a MM/DD/YYYY format.

Variations of these functions exist for converting between the Gregorian, Julian, French, and Jewish calendars and Unix timestamps.

# Further Reading

If you would like to read more about date and time functions in PHP and MySQL, you can consult the relevant sections of the manuals at: http://php.net/manual/en/book.datetime.php and http://dev.mysql.com/doc/refman/5/en/date-and-time-functions.html.

If you are converting between calendars, the true manual for PHP's calendar functions: http://php.net/manual/en/book/calendar.php.

# Next

We mentioned locales a bit during our discussion of dates and times, and understanding locales is part of understanding the internationalization of web applications. In Chapter 20, “Internationalization and Localization,” we discuss how localization is far more than just translation, and how to prepare your applications for localization.

# 20
## Internationalization and Localization

In this chapter, we discuss the basics of internationalizing your web applications in preparation for localizing their contents. Creating internationalized web applications with PHP is simple, and the benefits to your international audience are numerous. Start by understanding how internationalization and localization are different, but related, concepts, and you'll be prepared to capture a truly worldwide audience.

Key topics covered in this chapter include:

- Understanding and preparing for different character sets
- Structuring your application to produce localized content
- Using gettext() for internationalization and localization

# Localization Is More than Translation

A common misconception is localizing a website, application, or really anything, is just about translating the content for the target location. However, it is important to understand that neither internationalization nor localization is the same as content translation. In fact, if you have a website or web application full of content that is translated—such as all in German, all in Spanish, or all in Japanese—and it might not be considered an internationalized or even localized website or web application at all. It would just be a translated website or web application, and that's it.

In order to create localized software (encompassing websites and web applications, as well as other types), you must first internationalize. The basic aspects of internationalized software include:

- Externalized strings, icons, and graphics
- Modifiable display of formatting functions (dates, currency, numbers, and so on)

Only after you have constructed your software so that your strings are externalized—meaning when all strings used in functions, classes, and other places within your code are managed in one place and included or otherwise referred to as constant variables—and your formatting functions change per locale, can you begin the process of localization. Content translation happens to be part of localization, or targeting your software for a particular locale.

A locale is a place where something is set, such as the place where people live and speak English and the word "color" without a "u"—you might refer to that as "The United States of America." In the world of computing, a locale refers to a set of parameters that identifies a user's language, geographic region, and any other preferences based on locale that may be better to represent within a user interface.

Standard locales consist of both language and region indicators, such as en_US for "English language in the United States" and en_GB for "English language in Great Britain."

You might ask why the region differentiation, but just about the spelling differences between American and British English, also the contextual differences you might want to apply to your software for users in the United States versus Great Britain. To use another example, suppose you maintain a website with text in German and targeted for use by people in Germany—that would be the de_DE locale ("German language in Germany"). While Austrians speak German may well use that site perfectly fine as-is, unless you have located the site for the de_AT locale ("German language in Austria") that website would not be right for those others.

# Understanding Character Sets

Character sets are usually referred to as single-byte or multibyte, referring to the number of bytes needed to define a character with a language. English, German, and French (many others) are single-byte languages, as only 1 byte is necessary to represent such a character as the letter a or the number 9. Single-byte sets have, most 256 characters, including the entire set of ASCII characters, accented characters, and other characters necessary for formatting.

Multibyte character sets have more than 256 characters, including all the single-byte characters as a subset. Multibyte languages include Traditional and Simplified Chinese, Japanese, Korean, Thai, Arabic, and Hebrew, among others. These languages require more than 1 byte to represent a character. A good example is the word Tokyo, the capital of Japan. In English, it is spelled with four characters; in Japanese, the word is represented by two syllables, tou and kou, which uses 2 bytes, for a total of 4 bytes used.

To properly interpret and display the text of web pages in their intended language, it is up to tell the web browser which character set to use. This goal is achieved by sending the appropriate headers before all content.

The headers in question are the Content-type and Content-language headers, and these can be set as HTML5 tag attributes. Because PHP provides you with the ability to create dynamic environment, go ahead and cover all bases by sending the appropriate headers and also print the correct HTML5 tags.

The following is an example of the header() function outputting the proper character set for an English site:

```php
header("Content-Type: text/html;charset=ISO-859-1");
header("Content-Language: en");
```

The accompanying HTML5 tags for the above are:

```html
<html lang="en">
<meta charset="ISO-859-1">
```

A Japanese site uses a different character set and different language code:

```php
header("Content-Type: text/html;charset=UTF-8");
header("Content-Language: ja");
```

The accompanying HTML5 tags for these headers are:

```html
<html lang="ja">
<meta charset="UTF-8">
```

It is important to set your headers appropriately because, for example, if you have a set of pages that include Japanese text and you do not set the correct headers regarding language and character set, those pages will not render correctly. In other words, no character set information was included, the browser would assume that it is proper to render the text using its default character set.

# Implications of Character Sets

Throughout the PHP Manual—and especially in the sections that interact with databases as MySQL—you may see about the security implications of character sets. It is not to say that character sets themselves are inherently insecure. Instead, these are cautions to ensure that developers understand a little about the character sets and how security issues may arise if precautions are not taken when working with strings that contain these characters—for example, in SQL statements.

A classic example of character set-related security issues is the encoding mismatch between the server, PHP and MySQL, and especially with multibyte languages. Let's say that PHP thinks it is sending ASCII text to MySQL, and the database's default character set is Big5. In this situation, when you use a function such as mysql_real_escape_string() (or its objectoriented counterpart) to escape strings before sending them to the database, PHP will miss the trailing character of the double-byte character set because it simply didn't know to look for it.
