
So to match a digit character anywhere in the target string you could use either of the following two expressions:

```
/[0-9]/
```

/\d/

Incidentally, you can also use a shorthand character class within a longhand class. The following expression matches the letter "e" or "p", or any digit, in the target string:

```
/[ep\d]/
```

Here are some examples:

```
echo preg_match( "/\d[A-Z]/", "3D" ); // Displays "1"
echo preg_match( "/\d[A-Z]/", "CD" ); // Displays "0"
echo preg_match( "/\S\S\S/", "6&c" ); // Displays "1"
echo preg_match( "/\S\S\S/", "6 c" ); // Displays "0"
```

To match any character at all, use a dot (.):

```
echo preg_match( "/He.../", "Hello" ); // Displays "1"
```

## Matching Multiple Characters

If you want to match the same character (or character class) multiple times in a row, you can use _quantifiers_. A quantifier is placed after the character or character class, and indicates how many times that character or class should repeat in the target string. The quantifiers are:

| Quantifier | Meaning |
| :--- | :--- |
| * | Can occur zero or more times |
| + | Can occur one or more times |
| ? | Can occur exactly once, or not at all |
| {n} | Must occur exactly _n_ times |
| {n,} | Must occur at least _n_ times |
| {n,m} | Must occur at least _n_ times but no more than _m_ times |

For example, you can match a string of at least one digit with:

```
/\d+/
```

Say you wanted to search a string for a date in the format mm/dd/yy or mmm/dd/yyyy (for example, jul/15/06 or jul/15/2006). That's three lowercase letters, followed by slash, followed by one or two digits, followed by a slash, followed by between two and four digits. This regular expression will do the job:

```
echo preg_match( "/[a-z]{3}\d{1,2}\d{2,4}/", "jul/15/2006" ); // Displays "1"
```

(This expression isn't perfect — for example, it will also match three-digit "years," but you get the idea.)

## Greedy and Non-Greedy Matching

When you use quantifiers to match multiple characters, the quantifiers are greedy by default. This means that they will try to match the largest number of characters possible. Consider the following code:

```
preg_match( "/P.*r/", "Peter Piper", $matches ); echo $matches[0]; // Displays "Peter Piper"
```

The regular expression reads, "Match the letter 'P' followed by zero or more characters of any type, followed by the letter 'r'." Because quantifiers are, by nature, greedy, the regular expression engine matches as many characters as it can between the first "P" and the last "r" — in other words, it matches the entire string.

You can change a quantifier to be non-greedy. This causes it to match the smallest number of characters possible. To make a quantifier non-greedy, place a question mark (?) after the quantifier. For example, to match the smallest possible number of digits use:

```
/\d+?/
```

Rewriting the Peter Piper example using a non-greedy quantifier gives the following result:

```
preg_match( "/P.*?r/", "Peter Piper", $matches ); echo $matches[0]; // Displays "Peter"
```

Here, the expression matches the first letter "P" followed by the smallest number of characters possible ("ete"), followed by the first letter "r".

## Using Subpatterns to Group Patterns

By placing a portion of your regular expression's rules in parentheses, you can group those rules into a subpattern. A major benefit of doing this is that you can use quantifiers (such as * and ?) to match the whole subpattern a certain number of times. For example:

```
// Displays '1' echo preg_match( "/(row, ?)+your boat/", "row, row, row your boat" );
```

The subpattern in this regular expression is "(row, ?) ". It means: "The letters 'r', 'o', and 'w', followed by either zero or one comma, followed by a space character." This subpattern is then matched at least one time thanks to the following + quantifier, resulting in the "row, row, row" portion of the target string being matched. Finally the remaining characters in the pattern match the "your boat" part of the string. The end result is that the entire string is matched.

A side-effect of using subpatterns is that you can retrieve the individual subpattern matches in the matches array passed to preg_match(). The first element of the array contains the entire matched text as usual, and each subsequent element contains any matched subpatterns:

```
preg_match( "/(\d+)\/(\d+)\/(\d+) (\d+):(\d+.)/", "7/18/2004 9:34AM", $matches );
echo $matches[0] . "<br />"; // Displays "7/18/2004 9:34AM"
echo $matches[1] . "<br />"; // Displays "7/18/2004"
echo $matches[2] . "<br />"; // Displays "9:34AM"
```

## Referring to Previous Subpattern Matches

You can take the text that matched a subpattern and use it elsewhere in the expression. This is known as a backreference. Backreferences allow you to create quite powerful, adaptable regular expressions.

To include a subpattern's matched text later in the expression, write a backslash followed by the subpattern number. For example, you'd include the first subpattern's matched text by writing \1, and the next subpattern's matched text by writing \2.

Consider the following example:

```
$myPets = "favoritePet=Lucky, Rover=dog, Lucky=cat";
preg_match( '/favoritePet=(\w+).*\\1=(\w+)/', $myPets, $matches );

// Displays "My favorite pet is a cat called Lucky."
echo "My favorite pet is a " . $matches[2] . " called " . $matches[1] . ".";
```

This code contains a string describing someone's pets. From the string you know that their favorite pet is Lucky, and that they have two pets: a dog called Rover and a cat called Lucky. By using a regular expression with a backreference, the code can deduce that their favorite pet is a cat.

Here's how the expression works. It first looks for the string "favoritePet=" followed by one or more word characters ("Lucky" in this case):

```
/favoritePet\=(\w+)/
```

Next the expression looks for zero or more characters of any type, followed by the string that the first subpattern matched ("Lucky"), followed by an equals sign, followed by one or more word characters ("cat" in this example):

```
.*\\1=(\w+)
```

Finally, the code displays the results of both subpattern matches ("Lucky" and "cat") in a message to the user.

By the way, notice that the expression string was surrounded by single quotes in this example, rather than the usual double quotes. If the code had used double quotes, an extra backslash would have been needed before the \1 (because PHP assumes \1 to be the ASCII character with character code 1 when inside a double-quoted string):

```
preg_match( "/favoritePet\=(\w+).*\1=(\w+)/", $myPets, $matches );
```

Character escaping issues like this have been known to trip up many a seasoned programmer, so this is something to watch out for:

## Matching Alternative Patterns

Regular expressions let you combine patterns (and subpatterns) with the | (vertical bar) character to create alternatives. This is a bit like using the | (or) operator; if any of the patterns combined with the | character match, the overall pattern matches.

The following pattern matches if the target string contains any one of the abbreviated days of the week (mon–sun):

```
$day = "wed";
echo preg_match( "/mon|tue|wed|thu|fri|sat|sun/", $day ); // Displays "1"
```

You can also use alternatives within subpatterns, which is very handy. Here's the earlier "date detection" example, rewritten to be more precise:

```
echo preg_match( "/(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)" .
    "\d{1,2})\d{2,4})/", "jul/15/2006" ); // Displays "1"
```

## Using Anchors to Match at Specified Positions

Often you're interested in the *position* of a pattern within a target string, as much as the pattern itself. For example, say you wanted to make sure that a string started with one or more digits followed by a colon. You might try this:

```
echo preg_match( "/\d+:/", "12: The String" ); // Displays "1"
```

However, this expression would also match a string where the digits and colon are somewhere in the middle:

```
echo preg_match( "/\d+:/", "Die Hard 2: Die Harder" ); // Displays "1"
```

How can you make sure that the string only matches if the digits and colon are at the start? The answer is that you can use an *anchor* (also known as an *assertion*), as follows:
