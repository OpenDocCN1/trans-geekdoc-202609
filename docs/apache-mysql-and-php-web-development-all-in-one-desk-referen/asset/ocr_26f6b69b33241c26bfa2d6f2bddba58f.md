# # Chapter 5: Joining, Splitting, and Making Up

# ## In This Chapter

+   - Splitting strings into multiple substrings
+   - Splitting in Perl, PHP, and Tcl
+   - Obtaining individual characters
+   - Joining back together

A common problem in computer programming is dividing a string into various substrings and then individually processing the different parts. For example, suppose you have an entire paragraph stored in a single string and you want to get an array containing every word in the paragraph.

Sometimes when faced with this problem, the programmer will write a function (or find a function written by somebody else) that will go through a string and break up the string based on spaces. Although this works, it’s not very flexible. For example, if you like to put two spaces after each sentence, this may result in a “word” between the two spaces that’s really just an empty string. And what about punctuation?

The languages I cover in this book all support various splitting techniques whereby you can split up your strings based not on a fixed character (such as a space) but on a regular expression. Here's a quick example using Perl:

```
```perl
$paragraph =
  "This is a paragraph. It consists of ".
  "several words, and several lines, and ".
  "lots of punctuation! Sentences are separated ".
  "by two spaces (oh my!).";
@words = split(/\\W+/, $paragraph);
foreach (@words) {
  print "$_\\n";
}
```
```

This example uses the split function to divide up the string by words. The regular expression specifies what the separator characters are. You want to separate based on whitespace and punctuation — that is, anything that is