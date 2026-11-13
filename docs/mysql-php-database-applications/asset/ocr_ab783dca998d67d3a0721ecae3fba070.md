# time

Usage: time

This type stores time in the format HH:MM:SS and has a value range from -838:59:59 to 838:59:59. The reason for the large values is that the time column type can be used to store the results of mathematical equations involving times.

# year

Usage: year[(2|4)]

In these post-Y2K days it's hard to imagine that you'd want to store your years in two-digit format, but you can. In two-digit format, allowable dates are those between 1970 and 2069, inclusive. The digits 70–99 are prefaced by 19, and 01–69 are by 20.

Four-digit-year format allows values from 1901 to 2155.

# Creating Indexes

MySQL can create an index on any column. There can be a maximum of 16 indexed columns for any standard table. (MyISAM tables support 32 indexes by default and can be made to support 64.) The basic syntax is as follows:

```
index [index_name] (indexed_column)
```

> Although the index name is optional, you should always name your indexes. It becomes very important should you want to delete or change your index using the SQL alter statement. If you don't specify a name, MySQL will base the index name on the first column in your index.

Another way to create an index is to declare a column as a primary key. Note that any auto_increment column must be defined as part of a unique index and is normally (but not necessarily) the primary key of the table. In the following code, the id_col column is indexed:

```
create table my_table (
  id_col int unsigned auto_increment primary key,
  another_col text
);
```