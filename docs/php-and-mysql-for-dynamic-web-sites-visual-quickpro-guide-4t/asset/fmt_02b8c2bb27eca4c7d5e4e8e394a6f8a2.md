
```php
30  // Fetch and print all the records:
31  while ($row = $r->fetch_object()) {
32      echo '<tr><td align="left">' .
             $row->name . '</td><td align="left">' . $row->dr . '</td></tr>';
33  }
34
35  echo '</table>'; // Close the table.
36
37  $r->free(); // Free up the resources.
38  unset($r);
39
40  } else { // If no records were returned.
41
42      echo '<p class="error">There are currently no registered users.</p>';
43
44  }
45
46  // Close the database connection.
47  $mysqli->close();
48  unset($mysqli);
49
50  include('includes/footer.html');
51  ?>
```

---

**6.** Within the `while` loop, change how each column’s value is printed:

```php
echo '<tr><td align="left">' . $row->name . '</td><td align="left">' . $row->dr . '</td></tr>';
```

Since the `$row` variable is now an object, object notation, instead of array notation, must be used to refer to the columns in each row: `$row->name` and `$row->dr` instead of `$row['name']` and `$row['dr']`.

**7.** Change how the resources are freed:

```php
$r->free();
unset($r);
```

To free the memory taken by the returned results, call the `MySQLi_Result` object’s `free()` method. Furthermore, since that object won’t be used anymore in the script, it can be unset.

**8.** Update how the database connection is closed:

```php
$mysqli->close();
unset($mysqli);
```

**9.** Save the script, place it in your Web directory, and test it in your Web browser.

The object-oriented version of `view_users.php` (Script 16.3) looks the same as the original procedural version.

> **Tip**
>
> The real benefit of using the `fetch_object()` method is that you can have the results fetched as a *particular type of object*. For example, say you have defined a `Car` class in PHP and a script fetches all of the stored information about cars from the database. In the PHP script, each record can be fetched as an object of `Car` class type. By doing so, you’ll have created a PHP `Car` object, whose data is populated from the database record, but can still invoke the methods of the `Car` class.

---

#### Prepared Statements

Chapter 13 introduced another way of executing queries: using *prepared statements*. Prepared statements can offer improved security, and possibly even better performance, over the standard approach to running queries. Naturally, you can execute prepared statements using the MySQL Improved extension as objects. The steps are the same: after creating a `MySQLi` object (and therefore a connection to the database), you

*   Prepare the query
*   Bind the parameters
*   Execute the query

In actual code that looks like:

```php
$q = 'INSERT INTO tablename (this, that) VALUES (?, ?)';
$stmt = $mysqli->prepare($q);
$stmt->bind_param('si', $this, $that);
$this = 'Larry';
$that = 234;
$stmt->execute();
```

The `MySQLi::prepare()` method returns an object of type `MySQLi_STMT`. That object has a few key properties:

*   `affected_rows` stores how many rows were affected by the statement, normally applicable to `INSERT`, `UPDATE`, and `DELETE` queries.
*   `num_rows` reflects the number of records in the result set for a `SELECT` query.
*   `insert_id` stores the automatically generated ID value for the previous `INSERT` query.
*   `error` represents any error that might have occurred.

Once you’re done executing the prepared statement, you should close the statement:

```php
$stmt->close();
```

Let’s apply this information by updating `post_message.php` (Script 13.6). This is a stand-alone script that uses the *forum* database and isn’t, in Chapter 13 or this chapter, tied to any other scripts.

#### To execute prepared statements

**1.** Open `post_message.php` (Script 13.6) in your text editor or IDE.

**2.** Change the creation of the database connection to (Script 16.4):

```php
$mysqli = new MySQLi('localhost', 'username', 'password', 'forum');
$mysqli->set_charset('utf8');
```

The previous version of the script did not use a separate connection script, and neither will this one. Make sure your values are correct for connecting to the *forum* database on your server.

**3.** Alter the preparation of the query to read (line 21 of the original script):

```php
$stmt = $mysqli->prepare($q);
```

The `MySQLi::prepare()` method prepares a statement, taking the query as its lone argument. It returns an object of type `MySQLi_STMT`, assigned to `$stmt` here.

**4.** Change the binding of parameters to:

```php
$stmt->bind_param('iiiss', $forum_id, $parent_id, $user_id, $subject, $body);
```

This code change is simply from `mysqli_stmt_bind_param($stmt...` to `$stmt->bind_param(...`. The method’s first argument is an indicator of the data types to follow. The subsequent arguments are the PHP variables to which the query’s placeholders are bound.

**5.** Update the execution of the statement to:

```php
$stmt->execute();
```

**Script 16.4.** In this version of a script from Chapter 13, the `MySQLi_STMT` class is used to execute a prepared statement.

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
2       1.0 Transitional//EN" "http://www.w3.org/
3       TR/xhtml1/DTD/xhtml1-transitional.dtd">
4   <html xmlns="http://www.w3.org/1999/
5       xhtml" xml:lang="en" lang="en">
6   <head>
7       <meta http-equiv="Content-Type"
8           content="text/html; charset=utf-8" />
9       <title>Post a Message</title>
10  </head>
11  <body>
12  <?php # Script 16.4 - post_message.php
13  // This is an OOP version of the script
14      from Chapter 13.
15
16  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
17
18      // Validate the data (omitted)!
19
20      // Connect to the database:
21      $mysqli = new MySQLi('localhost',
22          'username', 'password', 'forum');
23      $mysqli->set_charset('utf8');
24
25      // Make the query:
26      $q = 'INSERT INTO messages (forum_id,
27          parent_id, user_id, subject, body,
28          date_entered) VALUES (?, ?, ?, ?, ?,
29          NOW())';
30
31      // Prepare the statement:
32      $stmt = $mysqli->prepare($q);
33
34      // Bind the variables:
35      $stmt->bind_param('iiiss',
36          $forum_id, $parent_id, $user_id,
37          $subject, $body);
38
39      // Assign the values to variables:
40      $forum_id = (int) $_POST['forum_id'];
41      $parent_id = (int) $_POST['parent_id'];
42      $user_id = 3; // The user_id value
43          would normally come from the session.
44      $subject = strip_tags($_POST
45          ['subject']);
46      $body = strip_tags($_POST['body']);
47
48      // Execute the query:
49      $stmt->execute();
50
51      // Print a message based upon the
52          result:
53      if ($stmt->affected_rows == 1) {
54          echo '<p>Your message has been
55              posted.</p>';
56      } else {
57          echo '<p style="font-weight: bold;
58              color: #C00">Your message could
59              not be posted.</p>';
60          echo '<p>' . $stmt->error . '</p>';
61      }
62
63      // Close the statement:
64      $stmt->close();
65      unset($stmt);
66
67      // Close the connection:
68      $mysqli->close();
69      unset($mysqli);
70
71  } // End of submission IF.
72
73  // Display the form:
74  ?>
75  <form action="post_message.php"
76      method="post">
77
78      <fieldset><legend>Post a message:
79          </legend>
80
81      <p><b>Subject</b>: <input
```
