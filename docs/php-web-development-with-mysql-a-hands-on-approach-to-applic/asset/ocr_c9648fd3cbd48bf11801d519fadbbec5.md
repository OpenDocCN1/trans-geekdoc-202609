# Listing 18.8.

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

# Using Bootstrap’s Client-side Validation

As in the addmovie.php script, we are using Bootstrap's client side validation. This requires we do the following:

+   1. Set the form's class attribute to needs-validation and adding the novalidate attribute:

```
<form class="needs-validation" novalidate ...
```

[3] in_array(): https://php.net/in_array