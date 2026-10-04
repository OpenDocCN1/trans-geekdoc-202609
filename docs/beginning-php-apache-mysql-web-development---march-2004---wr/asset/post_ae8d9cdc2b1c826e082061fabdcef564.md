
# Using Tables to Display Data

Then we simply echo the contents of $table. And finally, we close the PHP script using the ?>

By using these two tags, we can use raw HTML code (that is, HTML code that does not need any modification at all).

As you may recall from Chapter 2 in the discussion regarding heredoc, we can change the text 'EOD' to whatever we'd like, but the beginning and ending tags must match. For example, this will work fine:

```
$table <<<HAHAHA
code here
HAHAHA;
```

but this:

```
$table <<<HAHAHA
code here
BOOHOO;
```

it will not work. You will receive an error such as the one shown in Figure 4-2.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_135_0.png)

Figure 4-2

# Chapter 4

Note that there must be no spaces after the <<EOD and the EOD; In addition, there can be no leading space, indents, or any other characters on the closing tag (semicolons are permissible). If there is even one space, you'll receive an error. (You can potentially spend hours to fix an error as a result of having a single space after these tags!) Always remember to delete all spaces after these tags.

Now that you can create a table, let's fill it with some data from your movie review database. After all, that's what you're here for!

# Populating the Table

Looking at our empty skeleton of a table gives you the blueprint for how our data will be laid out once it is retrieved from the database.

| Try It Out | Filling the Table with Data |

As this is a large piece of code, we'll explain what's going on as we go through it. All changes are in bold. A few things are taken out from the original script (we'll see soon who has been paying attention).

- Open the table.php with your favorite text/HTML editor make the following changes to the existing code. We use the databases in Chapter 3 for the purposes of the example here.
- Remember to replace servername, username, password, and databasename with your values.

```php
$link = mysqli_connect("servername","username","password") or die(mysqli_error());
mysql_select_db("wiley") or die (mysqli_error());
```

- Start by making a connection to the database. (You have remembered to change the settings to reflect your own, haven't you? Good.)

```php
$query = "SELECT
movie_name,
movie_director,
movie_leadactor
FROM
movie";
$result = mysqli_query($query,$link) or die(mysqli_error());
$num_movies = mysqli_num_rows($result);
```

- Run a SQL query against the database and get the results. And while you are at it, count how many records were returned from the query.

As we discuss in Chapter 3, we've put the SQL words in capital letters. This is good practice, as it allows you to easily identify what words are field names and which ones are SQL keywords. It is also good practice to make your SQL query as easy to read as possible. That is why we have written the SQL query over several lines.

# Using Tables to Display Data

```php
$movie_header <<=EOD
h2<center>Movie Review Database</center>/h2
<table width='70%' border='1' cellpadding='2' cellspacing='2' align='center'>
<tr>
  <th align='left'>Movie Title</th>
  <th align='left'>Movie Director</th>
  <th align='left'>Movie Lead Actor</th>
</tr>
</table>
EOD;
```

- 4. Then enter the block of code that was originally there (minus the echo statement).

```php
Pay attention to the fact that it's called $movie_header, not $movie (as it was in the first example).
while($row = mysql_fetch_array($result)) {
  $movie_name = $row['movie_name'];
  $movie_director = $row['movie_director'];
  $movie_leadactor = $row['movie_leadactor'];

  $movie_details <<=EOD
<tr>
    <td>$movie_name</td>
    <td>$movie_director</td>
    <td>$movie_leadactor</td>
</tr>
EOD;
}
$movie_details .= <<=EOD
<tr>
  <td>&nbsp;</td>
</tr>
<tr>
  <td>Total: $num_movies Movies</td>
</tr>
EOD;
```

# How It Works

The preceding code does quite a lot of work for us, so let's look at it in more detail. As you know, the while statement loops through the records that have been returned. For each record, it executes the block of code between the brackets. Don't worry; PHP is smart enough to know how many records are and what record number is current in this case. There is no danger of having the wrong values assigned to the wrong record. The first line within the while loop tells the script to pull out the value of movie_name in the current record and put it into a variable called $movie_name. The next four lines do the same (well, almost the same—they simply assign field values to differently named variables).

# Chapter 4

Then come across the familiar tag that you saw at the beginning of this chapter. It's not quite the same as the one before this one has <<=EOD. So instead of just having record's values, $movie_details contains all of the record values that have been returned. Then we have included the total number of movies in our database. By adding .= in front of <<=EOD, you are adding the current value to the existing values. If you forget to add .= then you will get the last record's values. That's because $var = "1" makes $var become equal to the value of "1". In the preceding example, notice that we've assigned the name of the movie to the variable $movie_name and used $movie_name instead of doing the following:

```php
while($row = mysql_fetch_array($result)) {
  $movie_details <<=EOD
  <tr>
    <td>$row['movie_name']</td>
  </tr>
EOD;
}
```

The preceding snippet does exactly the same thing, but it would limit you if you wanted to do any formatting on the variable' values (you'll see why a bit later).

# Try It Out

The data has been retrieved, but we need to send all to the browser so it will display in the table.

- 1. We assign the $movie_footer variable by entering the following:
```php
$movie_footer = "<<table";
$movie .= $movie_header$movie_details$movie_footer;
print "There are $num_movies movies in our database";
print $movie;
?>
```
2. Save this file as table2.php and upload it to your Web server.
3. Load that page into your Web browser.
You should see something similar to the screen shown in Figure 4-3.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_139_0.png)

Figure 4-3

# Try It Out

# Improving Our Table

The table may look pretty, but as in Chapter 3, it doesn't do us much good if we don't have our secret decoder ring to decipher what actors and directors were associated with our movies. You need to link your tables to pull this information.

- 1. Modify table2.php file as shown in bold text:

```php
$link = mysqli_connect("localhost","root","$mysqlpass") or die(mysqli_error());
mysql_select_db("wiley") or die(mysqli_error());

$query = "SELECT
movie_name,
movie_director,
movie_leadactor
FROM";
```

```php
movie";

$result = mysqli_query($query, $link) or die(mysqli_error());
$num_movies = mysqli_num_rows($result);
```

```php
$movie_header <<=EOD
<h2><center>Movie Review Database</center></h2>
<table width='70%' border='1' 
cellpadding='2' align='center'>
<tr>
<th>Movie Title</th>
<th>Movie Director</th>
<th>Movie Lead Actor</th>
</tr>
</table>
EOD;
```

```php
function get_director() {
    global $movie_director;
    global $director;

    $query_d = "SELECT people_fullname
FROM people
WHERE people_id='$movie_director'; 
$results_d = mysqli_query($query_d) or die(mysqli_error());
    $row_d = mysql_fetch_array($results_d);
    extract($row_d);
    $director = $people_fullname;
}

function get_leadactor() {
    global $movie_leadactor;
    global $leadactor;

    $query_a = "SELECT people_fullname
FROM people
WHERE people_id='$movie_leadactor";
$results_a = mysqli_query($query_a) or die(mysqli_error());
    $row_a = mysql_fetch_array($results_a);
    extract($row_a);
    $leadactor = $people_fullname;
}
```

```php
while($row = mysql_fetch_array($result))
{
  $movie_name = $row['movie_name'];
  $movie_director = $row['movie_director'];
  $movie_leadactor = $row['movie_leadactor'];

  $movie_details <<=EOD
<tr>
    <td>$movie_name</td>
    <td>$movie_director</td>
    <td>$leadactor</td>
</tr>
EOD;
}
$movie_details .= <<=EOD
<tr>
  <td>&nbsp;</td>
</tr>
<tr>
  <td>Total: $num_movies Movies</td>
</tr>
EOD;
```
