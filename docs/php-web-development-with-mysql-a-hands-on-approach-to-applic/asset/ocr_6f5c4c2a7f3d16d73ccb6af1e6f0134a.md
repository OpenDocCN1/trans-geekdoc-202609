# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE



Now we need to modify moviedetails.php so that the movie's image is displayed on the “Movie Details” page to identify the movie better. This process will be very similar to the modifications we made to addmovie.php that displays the movie details after the user selected “Add a Movie” and look like Figure 19.18.

```
if (isset($_GET['id'])):
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');
```

Next, just inside the condition if (mysqli_num_rows($result) == 1), right after the line:
$row = mysqli_fetch_assoc($result);, we need to add code that displays the default image if the image_file field is an empty string. See Listing 19.21.

```
if (mysqli_num_rows($result) == 1):
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];

  if (empty($movie_image_file)):
    $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  endif;

endif;
```

Finally, as we did in addmovie.php, we need to add the movie image file (or the default image) to the table to display the movie details.

![](bbox=[0.05, 0.77, 0.95, 0.2])