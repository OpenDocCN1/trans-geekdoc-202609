# 5

# Importing data: plain-text files

In this chapter:

+   - Importing data from delimited text files
+   - Importing data from fixed-width text files

# 5.1 Delimited plain-text files

Plain-text files (sometimes called “ASCII files”, after the character encoding standard they use) are often used to share data. They are limited in what they can contain, which has both downsides and upsides. On the downside, they can’t carry any additional information with them, such as variable types and labels. But on the upside, they don’t carry any additional information that requires additional interpretation by the software. This means they can be read consistently by a wide variety of software tools.

Plain-text files come in two varieties: delimited and fixed-width. “Delimited” is a reference to the fact that the files have a character that marks the boundary between two variables. A very common delimited format is the CSV file; the letters in the file name stand for “Comma Separated Values”, and use a comma as the variable delimiter. Another delimited type, somewhat less common, uses the tab character to separate the variables, and will have the extension “TSV” for, you guessed it, “Tab Separated Values”. Occasionally you will find files that use semi-colons, colons, or spaces as the delimiters.

There are base R functions to read this type of file. The functions within the {readr} (Wickham and Hester, 2020) package has some advantages over the base R functions when it comes to plain-text files. (The {readr} package is part of the tidyverse.) Compared to the equivalent base R functions, the {readr} functions are quite a bit faster, and the package’s functions provide some useful flexibility when it comes to defining variable types as part of the read operation (rather than reading in the dat and then altering the variable types). As well, it returns a tibble instead of a dataframe. (For information about the