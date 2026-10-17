
### 完整代码列表

```php
<body>
    <div class="card">
        <div class="card-body">
            <h1>Add a Movie</h1>
            <nav class="nav">
                <a class="nav-link" href="index.php">Movies I Like</a>
            </nav>
            <hr/>
            <?php
                $display_add_movie_form = true;

                $genres = [
                    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
                    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
                ];
                // pro-tip: you can test multiple variables within a single isset() call
                if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
                        $_POST['movie_rating'], $_POST['movie_director'],
                        $_POST['movie_running_time_in_minutes']))
                {
                    require_once('dbconnection.php');

                    $movie_title = $_POST['movie_title'];
                    $movie_rating = $_POST['movie_rating'];
                    $movie_director = $_POST['movie_director'];
                    $movie_runtime = $_POST['movie_running_time_in_minutes'];
                    $checked_movie_genres = $_POST['movie_genre_checkbox'];

                    $movie_genre_text = "";
                    if (isset($checked_movie_genres))
                    {
                        $movie_genre_text = implode(", ", $checked_movie_genres);
                    }

                    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
                        or trigger_error(
                            'Error connecting to MySQL server for ' . DB_NAME,
                            E_USER_ERROR
                        );

                    $query = "INSERT INTO movielisting (title, rating, director, "
                            . " running_time_in_minutes, genre) "
                            . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
                            . "'$movie_runtime', '$movie_genre_text')";

                    mysqli_query($dbc, $query)
                        or trigger_error(
                            'Error querying database movielisting: Failed to insert movie listing',
                            E_USER_ERROR
                        );

                    $display_add_movie_form = false;
            ?>
```

### 完整代码清单

```html
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

## 16. 使用 Web 应用程序添加数据

```html
<option value="G">G</option>
<option value="PG">PG</option>
<option value="PG-13">PG-13</option>
<option value="R">R</option>
</select>
<div class="invalid-feedback">
Please select a movie rating.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_director"
class="col-sm-3 col-form-label-lg">Director</label>
<div class="col-sm-8">
<input type="text" class="form-control" id="movie_director"
name="movie_director" placeholder="Director" required>
<div class="invalid-feedback">
Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_running_time_in_minutes"
class="col-sm-3 col-form-label-lg">Running Time (min)</label>
<div class="col-sm-8">
<input type="number" class="form-control"
id="movie_running_time_in_minutes"
name="movie_running_time_in_minutes"
placeholder="Running time (in minutes)" required>
<div class="invalid-feedback">
Please provide a valid running time in minutes.
</div>
</div>
</div>
<div class="form-group row">
<label class="col-sm-3 col-form-label-lg">Genre</label>
<div class="col-sm-8">
<?php
foreach ($genres as $genre)
{
?>
<div class="form-check form-check-inline col-sm-3">
<input class="form-check-input" type="checkbox"
id="movie_genre_checkbox_action"
name="movie_genre_checkbox[]"
value="<?= $genre ?>">
<label class="form-check-label"
for="movie_genre_checkbox_action"><?= $genre ?></label>
</div>
<?php
}
?>
```
