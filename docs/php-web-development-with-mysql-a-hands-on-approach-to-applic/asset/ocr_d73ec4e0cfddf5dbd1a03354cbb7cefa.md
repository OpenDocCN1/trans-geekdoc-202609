```
9. characters, is the right image type (jpg/png/gif), and not greater than 512KB.
10. This function will return an empty string ('') if the file validates successfully,
11. otherwise, the string will contain error text to be output to the web page before
12. redisplaying the form.
13. */
```

Next, we make our call to validateMovieImageFile() and set the return value to a new variable that captures the file error message:

```
otherwise, the string will contain error text to be output to the web page before
redis playing the form.
*/

$file_error_message = validateMovieImageFile();
```

Just as we did in addmovie.php, if validateMovieImageFile() returns anything but an empty string, there was an error uploading the file. We want to display this error message and redisplay the form instead of updating the data in the database, allowing the user to correct the error. The two common reasons for the error are: the image is too big, or the image is the wrong file type.

Create an if condition for file_error_message being empty, and move all the database code into this new if block. The new if block should now look like Listing 19.29.

# Listing 19.29.

```
1. $file_error_message = validateMovieImageFile();
2.
3. if (empty($file_error_message))
4. {
5.     $query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
6.         . "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
7.         . "genre = '$movie_genre_text' WHERE id = $id_to_update";
8.
9.     mysqli_query($dbc, $query)
10.         or trigger_error(
11.             'Error querying database movielisting: Failed to update movie listing',
12.             E_USER_ERROR
13.         );
14.
15.     $nav_link = 'moviedetails.php?id=' . $id_to_update;
16.
17.     header("Location: $nav_link");
18.     exit();
19. }
```