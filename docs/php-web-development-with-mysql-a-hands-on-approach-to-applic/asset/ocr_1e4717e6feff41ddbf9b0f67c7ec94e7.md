# 16. ADDING DATA USING THE WEB APPLICATION

```
```php
10. <body>
11.     <div class="card">
12.         <div class="card-body">
13.             <h1>Add a Movie</h1>
14.             <nav class="nav">
15.                 <a class="nav-link" href="index.php">Movies I Like</a>
16.             </nav>
17.             <hr/>
18.         <?php
19.             $display_add_movie_form = true;
20.
21.             $genres = [
22.                 'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
23.                 'Fantasy', 'Horror', 'Romance', 'Science Fiction'
24.             ];
25.             // pro-tip: you can test multiple variables within a single isset() call
26.             if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
27.                     $_POST['movie_rating'], $_POST['movie_director'],
28.                     $_POST['movie_running_time_in_minutes']))
29.             {
30.                 require_once('dbconnection.php');
31.
32.                 $movie_title = $_POST['movie_title'];
33.                 $movie_rating = $_POST['movie_rating'];
34.                 $movie_director = $_POST['movie_director'];
35.                 $movie_runtime = $_POST['movie_running_time_in_minutes'];
36.                 $checked_movie_genres = $_POST['movie_genre_checkbox'];
37.
38.                 $movie_genre_text = "";
39.                 if (isset($checked_movie_genres))
40.                 {
41.                     $movie_genre_text = implode(", ", $checked_movie_genres);
42.                 }
43.
44.                 $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
45.                     or trigger_error(
46.                         'Error connecting to MySQL server for ' . DB_NAME,
47.                         E_USER_ERROR
48.                     );
49.
50.                 $query = "INSERT INTO movielisting (title, rating, director, "
51.                         . " running_time_in_minutes, genre) "
52.                         . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
53.                         . "'$movie_runtime', '$movie_genre_text')";
54.
55.                 mysqli_query($dbc, $query)
56.                     or trigger_error(
57.                         'Error querying database movielisting: Failed to insert movie listing',
58.                         E_USER_ERROR
59.                     );
60.
61.                 $display_add_movie_form = false;
62.         ?>
```
```