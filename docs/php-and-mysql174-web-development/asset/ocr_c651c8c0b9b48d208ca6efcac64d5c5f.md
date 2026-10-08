# Implementing Bookmark Storage and Retrieval

You begin this script by performing the usual validations. When you know the user has selected some bookmarks for deletion, you delete them in the following loop:

```
foreach($del_me as $url) {
    if (delete_bm($valid, $url)) {
        echo 'Deleted ' . htmlspecialchars($url) . '<br>';
    } else {
        echo 'Could not delete ' . htmlspecialchars($url) . '<br>';
    }
}
```

As you can see, the delete_bm() function does the actual work of deleting the bookmark from the database. This function is shown in Listing 27.25.

+   Listing 27.25 delete_bm() Function in url_fns.php—This Function Deletes a Single Bookmark from a User's List

```
function delete_bm($user
```

As you can see, delete_bm() is also a pretty simple function. It attempts to delete the bookmark for a particular user from the database. Note that you want to remove a particular username-bookmark pair in this case. Other users might still have this URL marked.

Some sample output from running the deletion script is shown in Figure 27.10.