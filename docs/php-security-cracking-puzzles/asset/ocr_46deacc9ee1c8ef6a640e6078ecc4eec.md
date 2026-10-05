# Chapter II.2: Regular Expressions 125

# II.2.4. Converting MySQL Date Format into Calendar Format

The date format can be converted to the calendar format using the script shown in Listing II.2.5.

Listing II.2.5. Converting from the YYYY-MM-DD format to the DD.MM.YYYY format

The search results produced by the preg_match() function can be saved in an array specified by the optional third parameter. The 0 array element will hold the match to the entire regular expression; the first array element will hold the match to the regular expression in the first set of parentheses (the year); the second array element will hold the match to the regular expression in the second set of parentheses (the month); and the third array element will hold the match to the regular expression in the third set of parentheses (the day).

# II.2.5. Verifying the Email Address Format

Assume the format of the address should be something@server.com. Moreover, the address consists of two parts delimited by the @ character; these are the user name and the domain name. The user name can contain uppercase and lowercase letters, digits, underscores, periods, and hyphens. To check the separator between the user name and the domain name, the @ character must be added to the regular expression. Like the user name, the domain name can use uppercase and lowercase letters, digits, underscores, periods, and hyphens. Consequently, the following regular expression for verifying that the user name and the domain name of an email address are in the appropriate format can be constructed:

```
[0-9a-z_]+@[0-9a-z_^\.]+
```