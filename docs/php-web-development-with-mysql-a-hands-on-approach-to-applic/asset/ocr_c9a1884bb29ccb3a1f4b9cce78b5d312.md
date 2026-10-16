# 26. INTRODUCTION TO OBJECT-ORIENTED PROGRAMMING IN PHP

PDO is the library of choice for interacting with databases, primarily because it works with many different database technologies. This library gives us a familiar API no matter where we store our data.

First, we need to create a database and a simple table we can work on. I'll make a simple database called Student and a table called student used to hold a student's first name, last name, and email address for this demonstration as shown in Figure 26.5

A common way to use PDO is to create a class known as a CRUD wrapper that manages all queries to a database table. CRUD stands for Create, Read, Update, and Delete, which are the common operations we perform on database tables. It is a good practice to name our classes using a “Studly Caps” interpolation of our database table and concatenate the word “Manager” onto the end of our class. In this case, we should name our class StudentManager since our table is called student.

![](bbox=[0.48, 0.2, 0.85, 0.57])

# Using PDO to Create New Database Entries

Listing 26.22 is the class along with a create() method to insert rows into our student table.

# Listing 26.22.

```
```php
1. <?php
2. 
3. class StudentManager
4. {
5.     // Database connection constants
6.     private const DB_TECHNOLOGY = "mysql";
7.     private const DB_HOST = "localhost";
8.     private const DB_NAME = "Student";
9.     private const DB_USER = "testuser";
10.    private const DB_PASSWORD = "testuser";
11. ```
```