How can a line break be used within HTML? That's easy: with the <br /> HTML element. However, what if there is data with \n or \r\n line breaks? Search and replace comes to mind; however, it is much easier to use a built-in PHP function: nl2br(). This parses a string and converts all line breaks to <br /> elements, as the preceding script shows.

As you can see, the line breaks are still there, but the <br /> elements were added.

# Encrypting Strings

```
<?php
$pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
$encpass = '$1$FK3.qn2.$S15Kh...';

if (crypt($pass, $encpass) === $encpass) {
    echo 'Login successful.';
} else {
    echo 'Login failed.';
}
?>
```

Checking Logins Using an Encrypted Password (crypt.php)

Passwords should never be stored verbatim in a database, but should instead be stored in an encrypted way. Some databases internally offer encryption; for all the others,