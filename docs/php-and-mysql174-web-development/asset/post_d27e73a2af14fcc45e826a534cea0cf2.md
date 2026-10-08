
This miscommunication will cause the encoded character to essentially become gibberish, which is bad enough if you intend to display it in a user interface. However, an worse outcome is when someone takes advantage of this mismatch by injecting SQL into what is an open string making its way to your database for possible execution.

## Multibyte String Functions in PHP

Having mentioned multibyte character encoding schemes previously in this chapter, I would not remit to point out that PHP includes a set of built-in functions specifically to handle the manipulation of multibyte strings. With a non-multibyte-aware string function, if you attempt multibyte strings you very likely will not parse the string correctly—these single-byte characters shouldn't know what to do (or do something messy) when faced with multibyte strings.

In order to use the multibyte string functions in PHP, they must be enabled during the configuration process using --mbstring when configuring and building PHP. Windows users will need to enable the php_mbstring extension in php.ini. After this is configured, you can use any of the more than 40 mbstring-related functions for handling multibyte input in PHP.

You can read about these multibyte string-related functions in detail in the PHP Manual at http://www.php.net/mbstring. As a general rule when working with multibyte strings, just look for a similarly named function (e.g., mb_stripos() versus just strpos() to find the first occurrence of a string within another string).

## Creating a Basic Localizable Page Structure

Now that you've learned some foundational information about internationalization, localization, and character sets, take a look at a basic localizable page structure for a website. These pieces here enable a user to select a target language and receive a welcome message in the appropriate language.

The goal of this section is to provide a basic example of extraling strings—which is one of the characteristics of internationalization—and presenting localized text based on user preferences. The workflow of this set of scripts is that a user happens upon your English-based website but is also presented with an option to browse within the locale of the user's choice (only English or Japanese in this example).

Three elements are introduced in this process:

- Creating and using a master file for sending locale-specific header information
- Creating and using a master file for displaying the information based on the selected locale
- Using the script itself

Listing 20.1 shows the contents of the master file used for sending locale-specific header information.

## Listing 20.1 define_lang.php—Language Definition File

```php
<?php
if ((isset($_SESSION['lang'])) || (isset($_GET['lang']))) {
    $_SESSION['lang'] = "en";
    $currLang = "en";
} else {
    $currLang = $_GET['lang'];
    $_SESSION['lang'] = $currLang;
}

switch($currLang) {
    case "en":
        define("CHARSET", "ISO-8859-1");
        define("LANGCODE", "en");
        break;
    case "ja":
        define("CHARSET", "UTF-8");
        define("LANGCODE", "ja");
        break;
    default:
        define("CHARSET", "ISO-8859-1");
        define("LANGCODE", "en");
        break;
}

header("Content-Type: text/html;charset=".CHARSET);
header("Content-Language: ".LANGCODE);
?>
```

In 20.1 you can see that if no session value exists, the English locale settings are used. If your site is a Japanese site by default, you would change this file to use the Japanese locale by default. This script is meant to be used with the next script that you will (see in 20.2), which contains an input-selection mechanism, by setting the value of $currLang to the result of this input in line 6 of 20.1.

The switch statement beginning on line 10 contains a few case statements designed to assign the appropriate values to the constant variables CHARSET and LANGCODE. Lines 27–28 actually use these variables for the first time when dynamically creating and sending the headers for Content-type and Content-language.

## Listing 20.2 lang_strings.php—String Definition File

```php
<?php
function defineStrings() {
    switch($_SESSION['lang']) {
        case "en":
            define("WELCOME_TXT", "Welcome!");
            define("CHOOSE_TXT", "Choose Language");
            break;
        case "ja":
            define("WELCOME_TXT", "ようこそ!");
            define("CHOOSE_TXT", "言語を選択");
            break;
        default:
            define("WELCOME_TXT", "Welcome!");
            define("CHOOSE_TXT", "Choose Language");
            break;
    }
}
?>
```

Within the cases of the switch statement you can see two constants defined for each language. The constants are CHARSET and LANGCODE, which correspond to the character set and language code for each locale. The display script in Listing 20.3 uses these constants to create the proper META tags for character set and language code.

Listing 20.2 creates the function that will be used in Listing 20.3 to pass localized strings to the browser. Like Listing 20.1, this code uses a switch statement to define the strings for two constants—in this instance WELCOME_TXT and CHOOSE_TXT—which will be displayed in the script shown in Listing 20.3.

The last piece of the puzzle is the display script itself, shown in Listing 20.3. This script simply starts a session so it can read the session value for the user, then fills in the blanks with the constants defined for language.

## Listing 20.3 lang_selector.php—Select and Display

```php
<?php
session_start();
include 'define_lang.php';
include 'lang_strings.php';
defineStrings();
?>
<!DOCTYPE html>
<html lang="<?php echo LANGCODE; ?>">
<meta charset="<?php echo CHARSET; ?>" />
<title><?php echo WELCOME_TXT; ?></title>
<body>
  <h1><?php echo WELCOME_TXT; ?></h1>
  <h2><?php echo CHOOSE_TXT; ?></h2>
  <ul>
    <li><a href="<?php echo $_SERVER['PHP_SELF']; ?>?lang=en">English</a></li>
    <li><a href="<?php echo $_SERVER['PHP_SELF']; ?>?lang=ja">Japanese</a></li>
  </ul>
</body>
</html>
```
