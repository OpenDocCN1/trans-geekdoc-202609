# # How to insert, update,
and delete rows

Now that you know how to code subqueries, you’re ready to learn the details of coding the INSERT, UPDATE, and DELETE statements. You can use these three statements to add new rows to a table, to modify existing rows in a table, or to delete rows from a table.

# ## How to insert rows

To add new rows to a table, you use the INSERT statement as shown in figure 18-15. To start, this figure shows a CREATE TABLE statement for a products table. This table has seven columns, and two of these columns have default values.

Then, the second statement in this figure uses an INSERT statement to add a single row to the products table. This statement uses the INSERT INTO clause to specify the name of the table. Then, it uses the VALUES clause to specify the values for each column.

There are four points to note about this VALUES clause. First, it includes a value for every column in the table. Second, it lists the values in the same sequence that the columns appear in the table so MySQL knows which value to assign to which column. Third, it uses the DEFAULT keyword for two columns to use the default value for that column. As a result, the first column uses the integer value that’s automatically generated for the productID column, and the sixth column uses the default value of 0.00 for the discountPercent column. Fourth, it uses MySQL’s built-in NOW function to insert the current date and time into the dateAdded column.

The third statement includes a column list in the INSERT clause. Note that this list doesn’t include the productID or discountPercent columns since they provide default values. Similarly, you can omit any columns that allow NULL values. Note also that you don’t need to code the columns in the same sequence as the columns in the products table when you include a list of columns. Instead, you can code the columns in any sequence you like as long as you make sure that you use the same sequence for the values in the VALUES clause.

The fourth statement adds multiple rows to the categories table. To do that, it separates each list of values with a comma.

When you specify the values for the columns to be inserted, you must be sure that those values are compatible with the data types of the columns. In this figure, note how the values for the products table have data types that are compatible with the column definitions of the products table.