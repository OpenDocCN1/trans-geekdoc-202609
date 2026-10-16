# 19. WORKING WITH FILES AND FEATURE ADDITIONS TO EXISTING CODE

```
mysql_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to insert movie listing',
E_USER_ERROR
);
}
```

The next line should already be set to not display the form:

```
if (empty($movie_image_file_path))
{
$movie_image_file_path = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
}
```

Finally, we need to add the movie image file (or the default image) to the table to display the added movie details.

Since we are using Bootstrap's Flexbox grid implementation, it is best to encapsulate the image and table in separate columns and put them both in a single row, all just below the movie title located in the <h1> element as in Listing 19.16.



```
<h1><?= $movie_title ?></h1>
<div class="row">
<div class="col-2">
<img src="<?= $movie_image_file_path ?>" class="img-thumbnail" style="max-height: 200px;" alt="Movie image">
</div>
<div class="col">
<table class="table table-striped">
...
</table>
</div>
</div>
</div>
```

Notice we set the style attribute to a maximum height of 200 pixels.