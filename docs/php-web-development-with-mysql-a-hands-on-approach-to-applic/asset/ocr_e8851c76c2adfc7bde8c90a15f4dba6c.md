# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

First, right after setting $id_to_update from the form data, create a variable named $movie_image_file and set it to the hidden variable now within the $_POST superglobal:

```
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
    $_POST['movie_image_file']))
{
    // ...
    $id_to_update = $_POST['id_to_update'];
    $movie_image_file = $_POST['movie_image_file'];
}
```

We need to test if an image file was previously set for the movie right after checking if checked_movie_genres is set and before connecting to the database. If not, set the previously displayed movie to the default image (Listing 19.27).

# Listing 19.27.

```
1. if (isset($checked_movie_genres))
2. {
3.     $movie_genre_text = implode(", ", $checked_movie_genres);
4. }
5. 
6. if (empty($movie_image_file))
7. {
8.     $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
9. }
10. else
11. {
12.     $movie_image_file_displayed = $movie_image_file;
13. }
```

Just as with addmovie.php, we will validate the uploaded movie image file right before the call connecting to the database. It might be a good idea to add an appropriate comment here, something like I have in Listing 19.28.

# Listing 19.28.

```
1. else
2. {
3.     $movie_image_file_displayed = $movie_image_file;
4. }
5. 
6. /*
7. Here is where we will deal with the file by calling validateMovieImageFile().
8. This function will validate that the movie image file is not greater than 128
```