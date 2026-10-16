
## 25. ADDING RESERVATION FEATURES

Line 35 (`elseif (isset($_POST['reserve_movies'])):`) is the condition to check if the user reserved the movies in their cart. This condition is where we delete the shopping cart and redirect the user back to the home page.

Line 39 (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`) is the condition to check that the user's shopping cart has movies in it. This condition is where we display a list of the movies in the user's cart with the ability to delete each movie. Displayed will also be a form with a button for reserving the movies in the cart.

Line 43 (`else:`) is a “catch-all” condition indicating there are no movies in the user's cart, so line 43 will display that there are no movies in the cart.

The rest of the code is the standard Bootstrap boilerplate script inclusions.

### Add Form for Reserving Movies

Let's add the following code for the shopping cart and the form for reserving the movies into the condition (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`). I will explain the code in Listing 25.38 below.

### Listing 25.38

```php
1. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
2.
3.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.         or trigger_error(
5.             'Error connecting to MySQL server for ' . DB_NAME,
6.             E_USER_ERROR
7.         );
8.
9.     $user_id = $_SESSION['user_id'];
10.
11.     $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
12.               FROM movielisting
13.               INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
14.               WHERE reservation.user_id = ?";
15.
16.     $result = parameterizedQuery($dbc, $query, 'i', $user_id);
17.
18.     if (mysqli_errno($dbc))
19.     {
20.         trigger_error('Error querying database movielisting', E_USER_ERROR);
21.     }
22.
23.     if (mysqli_num_rows($result) > 0):
24. ?>
```

### Add a Script for a Shopping Cart

```html
<table class="table table-striped table-hover">
    <thead>
        <tr>
            <th scope="col"><h4>Movies to Reserve</h4></th>
            <th scope="col"></th>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
    <?php

    while ($row = mysqli_fetch_assoc($result))
    {
        // Only display what's in the shopping cart
        if (array_search($row['id'], $_SESSION['cart']) !== false)
        {
            $movie_image_file = $row['image_file'];

            if (empty($movie_image_file))
            {
                $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
            }

            $movie_title_row = "<tr><td><img src=\"" . $movie_image_file . "\" class='img-thumbnail'"
                . "style='max-height: 75px;' alt='Movie image'></td>"
                . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
                . $row['id'] . "'>" . $row['title'] . "</a></td>"
                . "<td class='align-middle'><form method='POST' action='"
                . $_SERVER['PHP_SELF'] . "'><button class='btn btn-danger' type='submit' "
                . "name='id_to_delete' value='" . $row['id'] . "'>"
                . "<i class='far fa-trash-alt'></i></button></form></td>";

            $movie_title_row .= "</tr>";

            echo $movie_title_row;
        }
    }
    ?>
    </tbody>
</table>
<form method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
    <button class="btn btn-success" type="submit" name="reserve_movies">Reserve Movies</button>
</form>
<?php
else:
?>
<h3>No Movies in your cart :-(</h3>
<?php
endif;
else:
```

## 25. ADDING RESERVATION FEATURES

After connecting to the movielisting database in line 3, we create an INNER JOIN query of the movielisting and reservation tables on lines 11–14 that returns the id, title, and image_file for each movie the user has reserved.

Assuming the query returns at least one movie (line 23), lines 25–65 display a table containing all the movies in the user's cart. Because the query returns all the movies from the reservation table, we need to keep only the ones in the cart. This distinction is important because the user might already have movies on reserve, which we display elsewhere.

Let’s take a closer look at lines 36–62. Line 36 iterates through each reservation for the user. However, line 39 (`if (array_search($row['id'], $_SESSION['cart']) !== false)`) only allows the display of reservation rows that are also contained in the user’s shopping cart, which are handled by lines 41–60.

On lines 48–51, we display the image and the title of the movie that links back to the `moviedetails.php` script with the movie ID as a query parameter:

```php
$movie_title_row = "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
    . "style='max-height: 75px;' alt='Movie image'></td>"
    . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
    . $row['id'] . "'>" . $row['title'] . "</a></td>";
```

Notice on line 53 that the delete button in a form added to `$movie_title_row` links back to this page with a value of `id_to_delete` set to the movie ID:

```php
$movie_title_row .= "<td class='align-middle'><form method='POST' action="
    . $_SERVER['PHP_SELF'] . "><button class='btn btn-danger' type='submit' "
    . "name='id_to_delete' value=" . $row['id'] . ">"
    . "<i class='far fa-trash-alt'></i></button></form></td>";
```

Also, note that I’m using the Font Awesome icon for the trash can with a red background as in Figure 25.25.

Lines 66–68 display a form with a “Reserve Movies” button with the `name` attribute set to `reserve_movies`.

Line 70 is the condition where the query returned no reservations, so line 72 displays that there are no movies in the cart.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_446_0.png)

### Removing a Movie from Cart

If a user changes their mind and doesn’t want a movie, we need to remove it from their shopping cart and the reservation table. Add the code in Listing 25.39 into the condition (`elseif (isset($_POST['id_to_delete'])):`). I explain the code afterward.

### Listing 25.39

```php
1. elseif (isset($_POST['id_to_delete'])):
2.
3. $movie_to_delete = $_POST['id_to_delete'];
4.
5. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
6.     or trigger_error(
7.         'Error connecting to MySQL server for ' . DB_NAME,
8.         E_USER_ERROR
9.     );
10.
11. $user_id = $_SESSION['user_id'];
12.
13. $query = "DELETE FROM reservation
14.         WHERE user_id = ? AND movielisting_id = ?";
15. $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);
16.
17. if (mysqli_errno($dbc))
18. {
19.     trigger_error('Error querying database movielisting', E_USER_ERROR);
20. }
21.
22. $query = "UPDATE movielisting SET number_reserved = number_reserved - 1
23.         WHERE id = ?";
24. $result = parameterizedQuery($dbc, $query, 'i', $movie_to_delete);
25.
26. if (mysqli_errno($dbc))
27. {
28.     trigger_error('Error querying database movielisting', E_USER_ERROR);
29. }
30.
31. if (($key = array_search($movie_to_delete, $_SESSION['cart'])) !== false)
32. {
33.     unset($_SESSION['cart'][$key]);
34. }
35.
36. header("Location: " . $_SERVER['PHP_SELF']);
37. exit;
38.
39. elseif (isset($_POST['reserve_movies'])):
```

## 25. ADDING RESERVATION FEATURES

After connecting to the movielisting database in line 5, we create a query to delete the reservation for this movie in lines 13–14 and perform the query in line 15.

In line 22, we create a query to decrement the number of reserved movies for this title and perform the query in line 24.

In line 31, we search for the key associated with the movie ID we want to delete, and in line 33, remove it from the user's cart.

Finally, line 36 redirects the browser to this shopping cart page. When that page loads, the updated shopping cart contents are refreshed in the table.

### Add Code for Reserving Movies in Cart

When the user reserves the movies in their cart, execution resumes in the (`elseif (isset($_POST['reserve_movies'])):`) condition. Because we've already added their movies to the reservation table, here we delete the shopping cart session variable, in effect emptying it, and redirect the user back to the home page.

Add the code from Listing 25.40 to this condition.

### Listing 25.40

```php
1. elseif (isset($_POST['reserve_movies'])):
2.
3.   // Delete the shopping cart (it's already in the reservation table),
4.   // and route back to the Home page
5.   unset($_SESSION['cart']);
6.
7.   header("Location: " . dirname($_SERVER['PHP_SELF']));
8.   exit;
9.
10. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
```
