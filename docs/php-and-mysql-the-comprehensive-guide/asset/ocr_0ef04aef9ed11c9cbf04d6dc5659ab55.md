# # 7.7 Compare

You already know the simple string comparison from <u>Chapter 5</u>. With exact equality and exact inequality, you can even check the data type.

```
4 == "4"
```

therefore results in false.

PHP's string functions now provide a few more comparisons that go beyond this basic check.

# ## 7.7.1 Comparison Functions

The strcmp(String1, String2) and strcasecmp(String1, String2) functions are used to perform a binary comparison with two strings. The only difference is that strcasecmp() is not case-sensitive. In contrast to the comparison with the corresponding comparison operators, the functions return the result of which string is larger. If String1 is smaller, the return value is less than 0; if both strings are the same, the return value is 0; if String1 is larger, the return value is greater than 0.

> > **Note**
> >
> > There is also a comparison function that only compares parts of two strings with each other: substr_compare(String1, String2, Start, Length, Case-sensitive). The mandatory parameters are the two strings and the position from which they are to be compared. The length—the number of characters to be compared—is optional. Since PHP 5.6, the value 0 is also permitted. Also optional is the Boolean parameter Case-sensitive, which disables the distinction between upper- and lowercase with false (default value is true).

# ## 7.7.2 Similarities and Differences

Quantifying similarities or differences between strings isn't only useful if you want to determine whether a lazy author (pupil, student, professor, etc.) has committed plagiarism.

# ### Similarity

The similar_text(String1, String2, percent) function calculates the similarity between two strings. Optionally, you can specify a variable (as a reference) for the third parameter. The function then writes the result of the comparison to this variable as a percentage value. The return value of the function is somewhat less meaningful than the percentage. It indicates how many letters are recognized as the same.