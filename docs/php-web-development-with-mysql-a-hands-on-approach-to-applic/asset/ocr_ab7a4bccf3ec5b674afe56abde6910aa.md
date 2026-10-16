# Anticipating Paths to the Edit Page

There are two expected ways and various unanticipated ways to navigate to the editmovie.php script. The first expected way is for the user to select the “edit it” link on the “Movie Details” page as in Figure 18.4.

![](bbox=[0.48, 0.13, 0.88, 0.23])

Doing so sends a single query parameter contained in the id_to_edit element of the $_GET super global variable.

The second expected way is when the user selects “Update Movie.” When the user successfully enters the required data in the form fields and submits the form, we will want to update the data for this movie in the movieListing table of the Movie database. You can find the submitted form fields in the $_POST super global variable.

All other mechanisms are unanticipated. So this essentially gives us three choices we are looking for. Therefore, the best way to deal with these three choices is to create an if/elseif/else block of code structure in Listing 18.2.

# Listing 18.2.

```
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

if (isset($_GET['id_to_edit']))
{
    // ...
}
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
        $_POST['movie_rating'], $_POST['movie_director'],
        $_POST['movie_running_time_in_minutes']))
{
    // ...
}
else // Unintended page link
{
    // ...
}
```

> In the elseif block of code above: even though we are validating the field inputs on the client-side, it is still important to validate the field inputs on the server-side.