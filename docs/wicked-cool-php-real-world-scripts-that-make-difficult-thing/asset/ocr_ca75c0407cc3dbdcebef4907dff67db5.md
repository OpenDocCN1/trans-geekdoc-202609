Finally, regardless of whether or not the user has previously voted, we send the user to the poll results:

```
/* Redirect to poll results. */
header("Location: vote_tally.php?poll=$poll");
?>
```

Let's look at the results now.

# Getting Poll Results

Of course, everyone voting in a poll wants to know the results. We’ll use some cheap HTML tricks to display the results as in Figure 12-2.

![](bbox=[0.57, 0.21, 0.89, 0.35])

Figure 12-2: Poll results

The vote_tally.php script starts much like our other two, by loading the database configuration and checking for a valid poll ID in the poll parameter:

```
<?php
/* Display the results of a poll. */
require_once("vote_config.php");

$poll = $_REQUEST['poll'];
if (!is_numeric($poll)) {
    die("Invalid poll");
}
```

When checking for a valid poll ID, we may as well look up the poll question at the same time, because we eventually want to display this information:

```
/* Look up the question. */
$sql = "SELECT question
        FROM poll
        WHERE ID = $poll";
$result = @mysql_query($sql, $db) or die ("mysql error: " . mysql_error());
if (mysql_num_rows($result) != 1) {
    die('Invalid poll.');
}
$row = mysql_fetch_array($result);
$question = $row["question"];
```

Let's find out the total number of votes in order to give some percentages on the individual choices later on:

```
$query = "SELECT count(*) AS num_total_votes
FROM vote V
```