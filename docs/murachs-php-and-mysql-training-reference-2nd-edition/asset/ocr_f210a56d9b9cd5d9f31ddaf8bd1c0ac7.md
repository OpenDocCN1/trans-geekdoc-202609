# # How to work with mysqli

Although we recommend PDO for new development, many programmers prefer mysqli and have used it for years for existing web applications. As a result, if you need to maintain legacy code that uses mysqli, you can use the skills presented in this topic to do that. Of course, if you are using PDO and don’t need mysqli, you can skip or skim this topic.

When you use mysqli, you can choose between a *procedural style* that uses functions and an *object-oriented style* that uses objects, methods, and properties. In this topic, the first figure shows how to use either style to connect to a database, and the next three figures show how to use the object-oriented style. Then, the last figure shows how the object-oriented style compares with the procedural style. Once you learn one style, it’s pretty easy to switch to the other style whenever that’s necessary.

# ## How to connect to a database

Figure 19-7 shows how to use mysqli to connect to a database. The first example uses the object-oriented style to create a mysqli object that represents a connection to the database. The second example uses the procedural style to return a variable that represents a connection to the database.

For both styles, you need to specify four parameters: host, username, password, and database name. Most of the time, the MySQL database runs on the same server as PHP. As a result, you can usually use the localhost keyword to specify the host computer.

In the first two examples, the statement that gets a connection to the database begins with the *error suppression operator* (@). As a result, PHP doesn’t display a warning if it encounters an error. Although this is probably what you want for a production application, you might want to display warnings when you’re testing and debugging the application. To do that, you can remove the error suppression operator from the start of this line.

After you attempt to connect to a database, you typically want to check to make sure you were able to connect successfully. That way, if your code wasn’t able to connect successfully, you can display an appropriate error message and exit the script.

With the object-oriented style, you can use the connect_errno and connect_error properties of the mysqli object to get the error number and message if they exist. With the procedural style, you can use the mysqli_connect_errno and mysqli_connect_error functions to get the error number and message if they exist. Either way, you can test the error number and method, display an appropriate message, and take an appropriate action. In this figure, the examples display the error message to the user and exit the script, which is an appropriate action for many types of applications.