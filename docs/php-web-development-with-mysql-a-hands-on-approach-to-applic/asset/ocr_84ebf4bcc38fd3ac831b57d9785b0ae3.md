# 25. ADDING RESERVATION FEATURES

This code should be familiar to you by now. We use our parameterized query function to look up and display the movie details based on the movie ID parameter we receive or show an error message if no match is found.

> Since we see some duplication of code in multiple pages, it would be an excellent exercise to refactor this out soon by modularizing. I leave that to you as an exercise.

# Adding a Movie to the Cart

Once the user clicks the “Add to Cart” button (Figure 25.15), the HTML POST routes back to the same page since the form’s action attribute is set to <?= $_SERVER['PHP_SELF'] ?>. Since the form’s input element’s name attribute is set to add_to_cart, the code will execute in this condition:

![](bbox=[0.7, 0.27, 0.85, 0.38])

```
if (isset($_POST['add_to_cart']) && isset($_POST['id'])):
```

Here is where we:

+   1. check to see if the movie is still reservable
+   2. reserve the movie if it is still reservable
+   3. update number_reserved in the movieListing table (if reserved).
+   4. Add the movie to the user's shopping cart.
+   5. Redirect back to the Home page.

Add the code in Listing 25.34 to the if (isset($_POST['add_to_cart']) && isset($_POST['id'])): condition, and I will walk through it below.

# Listing 25.34.

```
<?php
if (isset($_POST['add_to_cart']) && isset($_POST['id'])):

$movie_id = $_POST['id'];

// Query if movie is still reservable
$query = "SELECT id FROM movieListing
          WHERE id = ? AND number_of_copies - number_reserved > 0";
$result = parameterizedQuery($dbc, $query, 'i', $movie_id);
```