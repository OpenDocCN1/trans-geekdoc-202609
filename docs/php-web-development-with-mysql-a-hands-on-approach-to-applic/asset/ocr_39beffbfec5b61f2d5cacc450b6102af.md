> Note that you can test multiple variables in a single isset() function call.

Assuming the user enters all the required data, we can now insert the data into the database.
Refer to Listing 16.9.

# Listing 16.9.

```
```php
1. <?php
2. if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
3.     $_POST['movie_rating'], $_POST['movie_director'],
4.     $_POST['movie_running_time_in_minutes']))
5. {
6.     require_once('dbconnection.php');
7. 
8.     $movie_title = $_POST['movie_title'];
9.     $movie_rating = $_POST['movie_rating'];
10.    $movie_director = $_POST['movie_director'];
11.    $movie_runtime = $_POST['movie_running_time_in_minutes'];
12.    $checked_movie_genres = $_POST['movie_genre_checkbox'];
13. 
14.    $movie_genre_text = "";
15.    if (isset($checked_movie_genres))
16.    {
17.        $movie_genre_text = implode(",", $checked_movie_genres);
18.    }
19. 
20.    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
21.        or trigger_error(
22.        'Error connecting to MySQL server for ' . DB_NAME,
23.        E_USER_ERROR
24.        );
25. 
26.    $query = "INSERT INTO movieListing (title, rating, director,
27.             running_time_in_minutes, genre)"
28.        . "VALUES ('$movie_title', '$movie_rating', '$movie_director',
29.            '$movie_runtime', '$movie_genre_text')";
30. 
31.    mysqli_query($dbc, $query)
32.        or trigger_error(
33.        'Error querying database movieListing: Failed to insert movie listing',
34.        E_USER_ERROR
35.        );
36. 
37.    //
```
```