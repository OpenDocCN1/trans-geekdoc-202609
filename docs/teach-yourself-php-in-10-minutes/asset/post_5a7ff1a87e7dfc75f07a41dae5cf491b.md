
The dot or period ( . ) character in a regular expression is a wildcard it matches any character at all. For example, the following condition matches any four-letter word that contains a double o :

```
if ( ereg("^oo.$", $word) ) ...
```

The ^ and $ characters indicate the start and end of the string, and each dot can be any character. This expression would match the words book and tool, but not buck or stool.

**Wildcards** A regular expression that simply contains a dot matches any string that contains at least one character. You must use the ^ and $ characters to indicate length limits on the expression.

## Repeating Patterns

You have now seen how to test for a particular character or for a set or class of characters within a string, as well as how to use the wildcard character to define a wide range of patterns in a regular expression. Along with these, you can use another set of characters to indicate where a pattern can or must be repeated a number of times within a string.

You can use an asterisk ( * ) to indicate that the preceding item can appear zero or more times in the string, and you can use a plus ( + ) symbol to ensure that the item appears at least once.

The following examples, which use the * and + characters, are very similar to one another. They both match a string of any length that contains only alphanumeric characters. However, the first condition also matches an empty string because the asterisk denotes zero or more occurrences of [[:alnum:]]:

```
if ( ereg("^[[:alnum:]]*$", $phrase) ) ...
```

```
if ( ereg("^[[:alnum:]]+$", $phrase) ) ...
```

To denote a group of matching characters that should repeat, you use parentheses around them. For example, the following condition matches a string of any even length that contains alternating letters and numbers:

```
if ( ereg("^([[:alpha:]][[:digit:]])+$", $string) ) ...
```

This example uses the plus symbol to indicate that the letter/number sequence could repeat one or more times. To specify a fixed number of times to repeat, the number can be given in braces.

A single number or a comma-separated range can be given, as in the following example:

```
if (ereg("^([[:alpha:]][[:digit:]]){2,3}$", $string)) ...
```

This expression would match four or six character strings that contain alternating letters and numbers. However, a single letter and number or a longer combination would not match.

The question mark ( ? ) character indicates that the preceding item may appear either once or not at all. The same behavior could be achieved by using {0,1} to specify the number of times to repeat a pattern.

## Some Practical Examples

You use regex mostly to validate user input in scripts, to make sure that a value entered is acceptable. The following are some practical examples of using regular expressions.

## Zip Codes

If you have a customer's zip code stored in $zip, you might want to check that it has a valid format. A U.S. zip code always consists of five numeric digits, and it can optionally be followed by a hyphen and four more digits. The following condition validates a zip code in this format:

```
if (ereg("^[[:digit:]]{5}(-[[:digit:]]{4})?$", $zip)) ...
```

The first part of this regular expression ensures that $zip begins with five numeric digits. The second part is in parentheses and followed by a question mark, indicating that this part is optional. The second part is defined as a hyphen character followed by four digits.

Regardless of whether the second part appears, the $ symbol indicates the end of the string, so there can be no other characters other than those allowed by the expression if this condition is to be satisfied. Therefore, this condition matches a zip code that looks like either 90210 or 90210-1234.

## Telephone Numbers

You might want to enforce the format of a telephone number to ensure that it looks like (555)555-5555. There are no optional parts to this format. However, because the parentheses characters have a special meaning for regex, they have to be escaped with a backslash.

The following condition validates a telephone number in this format:

```
if (ereg("^\([[:digit:]]{3}\)[[:digit:]]{3}-[[:digit:]]{4}$",
$telephone)) ...
```

## Email Addresses

You need to consider many variables when validating an email address. At the very simplest level, an email address for a .com domain name looks like somename@somedomain.com.

However, there are many variations, including top-level domain names that are two characters, such as .ca, or four characters, such as .info.

Some country-specific domains have a two-part extension, such as .co.uk or .com.au.

As you can see, a regular expression rule to validate an email address needs to be quite forgiving. However, by making some general assumptions about the format of an email address, you can still create a rule that rejects many badly formed addresses.

There are two main parts to an email address, and they are separated by an @ symbol. The characters that can appear to the left of the @ symbol usually the recipient's mailbox name can be alphanumeric and can contain certain symbols.

Let's assume that the mailbox part of an email address can consist of any characters except for the @ symbol itself and can be any length. Rather than try to list all the acceptable characters you can think of, for instance, should you allow an apostrophe in an email address? It is usually good enough to enforce that email address can contain only one @ character and that anything up to that character is a valid mailbox name.

For the regex rule, you can define that the domain part of an email address consists of two or more parts, separated by dots. You can also assume that the last part may only be between two and four characters in length, which is sufficient for all top-level domain names currently in use.

The set of characters that can be used in parts of the domain is more restrictive than the mailbox name; only lowercase alphanumeric characters and a hyphen can be used.

Taking these assumptions into consideration, you can come up with the following condition to test the validity of an email address:

```
if (ereg("^[^@]+@([a-z0-9-]+\.)+[a-z]{2,4}$", $email)) ...
```

This regular expression breaks down as follows: any number of characters followed by an @ symbol, followed by one or more parts consisting of only lowercase letters, numbers, or a hyphen. Each of those parts ends with a dot, and the final part must be between two and four letters in length.

**How Far to Go** This expression could be even further refined. For instance, a domain name cannot begin with a hyphen and has a maximum length of 63 characters. However, for the purpose of catching mistyped email addresses, this expression is more than sufficient.

## Breaking a String into Components

You have used parentheses to group together parts of a regular expression to indicate a repeating pattern. You can also use parentheses to indicate subparts of an expression, and ereg allows you to break a pattern into components based on the parentheses.

When an optional third argument is passed to ereg, that variable is assigned an array of values that correspond to the parts of the pattern identified by the parentheses in the regular expression.

Let's use the email address regular expression as an example. The following code includes three sets of parentheses to isolate the mailbox name, domain name (apart from the extension), and domain extension:

```
$email = "chris@lightwood.net";
if (ereg("^([^@]+)@([a-z\-]+\.)+([a-z]{2,4}$)",
    $email, $match)) {
    echo "Mailbox: " . $match[1] . "<br>";
    echo "Domain name: " . $match[2] . "<br>";
    echo "Domain type: " . $match[3] . "<br>";
}
else {
    echo "Email address is invalid";
}
```

If you run this script in a web browser, you get output similar to the following:

```
Mailbox: chris
Domain name: lightwood.
Domain type: net
```

Note that the first key of $match refers to the first pattern found. The array keys are numbered from zero, as usual; however, $match[0] contains the entire matched pattern.

## Searching and Replacing

You can use regular expressions to perform search and replace operations on a string with the ereg_replace function. Its three arguments are a regex search pattern, the replacement string, and the string to replace into. The modified string is returned.

**str_replace** If you want to perform a simple string replace operation that does not require a regular expression, you can use `str_replace` instead of `ereg_replace` . `str_replace` is more efficient because PHP does not even have to consider that you might be looking for a regular expression.
