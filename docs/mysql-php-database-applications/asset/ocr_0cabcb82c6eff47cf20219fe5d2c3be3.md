# char

Usage: char(length)

The char column type has a maximum length of 255 characters. This is a fixed-length type, meaning that the field will be right-padded with spaces when a value is inserted that has fewer characters than the maximum length of the column. So if a column has been defined as char(10) and you want to store the value happy, MySQL will actually store happy and then five spaces. The spaces are removed from the result when the value is retrieved from the table. Values longer than the column width are truncated.

# varchar

Usage: varchar(length)

This type is nearly identical to char and is used in many of the same places. It also has a maximum length of 255 characters. The difference is that varchar is a variable-length column type, meaning that values will not be padded with spaces. Instead MySQL will add one character to each varchar field to store the length of the field.

MySQL removes spaces from the end of strings in varchar fields, but this behavior might change in future releases of the language.

> If you define a column as varchar with a column length of less than four, MySQL will automatically change the column to the char type. Similarly, if you try to mix chars and varchars with a column length of more than four, they all become varchars.

# Using char or varchar

For the most part, there is little practical difference between char and varchar. Which one you decide to use will depend on which will require more space, the trailing spaces in a char column or the size byte in varchar. If your field stores something like last names, you'll probably want to allow 25 characters, just to be safe. If you were to use the char column type and someone had the last name Smith, your column would contain 20 trailing spaces. There's no need for that; you're much better off using varchar and allowing MySQL to track the size of the column. However, when you want to store passwords of five to seven characters, it would be a waste to use varchar to track the size of the column. Every time a varchar field is updated, MySQL has to check the length of the field and change the character that stores the field length. You'd be better off using char(7).