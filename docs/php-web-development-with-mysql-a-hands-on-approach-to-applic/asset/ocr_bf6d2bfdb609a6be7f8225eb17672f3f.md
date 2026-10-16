# 15. DISPLAYING A LIST OF ITEM DETAILS

This query should only return one row, and we should ensure that it always does or show no movie details if it does not. Calling the function mysqli_num_rows() on the result gives us the number of rows returned from the query.

Add the following (Listing 15.13) if and else condition clause below the mysqli_query() function, and output another no movie details within an <h3> tag set after the inner else clause before the endif:

# Listing 15.13.

```
$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movieListing', E_USER_ERROR);

    if (mysqli_num_rows($result) == 1):
    else:
    ?>
<h3>No Movie Details :-</h3>
<?php
    endif;
    else:
?>
<h3>No Movie Details :-</h3>
<?php
    endif;
?>
```

If we do get one row back from our query, we can display a table containing the movie listing details. Add the code in Listing 15.14 below the statement:
if (mysqli_num_rows($result) == 1):

# Listing 15.14.

```
<?php
...
    if (mysqli_num_rows($result) == 1):

        $row = mysqli_fetch_assoc($result)
?>
<h1><?= $row['title'] ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $row['rating'] ?></td>
        </tr>
        <tr>
```