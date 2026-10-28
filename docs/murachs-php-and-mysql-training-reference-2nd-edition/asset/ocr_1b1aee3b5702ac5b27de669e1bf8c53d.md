# How to select rows with a LIMIT clause

In the database for this chapter, each table has a small number of rows. As a result, you don’t need to limit the number of rows that your SELECT statements retrieve from this database. With a production database, however, it’s common for a table to have thousands or even millions of rows. Then, you don’t want to accidentally retrieve hundreds or thousands of rows.

One way to limit the number of rows that a SELECT statement retrieves is to code a LIMIT clause at the end of the statement as shown in figure 18-3. The easiest way to do that is to code the LIMIT keyword followed by the number of rows as shown in the first example. This retrieves the same rows as coding the LIMIT keyword followed by a row offset of 0, a comma, and the number of rows to retrieve as shown in the second example.

However, if you don’t want to begin retrieving rows starting at the first row, you can specify another offset. In this figure, for example, the third statement specifies an offset of 1 to begin retrieving rows at the second row. To begin retrieving rows at the third row, specify an offset of 2. To begin at the fourth row, specify an offset of 3. And so on.

By default, phpMyAdmin automatically adds a LIMIT clause to most SELECT statements so they only retrieve the first 30 rows of a table. This is usually what you want since it prevents you from accidentally retrieving thousands of rows from a database. However, if you want to use phpMyAdmin to view more than 30 rows, you can override this default setting by coding your own LIMIT clause.