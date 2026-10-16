# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

```
10. <body>
11. <div class="card">
12.     <div class="card-body">
13.         <h1>Edit a Movie</h1>
14.         <nav class="nav">
15.             <a class="nav-link" href="index.php">Movies I Like</a>
16.         </nav>
17.         <hr/>
18. <?php
19. require_once('dbconnection.php');
20. require_once('movieimagefileutil.php');
21. 
22. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
23.     or trigger_error(
24.         'Error connecting to MySQL server for ' . DB_NAME,
25.         E_USER_ERROR
26.     );
27. 
28. $genres = [
29.     'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
30.     'Fantasy', 'Horror', 'Romance', 'Science Fiction'
31. ];
32. 
33. if (isset($_GET['id_to_edit'])) {
34.     $id_to_edit = $_GET['id_to_edit'];
35. 
36.     $query = "SELECT * FROM movieListing WHERE id = $id_to_edit";
37. 
38.     $result = mysqli_query($dbc, $query)
39.         or trigger_error(
40.             'Error querying database movieListing',
41.             E_USER_ERROR
42.         );
43. 
44.     if (mysqli_num_rows($result) == 1) {
45.         $row = mysqli_fetch_assoc($result);
46. 
47.         $movie_title = $row['title'];
48.         $movie_rating = $row['rating'];
49.         $movie_director = $row['director'];
50.         $movie_runtime = $row['running_time_in_minutes'];
51.         $movie_genre_text = $row['genre'];
52.         $movie_image_file = $row['image_file'];
53. 
54.         if (empty($movie_image_file)) {
55.             $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
56.         } else {
57.             $movie_image_file_displayed = $movie_image_file;
58.         }
59.
```