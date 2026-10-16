# Creating a Page to Add Movies

```
```html
<div class="invalid-feedback">
    Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
    <label for="movie_running_time_in_minutes" class="col-sm-3 col-form-label-lg">Running Time (min)</label>
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
    </div>
</div>
    <button class="btn btn-primary" type="submit"
        name="add_movie_submission">Add Movie</button>
</form>
```
```

Note that the page is self referencing as the action attribute is set to $_SERVER['PHP_SELF']:

```
`<form ... action="<?= $_SERVER['PHP_SELF']; ?>">`
```