
Also, I would strongly recommend that you use the same name for your form inputs as the corresponding column in the database where that value will be stored. Further, you should set the maximum input length in the form equal to the maximum column length in the database. Both of these habits help to minimize errors.

**13.** Complete the HTML form:

```html
<p>Email Address: <input type="text" name="email" size="20" maxlength="60" value="<?php if (isset($_POST['email'])) echo $_POST['email']; ?>" /> </p>

<p>Password: <input type="password" name="pass1" size="10" maxlength="20" value="<?php if (isset($_POST['pass1'])) echo $_POST['pass1']; ?>" /></p>

<p>Confirm Password: <input type="password" name="pass2" size="10" maxlength="20" value="<?php if (isset($_POST['pass2'])) echo $_POST['pass2']; ?>" /></p>

<p><input type="submit" name="submit" value="Register" /></p>

</form>
```

This is all much like that in Step 12, with the addition of a submit button.

As a side note, I don’t need to follow my `maxlength` recommendation (from Step 12) with the password inputs, because they will be encrypted with `SHA1()`, which always creates a string 40 characters long. And since there are two of them, they can’t both use the same name as the column in the database.

**14.** Complete the template:

```php
<?php include ('includes/footer.html'); ?>
```

**15.** Save the file as `register.php`, place it in your Web directory, and test it in your Web browser.

Note that if you use an apostrophe in one of the form values, it will likely break the query ![Image](graphics/circle-e.jpg). The section “[Ensuring Secure SQL](#ch09.html#ch09lev1sec5)” later in this chapter will show how to protect against this.

![Image](graphics/09_figure_11_e.jpg)

![Image](graphics/circle-e.jpg)Apostrophes in form values (like the last name here) will conflict with the apostrophes used to delineate values in the query.

***

Tip

After running the script, you can always ensure that it worked by using the mysql client or phpMyAdmin to view the records in the *users* table.

***

Tip

You should not end your queries with a semicolon in PHP, as you do when using the mysql client. When working with MySQL, this is a common, albeit harmless, mistake to make. When working with other database applications (Oracle, for one), doing so will make your queries unusable.

***

Tip

As a reminder, the `mysqli_query()` function returns a TRUE value if the query could be executed on the database without error. This does not necessarily mean that the result of the query is what you were expecting. Later scripts will demonstrate how to more accurately gauge the success of a query.

***

Tip

You are not obligated to create a `$q` variable as I tend to do (you could directly insert your query text into `mysqli_query()`). However, as the construction of your queries becomes more complex, using a variable will be the only option.

***

Tip

Practically any query you would run in the mysql client can also be executed using `mysqli_query()`.

***

Tip

Another benefit of the Improved MySQL Extension over the standard extension is that the `mysqli_multi_query()` function lets you execute multiple queries at one time. The syntax for doing so, particularly if the queries return results, is a bit more complicated, so see the PHP manual if you have this need.

### Retrieving Query Results

The preceding section of this chapter demonstrates how to execute simple queries on a MySQL database. A *simple query*, as I’m calling it, could be defined as one that begins with `INSERT`, `UPDATE`, `DELETE`, or `ALTER`. What all four of these have in common is that they return no data, just an indication of their success. Conversely, a `SELECT` query generates information (i.e., it will return rows of records) that has to be handled by other PHP functions.

The primary tool for handling `SELECT` query results is `mysqli_fetch_array()`, which uses the query result variable (that I’ve been calling `$r`) and returns one row of data at a time, in an array format. You’ll want to use this function within a loop that will continue to access every returned row as long as there are more to be read. The basic construction for reading every record from a query is

```php
while ($row = mysqli_fetch_array($r))
{

    // Do something with $row.

}
```

*You will almost always want to use a* `while` loop to fetch the results from a `SELECT` query.

The `mysqli_fetch_array()` function takes an optional second parameter specifying what type of array is returned: associative, indexed, or both. An associative array allows you to refer to column values by name, whereas an indexed array requires you to use only numbers (starting at 0 for the first column returned). Each parameter is defined by a constant listed in **[Table 9.1](#ch09.html#ch09table01)**, with `MYSQLI_BOTH` being the default. The `MYSQLI_NUM` setting is marginally faster (and uses less memory) than the other options. Conversely, `MYSQLI_ASSOC` is more overt (`$row['column']` rather than `$row[3]`) and may continue to work even if the query changes.

**Table 9.1. mysqli_fetch_array() Constants**

![Image](graphics/09tab01.jpg)

An optional step you can take when using `mysqli_fetch_array()` would be to free up the query result resources once you are done using them:

```php
mysqli_free_result ($r);
```

This line removes the overhead (memory) taken by `$r`. It’s an optional step, since PHP will automatically free up the resources at the end of a script, but—like using `mysqli_close()`—it does make for good programming form.

To demonstrate how to handle results returned by a query, let’s create a script for viewing all of the currently registered users.

#### To retrieve query results

**1.** Begin a new PHP document in your text editor or IDE, to be named `view_users.php` (**[Script 9.4](#ch09.html#ch09ex04)**):

```php
<?php # Script 9.4 - view_users.php

$page_title = 'View the Current Users';

include ('includes/header.html');

echo '<h1>Registered Users</h1>';
```

**2.** Connect to and query the database:

```php
require ('../mysqli_connect.php');

$q = "SELECT CONCAT(last_name, ', ', first_name) AS name, DATE_FORMAT(registration_date, '%M %d, %Y') AS dr FROM users ORDER BY registration_date ASC";

$r = @mysqli_query ($dbc, $q);
```

The query here will return two columns ![Image](graphics/circle-a.jpg): the users’ names (formatted as *Last Name, First Name*) and the date they registered (formatted as *Month DD, YYYY*). Because both columns are formatted using MySQL functions, aliases are given to the returned results (*name* and *dr*, accordingly). See [Chapter 5](#ch05.html#ch05) if you are confused by any of this syntax.

![Image](graphics/09_figure_12_a.jpg)

![Image](graphics/circle-a.jpg)The query results as run within the mysql client.

**3.** Create an HTML table for displaying the query results:

```php
if ($r) {
    echo '<table align="center" cellspacing="3" cellpadding="3"
    width="75%">
    <tr><td align="left"><b>Name</b></td><td align="left"><b>Date Registered</b></td></tr>
    ';
```

If the `$r` variable has a TRUE value, then the query ran without error and the results can be displayed. To do that, start by making a table and a header row in HTML.

**4.** Fetch and print each returned record:

```php
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
    echo '<tr><td align="left">' . $row['name'] . '</td><td align="left">' . $row['dr'] . '</td></tr>
    ';
}
```
