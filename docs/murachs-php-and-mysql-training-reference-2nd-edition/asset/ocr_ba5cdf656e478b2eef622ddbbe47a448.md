# # How to create complex patterns

The techniques you’ve learned so far allow you to write some interesting regular expressions. When you add positional indicators and subpattern repetition as shown in figure 15-4, you can create complex patterns that can be used to validate almost any type of form data.

The first table describes the position indicator characters. Of these characters, the caret and dollar sign are commonly used to validate form data. When you use the two together together, you can indicate a pattern that the entire string must match.

The second table describes how to group part of a pattern into a subpattern. Here, the parentheses are used to create a numbered subpattern. You can then match the same pattern again later in the string using the \n sequence. You can also create an unnumbered subpattern by following the opening parenthesis with the ?: sequence.

In the examples, the first pattern matches the name Rob or Bob at the start of the string. The \b makes sure that the last letter of the name is the end of the name.

The second pattern matches three word characters at the start of the string followed by a space and the same three characters again. When the subpattern in parentheses is matched (to “Rob” in this example), the \1 sequence now stands for those three exact characters, not just the general pattern of three characters. As a result, this pattern will also match the string “Bob Bobbins” but not “Bob Robertson”.

The third table describes how to match a repeating subpattern. The last three characters (?, +, and *) are convenient shortcuts for subpatterns that you can create using braces.

In the examples, the first pattern matches numbers in the format 559-555-1234. That is, three digits, a dash, three digits, a dash, and four digits.

The second pattern matches numbers in the format (559) 555-1234 with the space after the area code being optional. The pattern is a left parenthesis, three digits, a right parenthesis, an optional space, three digits, a dash, and four digits. Since this pattern uses the parentheses as regular characters rather than grouping metacharacters, they must be preceded by a backslash.

The third pattern combines the two previous patterns. For an area code, it matches three characters followed by a dash. Or, it matches a left parenthesis, three digits, a right parenthesis, and an optional space. Then, the rest of the pattern matches three digits, a dash, and four digits.