# Appendix F

# Regular Expressions
Overview

REGULAR EXPRESSIONS provide a means for pattern matching in strings. Patterns may be as simple as a literal string or a literal string with a wildcard character, or they can grow to very complex. How complex? Check out the following example, which is intended for e-mail validation. If you're new to regular expressions this may look bad, but to tell the truth, it's not nearly nasty enough. In fact to properly validate an e-mail, it takes about 200 lines of regular expressions. See Appendix G for an e-mail validation function that's a bit more complete.

```
^[\._0-9a-z-]+@([0-9a-z-]+\.[a-z]{2,3})$
```

When you're working with PHP and MySQL there are three variants of regular expressions you might need to use, the regular PHP functions, the Perl-compatible regular expression functions and MySQL regular functions. The PHP preg(), erei(), ere_replace(), and erei_replace() functions use the patterns described here.

The Perl Compatible Regular Expressions (PCRE) are quite different in places, and they offer some functionality that cannot be replicated with the standard eregi() functions. After you have a good feel for regular expressions, you should probably head over to this page to see the differences of yours: http://www.perl.com/pub/doc/manual/html/pod/perlre.html. The major PCRE functions are preg_match(), preg_match_all(), and preg_replace().

Finally, there is another slight variant of the regular expressions used in MySQL, which is described in Appendix I of the MySQL manual.

# Literal Patterns

The simplest possible pattern match is to a series of known characters. For instance, to match "jay" within a string, you could do this.

```
$str = "this is a string with my name: jay";
{
  echo "pattern found";
```