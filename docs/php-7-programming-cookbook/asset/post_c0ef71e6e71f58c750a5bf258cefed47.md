
## Next, define a calling program called chap_12_captcha_text.php that implements a text CAPTCHA.

You first need to set up autoloading and use the appropriate classes:

```php
<?php
    require __DIR__ . './../Application/Autoload/Loader.php';
    Application\Autoload\Loader::init(__DIR__ . './../');
    use Application\Captcha\Reverse;
```

After that, be sure to start the session. You would use appropriate measures to protect the session as well. To conserve space, we only show one simple measure, `session_regenerate_id()`:

```php
session_start();
session_regenerate_id();
```

Next, you can define a function that creates the CAPTCHA; retrieves the phrase, label, and image (in this case, reverse text); and stores the value in the session:

```php
function setCaptcha(&$phrase, &$label, &$image)
{
    $captcha = new Reverse();
    $phrase = $captcha->getPhrase();
    $label = $captcha->getLabel();
    $image = $captcha->getImage();
    $_SESSION['phrase'] = $phrase;
}
```

Now is a good time to initialize variables and determine the loggedIn status:

```php
$image = '';
$label = '';
$phrase = $_SESSION['phrase'] ?? '';
$message = '';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$loggedUser = $_SESSION['user'] ?? 'guest';
```

You can then check to see whether the login button has been pressed. If so, check to see whether the CAPTCHA phrase has been entered. If not, initialize a message informing the user they need to enter the CAPTCHA phrase:

```php
if (!empty($_POST['login'])) {
    if (empty($_POST['captcha'])) {
        $message = 'Enter Captcha Phrase and Login Information';
```

If the CAPTCHA phrase is present, check to see whether it matches what is stored in the session. If it doesn't match, proceed as if the form is invalid. Otherwise, process the login as you would have otherwise. For the purposes of this illustration, you can simulate a login by using hard-coded values for the username and password:

```php
    } else {
        if ($_POST['captcha'] == $phrase) {
            $username = 'test';
            $password = 'password';
            if ($_POST['user'] == $username
                    && $_POST['pass'] == $password) {
                $loggedIn = TRUE;
                $_SESSION['user'] = strip_tags($username);
                $_SESSION['isLoggedIn'] = TRUE;
            } else {
                $message = 'Invalid Login';
            }
        } else {
            $message = 'Invalid Captcha';
        }
    }
}
```

You might also want to add code for a logout option, as described in the Safeguarding the PHP session recipe:

```php
} elseif (isset($_POST['logout'])) {
    session_unset();
    session_destroy();
    setcookie('PHPSESSID', 0, time() - 3600);
    header('Location: ' . $_SERVER['REQUEST_URI']);
    exit;
}
```

You can then run `setCaptcha()`:

```php
setCaptcha($phrase, $label, $image);
```

Lastly, don't forget the view logic, which, in this example, presents a basic login form. Inside the form tag, you'll need to add view logic to display the CAPTCHA and label:

```html
<tr>
    <th><?= $label; ?></th>
    <td><?= $image; ?><input type="text" name="captcha" /></td>
</tr>
```

Here is the resulting output:

![](img/39390f6d56c5a83b28db083a8bd5185c_495_0.png)

To demonstrate how to use the image CAPTCHA, copy the code from `chap_12_captcha_text.php` to `chap_12_captcha_image.php`. We define constants that represent the location of the directory in which we will write the CAPTCHA images. (Be sure to create this directory!) Otherwise, the autoloading and use statement structure is similar. Note that we also define a TrueType font. Differences are noted in **bold**:

```php
<?php
define('IMAGE_DIR', __DIR__ . '/captcha');
define('IMAGE_URL', '/captcha');
define('IMAGE_FONT', __DIR__ . '/FreeSansBold.ttf');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Captcha\Image;

session_start();
session_regenerate_id();
```

> **Important!** Fonts can potentially be protected under copyright, trademark, patent, or other intellectual property laws. If you use a font for which you are not licensed, you and your customer could be held liable in court! Use an open source font, or one that is available on the web server for which you have a valid license.

Of course, in the `setCaptcha()` function, we use the Image class instead of Reverse:

```php
function setCaptcha(&$phrase, &$label, &$image)
{
    $captcha = new Image(IMAGE_DIR, IMAGE_URL, IMAGE_FONT);
    $phrase  = $captcha->getPhrase();
    $label = $captcha->getLabel();
    $image = $captcha->getImage();
    $_SESSION['phrase'] = $phrase;
    return $captcha;
}
```

Variable initialization is the same as the previous script, and login processing is identical to the previous script:

```php
$image = '';
$label = '';
$phrase = $_SESSION['phrase'] ?? '';
$message = '';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$loggedInUser = $_SESSION['user'] ?? 'guest';

if (!empty($_POST['login'])) {
// etc. -- identical to chap_12_captcha_text.php
```

Even the view logic remains the same, as we are using `getImage()`, which, in the case of the image CAPTCHA, returns directly usable HTML. Here is the output using a TrueType font:

![](img/39390f6d56c5a83b28db083a8bd5185c_496_0.png)

## There's more...

If you are not inclined to use the preceding code to generate your own in-house CAPTCHA, there are plenty of libraries available. Most popular frameworks have this ability. Zend Framework, for example, has its `Zend\Captcha` component class. There is also reCAPTCHA, which is generally invoked as a service in which your application makes a call to an external website that generates the CAPTCHA and token for you. A good place to start looking is the [http://www.captcha.net/](http://www.captcha.net/) website.

## See also

For more information on the protection of fonts as intellectual property, refer to the article present at [`https://en.wikipedia.org/wiki/Intellectual_property_protection_of_typefaces`](https://en.wikipedia.org/wiki/Intellectual_property_protection_of_typefaces).

## Encrypting/decrypting without mcrypt

It is a little-known fact among members of the general PHP community that the `mcrypt` extension, the core of most PHP-based encryption considered secure, is anything but secure. One of the biggest issues, from a security perspective, is that the `mcrypt` extension requires advanced knowledge of cryptography to successfully operate, which few programmers have. This leads to gross misuse and ultimately problems such as a 1 in 256 chance of data corruption. Not good odds. Furthermore, developer support for `libmcrypt`, the core library upon which the `mcrypt` extension is based, was *abandoned* in 2007, which means the code base is out-of-date, bug-ridden, and has no mechanism to apply patches. Accordingly, it is extremely important to understand how to perform strong encryption/decryption *without* using `mcrypt`!

## How to do it...

1.  The solution to the problem posed previously, in case you're wondering, is to use `openssl`. This extension is well maintained, and has modern and very strong encryption/decryption capabilities.

    > **Important**
    >
    > In order to use any `openssl*` functions, the `openssl` PHP extension must be compiled and enabled! In addition, you will need to install the latest OpenSSL package on your web server.

2.  First, you will need to determine which cipher methods are available on your installation. For this purpose, you can use the `openssl_get_cipher_methods()` command. Examples will include algorithms based on **Advanced Encryption Standard** (AES), **BlowFish** (BF), **CAMELLIA**, **CAST5**, **Data Encryption Standard** (DES), **Rivest Cipher** (RC) (also affectionately known as **Ron's Code**), and **SEED**. You will note that this method shows cipher methods duplicated in upper and lowercase.

3.  Next, you will need to figure out which method is most appropriate for your needs. Here is a table that gives a quick summary of the various methods:

| Method | Published | Key size (bits) | Key block size (bytes) | Notes |
| :--- | :--- | :--- | :--- | :--- |
| camellia | 2000 | 128, 192, 256 | 16 | Developed by Mitsubishi and NTT |
| aes | 1998 | 128, 192, 256 | 16 | Developed by Joan Daemen and Vincent Rijmen. Originally submitted as Rijndael |
| seed | 1998 | 128 | 16 | Developed by the Korea Information Security Agency |
| cast5 | 1996 | 40 to 128 | 8 | Developed by Carlisle Adams and Stafford Tavares |
| bf | 1993 | 1 to 448 | 8 | Designed by Bruce Schneier |
| rc2 | 1987 | 8 to 1,024 (defaults to 64) | 8 | Designed by Ron Rivest (one of the core founders of RSA) |
| des | 1977 | 56 (+8 parity bits) | 8 | Developed by IBM, based on work done by Horst Feistel |

4.  Another consideration is what your preferred block cipher **mode of operation** is. Common choices are summarized in this table:

| Mode | Stands For | Notes |
| :--- | :--- | :--- |
| ECB | Electronic Code Book | Does not require initialization vector (IV); supports parallelization for both encryption and decryption; simple and fast; does not hide data patterns; not recommended!!! |
| CBC | Cipher Block Chaining | Requires IV; subsequent blocks, even if identical, are XOR'ed with previous block, resulting in better overall encryption; if the IVs are predictable, the first block can be decoded, leaving remaining message exposed; message must be padded to a multiple of the cipher block size; supports parallelization only for decryption |
| CFB | Cipher Feedback | Close relative of CBC, except that encryption is performed in reverse |
