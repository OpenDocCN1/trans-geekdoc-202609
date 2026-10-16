
```
<?php
$input = 'My parents <i>hate</i> me, <br />' .
'therefore I <b>crack</b> websites. ' .
'<script>alert("Nice try!");</script> ' .
'<img src="explicit.jpg" />';

echo strip_tags($input, '<b><br><i>');
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_24_0.png)

Figure 1.1 Some HTML tags were stripped, but not all.

## Using Line Breaks

```
<?php
$input = "One\nTwo\r\nThree";
echo nl2br($input);
?>
```

Adding <br /> Elements at Every Line Break (nl2br.php)

How can a line break be used within HTML? That's easy: with the <br /> HTML element. However, what if there is data with \n or \r\n line breaks? Search and replace comes to mind; however, it is much easier to use a built-in PHP function: nl2br(). This parses a string and converts all line breaks to <br /> elements, as the preceding script shows.

As you can see, the line breaks are still there, but the <br /> elements were added.

## Encrypting Strings

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

PHP is there to help. The crypt() function encrypts a string using Data Encryption Standard (DES). This is a one-way encryption, so there is no way back. Also, subsequent calls to crypt() result in different results.

For instance, the string 'TopSecret' is encrypted into $1$FK3.qn2.$5i5KhnprsRb.N.SEF4GMW0 (and also $1$Sm61.i12.$0p1j3EHWk1XycncyepP1FZ0 and $1$9S3.c/3.$5I01Bm4v3cnBNOb1AECi1., but this example sticks with the first one). Checking whether a value corresponds to a result from calling crypt() can be done by calling crypt() again: crypt($value, $encryptedValue) must return $encryptedValue.

The preceding script checks whether a password provided via the URL matches the previous result of crypt(). Calling this script with the GET parameter pass=TopSecret succeeds in logging in; all other passwords fail.

**NOTE:** To provide more details: The second parameter to crypt() is the salt (initialization value) for encrypting the data. You can also use a salt when encrypting the original password. However, you do have to make sure that the salt values are unique; otherwise, the encryption is not secure. Therefore, do not use a custom salt value and let PHP do the work. Be also advised, though, that DES encryption can be cracked in about 24 hours, so it's not bulletproof any more. A more recent alternative is Advanced Encryption Standard (AES).

## Checksumming Strings

```
<?php
    $pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
    
    $md5pass = '6958b43cb096e036f872d65d6a4dc01b';
    $sha1pass = '61c2feed11e0e53eb8e295ab8da78150be12f301';
    
    if (sha1($pass) === $sha1pass) {
        echo 'Login successful.';
    } else {
        echo 'Login failed.';
    }
    
    // Alternatively, using MD5:
    // if (md5($pass) === $md5pass) {
    //     echo 'Login successful.';
    // } else {
    //     echo 'Login failed.';
    // }
?>
```

Checking Logins Using SHA1 and MD5 Hashes
(checksum.php)

PHP offers these two main functions for creating checksums:

- md5() calculates the MD5 hash of a string.
- sha1() calculates the SHA1 hash of a string.

Using crypt() with strings is similar to creating a checksum of something; It can be easily determined whether a string matches the checksum; however, it is not (easily) possible to re-create the original string from the checksum.

Two algorithms whose purpose is to do exactly this checksumming are Secure Hash Algorithm 1 (SHA1) and Message Digest Algorithm 5 (MD5). They create such a checksum, or hash. The main difference between these two algorithms and the one used in DES/crypt() is that the SHA1 or MD5 checksum of a string is always the same, so it is very easy to verify data. As Figure 1.2 shows, even the PHP distributions have a MD5 checksum mentioned on the Web site to validate the downloads.

![](img/2862989e5dc7f1b1d0bc64321737f084_28_0.png)

Figure 1.2 The PHP downloads page shows MD5 hashes of the PHP distributions.

Again, the goal is to validate a password the user provides using GET (which, as mentioned previously, is bad practice and only used for the sake of demonstration).

The correct password is, once again, 'TopSecret' with the following hashes:

- 6958b43cb096e036f872d65d6a4dc01b is the MD5 hash.
- 61c2feed11e0e53eb8e295ab8da78150be12f301 is the SHA1 hash.

From a security perspective, you should not rely on MD5 (because it can be broken with modern computers). SHA1 is not completely secure anymore, either, given the advances in hardware performance. You should consider additional safeguards:

- Before hashing a value, salt it—that is, prepend a known string, making it harder for attackers to crack it. That does not help against an attacker who uses brute force and tries almost all possible input combinations.
- Use crypt() with a more secure algorithm such as DES.

## TIP:

When calculating the MD5 or SHA1 hash of a file, no call to file_get_contents() or other file functions is required; PHP offers two functions that calculate the hashes of a file (and takes care of opening and reading in the file data):

- md5_file()
- sha1_file()

## Extracting Substrings

### substr()

```
<?php
$php = "PHP: Hypertext Preprocessor";
echo substr($php, 15, 4); //returns "Prep"
?>
```

*Extracting a Substring Using substr() (substr.php; excerpt)*

The substr() function returns a part of a string. You provide a string and the position of the first character to be extracted. (Keep in mind that the first character has the index 0). From this character on, the rest of the string is returned. If you only want to return a part of it, provide the length in the third parameter. The preceding code shows substr() in action and extracts Prep from PHP: Hypertext Preprocessor.

**TIP:** If you want to count from the end of the string, use a negative value as the second parameter of substr():

```
echo substr($php, -12, 4);
```

If you provide a negative value for the third parameter of substr() (for example, -n,) the last n characters are not part of the substring.

```
echo substr($php, -12, -8);
```

All of these calls to substr() return Prep and are included in the complete code.

## Protecting Email Addresses

### Using ASCII Codes

```php
<?php
function protectMail($s) {
    $result = '';
    $s = 'mailto:' . $s;
    for ($i = 0; $i < strlen($s); $i++) {
        $result .= '&#' . ord(substr($s, $i, 1)) . ';';
    }
    return $result;
}

echo '<a href="' .
    protectMail('email@address.xy') .
    '">Send mail</a>';
?>
```

*Protecting Email Addresses (protectMail.php)*

In the browser, you just see an email link, but the underlying HTML markup is indecipherable:

```html
<a
href="&#109;&#97;&#105;&#108;&#116;&#111;&#58;
&#101;&#109;&#97;&#105;&#108;&#64;&#97;&#100;&#100;&#114;
&#101;&#115;&#115;&#46;&#120;&#121;">Send
mail</a>
```

However, take a look at Figure 1.3: The Web browser email address correctly decoded the email address, as shown in the status bar.

![](img/2862989e5dc7f1b1d0bc64321737f084_32_0.png)

**Figure 1.3**  Machine beats man (when deciphering the email address).

Some special characters are difficult to use in strings because they are hard to enter using a keyboard. However, they all have an ASCII value. PHP offers two functions to deal with this:

- `chr()` converts the ASCII code into the corresponding character.
- `ord()` returns the ASCII code for a character.

This can be used to protect email addresses, for instance. Because spammers are writing software to search for certain patterns (email addresses) on Web pages, this might help keep spam low. The trick is to use HTML character codes for email addresses, making it much harder for spambots to find email data.

The preceding code takes an email address (in the format `email@address.xy`) as a parameter and returns `mailto:email@address.xy`—but converted into HTML entities. For instance, the m of `mailto:` has the ASCII
