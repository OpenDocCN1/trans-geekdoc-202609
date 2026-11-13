# What is AJAX ?

+   - AJAX stands for **Asynchronous JavaScript** and **XML**. AJAX is a new technique for creating better, faster, and more interactive web applications with the help of XML, HTML, CSS and Java Script.
+   - Conventional web application transmit information to and from the sever using synchronous requests. This means you fill out a form, hit submit, and get directed to a new page with new information from the server.
+   - With AJAX when submit is pressed, JavaScript will make a request to the server, interpret the results and update the current screen. In the purest sense, the user would never know that anything was even transmitted to the server.
+   For complete learning on AJAX, please refer our AJAX Tutorial.

# PHP and AJAX Example

To clearly illustrate how easy it is to access information from a database using Ajax and PHP, we are going to build MySQL queries on the fly and display the results on "ajax.html". But before we proceed, let's do a bit of ground work first. Create a table using the following command. **NOTE:** We are assuming you have sufficient privilege to perform following MySQL operations

```
CREATE TABLE `ajax_example` (
 `name` varchar(50) NOT NULL,
 `age` int(11) NOT NULL,
 `sex` varchar(1) NOT NULL,
 `wpm` int(11) NOT NULL,
 PRIMARY KEY (`name`)
)
```

Now dump the following data into this table using the following SQL statements:

```
INSERT INTO `ajax_example` VALUES ('Jerry', 120, 'm', 20);
INSERT INTO `ajax_example` VALUES ('Regis', 75, 'm', 44);
INSERT INTO `ajax_example` VALUES ('Frank', 45, 'm', 87);
INSERT INTO `ajax_example` VALUES ('Jill', 22, 'f', 72);
INSERT INTO `ajax_example` VALUES ('Tracy', 27, 'f', 0);
INSERT INTO `ajax_example` VALUES ('Julie', 35, 'f', 90);
```