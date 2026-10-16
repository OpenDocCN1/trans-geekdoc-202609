# Displaying Thumbnail Images of Movies on Main Page

Now that we can add images to our movies let’s modify the main “Movies I Like” page (index.php) to display a thumbnail image of the movie at the beginning of each movie row or a default image (generic_movie.jpg) if the user did not upload an image for the movie. We want our modified “Movies I Like” page to look like Figure 19.17.

![](bbox=[0.42, 0.18, 0.86, 0.38])

The modifications are relatively simple since all we need to do is modify our query to get the new image_file field from the movielisting database table and add a column to our HTML table for displaying a thumbnail image at the beginning of each row of the table.

So let’s get to it. First, add a reference to the movielistingfileconstants.php script by adding the following require_once() following the reference to dbconnection.php:

```
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');
```

Next, modify the SQL query statement (that follows the connection to the database) to include the image_file field in the movieListing database table:

```
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

$query = "SELECT id, title, image_file FROM movieListing ORDER BY title";
```

Down where the HTML table is displayed, we need to add a column for our thumbnail image. First, add an HTML table header field (so there are three columns instead of two) as in Listing 19.18.