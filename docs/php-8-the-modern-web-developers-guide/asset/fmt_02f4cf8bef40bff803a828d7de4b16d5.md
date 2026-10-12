
Here’s an example of how to format a currency value using `NumberFormatter`:

```php
// Create a currency formatter for the 'en_US' (U.S. English) locale
$locale = 'en_US';
$formatter = new NumberFormatter($locale, NumberFormatter::CURRENCY);

// Format a currency amount
$amount = 1234.56;
$formattedCurrency = $formatter->formatCurrency($amount, 'USD');
```

In this example, we create a currency formatter for the ‘en_US’ locale and format a currency amount of 1234.56 USD. The resulting `$formattedCurrency` variable will contain the formatted currency string, including the currency symbol.

### Customizing Currency Formatting

You can customize currency formatting by specifying options such as currency symbol style, currency code, and fraction digits:

```php
// Create a currency formatter with custom options
$locale = 'fr_FR';
$options = [
    NumberFormatter::CURRENCY_SYMBOL => '€',  // Custom currency symbol
    NumberFormatter::CURRENCY_CODE => 'EUR',  // Currency code
    NumberFormatter::FRACTION_DIGITS => 2,    // Decimal places
];

$formatter = new NumberFormatter($locale, NumberFormatter::CURRENCY, NumberFormatter::CURRENCY_PATTERN, null, null, $options);

// Format a currency amount
$amount = 1234.56;
$formattedCurrency = $formatter->formatCurrency($amount, 'EUR');
```

In this example, we create a currency formatter for the ‘fr_FR’ (French) locale with custom options. The result is a currency string formatted according to the specified preferences.

### Number Formatting

PHP’s `NumberFormatter` class is versatile and can also be used for formatting non-currency numbers. You can format integers, decimals, and percentages with ease:

```php
// Create a number formatter for the 'de_DE' (German) locale
$locale = 'de_DE';
$formatter = new NumberFormatter($locale, NumberFormatter::DECIMAL);

// Format a number
$number = 1234.567;
$formattedNumber = $formatter->format($number);
```

In this example, we create a number formatter for the ‘de_DE’ locale and format a decimal number. The result will use the German conventions for decimal and grouping separators.

### Best Practices for Currency and Number Formatting

To ensure effective currency and number formatting in your PHP 8 applications, consider the following best practices:

1.  **User Preferences**: Allow users to specify their preferred currency symbol, decimal separators, and grouping separators.
2.  **Automatic Detection**: Detect the user’s browser settings or location to automatically choose an appropriate locale and currency.
3.  **Localization**: Use locale-specific formatting for currency and numbers to create a familiar experience for users.
4.  **Testing**: Test currency and number formatting thoroughly with different locales to ensure accuracy.

By following these practices and leveraging PHP’s `NumberFormatter` class, you can create applications that present currency and numeric values in a way that aligns with the expectations of your global user base. In the next section, we’ll explore character encoding and text processing, essential for handling multilingual content in PHP 8 applications.

---

## Section 16.4: Character Encoding and Text Processing

Character encoding and text processing are fundamental aspects of internationalization (i18n) and localization (l10n) in PHP 8 applications. Handling different character sets, encoding conversions, and text manipulation is essential when dealing with multilingual content.

### Character Encoding Basics

Character encoding defines how characters are represented as binary data in computer systems. In PHP 8, the most commonly used character encoding is UTF-8, which supports a wide range of characters from different languages and scripts.

Here’s how you can set the character encoding for your PHP scripts:

```php
// Set the character encoding to UTF-8
header('Content-Type: text/html; charset=utf-8');
```

By setting the charset to UTF-8, you ensure that your PHP script can handle and display characters from various languages.

### Encoding and Decoding Text

PHP provides functions to encode and decode text between different character encodings. The `mb_convert_encoding` function is a versatile tool for encoding conversions:

```php
// Convert a string from ISO-8859-1 to UTF-8
$text = "Café";
$utf8Text = mb_convert_encoding($text, 'UTF-8', 'ISO-8859-1');
```

In this example, we convert a string from ISO-8859-1 encoding to UTF-8, a common conversion when dealing with legacy data.

### Text Length and Manipulation

When working with multilingual text, it’s important to consider the length of strings, as some characters may occupy more than one byte. The `mb_strlen` function allows you to correctly calculate the length of a multibyte string:

```php
// Calculate the length of a UTF-8 string
$text = "Café";
$length = mb_strlen($text, 'UTF-8');
```

In this case, the length will correctly be calculated as 4, accounting for the accented character.

You can also perform various text manipulation tasks, such as substring extraction and replacement, while respecting character boundaries. The `mb_substr` and `mb_str_replace` functions are helpful for these tasks.

### Sorting Multilingual Text

Sorting multilingual text can be challenging due to different collation rules for various languages. PHP 8’s `Collator` class provides a solution for locale-aware sorting:

```php
// Create a collator for the 'fr_FR' (French) locale
$collator = new Collator('fr_FR');

// Sort an array of French words
$words = ["éclair", "chocolat", "amour", "bonjour"];
$collator->sort($words);
```

In this example, we create a collator for the French locale and use it to sort an array of French words, respecting the correct collation order.

### Handling Multilingual Input

When processing user input, especially through forms, be aware of character encoding issues. Ensure that user input is consistently converted to the desired character encoding (typically UTF-8) before any further processing or storage.

In conclusion, character encoding and text processing are essential for building PHP 8 applications that support multiple languages and character sets. By understanding encoding, using appropriate functions, and considering character boundaries, you can create robust and user-friendly multilingual applications. Next, we’ll explore best practices for creating global PHP 8 applications.

---

## Section 16.5: Best Practices for Global PHP 8 Applications

Building global PHP 8 applications that cater to an international audience requires adherence to best practices in internationalization (i18n) and localization (l10n). These practices ensure that your software can handle various languages, regions, and cultural preferences effectively.

### 1. Use UTF-8 Everywhere

Consistently use UTF-8 character encoding throughout your PHP 8 application. UTF-8 is a versatile encoding that supports a wide range of characters from different languages and scripts. Ensure that your database, file handling, and text processing all work with UTF-8.

### 2. Separate Content from Code

Avoid hardcoding text directly into your PHP scripts. Instead, externalize content such as labels, messages, and user interface elements into separate resource files. PHP’s `gettext` extension is a popular choice for handling message catalogs and translations.

### 3. Properly Identify User’s Locale

Detect the user’s preferred locale, language, and region settings. You can use the `Accept-Language` header sent by the user’s browser or provide an option for users to choose their preferred language. The locale functions in PHP help you set the correct locale for user interactions.

### 4. Use Language Constants

Define constants for different languages and regions to ensure consistency in your application. These constants can represent keys in your resource files and make it easier to switch between languages dynamically.

```php
define('LANG_EN_US', 'en_US');
define('LANG_FR_FR', 'fr_FR');
```

### 5. Employ Pluralization Rules
