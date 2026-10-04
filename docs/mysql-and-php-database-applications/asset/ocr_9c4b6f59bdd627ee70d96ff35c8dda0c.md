# 36 Part I: Working with MySQL

indexes; add or drop columns and indexes; and redefine the definitions of columns and indices. This statement will always start with alter table table_name. The rest of the command will depend on the action needed as described below.

# Changing a table name

The syntax for changing a table name is as follows:

```
alter table table_name rename new_table_name
```

![](bbox=[0.162, 0.296, 0.237, 0.363])

If you have MySQL version 3.23.27 or higher you can make use of the rename statement. The basic syntax is
rename table_name to new_table_name

# Adding and dropping columns

When adding a column, you will need to include all the column definitions defined in the previous section. In addition, starting in version 3.22, MySQL allows you to specify where in the table the column will reside, although this specification is optional. The basic syntax is:

```
alter table table_name add column column_name column attributes
```

For example:

```
alter table my_table add column my_column text not null
```

To specify the location of the column, use first to specify your inserted column as the first column in the table or after to place the column following a column that already exists, as shown in the following examples.

```
alter table my_table add column my_next_col text not null first
alter table my_table add column my_next_col text not null after
my_other_column,
```

To drop a column, you need only the following:

```
alter table table_name drop column column name
```