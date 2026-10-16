> **Variable-length format:** In this format, MySQL stores the string in a field that is the same length as the string. You still specify a length for the string, but if the string is shorter than the specified length, MySQL only uses the space required rather than leaving the extra space empty. If the string is longer than the space specified, the extra characters are not stored.

If a character string length varies only a little, use the fixed-length format. For example, a length of 10 works for all ZIP codes, including those with the ZIP+4 number. If the ZIP code does not include the ZIP+4 number, only five spaces are left empty. However, if your character string can vary more than a few characters, use a variable-length format to save space. For example, your pet description might be *Small bat* or it might run to several lines of description. So it would be better to store this description in a variable-length format.

# Numerical data

Another common type of data is *numerical data* — data that is stored as a number. Decimal numbers (for example, 10.5, 2.34567, 23456.7) can be stored as well as integers (for example, 1, 2, 248). When data is stored as a number, it can be used in numerical operations, such as adding, subtracting, squaring, and so on. If data isn’t used for numerical operations, however, storing it as a character string is better because the programmer will be using it as a character string. No conversion is required. For example, you probably won’t want to add the digits in the users’ phone numbers, so phone numbers should be stored as character strings.

MySQL stores positive and negative numbers, but you can tell MySQL to store only positive numbers. If your data will not be negative, store the data as *unsigned* (without using a + or − sign before the number). For example, a city population or the number of pages in a document can never be negative.

# Date and time data

A third common type of data is date and time data. Data stored as a date can be displayed in a variety of date formats. It can also be used to determine the length of time between two dates or two times — or between a specific date or time and some arbitrary date or time.

# Enumeration data

Sometimes data can have only a limited number of values. For example, the only possible values for a column might be yes or no. MySQL provides a data type called *enumeration* for use with this type of data. You tell MySQL what