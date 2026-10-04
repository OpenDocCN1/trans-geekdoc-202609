# Part I: Working with MySQL

You will not see this column type used in this book. We do not like to see multi-ple values in a single field as it violates very basic rules of database design. Re-read Chapter 1 if you don't know what this means.

# Numeric column types

MySQL has seven column types suitable for storing numeric values. Note that the following are synonyms: int and integer; double, double precision, and real; and decimal and numeric.

+   * int/integer
* tinyint
* mediumint
* bigint
* float
* double/double precision/real
* decimal/numeric

For numeric types the maximum display size is 255. For most numeric types you will have the option to zerill a column —to left-pad it with zeros. For example, if you have an int column that has a display size of 10 and you insert a value of 25 into this column, MySQL will store and display 0000000025. The numeric column types may also be defined as signed or unsigned. Signed is the default definition.

# INT/INTEGER

Usage:(display size) [unsigned] [zerill]
If you use the unsigned flag, this column can store integers from 0 to 4,294,967,295. If the range is from -2,147,483,648 to 2,147,483,647. Int will be used with auto_increment to define the primary key of a table.

```
create table my_table (
  table_id int unsigned auto_increment primary key,
  next_column text
);
```

Note that I've used an unsigned column because an auto_increment column has no need for negative values.

# TINYINT

Usage:tinyint(display size) [unsigned] [zerill]
If unsigned, tinyint stores integers between 0 and 255. If signed, the range is from -128 to 127.