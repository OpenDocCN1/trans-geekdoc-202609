
## 19. Working With Files and Feature Additions to Existing Code

```php
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}

/*
Here is where we will deal with the file by calling validateMovieImageFile().
This function will validate that the movie image file is not greater than 128
characters, is the right image type (jpg/png/gif), and not greater than 512KB.
This function will return an empty string ('') if the file validates successfully,
otherwise, the string will contain error text to be output to the web page before
redisplaying the form.
*/

$file_error_message = validateMovieImageFile();

if (empty($file_error_message))
{
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $movie_image_file_path = addMovieImageFileReturnPathLocation();

    $query = "INSERT INTO movieListing (title, rating, director,"
        . "running_time_in_minutes, genre, image_file)"
        . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
        . "'$movie_runtime', '$movie_genre_text', '$movie_image_file_path')";

    mysqli_query($dbc, $query)
        or trigger_error(
            'Error querying database movieListing: Failed to insert movie listing',
            E_USER_ERROR
        );

    if (empty($movie_image_file_path))
    {
        $movie_image_file_path = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }

    $display_add_movie_form = false;
}
?>
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>

<h1><?= $movie_title ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file_path ?>" class="img-thumbnail"
             style="max-height: 200px;" alt="Movie image">
    </div>
    <div class="col">
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
</div>
</div>
<hr/>
<p>Would you like to <a href='<?= $_SERVER['PHP_SELF']; ?>'> add another movie</a>?</p>
<?php
}
else
{
// echo error message
echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
}
}
if ($display_add_movie_form)
{
?>
<form enctype="multipart/form-data" class="needs-validation" novalidate
method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group row">
<label for="movie_title"
class="col-sm-3 col-form-label-lg">Title</label>
<div class="col-sm-8">
<input type="text" class="form-control" id="movie_title"
name="movie_title" value="<?= $movie_title ?>"
placeholder="Title" required>
<div class="invalid-feedback">
Please provide a valid movie title.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_rating" class="col-sm-3 col-form-label-lg">Rating</label>
<div class="col-sm-8">
<select class="custom-select" id="movie_rating"
name="movie_rating" value="<?= $movie_rating ?>" required>
## 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

156.     <option value="" disabled selected>Rating...</option>
157.     <option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G</option>
158.     <option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG</option>
159.     <option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13</option>
160.     <option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R</option>
161.     </select>
162.     <div class="invalid-feedback">
163.     Please select a movie rating.
164.     </div>
165.     </div>
166.     </div>
167.     <div class="form-group row">
168.     <label for="movie_director" class="col-sm-3 col-form-label-lg">Director</label>
169.     <div class="col-sm-8">
170.     <input type="text" class="form-control" id="movie_director"
171.     name="movie_director" value="<?= $movie_director ?>"
172.     placeholder="Director" required>
173.     <div class="invalid-feedback">
174.     Please provide a valid movie director.
175.     </div>
176.     </div>
177.     </div>
178.     <div class="form-group row">
179.     <label for="movie_running_time_in_minutes"
180.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
181.     <div class="col-sm-8">
182.     <input type="number" class="form-control"
183.     id="movie_running_time_in_minutes"
184.     name="movie_running_time_in_minutes"
185.     value="<?= $movie_runtime ?>"
186.     placeholder="Running time (in minutes)" required>
187.     <div class="invalid-feedback">
188.     Please provide a valid running time in minutes.
189.     </div>
190.     </div>
191.     </div>
192.     <div class="form-group row">
193.     <label class="col-sm-3 col-form-label-lg">Genre</label>
194.     <div class="col-sm-8">
195.     <?php
196.     foreach ($genres as $genre)
197.     {
198.     ?>
199.     <div class="form-check form-check-inline col-sm-3">
200.     <input class="form-check-input" type="checkbox"
201.     id="movie_genre_checkbox_action_<?= $genre ?>"
202.     name="movie_genre_checkbox[]"
203.     value="<?= $genre ?>"<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>>
204.     <label class="form-check-label"
205.     for="movie_genre_checkbox_action_<?= $genre ?>"><?= $genre ?></label>
206.     </div>
207.     <?php
208.     }
## Adding File Upload Capability

?> 
</div>
</div>
<div class="form-group row">
    <label for="movie_image_file"
        class="col-sm-3 col-form-label-lg">Movie Image File</label>
    <div class="col-sm-8">
        <input type="file" class="form-control-file"
            id="movie_image_file" name="movie_image_file">
    </div>
</div>
<button class="btn btn-primary" type="submit"
    name="add_movie_submission">Add Movie</button>
</form>
<script>
// Javascript for disabling form submissions if there are invalid fields
(function() {
    'use strict';
    window.addEventListener('load', function() {
        // Fetch all the forms we want to apply custom Bootstrap validation styles to
        var forms = document.getElementsByClassName('needs-validation');
        // Loop over them and prevent submission
        var validation = Array.prototype.filter.call(forms, function(form) {
            form.addEventListener('submit', function(event) {
                if (form.checkValidity() == false) {
                    event.preventDefault();
                    event.stopPropagation();
                }
                form.classList.add('was-validated');
            }, false);
        });
    }, false);
})();
</script>
<?php
    } // Display add movie form
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzO0rT7abK1JLJStQIAqVqVzpbo5smXKp0yVhVh+8abtTE1Pi6jizo"
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiFfRl0JPyJ4MwYrtyAdNaJCcmZs5jDFfspbIwwj/QRKioJHL4Jg=="
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-384-..."
    crossorigin="anonymous"></script>
</body>
</html>

## Displaying Thumbnail Images of Movies on Main Page

Now that we can add images to our movies let’s modify the main “Movies I Like” page (index.php) to display a thumbnail image of the movie at the beginning of each movie row or a default image (generic_movie.jpg) if the user did not upload an image for the movie. We want our modified “Movies I Like” page to look like Figure 19.17.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_268_0.png)

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
