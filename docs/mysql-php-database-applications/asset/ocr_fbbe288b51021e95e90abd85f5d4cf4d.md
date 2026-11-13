The primary key can also be declared like other indexes, after the column definitions, as in the following code:

```
create table my_table (
 id_col int unsigned not null auto_increment,
 another_col text,
 primary key(id_col)
);
```

Indexes can span more than one row. If a query uses two rows in concert during a search, you can create an index that covers the two with this statement:

```
create table mytable(
 id_col int unsigned not null,
 another_col char(200) not null,
 index dual_col_index(id_col, another_col)
);
```

The preceding index will be used for searches that start on id_col and can include another_col. Indexes of this kind work from left to right. So this index will be used for searches that are exclusively on id_col. However, it will not be used for searches on another_col.

You can also create indexes on only part of a column. For char, varchar, and blob columns, you can create indexes for the initial portion of a column. Here the syntax is as follows:

```
index index_name (column_name(column_length))
```

For example:

```
create table my_table(
 char_column char (255) not null,
 text_column text not null,
 index index_on_char (char_column(20)),
 index index_on_text (text_column(200))
);
```

An index can also assure that unique values exist in every row in a table by using the unique constraint, as follows.

```
create table my_table(
 char_column char (255) not null,
 text_column text not null,
 unique index index_on_char (char_column)
);
```