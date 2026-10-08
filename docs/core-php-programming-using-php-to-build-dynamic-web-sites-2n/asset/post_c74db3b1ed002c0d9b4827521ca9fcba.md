
# Core PHP Programming

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_550_0.png)

```php
<?php
/*
 ** SessionID
 ** generates a session id
 */
function getSessionID($length=16)
{
    // Set pool of possible characters
    $Pool = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    $Pool .= "abcdefghijklmnopqrstuvwxyz";
    $lastChar = strlen($Pool) - 1;

    for($i = 0; $i < $length; $i++)
    {
        $sid .= $Pool[mt_rand(0, $lastChar)];
    }
    return($sid);
}

// Seed the generator
mt_rand(100000000 * (double)microtime());

if($sid != "")
{
    print("Old Session ID was $sid<BR>\n");
}

$sid = getSessionID();

print("< HREF=\"PHP_SELF?id=$sid\">");
print("Get Another Session ID");
print("</A>\n");
?>
?>

IT-SC book 550

# Listing 15.12 Random Banner Ad

```php
<?php
//Seed the generator
mt_srand(doubleval(microtime()) * 1000000000);

//choose banner
switch(mt_rand(1
```

# Chapter 16. PARSING AND STRING EVALUATION

## Tokenizing

Regular Expressions

Defining Regular Expressions

Using Regular Expressions in PHP Scripts

Parsing is the act of breaking a whole into components, usually a sentence into words. PHP must parse the code you write as a first step in turning a script into an HTML document. There will come a time when you are faced with extracting or verifying data collected in a string. This could be as simple as a tab-delimited list. It could be as complicated as the string, breaking a browser uses to identify itself to a Web server. You may choose to tokenize the string, breaking it into pieces. Or you may choose to apply a regular expression. This chapter examines PHP's functions for parsing and string evaluation.

## Tokenizing

PHP allows for a simple model for tokenizing string. Certain characters, of your choice, are considered separators. Strings of characters between separators are considered tokens. You may change the set of separators with each token you pull from a string, which is handy for irregular strings—that is, ones that are not simply comma-separated lists.

Listing 16.1 accepts a sentence and breaks it into words using the strtok function, described in Chapter 9, "Data Functions." As far as the script is concerned, a word is surrounded by a space, punctuation, or either end of the sentence. Single and double quotes are left as part of the word.

Listing 16.1 Tokenizing a String

# Core PHP Programming

### Listing 16.1 - Microsoft Internet Explorer

| File | Edit | View | Fgrounds | Tools | Help |
|---|---|---|---|---|---|
| Submitted text: When in the Course of human events, it becomes necessary for one to dissolve the political bands which have connected them with another, and to assume the powers of the earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle them, a decent respect to the opinions of mankind requires that they should declare the causes which impel them to the separation. | | | | | |

### 71 Words Found

- the (9)
- of (5)
- to (5)
- and (3)
- them (3)

* Done

```php
<?php
/*
 * If submitted a sentence, parse it */
if (isset($sentence)) {
    print("<B>Submitted text:</B>");
    print("$sentence<BR><BR>\n");
}

// add end marker
$sentence .= "<END>";

// set characters that separate tokens
$separators = " .,!?";

// get each token
for ($token = strtok($sentence, $separators); $token != "<END>"; $token = strtok($separators)) {
    // skip empty tokens
    if ($token != "") {
        // count each word
        $word_count[strtolower($token)]++;
    }
}
// first sort by word
ksort($word_count);
// next sort by frequency
arsort($word_count);

print("<B>total Words Found</B>\n");
print("<ul>");
foreach ($word_count as $key => $value) {
    print("<li>$key ($value)</li>");
}
print("</ul>");
?>
```

# Core PHP Programming

Notice the addition of `<END>` to the variable. This special token allows the algorithm to detect the end of input. When strtok encounters the end of input, it returns FALSE, so your first inclination might be to test for FALSE in for loop. If two separators follow each other, strtok will return an empty string, as you'd expect. Since we don't want to stop tokenizing, we place a token at the end that we know not about in the input. In the string, we could strip it out first, but this is beyond the scope of this text and isn't something that will be typed by accident. Since there's no risk to tokenizing too soon, I prefer to let it get invalid results. The strtok function is useful only in simple situations. An example might be reading a tab-delimited file, filling each token from the line using a tab character, continuing by getting the next line

# Regular Expressions

Fortunately, PHP offers something more powerful than strtok: regular expressions. Written in a language of their own, regular expressions describe patterns that are compared to strings. PHP source code includes an implementation of regular expressions that conform to POSIX standard. This allows for expressions of an older style but carries modern advantages over PHP native expressions. They make it easier to copy an expression. An excellent resource for learning more about regular expressions is the official documentation <http://www.perl.com/CPAN/doc/manual/perl.html>. You will need to read the differences between Perl and the PHP implementation <http://www.php.net/manual/pcre.php>.

# Defining Regular Expressions

At the highest level, a regular expression is one or more branches separated by the vertical bar (|). This character is considered to have the properties of logical OR. Any of the branches could match with an evaluated string. Table 16-1 provides a few examples. Each branch contains one or more atoms. These atoms may be followed by characters that modify the number of times the atom may be matched. Table 16-2. An asterisk (*) means the atom can match any number of times. A plus (+) means the atom must match at least once. A question mark (?) signifies the atom may match once or not at all.

Alternatively, the atom may be bounded, which means it is followed by curly braces, {}, and if the braces contain a single number, the atom must be matched exactly that number of times. If the braces contain a number followed by a comma, the atom must be matched that number of times or more. If the braces contain two numbers separated by a comma, the atom must match at least the first number of times, but not more than the second.

An atom is a series of characters, having special meaning, others simply standing for a character that may match. A period (.) matches any character. A dollar sign ($) matches the end of the string. If you need to match one of the special characters (^ [ ] | *?), put a backslash in front of it. Any character preceded by a backslash will be treated literally, even if it has no special meaning. Any character with no special meaning will be considered just a character to be matched, backslash or not. You may also group atoms with parentheses so they are treated as an atom.

## Table 16-1. Branches in a Regular Expression

| Sample | Description |
|---|---|
| apple | Matches the word apple. |
| apple|ball | Matches either apple or ball. |
| begin|end|break | Matches either begin, end, or break. |

## Table 16-2. Repeating of Patterns in Regular Expressions

| Sample | Description |
|---|---|
| a(b*) | Matches a, ab, abb, ... — an a plus any number of b's. |
| a(b+) | Matches ab, abb, abbb, ... — an a plus one or more b's. |
| a(b?) | Matches either a or ab — an possibly followed by a b. |
| a(b3) | Matches only abbb. |
| a(b,2) | Matches abb, abbb, abbbb, ... — an a followed by two or more b's. |
| a(b,4) | Matches abb, abbb, abbbb, abbb — an a followed by two to four b's. |
