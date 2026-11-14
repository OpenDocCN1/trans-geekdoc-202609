# 4. Include the header file and display a page header:

```
$page_title = 'PDFs';
include ('./includes/header.html');
echo '<h3>PDF Guides</h3>';
```

# 5. Print a message if the user is not active:

```
if (isset($_SESSION['user_id']) && !isset($_SESSION['user_not_expired'])) {
    echo '<p class="error">Thank you for your interest in this content.
    Unfortunately your account has expired. Please <a href="renew.php">renew your account</a> in order to view any of the PDFs listed below.</p>';
} elseif (isset($_SESSION['user_id'])) {
    echo '<p class="error">Thank you for your interest in this content.
    You must be logged in as a registered user to view any of the PDFs listed below.</p>';
}
```

The messages differ slightly from those in category.php, but the checks on
the user's status are the same.

# 6. Get the PDFs:

```
$q = 'SELECT tmp_name, title, description, size FROM pdfs ORDER BY date_created DESC';
$r = mysqli_query($dbc, $q);
if (mysqli_num_rows($r) > 0) {
```

The query returns the temporary name, title, and description for each PDF
in the database, in order from newest to oldest.

# 7. Fetch and display every PDF:

```
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
    echo "<div><h2><a href=\"view_pdf.php?id={$row['tmp_name']}">{$row['title']}</a> ({$row['size']}kb)</h2><p>{$row['description']}</p></div>\n";
} // End of WHILE loop.
```

Each record is displayed as its own <DIV>, with the title as a linked <H4>,
followed by the size of the file. The file's description comes next. Each
link points to view_pdf.php, passing along the temporary name—the
40-character hash—in the URL.

# 8. Complete the page: