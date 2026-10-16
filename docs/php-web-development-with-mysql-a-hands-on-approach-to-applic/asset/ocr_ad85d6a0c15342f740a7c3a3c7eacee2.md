# 18. EDITING DATA USING THE WEB APPLICATION

Listing 18.5.

```
1. $result = mysqli_query($dbc, $query)
2.
    or trigger_error('Error querying database movieListing', E_USER_ERROR);
3.
4. if (mysqli_num_rows($result) == 1)
5. {
6.    $row = mysqli_fetch_assoc($result);
7.
8.    $movie_title = $row['title'];
9.    $movie_rating = $row['rating'];
10.   $movie_director = $row['director'];
11.   $movie_runtime = $row['running_time_in_minutes'];
12.   $movie_genre_text = $row['genre'];
13.
14.   $checked_movie_genres = explode(', ', $movie_genre_text);
15. }
```

Notice that last line of code:

```
$checked_movie_genres = explode(', ', $movie_genre_text);
```

The explode()[2] function takes the comma-delimited list of genres stored for this movie and turns it into an array called $checked_movie_genres. Using it converts this string:

```
'Action,Adventure,Science Fiction'
```

into this array:

```
$checked_movie_genres[0] = 'Action'
$checked_movie_genres[1] = 'Adventure'
$checked_movie_genres[2] = 'Science Fiction'
```

So we can use it to populate the correct checkboxes for the “Genre”.

The complete code for this if block looks like Listing 18.6.