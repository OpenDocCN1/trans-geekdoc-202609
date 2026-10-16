# Script for Reserving Movies

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