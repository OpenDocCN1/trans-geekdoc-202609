word COLUMN is completely optional, and has no effect one way or the other.

+   CHANGE [COLUMN] col_name create_definition

This action replaces an existing column (col_name) with a new column, as defined by create_definition (the syntax of which is as specified for CREATE TABLE on page 181). The data in the existing column is converted if necessary and placed in the new column.

Note that create_definition includes a new column name, so this action may be used to rename a column if you wish. If you want to leave the name of the column unchanged, however, don't forget to include it twice (once for col_name and once for create_definition), or use the MODIFY action below.

+   MODIFY [COLUMN] create_definition

Nearly identical to the CHANGE action above, this action lets you specify a new declaration for a column in the table, but assumes you will not be changing its name. Thus, you simply have to re-declare the column with the same name in the create_definition parameter (as defined for CREATE TABLE on page 181). As before, COLUMN is completely optional and does nothing.

Although convenient, this action is not standard SQL syntax, and was added for compatibility with an identical extension in Oracle database servers.

+   DROP [COLUMN] col_name

Fairly self-explanatory, this action completely removes a column from the table. The data in that column is irretrievable after this query completes, so be sure of the column name. COLUMN, as usual, can be left off – it doesn’t do anything but make the query sound better when read aloud.

+   DROP PRIMARY KEY

+   DROP INDEX index_name

The above two actions are quite self-explanatory: they remove from the table the primary key, and a specific index, respectively.

+   RENAME [TO | AS] new_tbl_name

This action renames the table. The words TO and AS are completely optional, and don’t do anything. Use ‘em if you like ‘em.