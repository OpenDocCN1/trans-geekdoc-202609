# Listing 27.23 get_user_urls() Function from url_fns.php—This Function
Retrieves a User's Bookmarks from the Database

```
function get_user_urls($username) {
    //extract from the database all the URLs this user has stored

    $conn = db_connect();
    $result = $conn->query("select bm_URL
                               from bookmark
                               where username = ''.$username.''");
\n    if (!$result) {
        return false;
    }

    //create an array of the URLs
    $url_array = array();
    for ($count = 0; $row = $result->fetch_row(); ++$count) {
        $url_array[$count] = $row[0];
    }
    return $url_array;
}
```

Let's briefly step through the get_user_urls() function. It takes a username as a parameter and retrieves the bookmarks for that from the database. It returns an array of URLs or false if the bookmarks could not be retrieved.

The array from get_user_urls() can be passed to display_user_urls(). This is a simple HTML output function to print the user's URLs in a nice table format, so we don't include it here. Refer to Figure 27.6 to see what the output looks like. The function actually puts the URLs into a form. Next to each URL is a checkbox that enables the user to mark bookmarks for deletion. We look at this capability next.

# Deleting Bookmarks

When a user marks bookmarks for deletion and clicks on the Delete BM link on the menu, containing one of the check boxes is produced by the following code in the display_user_urls() function
echo "<tr bgcolor=\\$color\"><td>
    <a href=\\

The name of each input is del_me]. This means that, in the PHP script activated by this form, you have access to an array called del_me that contains all the bookmarks to be deleted.