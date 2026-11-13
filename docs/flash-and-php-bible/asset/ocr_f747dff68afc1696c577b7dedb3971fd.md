# Connecting the PHP

The PHP code starts by connecting to the newly created database using the techniques learned in the previous section.

```
<?php

$link = mysql_connect("localhost", "username", "password");
mysql_select_db("music", $link);
```

When a connection is established, you can create the query that handles the loading of the album data. First, create the genre to look for by setting a static variable. In a more complete application, this variable would most likely be passed via URL or some other form of a call.

```
$genreID = 4;
```

```
$query = "SELECT g.name, a.artist, a.albumName";
$query .= " FROM albums a, genre g";
$query .= " WHERE a.genreID=g.id";
$query .= " AND g.id = . $genreID";
```

A call to mysql_query() is made, which is responsible for executing the previous SQL query. This function will return a resource id to be used in the remainder of the SQL calls.

```
$result = mysql_query($query);
```

This loaded album data will be stored in a name/value string for simplicity but a more real-world example would most likely use XML or another form of structured data.

```
$response = "resp=loaded\n";
```

XML data usage is explained in Chapter 3. This includes the loading and saving of XML while working with PHP/MySQL data objects.

At this point, the connection to MySQL and the call should be created, but you still can't test the code because nothing is outputted. The next section explains the outputting of the data using a common while loop to traverse the data returned from the tables in the music database.

The data will be returned in a basic list format, but there needs to be a way to differentiate the data. This is done by creating a unique id on each instance of the result and assigning it to the value name.

```
$index = 0;
```

The next part is the meat of the application, which is the while loop.

```
while($row = mysql_fetch_array($result))
{
...
}
```