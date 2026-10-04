# Using PHP with MySQL

```
) TYPE=MyISAM AUTO_INCREMENT=4 *;

$results = mysql_query($movie)
or or die (mysql_error());

////create 'movietype' table
$movietype="CREATE TABLE movietype (
mietype_id int(11) NOT NULL auto_increment,
mietype_label varchar(100) NOT NULL,
PRIMARY KEY (movietype_id)
) TYPE=MyISAM AUTO_INCREMENT=9";

$results = mysql_query($movietype)
or or die (mysql_error());

//create 'people' table
$people="CREATE TABLE people (
people_id int(11) NOT NULL auto_increment,
people_fullname varchar(255) NOT NULL,
people_isactor tintint(1) NOT NULL default 0,
people_isdirector tintint(1) NOT NULL default 0,
PRIMARY KEY (people_id)
) TYPE=MyISAM AUTO_INCREMENT=7";

$results = mysql_query($people)
or die (mysql_error_));
```

echo "Movie Database successfully created!";

?>

+   2. Save this file as createmovie.php.
3. Fill the database with this file, which you should save as moviedata.php:

```
<?php
//connect to MySQL
$connect = mysql_connect('localhost', 'root', '$mysqlpass') or
die (Hey loser, check your server connection);
n
// make sure we're using the right database
mysql_select_db('wiley');

//insert data into 'movie' table
$insert="INSERT INTO movie (movie_id, movie_name, movie_type, movie_year,
movie_leader, movie_director)
VALUES (1, 'Bruce Almy', 5, 2003, 1, 2),
(2, 'Office Space', 5, 1999, 5, 6),
(3, 'Grand Canyon 2, 1991, 4, 3)"
$results = mysql_query($insert)

//ninsert data into 'movietype' table
$type="INSERT INTO movietype (movietype_id, movietype_label)
VALUES (1, 'Sci Fi')";
```