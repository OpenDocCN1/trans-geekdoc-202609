# A model in mysqli

Figure 19-12 shows the model in figure 19-6 after it has been converted from PDO to mysqli. As a result, if you understand the PDO version of the model, you shouldn’t have much trouble understanding the mysqli version of the model. However, there are several significant differences.

The first significant difference is that the functions that retrieve data don’t use prepared statements. That’s because mysqli’s prepared statements don’t provide methods for returning arrays. Because this makes it difficult to separate the model from the view, I decided to not use prepared statements for these functions.

This allows the functions that retrieve data to use the fetch_assoc method of the result set to get an associative array for each row. Then, if necessary, the code can add that row to an array to create a two-dimensional array. For example, the get_categories method loops through the rows in the result set, gets an associative array for each row, and adds that array to the categories array. Then, it returns the categories array.

Another approach would be to use prepared statements and return the mysqli_stmt object. The advantage of this approach is that it allows you to use prepared statements, which improves the security and efficiency of your code. In addition, since you don’t store the entire result set in an array, the code runs more efficiently and uses less memory when you’re working with large result sets. Of course, the disadvantage is that it mixes the model and the view, which makes your code more difficult to maintain.

Note that the functions that modify data use prepared statements. As a result, these functions prepare the statement, bind the parameters to the statement, and execute the statement.

The second significant difference between PDO and mysqli is how these functions handle database errors. Here, the mysqli functions detect errors by checking the return values after making calls to the database. As a result, the functions that work with prepared statements check for errors twice, once after the statement is prepared and again after the statement is executed. Then, if an error has occurred, these functions handle the error appropriately by getting the error message from the mysqli object and passing that message to the display_db_error function.