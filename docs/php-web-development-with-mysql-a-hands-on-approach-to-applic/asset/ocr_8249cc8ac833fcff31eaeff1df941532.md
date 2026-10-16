# Listing 19.26.

```
```html
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
        name="edit_movie_submission">Update Movie</button>
</form>
```
```

In regards to $movie_image_file, just like the hidden `<input>` element for id_to_update, I created another hidden `<input>` element in the form and set it to the value of $movie_image_file and set the name attribute to movie_image_file. When the form data is posted back to editmovie.php as a result of the user pressing the **Update Movie** submit button, the name of the existing file name (prior to updating) will be available in the $_POST[] super-global array so that it can be removed (if not empty) if the user selected a new file:

```
```php
<input type="hidden" name="id_to_update" value="<? $id_to_edit ?>">
<input type="hidden" name="movie_image_file" value="<? $movie_image_file ?>">
```
```

> > *Please see the aside in chapter 17 titled: **THE WEB IS STATELESS!***

# Modifying Edit Code to Store Files

After the user submits the form data by selecting the “Update Movie” button in Figure 19.25, the form data is available within the elseif block checking to see if the form data is set in the $_POST super global variable. Notice we added movie_image_file hidden field to the condition.

```
```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
              $_POST['movie_rating'], $_POST['movie_director'],
              $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
              $_POST['movie_image_file']))
{
```
```

Inside this elseif block is where we want to validate the file, move it to the images/ folder, and modify the image_file field in the movieListing table in the database.