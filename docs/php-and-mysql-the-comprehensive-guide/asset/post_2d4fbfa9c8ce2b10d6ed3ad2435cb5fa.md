
For demonstration purposes, we will use an existing captcha—namely, the one from the PEAR Text_CAPTCHA project, which can be installed as follows:

```php
pear install Text_CAPTCHA
```

> **Note**
>
> If a stable version of the package has not yet been released by the time the book is published, you must explicitly state the status of the package—for example, as follows:
>
> `pear install Text_CAPTCHA-alpha`
>
> You can find the current version number on the package homepage at <http://s.prs.co/v602248>. You also need the Image_Text and Text_Password PEAR packages beforehand so that the installation of the captcha package works.

After installing the package, you can request a captcha graphic as follows and receive it back—in our example, in PNG format:

```php
<?php
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image'); //graphic CAPTCHA
$c->init(200, 80); //200, 80 pixels

$phrase = $c->getPhrase(); //text in CAPTCHA
$png = $c->getCAPTCHAAsPNG();
?>
```

However, this alone does not achieve much. You also need to take care of the administration. The following example is based directly on the package documentation. The term in the captcha is stored in a session variable and checked in this way. But first, the PHP session support is started:

```php
session_start();
```

The $ok variable remembers whether the captcha has already been solved:

```php
$ok = false;
```

The text that is displayed in the browser is saved in the $info variable:

```php
$info = "Please enter text in the image!";
```

If a captcha is to be displayed again ($ok is then false), a new graphic is generated, and the resulting PNG image is saved in a file. This file is then displayed with a form field for text input:

```php
if (!$ok) {
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image');
$c->init(200, 80);

$_SESSION["phrase"] = $c->getPhrase();

file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

echo "<form method=\"POST\">" .
"<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
"<input type=\"text\" name=\"phrase\" />" .
"<input type=\"submit\" /></form>";
}
```

> > **Tip**
> > Appending the current time in epoch format (using the `time()` call) prevents the web browser from saving old captchas in the cache.

But what happens when a user tries to solve the captcha? In this case, the input is compared with the captcha solution word in the session variable, and the `$ok` variable (and the `$info` variable) is set accordingly:

```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
$_POST["phrase"] == $_SESSION["phrase"]) {
$info = "OK!";
$ok = true;
unset($_SESSION['phrase']);
} else {
$info = "Please try again!";
unset($_SESSION['phrase']);
}
unlink(sha1(session_id()) . ".png");
}
```

The status message is output at the end:

```php
echo "<p>$info</p>";
```

The following listing shows the complete code for this example: Figure 32.10 shows the output.

```php
<?php
    session_start();
    $ok = false;
    $info = "Please enter text in the image!";
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
            strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
            $_POST["phrase"] === $_SESSION["phrase"]) {
            $info = "OK!";
            $ok = true;
            unset($_SESSION['phrase']);
        } else {
            $info = "Please try again!";
            unset($_SESSION['phrase']);
        }
        unlink(sha1(session_id()) . ".png");
    }

echo "<p>$info</p>";

if (!$ok) {
    require_once 'Text/CAPTCHA.php';

    $c = Text_CAPTCHA::factory('Image');
    $c->init(200, 80);

    $_SESSION["phrase"] = $c->getPhrase();

    file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

    echo "<form method=\"POST\">" .
        "<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
        "<input type=\"text\" name=\"phrase\" />" .
        "<input type=\"submit\" /></form>";
}
?>
```

### Listing 32.10 The Code for Using the Captcha ("captcha-code.php")

### Figure 32.10 The Captcha in Use

## 32.8 Encrypt Passwords

Finally, we will look at another security issue that is also well covered by PHP, even if the underlying programming error is not as obvious as with XSS, SQL injection, or CSRF. The topic here is the secure storage of passwords. Countless cases from the recent (or even older) past have shown that many companies are very careless when it comes to data storage. The Have I Been Pwned website (https://haveibeenpwned.com) is a well-known resource that is always active in major cases of stolen access data and offers a test that tells you whether your own email address has been successfully tapped.

### Figure 32.11 Have I Been Pwned

There are many reasons for successful intrusions—for example, SQL injection or simply an insider accessing and forwarding data within the company. Passwords are of particular interest here. If these are stored in plain text in a database, the catastrophe is as big as it gets. For this reason, encryption is the be-all and end-all. However, there are potential disadvantages here too: The web application may have to decrypt the data again, such as when a login attempt is made. If an attacker succeeds in reading the data from an application, they may also have access to the application itself and therefore to the key.

For this reason, it became common practice years ago for many web applications not to store passwords at all, but only a kind of fingerprint. The password can no longer be recovered from this fingerprint. However, when a user logs in to the application, the web application creates a new fingerprint from the specified password. This is then identical to the saved one and the login works.

However, if the attacker gains access to the application’s database, he only has fingerprints, but no “real” passwords. Although the attack was successful, anyone using the same password elsewhere does have to change it in a matter of seconds (but should still not take too long to do so).

The method chosen for the fingerprint is crucial, though—in the past, typically MD5 (and the PHP function for this, md5()) and SHA1 (or sha1() in PHP) have been used. This procedure has no longer been secure for some time; the password can be recovered from an MD5 hash (as the fingerprint is called) with standard hardware and in a comparably short time—or another password can be determined that has the same MD5 hash. The somewhat more secure SHA1 variant resists decryption for a little longer, but this method is now also considered to have been cracked.

Of course, there are other encryption and hashing mechanisms, but they have always been a bit cumbersome to use, even in PHP. For this reason, there is the Password Hashing API. All information about this built-in extension can be found at http://php.net/password. You can use this functionality without any configuration or further setup steps. Internally, the functionality offered relies on the powerful crypt() function, but the Password Hashing API itself condenses everything into four individual functions:

- password_hash()
  - Generates a hash from an input (such as a password)
- password_verify()
  - Checks whether an input matches a hash
- password_get_info()
  - Provides information about a hash
- password_needs_rehash()
  - Checks whether a hash has certain properties

The first two functions are the most important. The procedure is relatively simple: use `password_hash()` to generate a hash. In addition to the input itself, the algorithm to be used must also be specified; PHP offers two constants, `PASSWORD_DEFAULT` (by default, this is `bcrypt`, but this could change in future PHP versions) and `PASSWORD_BCRYPT`.

Here's an example:

```php
password_hash("top secret", PASSWORD_DEFAULT);
```

And here's a possible output:

```
$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu
```

This hash now ends up in the database; the password is not visible from this. However, we can use `password_verify()` to check whether an input matches the hash:

```php
password_verify("top secret", "$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu");
```

The return value is then, unsurprisingly, true. In this way, you could, for example, adapt the login logic from *Chapter 15, Listing 15.6*.

As the third parameter for `password_hash()`, you can specify an option for the encryption using an associative array: cost, the algorithmic cost of generating the hash value. The higher, the better, but the longer the calculation takes. 10 is the default value, but so long as the performance is good, you can also increase it.

Here's a small example of this:

```php
password_hash("top secret", PASSWORD_BCRYPT, ["cost"=>15]);
```

For example, this code generated the following return value during a test run—after waiting a few seconds:

```
$2y$15$LyWFa9f0JQB81Cfh1bN9KumpOXY0tKgfw8br3j1Qzt7.eStTPGBjG
```

As you can see, the hash also contains information about the algorithm and the costs. Everything after that is the actual hash.

**Note**

In the past, it was also possible to specify the value *salt*—the "salt" that is appended to the string to be hashed in order to make it even more difficult to trace the hash. PHP uses a random and safe salt value every time, so this configuration option has been removed in PHP 8.

This gives you access to a very simple API that still encrypts passwords securely. MD5 and SHA1 hashes are no longer sufficient.
