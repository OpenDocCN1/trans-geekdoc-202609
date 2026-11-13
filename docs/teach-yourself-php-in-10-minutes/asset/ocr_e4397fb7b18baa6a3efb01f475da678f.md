Although the encrypted string cannot be decoded back to the original password, every time you run crypt on the same password with the same salt , the result is the same. Knowing this, you can store only the encrypted version of the password and compare it to the freshly encrypted user input.

> **Salt s** If you do not specify a salt , a random one is chosen so subsequent calls to crypt will product different results. A two-character salt , as used by Unix password files and htpasswd , is sufficient.

How a string encoded using crypt looks may vary between different web servers as a system-level encryption library is used. Encrypted passwords are not guaranteed to be portable between different systems. The revised login.php file is shown in Listing 15.3 , but be aware that the encrypted passwords shown may not be valid for your system.

# Listing 15.3. A Login Processor Script with Encrypted Passwords

```
<?php
session_start();
$passwords = array("chris" => "ZXsDiRf.VBlWQ",
    "damon" => "bQLXBRzdBci7M",
    "shelley" => "KkTH39mVsoclc",
    "vanessa" => "69SvRIB9QVukk");
if (!$_POST["username"] or !$_POST["password"]) {
    echo "You must enter your username and password";
    exit;
}
$salt = substr($passwords[$_POST["username"]], 0, 2);
if (crypt($_POST["password"], $salt)
    == $passwords[$_POST["username"]]) {
    echo "Login successful";
    $_SESSION["auth_username"] = $_POST["username"];
} else {
    echo "Login incorrect";
}
?>
```

The salt is always found in the first two characters of the encrypted string, so you assign these two characters to $salt to use in the call to crypt . Other than this, the process is identical to using plain-text passwords.