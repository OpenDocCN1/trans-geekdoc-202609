# Creating a Bulletin Board System

The last pattern deserves a bit of explanation, as it introduces a couple of new concepts. The parentheses are there so we can use what we call back references. Note the $1 in the replacement pattern. This tells the function “Take whatever you found in the first set of parentheses and put it here.” If we had a more complex pattern with a second set of parentheses, we would refer to the data matched within those using $2.

Within those parentheses, we are matching any character at except a left square bracket. [^ tells the expression to match from 1 to any number of characters. If you wanted the expression to match 0 or more, use instead of -.

The ? can be confusing, especially for those not familiar with regular expressions. Because it is immediately preceded by a quantifier (+), it does not mean 0 characters or 1 character as it usually does. In this case, it is telling the regex not to be greedy

Imagine the following text:

Hello, [b]George[/b], how are [b]you[/b] doing today?

If we ran the regex %[b]\[[+]+\]\[/b]$i against that text (the lack of?), the regex would be “greedy” and match the maximum size it could find. The result is that the preceding text would look like so:

Hello, <b>George</b>, how are <b>you</b> doing today?

This isn't good in this particular case because we are trying to style “George” and “you” in boldface. We use the ? in our pattern after the + to tell the regex pattern to ungreedy, so that it finds the smallest matches. By in the ?, the result would be

Hello, <b>George</b>, how are <b>you</b> doing today?

which of course is the intended result.

We know regular expressions can be a bit confusing. Take the time to learn them, though. If you understand them, they can be your biggest ally. You will be surprised at the sort of patterns you can match with regex.

For more information on regular expressions, visit the following pages in the PHP manual:

+   - http://www.php.net/manual/en/ref.pcre.php
- http://www.php.net/manual/en/pcre.pattern.modifiers.php
- http://www.php.net/manual/en/pcre.pattern.syntax.php

# Searching

A bulletin board would not be much less unless you had the ability to search for old posts. Any visit board you might be familiar with, and most likely you will find a search function there.

There are many types of searches. The simplest requires that you enter text into an input field, and when you hit the Search button, it looks for any of the text you entered. That is the search we created for this application.