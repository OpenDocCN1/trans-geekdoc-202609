
### Listing 18.8.

```
<?php
foreach ($genres as $genre) {
?>
<div class="form-check form-check-inline col-sm-3">
<input class="form-check-input" type="checkbox"
id="movie_genre_checkbox_<?= $genre ?>"
name="movie_genre_checkbox[]"
value="<?= $genre ?>"<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>
<label class="form-check-label"
for="movie_genre_checkbox_action_<?= $genre ?>"> <?= $genre ?></label>
</div>
<?php
}
?>
```

Notice I added to the value attribute whether or not the genre was selected or not using the ternary operator:

```
... value="<?= $genre ?>" <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

In addmovie.php we merely have:

```
... value="<?= $genre ?>" ...
```

However, we want to know if a particular genre is selected or not, and that information is contained in the $checked_movie_genres array we created above using the explode() function. Using the function in_array() we can determine if $genre (the current genre we are processing in the foreach loop in the array $genres) is contained in the array $checked_movie_genres. in_array() returns true if $genre exists, otherwise it returns false. We can use the ternary operator to add the checked ('checked') attribute to the option for this genre if found, or an empty string (' ') if not found:

```
... <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

## Using Bootstrap’s Client-side Validation

As in the addmovie.php script, we are using Bootstrap's client side validation. This requires we do the following:

- 1. Set the form's class attribute to needs-validation and adding the novalidate attribute:

```
<form class="needs-validation" novalidate ...
```

[3] in_array(): https://php.net/in_array

## 18. EDITING DATA USING THE WEB APPLICATION

- 2. Marking input elements with a required attribute to ensure the fields we want validated get validated:

```
<input type="number" ... required>
```

- 3. Adding <div> elements with class attributes set to invalid-feedback containing the validation text we want the user to see if they forget to fill in the field. Again, we add these directly under the <input> elements we want validated. Listing 18.9 is the complete HTML markup for the “Running Time” input field along with the invalid feedback we want the user to see if they forget to enter a value.

### Listing 18.9.

```
1. <div class="form-group row">
2.   <label for="movie_running_time_in_minutes"
3.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
4.   <div class="col-sm-8">
5.     <input type="number" class="form-control"
6.       id="movie_running_time_in_minutes"
7.       name="movie_running_time_in_minutes"
8.       value="<?= $movie_runtime ?>"
9.       placeholder="Running Time (in minutes)" required>
10.     <div class="invalid-feedback">
11.       Please provide a valid running time in minutes.
12.     </div>
13.   </div>
14. </div>
```

- 4. Adding the JavaScript code in Listing 18.10 to <script> tags following the form.

### Listing 18.10.

```
1. </form>
2. <script>
3. // JavaScript for disabling form submissions if there are invalid fields
4. (function() {
5.   'use strict';
6.   window.addEventListener('load', function() {
7.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
8.     var forms = document.getElementsByClassName('needs-validation');
9.     // Loop over them and prevent submission
10.     var validation = Array.prototype.filter.call(forms, function(form) {
11.       form.addEventListener('submit', function(event) {
12.         if (form.checkValidity() === false) {
13.           event.preventDefault();
14.           event.stopPropagation();
15.         }
16.         form.classList.add('was-validated');
17.       }, false);
18.     });
19.   }, false);
20. }());
21. </script>
```

## DRY?

*This looks like we are repeating code from the addmovie.php script, doesn't it? In this case, since we are using boiler-plate Bootstrap validation code, it makes more sense to put the JavaScript code in an anonymous function directly below the form.*

## Pressing the Update Button

This is the second intended way we will navigate to the editmovie.php page. Therefore we will be dealing with the elseif block:

```
```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'])) {
```
```

When we get into this condition, it is because a user selected the **Update Movie** submit button. Doing so POSTs back to editmovie.php with the form variables edit_movie_submission, movie_title, movie_rating, movie_director, movie_running_time_in_minutes, and id_to_update in the $_POST[] superglobal array. Note, because genre is optional we do not check if it is set.

Speaking of id_to_update, notice I created a hidden <input> element in the form and set it to the ID of the movie and set the name attribute to id_to_update. When the form data is posted back to editmovie.php, the ID is available in the $_POST[] superglobal array so that it can be updated in the database:

```
```html
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
```
```

We need to do this to carry over the ID of the movie that was sent using a query parameter when editmovie.php was first called. Remember, HTTP requests and responses do not retain any state or information.

> *Please see the aside in the previous chapter titled: THE WEB IS STATELESS!*

Upon first entering a condition where either form or query parameters are being passed in, I create separate variables for each. Again, this is not required and can be just as readable if you created descriptive name attributes for your form fields and access them using the $_POST super global variable. However, I find it easier to type, and the purpose of the variable stands out, assuming you use sufficiently descriptive names. Add the code in Listing 18.11 immediately under and within the elseif line.

## 18. Editing Data Using the Web Application

### Listing 18.11.

```
```php
1. elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
2.     $_POST['movie_rating'], $_POST['movie_director'],
3.     $_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
4. {
5.
6.     $movie_title = $_POST['movie_title'];
7.     $movie_rating = $_POST['movie_rating'];
8.     $movie_director = $_POST['movie_director'];
9.     $movie_runtime = $_POST['movie_running_time_in_minutes'];
10.    $checked_movie_genres = $_POST['movie_genre_checkbox'];
11.    $id_to_update = $_POST['id_to_update'];
```
```

We also need to build a comma delimited string containing the movie genre from the checkbox array. Add the following code next:

```
```php
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}
```
```

Just like the addmovie.php script, a movie can have multiple genres. To store them all, we create a comma-delimited list of the chosen genres from the checkbox array. We do this by calling the implode()[4] function ONLY if the user selected at least one genre. If the user doesn't choose any genres, the checkbox array does not exist. Therefore we need to check that it is set first before calling implode(). If the user does not select a genre, we insert an empty string into the genre field of the movielisting table.

Now that we have all the updated movie listing data in the form we want, we can update the movieListing table with an SQL UPDATE query.

A SQL UPDATE query looks like this:

```
```sql
UPDATE <table_name> SET <field_name> = <value_[, ...]> WHERE <condition>
```
```

Thus, our query string and call to mysqli_query() should look like Listing 18.12

[4] implode(): https://php.net/implode

### Listing 18.12.

```
$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";

mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to update movie listing',
E_USER_ERROR
);
```

Finally, we can navigate back to the moviedetails.php using this movie's ID as a query parameter to display the updated movie details with the following lines of code:

```
$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
```

The complete listing for this elseif block looks like Listing 18.13.

### Listing 18.13.

```
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
{

$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$id_to_update = $_POST['id_to_update'];

$movie_genre_text = "";

if (isset($checked_movie_genres))
{
$movie_genre_text = implode(", ", $checked_movie_genres);
}

$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";
```
