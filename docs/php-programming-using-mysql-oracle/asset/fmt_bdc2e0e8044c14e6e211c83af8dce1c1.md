
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```
[/content]

Wait need actual content. Let's produce proper output.

[content]
The PHP file has a form at the end of it that will allow one to enter values for each of the field in the table. The `isset` function is used to check if the submit button is hit and if so the values entered into the form will be inserted into the database. One can write a friendly message after the `mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );` line.

It is very important to watch out for quotation errors in the insert line. The result of entry of data can be observed by browsing the table using `PHPMyadmin`.

The following is an example of a PHPMyadmin browse search for the above code.

![](images/00056.jpeg)

### Update method

To demonstrate the update method in PHP code for MySQL let us keep in mind that in the Staff table the `sid` is the prime key.

Thus the next code allows for all other fields to be updatable. The code is as follows:

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "update staff set name='{$_POST['name']}', job='{$_POST['job']}',salary='{$_POST['salary']}',location='{$_POST['location']}' where sid='{$_POST['sid']}'";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Table is updated.";}mysql_close( $link_id ); }?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

In the above code the form part is the same as in the case of the insert code. The change is in the query and the format used to set the update fields. The primary key is `sid`.

A new function `mysql_affected_rows()` is used here and this is used when update /delete is to be done in PHP. The result can be observed by browsing the table in PHPMyadmin as follows:

![](images/00057.jpeg)

# Delete data

Last but not the least the code for deleting data from a database is as follows:

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "delete from staff where sid='{$_POST['sid']}' limit 1";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Row has been deleted.";}mysql_close( $link_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

In the above code for deleting a row from the table the query ends with the words `LIMIT 1`. This makes sure only one row at most is removed.

Delete and update functions are to be used carefully in databases. Generally, this function is limited to certain roles. However, on internet websites users will need to update or delete their info.

The `mysql_affected_rows()` function is used with the delete code. There is a lot of similarity between the code for update and delete.

The result of the deletion can be observed through PHPMyadmin as follows:

![](images/00058.jpeg)

The row that was deleted in the above was the one that was entered in the insert code with `sid=107`.

The above code for delete can be modified to truncate the table leaving the structure but no data in the table. The code lines that will make this happen is as follows:

```
$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());
mysql_select_db( "thottungal", $link_id );
$sql = "truncate table staff";
```

One could modify the code lines above to drop the table also.

However, both truncate and drop are functions reserved for the administrator of the database and therefore in real situations unless specific permissions have been given the programmer might not be able to execute code to do these functions.

## Version 7 PHP

Version 7 of PHP is a major release in PHP and one of the areas that has been affected by new functions is in the way to deal with MySQL. The new functions are termed as `mysqli` where `i` stands for improvement. The good news is that for those who are familiar with the previous ways of connecting to MySQL, can easily migrate to the new functions because there is similarity in the way the connection will be made.

`mysqli_connect()` replaces `mysql_connect()`

`mysqli_query()` replaces `mysql_query()`

`mysqli_fetch_array()` replaces `mysql_fetch_array()`

In short instead of `mysql_` the new functions start as `mysqli_`. Let us look at an example of selecting data from the staff data using the new mysqli functions in PHP 7.

```
<html><body><?php$link_id = mysqli_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli_connect_error());$sql = "SELECT * FROM staff";$result_id = mysqli_query( $link_id, $sql ) or die ( "Statement failed: " . mysqli_error($sql) );$x=mysqli_num_rows($result_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysqli_fetch_array( $result_id ) ) {print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";}mysqli_free_result($result_id);mysqli_close( $link_id );print "</table>";?></body></html>
```

The flow of logic is the same as in the previous version 5. `$link_id` makes connection to the database. The difference here is that there are four elements to be entered within `mysqli_connect` brackets. The last one is the name of the database. The remaining entries holds true for local install for development purposes and will be slightly different on the hosting site. This values need to be obtained from the technical support of shared hosting site if that is where the website is located.

After giving the query to `$sql` the number of rows obtained from the array created by `mysqli_fetch_array` is printed. The array is then printed out as shown in the code above. The program is closed by freeing the query from memory and then closing the connection. The function `mysqli_fetch_array` can handle arrays with string or number keywords.

Thus the version in PHP 5 and 7 are very much similar except in the areas mentioned in the two paragraphs above. Now let us try to insert a row into the database. The same code from version 5 will be modified below to fit version 7.
