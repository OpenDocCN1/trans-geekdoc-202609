```
```php
if (isset($_SESSION['user_id'])) {
    echo '<p class="error">Thank you for your interest in this
    content. Unfortunately your account has expired. Please
    <a href="renew.php">renew your account</a> in order to
    access this file.</p>';
} else {
    echo '<p class="error">Thank you for your interest in this
    content. You must be logged in as a registered user to view this
    file.</p>';
}
echo "<div>{$row['description']}</div>";
include ('./includes/footer.html');
} // End of user IF-ELSE.
```
```

If the user is logged in but inactive (that is, their account has expired), they'll be asked to renew their account (Figure 5.17). If the user is not logged in, they'll be asked to log in (Figure 5.18).

![](bbox=[0.17, 0.45, 0.55, 0.54])

Figure 5.17

![](bbox=[0.57, 0.45, 0.93, 0.54])

Figure 5.18

+   8. Complete the conditionals:

```
```
} // End of mysqli_num_rows() IF.
} // End of file_exists() IF.
} // End of $_GET['id'] IF.
```
```

+   9. Indicate a problem and complete the page:

```
```php
if (!$valid) {
    $page_title = 'Error!';
    include ('./includes/header.html');
    echo '<p class="error">This page has been accessed in error.</p>';
    include ('./includes/footer.html');
}
?>
```
```

If the page did not receive an ID value corresponding to a database record and an actual file on the server, the user will see an error message like that in Figure 5.9.

+   10. Save the file and test it by clicking a link on pdfs.php.