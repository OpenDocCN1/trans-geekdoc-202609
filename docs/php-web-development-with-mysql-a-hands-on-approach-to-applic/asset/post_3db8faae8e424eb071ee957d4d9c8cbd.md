
Note that in the elseif() condition:

```
else if ($_SESSION['user_access_privileges'] == 'user'
    && ($row['number_of_copies'] > $row['number_reserved'])
    && !isMovieReservedByUser($row['id'], $_SESSION['user_id']))
```

We have three conditions to satisfy before displaying the shopping cart link to reserve a movie:

- Does the logged-in user have user privileges?
- Are the number of copies for this movie currently more than the number currently reserved?
- And, has the user already reserved this movie (which we check with our isMovieReservedByUser() function)?

Also, note that the link refers to the script reservemovie.php we will create below.

Since we are calling the function isMovieReservedByUser(), which resides in the queryutils.php script, let’s add an include for it right below our dbconnection.php and movielistingfileconstants.php includes. Refer to Listing 25.30.

```
<div class="card">
    <div class="card-body">
        <h1><?= $page_title ?></h1>
        <?php
        require_once('dbconnection.php');
        require_once('movielistingfileconstants.php');
        require_once('queryutils.php');
        ?>
    </div>
</div>
```

## Refactoring to Remove Duplicate Inclusions

Did you notice? Every script in our application that includes queryutils.php also includes navmenu.php. This script is a good place to remove duplicate inclusions and have navmenu.php include queryutils.php. Removing duplicate code improves maintainability. It would be tedious and error-prone to update all occurrences of the code in the future. Search for all require_once('queryutils.php'); statements in the application and remove them. There should be an inclusion in these files:

- addmovie.php
- editmovie.php
- index.php
- login.php
- moviedetails.php
- removemovie.php
- signup.php

## 25. ADDING RESERVATION FEATURES

Open the navmenu.php script and include queryutils.php right below the first condition that calls session_start() if it has not already been started (Listing 25.30).

```
```php
Unchanged Lines
<?php
$page_title = isset($page_title) ? $page_title : "";
if (session_status() == PHP_SESSION_NONE)
{
	session_start();
}
+ Added Line
+ require_once('queryutils.php');
Unchanged Lines
?>
<nav ...>
```
```

Also, notice that we have multiple inclusions of the Font Awesome style sheet in multiple scripts that already include navmenu.php. In addition to navmenu.php, there should be an inclusion in these files:

- login.php
- removemovie.php
- reservemovie.php
- unauthorizedaccess.php

Look for this line:

```
```html
<link rel="stylesheet" href="https://use.fontawesome.com/...">
```
```

Remove it from all of the above scripts and add this link right before the opening <nav ...> link as in Listing 25.31.

## Listing 25.31.

```
```php
1. Unchanged Lines
2. <?php
3.     $page_title = isset($page_title) ? $page_title : "";
4.
5.     if (session_status() == PHP_SESSION_NONE)
6.     {
7.         session_start();
8.     }
9.
10.    require_once('queryutils.php');
11. ?>
12. + Added Lines
13. +   <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
14. +       integrity="sha384-50oBUH..."
15. +       crossorigin="anonymous">
16. Unchanged Lines
17.     <nav ...>
18.     ...
```
```

## Script for Reserving Movies

Browsing and reserving movies should be similar to shopping for items in an online store. When a user finds an item, in our case a movie they like, they should be able to add it to a shopping cart by clicking on the shopping cart icon for a movie they're interested in. See Figure 25.13.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_427_0.png)

We want them to see a page like Figure 25.14 allowing them to add it to their cart.

First open pagetitles.php and add the following MR_RESERVE_MOVIE_PAGE definition right after the MR_REMOVE_MOVIE_PAGE definition:

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_427_1.png)

## 25. ADDING RESERVATION FEATURES

```
Unchanged Lines
    <?php
    // Page Titles
    define('MR_HOME_PAGE', 'Movie Reservations');
    ...
    define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
+ Added Line
+     define('MR_RESERVE_MOVIE_PAGE', 'Movie Reservations - Reserve Movie');
```

The reservation page is a standard Bootstrap page showing the movie details with a button for adding the movie to a shopping cart. There are two ways to get to this script. The first is through an HTTP GET from the homepage that includes the movie ID as a query parameter. The second is through an HTTP POST that includes the movie ID as a hidden form parameter when someone adds the movie to their cart on the same page.

Create a new script called reservemovie.php and add the code in Listing 25.32.

## Listing 25.32.

```
1. <!DOCTYPE html>
2. <?php
3. require_once('pagetitles.php');
4. $page_title = MR_RESERVE_MOVIE_PAGE;
5. ?>
6. <html>
7. <head>
8. <title><?= $page_title ?></title>
9. <link rel="stylesheet"
10. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
11. integrity="sha384-GJzZqFGwb10TTN6wy59sFFfF1BuGJpLSa9DkKmp0DgiMDm4iYMj70zNKyBI7o6tUS"
12. crossorigin="anonymous">
13. </head>
14. <body>
15. <?php
16. require_once('navmenu.php');
17. ?>
18. <div class="card">
19. <div class="card-body">
20. <h1>Reserve Movie</h1>
21. <?php
22. require_once('dbconnection.php');
23. require_once('movieimagefileutil.php');
24.
25. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
26.     or trigger_error(
27.         'Error connecting to MySQL server for ' . DB_NAME,
28.         E_USER_ERROR
29.     );
```

## Script for Reserving Movies

```
30.
31.    if (isset($_POST['add_to_cart']) && isset($_POST['id'])):
32.
33.    // ...
34.
35.    elseif (isset($_GET['id_to_reserve'])):
36.    // ...
37.    else: // Unintended page link - No movie to reserve, redirect to index
38.
39.        header("Location: " . dirname($_SERVER['PHP_SELF']));
40.        exit();
41.
42.    endif;
43. ?>
44.    </div>
45.    </div>
46. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
47.    integrity="sha384-q8i/X+965DzO0rT7abKljI5tQI..."
48.    crossorigin="anonymous"></script>
49. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
50.    integrity="sha384-wHAiFfRl..."
51.    crossorigin="anonymous"></script>
52. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
53.    integrity="sha384-B0Uglyr+jN..."
54.    crossorigin="anonymous"></script>
55. </body>
56. </html>
```

This code is a boilerplate script that should look familiar to you. Lines 3, 4, and 8 set and display the page title. Line 16 includes and displays the navbar. Line 20 displays “Reserve Movie” in an <h1> element set. Lines 22–29 include dbconnection.php, movieimagefileutil.php, and connect to the Movie database.

Line 31 (if (isset($_POST['add_to_cart']) && isset($_POST['id']))): is the condition to check whether the user pressed the “Add to Cart” button. The name attribute for this button is named add_to_cart. We add code within this condition that adds this movie to the user’s cart to be reserved.

Line 35 (elseif (isset($_GET['id_to_reserve']))): is the condition where the user navigated from the homepage by selecting the shopping cart icon for this movie. This condition is where we display the movie details and the “Add to Cart” form button. Remember, use GET for read-only operations.

## 25. ADDING RESERVATION FEATURES

Line 37 (else: // Unintended page link - No movie to reserve, redirect to index) is a ‘catch-all’ condition that covers someone typing in the name of the script in the URL field of their browser. If this occurs, line 39 redirects the user back to the homepage.

The rest of the code is the standard Bootstrap boilerplate script inclusions.

## Show Details and Form for Adding to Cart

When the user first navigates to this page as a result of selecting the shopping cart icon for this movie, code will execute in this condition:

```
elseif (isset($_GET['id_to_reserve'])):
    // ...
```

Here we display the movie details and a form button for adding the movie to our cart. The code for the movie details will be identical to the code in removemovie.php, except we don’t have to list the number of copies, and we only have one button.

Add the code in Listing 25.33 to the elseif (isset($_GET['id_to_reserve'])): condition:

## Listing 25.33.

```
1. elseif (isset($_GET['id_to_reserve'])):
2. ?>
3. <h3 class="text-success">Confirm Reservation of the Following Movie:</h3><br/>
4. <?php
5. $id = $_GET['id_to_reserve'];
6.
7. $query = "SELECT * FROM movieListing WHERE id = ?";
8.
9. $result = parameterizedQuery($dbc, $query, 'i', $id);
10.
11. if(mysqli_errno($dbc))
12. {
13.     trigger_error('Error querying database movieListing', E_USER_ERROR);
14. }
15.
16. if (mysqli_num_rows($result) == 1)
17. {
18.     $row = mysqli_fetch_assoc($result);
19.
20.     $movie_image_file = $row['image_file'];
21.
```
