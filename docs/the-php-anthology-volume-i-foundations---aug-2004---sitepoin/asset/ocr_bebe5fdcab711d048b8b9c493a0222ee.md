```
/*
function getStartRow()
{
    return $this->startRow;
}
}
```

We can simply pass this class the relevant row information, along with the number of the page that's being viewed when we instantiate it. It will then tell us the total number of pages and the row number at which we should start our select query.

Here it is in action:

```
File: 3.php (excerpt)
// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Find out how many rows are available
$sql = "SELECT COUNT(*) AS num_rows FROM user";
$result = $db->query($sql);
$row = $result->fetch();

// Define the number of rows per page
$rowsPerPage = 10;

// Set a default page number
if (!isset($_GET['page'])) {
    $_GET['page'] = 1;
}

// Instantiate the pager
$pager = new SimplePager($rowsPerPage, $row['num_rows'],
    $_GET['page']);

// Build a table for the pager
echo "<table align=\"center\"/>\n<tr>\n";

// Build the HTML for the pager
for ($i = 1; $i <= $pager->getTotalPages(); $i++) {
    echo "<td><a href="" . $_SERVER['PHP_SELF'] . "?page=$i">";
    if ($i == $_GET['page']) {
        echo "<strong>$i</strong>";
    } else {
        echo $i;
    }
}
```