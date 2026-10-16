
## Creating the Main Movie Listing Page

So, a better query of the above code would look like this:

```
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

When a user clicks a link to a specific movie title, we want to send the primary key for that row in the movieListing table as a query parameter to the moviedetails.php page. Therefore, we want to send $row['id'] as the query parameter.

In index.php, replace the code in Listing 15.7

```
<?php
while($row = mysqli_fetch_assoc($result)):
?>
<tr>
<td><?=$row['title']?></td>
</tr>
<?php
endwhile;
?>
```

with:

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

Listing 15.8 shows what the code should look like now within the <body> tags of the index.php file.

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

## 15. DISPLAYING A LIST OF ITEM DETAILS

Listing 15.8.

```
1. <body>
2.   //...
3.   <h1>Movies I Like</h1>
4. 
5.   <?php
6.     require_once('dbconnection.php');
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.       or trigger_error(
10.      'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
11.      );
12. 
13.     $query = "SELECT id, title FROM movielisting ORDER BY title";
14. 
15.     $result = mysqli_query($dbc, $query)
16.       or trigger_error('Error querying database movielisting', E_USER_ERROR);
17. 
18.     if (mysqli_num_rows($result) > 0):
19. ?>
20.     <table class="table table-striped">
21.       <thead>
22.         <tr>
23.           <th scope="col">Movie Title</th>
24.         </tr>
25.       </thead>
26.       <tbody>
27. <?php
28.     while($row = mysqli_fetch_assoc($result))
29.     {
30.       echo "<tr><td>" .
31.         "<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
32.     }
33. ?>
34.       </tbody>
35.     </table>
36. <?php
37.     else:
38. ?>
39. <h3>No Movies Found :-(</h3>
40. <?php
41.     endif;
42. ?>
43.   // ...
44. </body>
```

Figure 15.14 shows what our main movie listings page looks like now.

## Creating the Movie Details Page

Now we create a `moviedetails.php` page that displays the details of the movie we selected from the Movie Listings page.

## Laying Out the Details Page

Using the Bootstrap CSS framework and a striped table, Figure 15.15 displays what we want our movie details to look like.

## Scripting the Details Page

Create another PHP script and call it `moviedetails.php`. Again, we will start with a simple boilerplate that includes the necessary Bootstrap framework components and call the page title: “Movie Details”. We also add a couple of nested `<div>` tags right below our opening `<body>` tag to display our movies in What Bootstrap calls a “card” (Listing 15.9).

Listing 15.9.

```
<html>
<head>
  <link rel="stylesheet"
        href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
        integrity="sha384-GJzZqFGwb1QTTN6wy59ff1BuGJPjLSa9dKkMpo8giM4m1Yj7gZgWKYBI7O6tWS"
        crossorigin="anonymous">
  <title>Movie Details</title>
</head>
<body>
<div class="card">
  <div class="card-body">
  </div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK+1JSTQIAgVvRZvpzbo5smXKp4YfRVH+8abtTE1Pj6jizo"
        crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
        integrity="sha384-wHafrFfR..."
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
        integrity="sha384-B0UglyR+jN..."
        crossorigin="anonymous"></script>
</body>
</html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_1.png)

## 15. DISPLAYING A LIST OF ITEM DETAILS

Now within the innermost <div> tag, add a nav link back to the main Movie Listings page “Movies I Like” as in Listing 15.10.

### Listing 15.10.

```
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.       <nav class="nav">
5.         <a class="nav-link" href="index.php">Movies I Like</a>
6.       </nav>
7.     </div>
8. </div>
```
```

We only want to display the details of the selected movie if the user navigated from one of the movie title links instead of just typing moviedetails.php into the URL navigation bar (Figure 15.16).

Figure 15.17 shows the incorrect navigation from Movie Listing to Movie Details.

If a user does incorrectly navigate by typing moviedetails.php into the URL navigation bar, we want to display Figure 15.18.

Therefore, we need to add an if condition that checks that we received and set the query parameter.

Before we do that, an understanding of the $_GET[] super global variable is needed.

## Super Global $_GET

Similar to a $_POST[], $_GET[] is a superglobal array variable that holds either form data when sent from a form or query parameters embedded as data in a URL.

When sending a GET request from a form, the data is automatically sent and accessed using the name attributes as indexed keys into the array.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_2.png)

## Creating the Movie Details Page

When embedded as query parameters in a URL, the data is built as key-value pairs as part of the URL. Each value in the array is indexed using the key as mentioned earlier. See Figure 15.19.

Add the PHP conditional block from Listing 15.11 below the navigation link we just added.

### Listing 15.11.

```
```php
1. <nav class="nav">
2. <a class="nav-link" href="index.php">Movies I Like</a>
3. </nav>
4. <?php
5.     if (isset($_GET['id'])):
6. 
7.     else:
8. ?>
9. <h3>No Movie Details :-</h3>
10. <?php
11. endif;
12. ?>
```
```

We only want to display the movie listing details if a user navigated to this page due to selecting a movie listing link from the main page. Therefore, we will put our code that gets and displays the movie listing details in between the if and else statements.

In between the if and else clauses, let's add code to get all the fields from the movielisting table WHERE the id field equals the value specified by $_GET['id']. We need all the usual boilerplate code to connect and query the database as in Listing 15.12.

### Listing 15.12.

```
```php
1. <?php
2. if (isset($_GET['id'])):
3. 
4.     require_once('dbconnection.php');
5. 
6.     $id = $_GET['id'];
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.         or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);
10. 
11.     $query = "SELECT * FROM movielisting WHERE id = $id";
12. 
13.     $result = mysqli_query($dbc, $query)
14.         or trigger_error('Error querying database movielisting', E_USER_ERROR);
15. else:
16. ?>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_171_0.png)

## 15. DISPLAYING A LIST OF ITEM DETAILS

This query should only return one row, and we should ensure that it always does or show no movie details if it does not. Calling the function mysqli_num_rows() on the result gives us the number of rows returned from the query.

Add the following (Listing 15.13) if and else condition clause below the mysqli_query() function, and output another no movie details within an <h3> tag set after the inner else clause before the endif:

### Listing 15.13.

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

### Listing 15.14.

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
