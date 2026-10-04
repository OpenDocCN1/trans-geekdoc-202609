# Chapter 3

```
(2, 'Drama'),
(3, 'Adventure'),
(4, 'War'),
(5, 'Comedy'),
(6, 'Horror'),
(7, 'Action'),
(8, 'Kids');
$results=mysql_query($type)
or die(mysql_error()));

// insert data into "people" table
$people="INSERT INTO people\n(people_id, people_fullname, people_isactor, people_isdirector)\nVALUES (1, 'Jim Curry', 1, 0),\n(2, 'Tom Shadyac', 0, 1),\n(3, 'Lawrence Kasdan', 0, 1),\n(4, 'Kevin Kline', 1, 0),\n(5, 'Ron Livingston', 1, 0),\n(6, 'Mike Judge', 0, 1');
n$results=mysql_query($people)
or die(mysql_error()));
```

echo "Data inserted successfully!";
?>

+   1. First, run createmovie.php from your browser, then run viewdata.php.

# How It Works

We hope you didn't have too many errors when running the previous files and you saw the two "success" statements. Although we tried to insert comments throughout the code, let's dissect this thing one step at a time.

First, we connected to the MySQL server so that we could begin sending MySQL commands and working with the database and tables. We also wanted to be told if there was an error, and we wanted to immediately stop running. We did this in the first few lines of code:

```
<?php
//connect to MySQL; we've used our own parameters- you should use
//your own hostname, user, and password
$connect = mysql_connect('localhost', 'root', 'mysqlpass')
or die("Hey loser, check your server connection.");
```

Then we actually created the database, and if for some reason the database could not be created, we told the server to stop running and show what the problem was:

```
//create the main database
mysql_create_db('wiley')
or die(mysql_error());
```

We also made sure to select our database so the server would know which database we would be working with: