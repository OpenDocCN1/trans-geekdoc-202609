First, you can check for the session variable. The code from the beginning of this phrase must be included (with require_once) in all pages that are only accessible for authorized users.

The script login.php, to which the preceding code redirects the user, contains an HTML form (see also Figure 5.9) and checks whether the provided data is correct (you might have to add your own users and passwords). As you might have seen, the previous URL is provided as a GET parameter, so, if available, the login code redirects the user back to where she came from:

```
```php
<?php
    if (isset($_POST['user']) && $_POST['user'] ==
        'Damon' &&
        isset($_POST['pass']) && $_POST['pass'] ==
            'secret') {
    session_start();
    $_SESSION['authorized'] = 'ok';
    $url = (isset($_GET['url'])) ?
        $nl2br($_GET['url'] :
        'index.php';
    header("Location: $url");
    }
?>
```
```

*Checking the User Credentials (login.php; excerpt)*

And that's it! The script secret.php in the download archive contains some quite secret information and is protected by the code in the previous listings.