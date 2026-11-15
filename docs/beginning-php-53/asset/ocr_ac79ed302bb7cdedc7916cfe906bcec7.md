# String Matching with Regular Expressions

In Chapter 5 you explored many of PHP's powerful string manipulation functions, such as `strstr()` for finding text within a string and `str_replace()` for searching and replacing text within a string.

In this chapter you learn about PHP's even more powerful regular expression functions. These give you a lot more flexibility than the regular string-matching functions because they let you compare a string against a *pattern* of characters rather than against a fixed string. For example, you can search a string for a pattern of characters comprising exactly three digits, followed by either a comma or a dot, followed by from one to four letters.

Within a regular expression you use special symbols such as `?` and `^` to specify a pattern. Because patterns can get quite complex, it can be hard to decipher regular expressions when you first start out. However, with a bit of practice, as well as some of the hints in this chapter, you'll find that you can read regular expressions much more quickly and easily.

Although regular expressions aren't essential to PHP programming — you can usually do a similar job with the string matching functions and a loop or two — they're your best bet when you need to match patterns. For one thing, a single regular expression is usually much more compact and intuitive than a whole series of string matches and loops. The expression will often run much quicker, too.

By the time you've read this chapter you'll know about:

+   - [ ] **Matching strings against regular expressions:** You explore PHP's `preg_match()` and `preg_match_all()` functions that let you apply regular expressions to strings to find matches

+   - [ ] **The ins and outs of regular expression syntax:** You learn all about the special characters used in regular expressions, as well as how to match character types, several characters at once, alternative groups of characters, and much more