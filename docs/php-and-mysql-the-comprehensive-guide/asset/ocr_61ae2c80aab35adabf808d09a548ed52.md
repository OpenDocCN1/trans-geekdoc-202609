![](bbox=[0.142, 0.101, 0.678, 0.27])

Figure 7.21 The Two Expressions Sound Almost the Same

# ## 7.8 Helpful and Useful Information

This section is the repository for all functions that are too important to be left without an example but do not fit in well with any of the main topics.

# ### 7.8.1 ASCII and Conversion

Computers store data as bytes. A byte has a value between 0 and 255. The ASCII character code represents letters and characters within this value range. This means that if a byte has a numerical value, then a numerical code can be used to determine which character matches it. Although ASCII is an old character set, and UTF-8 character sets are now increasingly being used in browsers and HTML documents, you still sometimes need the ASCII code of characters or letters. PHP offers two functions for this:

+   - chr(ASCII) converts an ASCII code into the corresponding character.
+   - ord(character) returns the ASCII code for the corresponding character.

```
<?php
echo "Character: " . chr(65) . "<br />";
echo "ASCII: " . ord("A");
?>
```

Listing 7.38 "chr()" and "ord()" ("chr_ord.php")

# ### 7.8.2 Unicode Code Point

A codepoint is a value in a character set. Accordingly, the Unicode codepoint is a value in the Unicode character set. These values are often specified in hexadecimal form from 0 to 10FFFF (see Figure 7.22). With \u, PHP now provides a way of converting such a value into the corresponding UTF-8 character and outputting it.