The most common alterations you can make with this statement are shown in Table 10.5.

# Table 10.5 Possible Changes with the ALTER TABLE Statement

| Syntax | Description |
| --- | --- |
| ADD [COLUMN] column_description [FIRST | AFTER column ] | Adds a new column in the specified location (if not specified, then the column goes at the end). Note that column_description needs a name and a type, just as in a CREATE statement. |
| ADD [COLUMN] (column_description, column_description,...) | Adds one or more columns at the end of the table. |
| ADD INDEX [index] (column,...) | Adds an index to the table on the specified column or columns. |
| ADD CONSTRAINT [symbol] PRIMARY KEY (column,...) | Makes the specified column or columns the primary key of the table. The CONSTRAINT notation is for tables using foreign keys. See Chapter 13, "Advanced MySQL Programming," for more details. |
| ADD UNIQUE [CONSTRAINT [symbol]] [index] (column,...) | Adds a unique index to the table on the specified column or columns. The CONSTRAINT notation is for tables using foreign keys. |
| ADD CONSTRAINT [index] FOREIGN KEY (index_col,...) [reference_definition] | Adds a foreign key to a table. See Chapter 13 for more details. |
| ALTER [COLUMN] column [SET DEFAULT | DROP DEFAULT] | Adds or removes a default value for a particular column. |
| CHANGE [COLUMN] column new_column description | Changes the column called so that it has the description listed. Note that this syntax can be used to change the name of a column because a column_description includes a name. |
| MODIFY [COLUMN] column_description | Similar to CHANGE. Can be used to change column types, not names. |
| DROP [COLUMN] column | Deletes the named column. |