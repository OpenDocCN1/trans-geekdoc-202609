# Implementing User Authentication 577

```
// give menu of options
display_user_menu();
```

```
do_html_footer();
?>
```

You might recognize the logic in the member.php script: It reuses some of the ideas from Chapter 22.

First, you check whether the user has come from the front page—that is, whether the user has just filled in the login form—and to log the user in as follows:

```
if ($username && $password) {
  // they have just tried logging in
  try {
    login($username, $password);
    // if they are in the database register the user id
    $_SESSION['valid_user'] = $username;
```

You try to log in by using a function called login(). It is defined in the user_auth_fns.php library, and we look at the code for it shortly.

If the user is logged in successfully, you register the user's session as you did, storing the username in the session variable valid_user.

```
do_html_header('Home');
check_valid_user();
// get the bookmarks this user has saved
if ($url_array = get_user_urls($_SESSION['valid_user'])) {
  display_user_urls($url_array);
}
```

```
// give menu of options
display_user_menu();
```

```
do_html_footer();
```

This page is again using the output functions. Notice that the page uses several other new functions: check_valid_user() from user_auth_fns.php, get_user_urls() from url_fns.php, and display_user_urls() from output_fns.php. The check_valid_user() function checks that the current user has a registered session. This is aimed at users who have not logged in, but are mid-session. The get_user_urls() function gets a user's bookmarks from the database, and display_user_urls() outputs the bookmarks to the browser in a table. We look at check_valid_user() in a moment and at the other two in the section on bookmark storage and retrieval.