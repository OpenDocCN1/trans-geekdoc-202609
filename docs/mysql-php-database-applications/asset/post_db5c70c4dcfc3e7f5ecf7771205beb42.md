
## TABLE F-12 HTML-RELATED FUNCTIONS (Continued)

| Function | Return Value | Action |
|---|---|---|
| get_html_translation_table([int table [, int quote_style]]) | array | Returns the internal translation table used by htmlspecialchars and htmlentities |

## TABLE F-13 PHP-INFORMATION FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| phpinfo([int what]) | void | Outputs a page of useful information about PHP and the current request |
| phpversion([string extension]) | string | Returns the current PHP version |
| phpcredits([int flag]) | void | Prints the list of people who've contributed to the PHP project |
| php_sapi_name(void) | string | Returns the current SAPI module name |
| php_uname(void) | string | Returns information about the system PHP was built on |

## TABLE F-14 MATH FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| abs(int number) | int | Returns the absolute value of the number |
| ceil(float number) | float | Returns the next highest integer value from the number |
| floor(float number) | float | Returns the next lowest integer value from the number |
| round(float number [, int precision]) | float | Returns the number rounded to the specified precision |
| sin(float number) | float | Returns the sine of the number in radians |
| cos(float number) | float | Returns the cosine of the number in radians |
| tan(float number) | float | Returns the tangent of the number in radians |
| asin(float number) | float | Returns the arc sine of the number in radians |
| acos(float number) | float | Returns the arc cosine of the number in radians |
| atan(float number) | float | Returns the arc tangent of the number in radians |
| atan2(float y, float x) | float | Returns the arc tangent of y/x, with the resulting quadrant determined by the sines of y and x |
| sinh(float number) | float | Returns the hyperbolic sine of the number, defined as (exp(number) - exp(-number))/2 |
| cosh(float number) | float | Returns the hyperbolic cosine of the number, defined as (exp(number) + exp(-number))/2 |
| tanh(float number) | float | Returns the hyperbolic tangent of the number, defined as sinh(number)/cosh(number) |
| asinh(float number) | float | Returns the inverse hyperbolic sine of the number, that is, the value whose hyperbolic sine is number |
| acosh(float number) | float | Returns the inverse hyperbolic cosine of the number, that is, the value whose hyperbolic cosine is number |
| atanh(float number) | float | Returns the inverse hyperbolic tangent of the number, that is, the value whose hyperbolic tangent is number |
| pi(void) | float | Returns an approximation of pi |
| is_finite(float val) | bool | Returns whether argument is finite |
| is_infinite(float val) | bool | Returns whether argument is infinite |
| is_nan(float val) | bool | Returns whether argument is not a number |
| pow(number base, number exponent) | number | Returns base raised to the power of exponent; returns the integer result when possible |
| exp(float number) | float | Returns e raised to the power of number |
| expm1(float number) | float | Returns exp(number) – 1, computed in a way that is accurate even when the value of number is close to 0 |
| log1p(float number) | float | Returns log(1 + number), computed in a way that is accurate even when the value of number is close to 0 |
| log(float number) | float | Returns the natural logarithm of the number |
| log10(float number) | float | Returns the base-10 logarithm of the number |
| sqrt(float number) | float | Returns the square root of the number |
| deg2rad(float number) | float | Converts the number in degrees to the radian equivalent |
| rad2deg(float number) | float | Converts the radian number to the equivalent number in degrees |
| bindec(string binary_number) | int | Returns the decimal equivalent of the binary number |
| hexdec(string hexadecimal_number) | int | Returns the decimal equivalent of the hexadecimal number |
| octdec(string octal_number) | int | Returns the decimal equivalent of an octal string |
| decbin(int decimal_number) | string | Returns a string containing a binary representation of the number |
| decoct(int decimal_number) | string | Returns a string containing an octal representation of the given number |
| dechex(int decimal_number) | string | Returns a string containing a hexadecimal representation of the given number |
| base_convert(string number, int frombase, int tobase) | string | Converts a number in a string from any base smaller than or equal to 36 to any base smaller than or equal to 36 |
| _format(float number [, int num_decimal_places [, string dec_seperator, string thousands_separator]]) | string | Formats a number with grouped thousands |
| fmod(float x, float y) | float | Returns the remainder of dividing x by y as a float |
| srand([int seed]) | void | Seeds the random-number generator |
| mt_srand([int seed]) | void | Seeds the Mersenne Twister random-number generator |
| rand([int min, int max]) | int | Returns a random number |
| mt_rand([int min, int max]) | int | Returns a random number from the Mersenne Twister |
| getrandmax(void) | int | Returns the maximum value a random number can have |
| mt_getrandmax(void) | int | Returns the maximum value a random number from the Mersenne Twister can have |

## TABLE F-16 REGULAR EXPRESSION FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| ereg(string pattern, string string [, array registers]) | int | Regular expression match |
| eregi(string pattern, string string [, array registers]) | int | Case-insensitive regular expression match |
| ereg_replace(string pattern, string replacement, string string) | string | Replaces a regular expression |
| eregi_replace(string pattern, string replacement, string string) | string | Case-insensitive replace regular expression |
| split(string pattern, string string [, int limit]) | array | Splits the string into an array by regular expression |
| spliti(string pattern, string string [, int limit]) | array | Splits the string into an array by regular expression (case-insensitive) |
| sql_regcase(string string) | string | Makes a regular expression for case-insensitive match |

## TABLE F-17 PERL-COMPATIBLE REGULAR EXPRESSION FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| preg_match(string pattern, string subject [, array subpatterns]) | int | Performs a Perl-style regular-expression match |
| preg_match_all(string pattern, string subject, array subpatterns [, int order]) | int | Performs a Perl-style global-regular-expression match |
| preg_replace(mixed regex, mixed replace, mixed subject [, int limit]) | string | Performs a Perl-style regular-expression replacement |
| preg_replace(mixed regex, mixed callback, mixed subject [, int limit]) | string | Performs a Perl-style regular-expression replacement using replacement callback |
| preg_split(string pattern, string subject [, int limit [, int flags]]) | array | Splits the string into an array using a Perl-style regular expression as a delimiter |
| preg_quote(string str, string delim_char) | string | Quotes regular-expression characters plus an optional character |
| preg_grep(string regex, array input) | array | Searches the array and returns entries that match regex |

## TABLE F-18 VARIABLE-TYPING FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| gettype(mixed var) | string | Returns the type of the variable |
| settype(mixed var, string type) | bool | Sets the type of the variable |
| intval(mixed var [, int base]) | int | Gets the integer value of a variable using the optional base for the conversion |
| floatval(mixed var) | float | Gets the float value of a variable |
| strval(mixed var) | string | Gets the string value of a variable |
| is_null(mixed var) | bool | Returns true if the variable is NULL |
