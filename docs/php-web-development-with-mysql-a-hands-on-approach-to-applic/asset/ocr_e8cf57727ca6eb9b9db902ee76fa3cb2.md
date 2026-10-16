# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

```
```php
if (mysqli_num_rows($result) == 1) {
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (empty($movie_image_file)) {
        $movie_image_file =
            ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>"
             class="img-thumbnail"
             style="max-height: 200px;"
             alt="Movie image">
    </div>
    <div class="col">
        <table class="table table-striped">
            <tbody>
                <tr>
                    <th scope="row">Rating</th>
                    <td><?= $row['rating'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Director</th>
                    <td><?= $row['director'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Running Time (minutes)</th>
                    <td><?= $row['running_time_in_minutes'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Genre</th>
                    <td><?= $row['genre'] ?></td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
<p>
<form method="POST"
      action="<?= $_SERVER['PHP_SELF'] ?>">
    <div class="form-group row">
        <div class="col-sm-2">
            <button class="btn btn-danger" type="submit"
                    name="delete_movie_submission">
                Delete Movie
            </button>
        </div>
    </div>
</form>
```
```