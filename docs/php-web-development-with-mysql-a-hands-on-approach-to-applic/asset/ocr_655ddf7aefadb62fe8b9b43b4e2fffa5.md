# 18. EDITING DATA USING THE WEB APPLICATION

```
mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing: Failed to update movie listing',
        E_USER_ERROR
    );

$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
}
```

So, let us say we want to add five minutes to a movie because IMDB[5] may not have accounted for the end credits scene. We also believe this movie fits in the “Drama” and “Fantasy” genres as well. So, our edits might look something like Figure 18.7.

The application directs the user to the “Movie Details” page, where they can immediately see the results (Figure 18.8).

# Unanticipated Navigation Methods

As in the last chapter, since the HTTP request is coming from the client. In theory, unanticipated or malicious parameters can be in the query string (or even field parameters from the HTTP POST). Therefore, all other conditions we could navigate to the editmovie.php page are unintended, and we will be dealing with the else block:

```
else // Unintended page link
{
```

As in the last chapter, since all of the above conditions are the ones where we want the application to function in a specific way, it is a best practice to put the application’s response to unpredictable behavior in an else condition. In this case, we just want to link back to the main “Movies I Like” index.php page:

[5] IMDB: https://imdb.com

![](bbox=[0.5, 0.27, 0.91, 0.53])

![](bbox=[0.5, 0.54, 0.91, 0.75])