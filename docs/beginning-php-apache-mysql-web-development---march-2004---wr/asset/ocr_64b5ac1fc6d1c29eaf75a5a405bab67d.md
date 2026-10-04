# Building Databases

+   - Powers (multiple select field)
- Lair address, city, state, and ZIP
- Alignment (radio button: good/evil, default good)
- Enemies (multiple select field)

We need a form for adding/deleting powers. This form will be relatively simple and will contain the following elements:

+   - Checkbox list of every power currently available
- Delete Selected button
- A text field to enter a new power
- An Add Power button

We also need a PHP script that can handle database inserts, deletes, and so on. It simply requires a job and redirects the user on another page. We call this transaction page, and this page handles all transactions for the character application (with redirect), including the following:

+   - Inserting a new character (character listing page)
- Editing an existing character (character listing page)
- Deleting a character (character listing page)
- Adding a new power (power editor page)
- Deleting a power (power editor page)

That's basically all there is to the application. Four pages (if you count the config.php file you created earlier—it be used again) shouldn't be too difficult. Let's write them first, and then we'll tell you how they work.

# Try It Out The Comic Book Character Site

Some of these files are a bit long. Don't scare you. Most of the code consists of SQL statements, and we explain them clearly for you in the "How It Works" section that follows. Remember that this code can also be downloaded from the Web site (www.wrox.com).

Let's start with a short one.

+   1. Enter the code in your favorite PHP editor, and save it as poweredit.php:

```
<?php
require('config.php');

$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die('Could not connect to MySQL database. ' . mysql_error());
mysql_select_db(SQL_DB, $conn);

$sql = "SELECT id, power FROM char_power ORDER BY power";
```

253