
- User messages in native languages
- Code conversion support
- Input method support

This information must be determined during application execution. NLS provides these capabilities and a base upon which new languages and code sets can be supported. As a result, programs can be ported across national language and locale boundaries.

## Reasons for Internationalization

Though i18n is not important for every script, there are several applications for which i18n is a necessity. For instance, customers to an online store are more likely to buy a product that is presented to them in their native language than if they are reading a language not familiar to them.

Likewise, if we're writing PHP scripts and programs that are free or available as open source programs, prospective users like to adapt them to their site and their culture. They want the look, feel, and language of the script to match their site; consequently, our script should be easy to customize, both in appearance and in language. PHP has the necessary infrastructure to support i18n – it supports conditional inclusion of files (each file could contain a different language, which we'll see later) and it supports the Gettext library.

So, why is it so hard to translate web site content into another language? Can't we just copy the script to another file and then translate the text? The answer is, because this is not a good solution. It is not easy to keep two or more versions synchronized. The process becomes harder as the translators forget to fix the problems that the original document writers have discovered. Communication costs increase rapidly as soon as more than three or four languages have to be supported. We would end up with several different versions of the same program that will not do things in exactly the same way.

## The Problem

It is necessary to have some system that helps manage the translations. It helps to view natural and programming languages as grammars producing text strings with slightly differing purposes. The system should place the natural language strings in a place that is distinct from location of the PHP script routines.

This makes bug fixing a lot easier, since translated texts will be easier to find. If we fix a bug in a natural language string, then it is easier to fix the bug for all natural languages used in the script, and not just for the version and the language we are supposed to maintain. Ease of text string access in all languages is essential for every translation system.

By moving the strings out of the heart of the script, programmers also gain some other advantages:

- Translators don't have to decipher code. If the programmers want to have the GUI text or the web site documents translated into other languages, it's very important that translators have easy access to the natural language strings.
- Making it less likely for translators to break the code is an important defensive programming skill. Even just adding an apostrophe or a quote can break the script.

## Chapter 22

A translator should be able to write translated text strings that are in tune with the target language. The text string could be written in any language, and could use any kind of punctuation without running into problems caused by misplaced quotes and strange characters. Again, text display has to be adapted to the target language without disturbing the rest of our program.

The diagram below should help PHP programmers and translators visualize the way in which PHP handles translated text:

![](img/9cf7789dba9b16ef3f8576d5aea89186_815_0.png)

## Strings

Let's classify the different string output types that make text string translation easier:

- Static strings
- Dynamic strings

### Static Strings

These strings display simple messages to the user. Static strings are easy to translate, since they don't depend on context. They are self-contained, which gives the translator a free hand to do the translation. An example of a static string would be a greeting that is displayed when a user accesses a page.

The following HTML shows how easy it is to translate static strings:

```html
<html>
  <head>
  <title>Welcome!</title>
  </head>
  <body>
  <h1>Welcome to our Site!</h1>

  <p>We hope you'll find the information you're looking for. If you
  have any questions, please feel free to contact us.</p>

  </body>
</html>
```

### Dynamic Strings

It is very rare to find that all the text in a script is static. Dynamic strings are strings that contain numbers and other elements that change at run time. They might change as a result of user input or as a result of a change in the state of some OS routine. They might be messages or real time updates from the stock market or a weather report.

An example is the string that tells a user how many files there are in a given directory. This string would say something like "1 file" or "17 files". Here the numbers would change as the user browses the filesystem. Also, we would have to change the text from "file" to "files".

In a script that does not take i18n into account, we could write a function like this:

```php
function outNumFiles($count)
{
  if ($count <= 0) {
    echo("No files.");
  } elseif ($count == 1) {
    echo("1 file.");
  } else {
    echo("$count files.");
  }
}
```

The string literals should not be hard coded in the script, since the language used in the function might need to change at run time. If string literals should not be present, then how are we supposed to substitute other strings, especially of a different language?

Functions that can format strings can solve this problem:

- printf() Output the formatted string
- sprintf() Return the formatted string

These functions work by passing a formatting flag, plus one or more strings as arguments. The formatting flag dictates:

- Where the string arguments should be inserted in the output string
- The type and format of the string inserted in the output string

A %s formatting flag, present in the format string, will be replaced by one of the arguments to the function like this:

```php
printf('This is the %s. Hello %s', 'format string', 'World');
/* Outputs 'This is the format string. Hello World' */
```

### Storing the Strings

Since we need to store the strings somewhere else than directly in the main PHP code, let's take a look at how this can be done.

### Dividing Textual Data from Programming Functionality

PHP has the ability to include and parse files at run time, therefore the natural solution is to store the text strings in a separate data file. Later on, the data file can be included in the main program via an include() directive. We could use basic OO directive techniques, but for the moment, we will just assume that the data will be inserted right in front of the main PHP script routines.

Both approaches work well, and they fit all our requirements. The strings are removed from the core of the script, bugs can be fixed without changing the original text strings or one of the translations, and it makes it easy for inexperienced programmers to localize their script.

We can either store the strings in a lot of different variables, or use one array, like this:

```php
$strings = array('welcome' => 'Welcome to the application!',
                     'say_time' => 'The time is:',
                     'good_bye' => 'Goodbye - come again soon!');
```

Now enter the code and the text into a file called translate.php. We can prepend the text data before the main PHP core routines. Alternatively, data can be kept in a separate file by creating a small program containing the text strings and saving it into a new file. This code can be included before the following:

```php
<?php
include("translate.php");

echo( "<p>" . $strings['welcome'] . "</p>\n");
echo( "<p>" . $strings['say_time'] . " " . date('H:i') . "</p>\n");
echo( "<p>" . $strings['good_bye'] . "</p>\n");
?>
```

As long as the array indices are identical in both files, the new strings can be used. Other strings using the same array indices and string names can be used in the translation. To translate, we will have to edit the three strings in the previous file. As long as the indices are the same in the array, the new strings will be used.

The next step is to make sure that all functions have access to the array. Functions use global variables by default. Thus, without declaring `$strings` as a global variable, the function will simply create a local variable with the same name:

```php
function welcomeGoodbye()
{
    global $strings;

echo( "<p>" . $strings['welcome'] . "</p>\n");
echo( "<p>" . $strings['say_time'] . " " . date('H:i') . "</p>\n");
echo( "<p>" . $strings['good_bye'] . "</p>\n");
}
```

This is where a main difference between using string variables and using an array comes into play. If we had been using strings instead of an array we would have had to declare all the strings as global variables. However, when we do that, we have to be careful that we don't overwrite the variable later – doing so would change the translation at run time, something which we're most certainly not interested in. So we give the global variables a common prefix (str_ in this case). The sample function would then look like this:

```php
function welcomeGoodbye()
{
    global $str_welcome, $str_say_time, $str_good_bye;

echo( "<p>$str_welcome</p>\n");
echo( "<p>$str_say_time" . date('H:i') . "</p>\n");
echo( "<p>$str_good_bye</p>\n");
}
```

This approach to internationalization has some serious drawbacks, namely the lack of provision for redundancy in natural languages. Many phrases are repeated many times over in the same text segment. This is even more common in technical and web site documentation. Also, information on character sets, formatting conventions, dates, and currency have not been included.
