# Validating User Input

# Checking for Format Errors

Checking for errors in data or other formatted data is required in most systems because users
can't be guided in their input. You should always check for what is entered if you require a spe-
cific format or set of values.

At this point, we need the feared and powerful regular expressions. The regular expressions allow us to
define a pattern and check to see if it can be applied to our data. It's very useful to check for dates, social
security numbers, and any data that has to respect a predefined set of format requirements. (It helps to
be sure to always indicate the format in the source field).

# Try It Out Checking Dates and Numbers

First, we need to modify the database and a few pages slightly:

+   1. Open the well-known movie.php and modify it as follows (modifications are shown in bold):

```
<?php
$link = mysql_connect('localhost', 'root', '');
or die('Could not connect: ' . mysql_error());
$mysql_select_db('wiley2', $link) or die (mysql_error());
$peoplesql = "SELECT

FROM
people
**";
$result = mysql_query($peoplesql)
or die('Invalid query: ' . mysql_error());
while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
$people['movie_id'] ] = $row['movie_fullname'];
}
witch ($_GET['action']) {
case "edit":
$moviesql = "SELECT

FROM
WHERE
'movie_id` = ''.$_GET['id'].'.
*";
$result = mysql_query($moviesql)
or die('Invalid query: ' . mysql_error());
$row = mysql_fetch_array($result , MYSQL_ASSOC );
$row['name'] = $row['movie_name'];
$movie_type = $row['movie_type'];
$movie_year = $row['movie_year'];
$movie_release = $row['movie_release'];
$movie_leadactor = $row['movie_leadactor'];
$movie_director = $row['movie_director'];
$movie_rating = $row['movie_rating'];
break;
default:
$movie_name = "";

```

203