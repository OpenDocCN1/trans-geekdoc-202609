# # 3 Strings

+   $3.1. Literals, Operators, and Escapes ➤ 83
$3.2. Comparing Strings ➤ 86
$3.3. Characters and Strings ➤ 87
$3.4. Indexing and Slicing Strings ➤ 90
$3.5. String Formatting with the Fmt Package ➤ 93
$3.5.1. Formatting Booleans ➤ 97
$3.5.2. Formatting Integers ➤ 98
$3.5.3. Formatting Characters ➤ 99
$3.5.4. Formatting Floating-Point Numbers ➤ 104
$3.5.5. Formatting Strings and Slices ➤ 101
$3.5.6. Formatting for Debugging ➤ 103
$3.6. Other String-Related Packages ➤ 106
$3.6.1. The Strings Package ➤ 107
$3.6.2. The Strconv Package ➤ 113
$3.6.3. The Utf8 Package ➤ 117
$3.6.4. The Unicode Package ➤ 119
$3.6.5. The Regexp Package ➤ 120
$3.7. Example: M3u2pls ➤ 130

This chapter covers Go's string type and key string-related packages from the standard library. The chapter's sections include coverage of how to write literal strings and how to use the string operators; how to index and slice (take substrings of) strings; and how to format the output of strings, numbers, and other built-in and custom types.

Go's high-level string-related functionality, such as its for ... range loop which iterates over a string character by character, the functions from the strings and strconv packages, and Go's ability to slice strings, are all that is needed for every-day programming. Nonetheless, this chapter covers Go strings in depth, includ-