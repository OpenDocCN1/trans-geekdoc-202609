This pattern matches either a W or a w for the first character, and then a lowercase i, a lowercase l, and so on.

Here are a few Perl examples:

```
print "William" =~ /[Ww]illiam/;
print "william" =~ /[Ww]illiam/;
print "illiam" =~ /[Ww]illiam/;
```

The first two examples match because the first character can be either W or w. The third one, however, doesn't match because [Ww] means you must have either W or w, and illiam doesn't have either.

![](bbox=[0.12, 0.31, 0.2, 0.38])

[Ww] will match only a single character. For example, suppose this is your pattern:

```
[Tt]homas\s[Jj]jefferson
```

All the following strings match this pattern:

+   Thomas Jefferson
+   thomas jefferson
+   Thomas jefferson
+   thomas Jefferson

But the string thomas Jjefferson does not match the pattern because [JJ] matches only a single character. If you want to match any number of instances of w and W, use one of the usual quantifiers, like so:

```
print "Ttththomas JjjjjJJJJJJJefferson" =~ /[Tt]+homas\s[Jj]+efferson/;
```

This stuttering mess matches. The [Tt] has a + after it, meaning you can use one or more instance of T or t (or any combination thereof). Similarly, [JJ] has a + after it, meaning any number and combination of J and j works, as long as you have at least one J or j. So for this bizarre pattern, the good old string Thomas Jefferson also matches.

Here are the rules for matching characters in a set:

+   For a specific set of characters in a pattern, list the characters inside square brackets, as in [Ww]. But remember that this matches only a single W or a single w, not two characters.

+   If you want multiple characters, follow the bracket with +, *, or any of the other quantifiers.