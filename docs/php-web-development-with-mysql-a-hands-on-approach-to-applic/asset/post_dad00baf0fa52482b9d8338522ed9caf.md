
## 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

```php
. "genre = '$movie_genre_text', image_file = '$movie_image_file' "
. "WHERE id = $id_to_update";

mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movielisting: Failed to update movie listing',
        E_USER_ERROR
    );

$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit();
} else {
    // echo error message
    echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
}

} else // Unintended page link - No movie to edit, link redirect to index
{
    header("Location: index.php");
    exit();
}
?>
<div class="row">
    <div class="col">
        <form enctype="multipart/form-data"
            class="needs-validation" novalidate
            method="POST"
            action="<?php echo $_SERVER['PHP_SELF'] ?> ">
            <div class="form-group row">
                <label for="movie_title"
                    class="col-sm-3 col-form-label-lg">Title</label>
                <div class="col-sm-9">
                    <input type="text" class="form-control"
                        id="movie_title" name="movie_title"
                        value="<?php echo $movie_title ?>"
                        placeholder="Title" required>
                    <div class="invalid-feedback">
                        Please provide a valid movie title.
                    </div>
                </div>
            </div>
            <div class="form-group row">
                <label for="movie_rating"
                    class="col-sm-3 col-form-label-lg">Rating</label>
                <div class="col-sm-9">
                    <select class="custom-select"
                        id="movie_rating"
                        name="movie_rating"
```

### Add Image File Uploads to the Editing Page

```php
value='<?= $movie_rating ?>'
required
<option value="" disabled selected>
Rating...
</option>
<option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G</option>
<option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG</option>
<option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13</option>
<option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R</option>
</select>
<div class="invalid-feedback">
Please select a movie rating.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_director"
class="col-sm-3 col-form-label-lg">Director</label>
<div class="col-sm-9">
<input type="text" class="form-control" id="movie_director"
name="movie_director" value="<?= $movie_director ?>"
placeholder="Director" required>
<div class="invalid-feedback">
Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_running_time_in_minutes"
class="col-sm-3 col-form-label-lg">Running Time (min)</label>
<div class="col-sm-9">
<input type="number" class="form-control"
id="movie_running_time_in_minutes"
name="movie_running_time_in_minutes"
value="<?= $movie_runtime ?>"
placeholder="Running time (in minutes)"
required>
<div class="invalid-feedback">
Please provide a valid running time in minutes.
</div>
</div>
</div>
<div class="form-group row">
<label class="col-sm-3 col-form-label-lg">Genre</label>
<div class="col-sm-9">
<?php
foreach ($genres as $genre) {
?>
    <div class="form-check form-check-inline col-sm-3">
        <input class="form-check-input"
            type="checkbox"
            id="movie_genre_checkbox_action_<?php echo $genre ?>"
            name="movie_genre_checkbox[]"
            value="<?php echo $genre ?>"
            <?php echo in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>
        <label class="form-check-label"
            for="movie_genre_checkbox_action_<?php echo $genre ?>"
        ><?php echo $genre ?></label>
    </div>
<?php
}
?>
    </div>
    </div>
    <div class="form-group row">
        <label for="movie_image_file"
            class="col-sm-3 col-form-label-lg">Movie Image File</label>
        <div class="col-sm-8">
            <input type="file" class="form-control-file" id="movie_image_file"
                name="movie_image_file">
        </div>
    </div>
    <button class="btn btn-primary" type="submit"
        name="edit_movie_submission">Update Movie
    </button>
    <input type="hidden" name="id_to_update" value="<?php echo $id_to_edit ?>">
    <input type="hidden" name="movie_image_file"
        value="<?php echo $movie_image_file ?>">
    </form>
    </div>
    <div class="col-3">
        <img src="<?php echo $movie_image_file_displayed ?>" class="img-thumbnail"
            style="max-height: 400px;" alt="Movie Image">
    </div>
    </div>
    <script>
    // JavaScript for disabling form submissions if there are invalid fields
    (function () {
        'use strict';
        window.addEventListener('load', function () {
            // Fetch all the forms we want to apply custom Bootstrap validation styles to
            var forms = document.getElementsByClassName('needs-validation');
            // Loop over them and prevent submission
            var validation = Array.prototype.filter.call(forms, function (form) {
                form.addEventListener('submit', function (event) {
                    if (form.checkValidity() === false) {
                        event.preventDefault();
                        event.stopPropagation();
                    }
                    form.classList.add('was-validated');
                }, false);
            });
        }, false);
    })();
    </script>
    </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965Dz0rT7abK41JStQIAqVgRVzpbzo5snXKp4YfRvH+8abtTE1Pi6jizo"
        crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
        integrity="sha384-wHAiF1Rpf4etG03wPF2yD3e..."
        crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
        integrity="sha384-B0Uglyr..."
        crossorigin="anonymous"></script>
</body>
</html>
```

### Displaying Image on Deletion Page

Finally, we need to modify removemovie.php so that the movie's image is displayed on the “Remove a Movie” page for better identification of the movie. We need to delete the image file from the database and filesystem on confirmation of delete. We will add the image to the left side of the table so that it looks like Figure 19.26.

Open removemovie.php and add a reference to the movieimagefileutil.php script by adding the following require_once() following the reference to dbconnection.php towards the top of the script:

```php
<?php
    require_once('dbconnection.php');
    require_once('movieimagefileutil.php');
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_289_0.png)

### Displaying the Image on removiemovie.php

When first linking to the “Remove a Movie” page (removiemovie.php), it was because of an HTTP GET request/response when navigating from the index.php script as a result of selecting the trash can icon. Therefore, we need to make the following modifications to display movie image file details in the elseif (isset($_GET['id_to_delete'])) block of code:

```php
elseif (isset($_GET['id_to_delete'])):
 // ...
 if (mysqli_num_rows($result) == 1)
 {
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];
  if (empty($movie_image_file))
  {
   $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  }
 }
```

As we did in addmovie.php and editmovie.php, we need to add the movie image file (or the default image) to the left of the table to display the movie details.

Since we use Bootstrap's Flexbox grid implementation, we can encapsulate the image and table in separate columns and put them both in a single row. All this is just below the movie tile located in the <h1> element as in Listing 19.34.

```php
<h1><?= $row['title'] ?></h1>
<div class="row">
 <div class="col-2">
  <img src=... class="img-thumbnail" style="max-height: 200px;" alt="Movie image">
 </div>
</div>
<div class="col">
 ...
```
