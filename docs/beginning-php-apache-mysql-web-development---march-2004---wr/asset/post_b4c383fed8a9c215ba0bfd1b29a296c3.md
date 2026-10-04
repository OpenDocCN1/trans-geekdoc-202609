
# Chapter 6

| | | |
|---|---|---|
| Bruce Almighty | [EDIT] [DELETE] |
| Office Space | [EDIT] [DELETE] |
| Grand Canyon | [EDIT] [DELETE] |
| Jim Carver | People [ADD] [EDIT] [DELETE] |
| Tom Shadrac | [EDIT] [DELETE] |
| Lawrence Kaidan | [EDIT] [DELETE] |
| Kevin Kline | [EDIT] [DELETE] |
| Ron Livingston | [EDIT] [DELETE] |
| Mike Judge | [EDIT] [DELETE] |

Figure 6-1

## Inserting a Simple Record from phpMyAdmin

Note that in the following scripts, we will follow a simple rule concerning SQL: Always try the query in MySQL before trying to insert it in your code. The simple reason is that you are probably better off debugging one language at a time.

## Try It Out Inserting Simple Data

Now follow these steps to insert some data:

- 1. Open your database in phpMyAdmin and enter the following SQL code (yes, there is an error) as in Figure 6-2.

```
INSERT INTO
`movie`
(`movie_name`, `movie_type`, `movie_year` )
VALUES
(`Bruce Almighty','1','2003` )
```

## Letting the User Edit the Database

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_189_0.png)

Figure 6-2

- 2. The following message appears (see Figure 6-3 for details):

You have an error in your SQL syntax. Check the manual that corresponds to your MySQL server version for the right syntax to use near '2003' at line 5

- 3. Fix the error as this suggests (quite simple to do with the line reference) and run. phpMyAdmin displays the executed SQL and takes you back to the table content display as shown in Figure 6-4.

Before doing any SQL query in PHP, you should always test your SQL statement in phpMyAdmin. It will enable you to debug the SQL before inserting it in your code and prevent debugging in two different languages at the same time.

# Chapter 6

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_190_0.png)

Figure 6-3

## How It Works

When inserting a record in a table, you don't need to insert the id if you set the primary key field to auto increment. The engine will gladly handle that for you. This enables you to be sure you don't have duplicate keys in the table.

To get the just-inserted record auto increment id, just use the PHP `mysql_insert_id()` function after the `mysql_query()` function call. This function returns the primary key field when inserting a new record.

> The `mysql_insert_id` function syntax can be found on the PHP site at www.php.net/mysql_insert_id.

Because we have created the SQL query on more than one line, we can use the line number returned in the following error message.

> You have an error in your SQL syntax. Check the manual that corresponds to your MySQL server version for the right syntax to use near '2003' at line 5

## Letting the User Edit the Database

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_191_0.png)

This line corresponds to the value part of our SQL statement, as shown here:

> ( 'Bruce Almighty','1', '2003' )

If our SQL query then on one line, we've had only a useless "error in line 1" message. Here you can see that on the line we forget to close a quote in the movie_year value.

Now you can say that we omitted the 'movie'.'movie_id' field. We did this on purpose (yes, we did). Not specifying the primary key value forces the MySQL engine to automatically determine the auto increment value. Thanks to this, we don't need to know what the key will be.

## Inserting a Record in a Relational Database

Databases often hold more than one table. All those tables can be totally independent and would be like using your car to store things in the trunk but not to drive around in.

In old systems in which relational databases didn't exist, every row held all the information. Your system running with only one table holding all the information. Your movie table would store all the data about the actors and the directors and the movie types. Let's say that one day you were to decide that a movie category should change from action to adventure (things change). You would have to go through all records to change the movie type label.

In modern RDBMS (relational database management systems), this is not the case anymore; you will create a 'movetype' table storing a reference of all movie types possible, and you will link movies to the relevant movie type.

To link tables, you will use a primary/foreign key. The primary key of the 'movetype' table is a numeric identification of each type of movie. For example, in our database the id 1 references comedy. The foreign key is the reference in the movie table to the 'movetype' primary key.

In the following exercise, you will use PHP and SQL to insert a movie in your database. This movie is of

## Try It Out Inserting a Movie with Known Type

This time, let's do something more complicated. You will need to add a movie to the system specifying an existing movie type and director.

- 1. Create new empty file named movie.php and enter the following code:

```php
<?php
$link = mysqli_connect('localhost', 'root', '');
or die("Could not connect: " . mysqli_error());
mysqli_select_db($link, 'chapter6', $link) or die(mysqli_error());
$sql = "SELECT id, name FROM movetype ORDER BY name";
$result = mysqli_query($sql)
or die("Invalid query: " . mysqli_error());
while ($row = mysqli_fetch_array($result, MYSQLI_ASSOC)) {
?>
<html
<head>
<title>Add Movie</title>
</head>
<body>
<form action="commit.php?action=add&type=movie" method="post">
<table border="0" cellspacing="0" width="100%">
<tr>
<td>Movie Name</td>
<td><input type="text" name="movie_name"></td>
</tr>
<tr>
<td>Movie Type</td>
<td>
<select name="movie_type">
<option value="">Select a type...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td>Lead Actor</td>
<td>
<select name="movie_leadactor">
<option value="">Select an actor...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td>Director</td>
<td>
<select name="movie_director">
<option value="">Select a director...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td colspan="2" align="center">
<input type="submit" name="submit" value="Add">
</td>
</tr>
</table>
</form>
</body>
</html>
```
*(Note: The OCR text provided was highly fragmented and contained errors in the code blocks. I have reconstructed the logic based on the context of a PHP/MySQL application.)*

2. Save your file and upload it to a new chapter6 on your server.

3. Create a new empty file named commit.php and enter the following code:

```
<?php
// COMMIT ADD
$link = mysqli_connect("localhost", "root", "")
nor die("Could not connect: " . mysqli_error());
mysqli_select_db($link, "chapter6", $link) or die (mysqli_error());
switch ($_GET['action']) {
case "add":
witch ($_GET['type']) {
case "movie":
$Sql = "INSERT INTO
movie (
movie_name,
movie_year,
movie_type,
movie_leadactor,
movie_director
)VALUES
(
"".\$_POST['movie_name']."",
"".\$_POST['movie_year']."",
"".\$_POST['movie_type']."",
"".\$_POST['movie_leadactor']."",
"".\$_POST['movie_director']."\)";
```
