
> Note that you can test multiple variables in a single isset() function call.

Assuming the user enters all the required data, we can now insert the data into the database.
Refer to Listing 16.9.

### Listing 16.9.

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

## 16. ADDING DATA USING THE WEB APPLICATION

### Extracting the Genre from the Checkbox Array

Notice the section of code above that deals with the movie genre:

```
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}
```

Since a movie can have multiple genres, we create a comma-delimited list of the selected genres from the checkbox array. We do this by calling the implode() function ONLY if the user chose at least one genre. If the user doesn’t select any genres, the checkbox array does not exist. Therefore we need to check that it is set first before calling implode(). If the user does not select a genre, we insert an empty string into the genre field of the movieListing table.

### Preventing the Display of the “Add a Movie” Form

After inserting the new movie information into the database, we prevent the form from displaying again by setting $display_add_movie_form to false:

```
mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing: Failed to insert movie listing',
        E_USER_ERROR
    );

$display_add_movie_form = false;
```

### Displaying the Added Details and a Link to Add Another Movie

To make this page more useful, we should let the user know their movie information was successfully added to the database. Let us do this by displaying a page and a table that looks like Figure 16.6, including a link to add another movie as shown.

Listing 16.10 lists the HTML markup and PHP code to display the added movie details.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_188_0.png)

### Listing 16.10.

```
1. $display_add_movie_form = false;
2. ?>
3. <h3 class="text-info">The Following Movie Details were Added:</h3><br/>
4. 
5. <h1><?= $movie_title ?></h1>
6. <table class="table table-striped">
7. <tbody>
8. <tr>
9. <th scope="row">Rating</th>
10. <td><?= $movie_rating ?></td>
11. </tr>
12. <tr>
13. <th scope="row">Director</th>
14. <td><?= $movie_director ?></td>
15. </tr>
16. <tr>
17. <th scope="row">Running Time (minutes)</th>
18. <td><?= $movie_runtime ?></td>
19. </tr>
20. <tr>
21. <th scope="row">Genre</th>
22. <td><?= $movie_genre_text ?></td>
23. </tr>
24. </tbody>
25. </table>
26. <hr/>
27. <p>Would you like to <a href='<?= $_SERVER['PHP_SELF'] ?>'> add another movie</a>?</p>
28. <?php
29. }
30. 
31. if ($display_add_movie_form) {
```

### Complete Code Listing

And now, Listing 16.11 is the complete source code for the addmovie.php page.

### Listing 16.11.

```
1. <!DOCTYPE html>
2. <html>
3. <head>
4. <title>Add a Movie</title>
5. <link rel="stylesheet"
6. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
7. integrity="sha384-GJzqFGwb1QT..."
8. crossorigin="anonymous">
9. </head>
```

## 16. ADDING DATA USING THE WEB APPLICATION

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

### Complete Code Listing

```
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>
<h1><?= $movie_title ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $movie_rating ?></td>
        </tr>
        <tr>
            <th scope="row">Director</th>
            <td><?= $movie_director ?></td>
        </tr>
        <tr>
            <th scope="row">Running Time (minutes)</th>
            <td><?= $movie_runtime ?></td>
        </tr>
        <tr>
            <th scope="row">Genre</th>
            <td><?= $movie_genre_text ?></td>
        </tr>
    </tbody>
</table>
<hr/>
<p>Would you like to <a href="<?= $_SERVER['PHP_SELF']?>">add another movie</a>?</p>
<?php
}

if ($display_add_movie_form)
{
?>
<form class="needs-validation" novalidate method="POST"
    action="<?= $_SERVER['PHP_SELF']?>">
    <div class="form-group row">
        <label for="movie_title"
            class="col-sm-3 col-form-label-lg">Title</label>
        <div class="col-sm-8">
            <input type="text" class="form-control" id="movie_title"
                name="movie_title" placeholder="Title" required>
            <div class="invalid-feedback">
                Please provide a valid movie title.
            </div>
        </div>
    </div>
    <div class="form-group row">
        <label for="movie_rating"
            class="col-sm-3 col-form-label-lg">Rating</label>
        <div class="col-sm-8">
            <select class="custom-select" id="movie_rating"
                name="movie_rating" required>
                <option value="" disabled selected>Rating...</option>
```
