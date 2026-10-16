# Handling File Upload Errors

To handle errors encountered when a user tries to upload a file, we need to modify the above code. But, first, let's add an else condition after the if so we can output the error message as in Listing 19.11.

# Listing 19.11.

```
1. if (empty($file_error_message))
2. {
3.     //...
4. }
5. else
6. {
7.     // echo error message
8.     echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
9. }
```

Note that the form is redisplayed if this else executes because display_add_movie_form will already be set to true.

Before we get back to modifying the code in the if block, let's make the form sticky to handle the error condition in the else block. Near the top of the script, just below the line initializing $display_add_movie_form = true;, add the following variables Listing 19.12 initialized to empty strings and null.

# Listing 19.12.

```
1. // Initialization
2. $display_add_movie_form = true;
3. 
4. $movie_title = "";
5. $movie_rating = "";
6. $movie_director = "";
7. $movie_runtime = "";
8. $movie_genre_text = "";
9. $checked_movie_genres = null;
```

These values get set after the user submits the form in the if condition in Listing 19.13 that checks the $_POST form variables are set.