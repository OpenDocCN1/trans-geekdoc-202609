# Chapter 2: The Structured Query Language for Creating and Altering Tables

# TINYTEXT

Usage: tinytext

This is the first of the four binary (or blob) text character types. All of these types (tinytext, mediumtext, and largesttext) are variable column types, similar to varchar. They differ only in the size of string they can contain. The tinytext type has a maximum length of 255, so in fact it serves the same purpose as varchar(255). An index can be created for an entire textcolumn

# TEXT

Usage: text

The text type has a maximum length of 65,535 characters. Indexes can be created on the first 255 characters of a text column.

# MEDIUMTEXT

Usage: mediumtext

The mediumtext type has a maximum length of 16,777,215 characters. Indexes can be created on the first 255 characters of a mediumtext column.

# LONGTEXT

Usage: longtext

The longtext type has a maximum length of 4,294,967,295 characters. Indexes can be created on the first 255 characters of a longtext column. However, this column is currently not very useful, MySQL allows strings up to 16 million bytes.

# ENUM

Usage: enum ('value1', 'value2', 'value3' ...) [default 'value']

With enum, you can limit the potential of values to those you specify. It allows for 65,535 values, though it's difficult to see a situation where you'd want to use this column with more than a few potential values. This type would be of use when, for example, you want to allow only values of "yes" or "no". The create statement that makes use of enum will look like:

```
create table my_table (
  id int auto_increment primary key,
  answer enum ('yes', 'no') default 'no'
);
```

SET Usage: set ('value1', 'value2', 'value3' ...) [default 'value']

This column type defines a superset of values. This allows for zero or more values from the list you specify to be included in a field.