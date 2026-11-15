logged out. If the user is currently logged in, the welcome message is shown; otherwise the login form is displayed:

```
if ( isset( $_POST["login"] ) ) {
    login();
} elseif ( isset( $_GET["action"] ) and $_GET["action"] == "logout" ) {
    logout();
} elseif ( isset( $_SESSION["username"] ) ) {
    displayPage();
} else {
    displayLoginForm();
}
```

The login() function validates the username and password and, if correct, sets a session variable, $_SESSION["username"], to the logged-in user’s username. This serves two purposes: it indicates to the rest of the script that the user is currently logged in, and it also stores the user’s identity in the form of the username. (In a multi-user system this would allow the site to identify which user is logged in.) The function then reloads the page. However, if an incorrect username or password was entered, the login form is redisplayed with an error message:

```
function login() {
    if ( isset( $_POST["username"] ) and isset( $_POST["password"] ) ) {
        if ( $_POST["username"] == USERNAME and $_POST["password"] == PASSWORD ) {
            $_SESSION["username"] = USERNAME;
            session_write_close();
            header( "Location: login.php" );
        } else {
            displayLoginForm( "Sorry, that username/password could not be found. Please try again." );
        }
    }
}
```

The logout() function simply deletes the $_SESSION["username"] element to log the user out, then reloads the page:

```
function logout() {
    unset( $_SESSION["username"] );
    session_write_close();
    header( "Location: login.php" );
}
```

The final three functions are fairly self-explanatory. displayPage() displays the welcome message, along with the Logout link. displayLoginForm() displays the login page, optionally displaying an error message. Both these functions use a utility function, displayPageHeader(), to display the markup for the page header that is common to both pages.