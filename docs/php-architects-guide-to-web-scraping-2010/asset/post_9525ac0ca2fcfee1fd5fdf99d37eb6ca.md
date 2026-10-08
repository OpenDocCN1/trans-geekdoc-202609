
It's possible to check for multiple expressions simultaneously in a single pattern, also called **alternation**, using the pipe meta-character `|`.

```php
<?php
// Matches 'foo' or 'bar' or 'baz' anywhere
$matches = (preg_match('/foo|bar|baz/', $string) == 1);
?>
```

Note that the `^` and `$` are not implicitly applied to all expressions in an alternation; they must be used explicitly for each expression.

```php
<?php
// $result == 1
$result = preg_match('/^foo|bar/', 'abar');

// $result == 0
$result = preg_match('/^foo|^bar/', 'abar');
?>
```

The first example returns 1 because `abar` contains `bar`, since `^` is not applied to that expression in the pattern. The second example does apply `^` to `bar` and, since `abar` begins with neither `foo` nor `bar`, it returns 0.

Part of a pattern may or may not be present, or may be repeated a number of times. This is referred to as **repetition** and involves using meta-characters collectively referred to as **quantifiers**.

```php
<?php
// Matches 'a' 0 times or 1 time if present
$matches = (preg_match('/a?/', $string) == 1);

// Matches 'a' 0 or more times, however many that may be
$matches = (preg_match('/a*/', $string) == 1);

// Matches 'a' 1 or more times, however many that may be
$matches = (preg_match('/a+/', $string) == 1);

// Matches 'a' 0 times or 1 time if present, same as ?
$matches = (preg_match('/a{0,1}/', $string) == 1);

// Matches 'a' 0 or more times, same as *
$matches = (preg_match('/a{0,}/', $string) == 1);

// Matches 'a' 1 or more times, same as +
$matches = (preg_match('/a{1,}/', $string) == 1);

// Matches 'a' exactly 2 times
$matches = (preg_match('/a{2}/', $string) == 1);
?>
```

Note that any use of curly brackets that is not of the form {X}, {X,}, or {X,Y} will be treated as a literal string within the pattern.

### Subpatterns

You’ll notice in the examples from the previous section that only a single character was used. This is because the concept of **subpatterns** hadn’t been introduced yet. To understand these, it’s best to look at an example that doesn’t use them in order to understand the effect they have on how the pattern matches.

```php
<?php
// Matches 'a' followed by one or more instances of 'b'
$matches = (preg_match('/ab+/', $string) == 1);
?>
```

Without subpatterns there would be no way to match, for example, one or more instances of the string 'ab'. Subpatterns solve this by allowing individual parts of a pattern to be grouped using parentheses.

```php
<?php
// Matches 'ab' one or more times
$matches = (preg_match('/(ab)+/', $string) == 1);

// Matches 'foo' or 'foobar'
$matches = (preg_match('/foo(bar)?/', $string) == 1);

// Matches 'ab' or 'ac'
$matches = (preg_match('/a(b|c)/', $string) == 1);

// Matches 'ab', 'ac', 'abb', 'abc', 'acb', 'acc', etc.
$matches = (preg_match('/a(b|c)+/', $string) == 1);
```

## Matching

Subpatterns do a bit more than let you define parts of a pattern to which alternation or repetition apply. When a match is found, it's possible to obtain not only the substring from the original string that matched the entire pattern, but also substrings that were matched by subpatterns.

```php
<?php
if (preg_match('/foo(bar)?(baz)?/', $string, $match) == 1) {
    print_r($match);
}
?>
```

The third parameter to `preg_match()`, `$match`, will be set to an array of match data if a match is found. That array will contain at least one element: the entire substring that matched the pattern. Any elements that follow will be subpattern matches with an index matching that subpattern's position within the pattern. That is, the first subpattern will have the index 1, the second subpattern will have the index 2, and so on.

If a pattern is conditional (i.e. uses `?`) and not present, it will either have an empty element value in the array or no array element at all.

```php
<?php
if (preg_match('/foo(bar)?/', 'foo', $match) == 1) {
    // $match == array('foo');
}
```

- In the first example, the `(bar)?` subpattern ends the entire pattern and is not matched. Thus, it has no entry in `$match`.
- In the second example, the `(bar)?` subpattern does not end the entire pattern and is not matched. Thus, it has an empty entry in `$match`.

```php
<?php
if (preg_match('/foo(bar)?(baz)?/', 'foobaz', $match) == 1) {
    // $match == array('foo', '', 'baz');
}
?>
```

Subpatterns can also contain other subpatterns.

```php
<?php
if (preg_match('/foo(ba(r|z))?/', 'foobar', $match) == 1) {
    // $match == array('foobar', 'bar', 'r');
}
?>
```

Aside from passing `$match` to `print_r()` or a similar function, an easy way to tell what a subpattern's position will be in `$match` is to count the number of opening parentheses in the pattern from left to right until you reach the desired subpattern.

Using the syntax shown above, any subpattern will be captured (i.e. have its own element in the array of matches). Captured subpatterns are limited to 99 and total subpatterns, captured or not, is limited to 200. While this realistically shouldn't become an issue, it's best to denote subpatterns that do not require capture using `(?:` instead of `(` to begin them.

Additionally, since PHP 4.3.3, subpatterns may be assigned meaningful names to be used as their indices in the array of matches when they are captured. To assign a name to a subpattern, begin it with the syntax `(?P<name>` instead of `(` where `name` is the name you want to assign to that subpattern. This has the advantage of making code more expressive and easier to maintain as a result.

### Escaping

There may be instances where you want to include literal characters in patterns that are usually interpreted as meta-characters. This can be accomplished via a `\` meta-character.

```php
<?php
// Matches literal [
$matches = (preg_match('/\\[/', $string) == 1);

// Matches literal \
$matches = (preg_match('/\\\\/', $string) == 1);

// Matches expression delimiter /
$matches = (preg_match('/\\//', $string) == 1);

// Matches any of the standard escape sequences \r, \n, or \t
$matches = (preg_match('/\\r|\\n|\\t/', $string) == 1);
?>
```

Note that it is necessary to double-escape `\\` in the second example because the string `'\\'` is interpreted to be a single backslash by PHP whether or not it is used in a regular expression. In other cases, no escaping of `\` is needed for the escape sequence to be interpreted properly.

> **Double Escaping**
>
> For more information on the reasoning behind the double-escape example in this section, see `http://php.net/manual/en/language.types.string.php#language.types.string` and the Backslash section of `http://php.net/manual/en/regexp.reference.php`.

### Escape Sequences

There are three ways to match a single character that could be one of several characters.

The first way involves using the `.` meta-character, which will match any single character except a line feed (`"\n"`) without use of modifiers (which will be covered later). This can be used with repetition just like any other character.

The second way requires using special escape sequences that represent a range of characters. Aside from the escape sequences mentioned in the previous section's examples, here are some that are commonly used.

- `\d`: a digit, 0 through 9.
- `\h`: a horizontal whitespace character, such as a space or a tab.
- `\v`: a vertical whitespace character, such as a carriage return or line feed.
- `\s`: any whitespace character, the equivalent of all characters represented by `\h` and `\v`.
- `\w`: any letter or digit or an underscore.

Each of these escape sequences has a complement.

- `\D`: a non-digit character.
- `\H`: a non-horizontal whitespace character.
- `\V`: a non-vertical whitespace character.
- `\S`: a non-whitespace character.
- `\W`: a character that is not a letter, digit, or underscore.

The third and final way involves using **character ranges**, which are characters within square brackets (`[` and `]`). A character range represents a single character, but like normal single characters they can have repetition applied to them.

```php
<?php
// Matches the same as \d
$matches = (preg_match('/[0-9]/', $string) == 1);

// Matches the same as \w
$matches = (preg_match('/[a-zA-Z0-9_]/', $string) == 1);
?>
```
