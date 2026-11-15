# # Chapter 10
# Regular Expressions

*Regular expressions are the ultimate in dealing with strings. A regular expression is a pattern with which a string can be compared and edited.*

The regular expressions in PHP originally come from the Perl programming language. In practice, they are mainly used for validations and searches within strings that cannot be covered by simpler checks such as equality. Accordingly, after the basics and an overview of the functions, you will also find some application examples such as the filtering of zip codes, telephone numbers, and links.

> > **Note**
> > In PHP, there has long been a second type of regular expression (RegEx): POSIX.1 This type came from the regular expressions in the Unix command line. They were used with the ereg.* functions, but they are no longer recommended functions since PHP 5.3 and were removed in PHP 7.

# ## 10.1 Basics

As mentioned, regular expressions are patterns that can be used to recognize areas or an entire string. These patterns follow certain rules and use metacharacters to represent certain patterns. We present the basics of patterns and metacharacters here.

> > **Note**
> > This chapter mainly shows the PHP functions and can only lay the foundations for regular expressions. For more information, we recommend *Mastering Regular Expressions* by Jeffrey E. F. Friedl (O'Reilly, 2006).

The most important information is summarized here:

+   - Numbers and letters correspond to themselves.
+     a
+     therefore expects an a as a component.

1 POSIX stands for *Portable Operating System Interface*. The POSIX standard contains specifications for regular expressions, among other things.