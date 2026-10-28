
## The $_SERVER array

| Index | Description |
|---|---|
| PHP_AUTH_USER | Returns the username from the authentication dialog box or a NULL value if the dialog box hasn't been displayed. |
| PHP_AUTH_PW | Returns the password from the authentication dialog box or a NULL value if the dialog box hasn't been displayed. |

## Code that forces a valid admin user (util/valid_admin.php)

```
<?php
require_once('model/database.php');
require_once('model/admin_db.php');

$email = '';
$password = '';
if (isset($_SERVER['PHP_AUTH_USER']) && isset($_SERVER['PHP_AUTH_PW'])) {
    $email = $_SERVER['PHP_AUTH_USER'];
    $password = $_SERVER['PHP_AUTH_PW'];
}

if (!is_valid_admin_login($email, $password)) {
    header('WWW-Authenticate: Basic realm="Admin"');
    header('HTTP/1.0 401 Unauthorized');
    include('unauthorized.php');
    exit();
}
?>
```

## Code that's included at the top of each protected page

```
<?php
    require_once('util/secure_conn.php');    // require a secure connection
    require_once('util/valid_admin.php');    // require a valid admin user
?>
```

## Description

- The 401 (Unauthorized) response header doesn't display the requested page and causes most modern browsers to display a dialog box that prompts the user for a username and password.
- The WWW-Authenticate header must also be included in a 401 (Unauthorized) response. This header can specify the type of authentication (usually Basic) and a name for the authentication realm.
- The code at the top of all protected pages should force a secure connection. To do that, it can include a secure_conn.php file like the one shown in figure 21-5.
- The code at the top of all protected pages should also force a valid admin user. To do that, it can include a valid_admin.php file like the one shown in this figure.
- Due to a bug, you can't use the filter_input function to access the PHP_AUTH_USER and PHP_AUTH_PW indexes of the $_SERVER array. As a result, you must access them directly.

## How to work with encrypted data

In figure 21-7, you learned how to use the sha1 function to encrypt passwords. However, the sha1 function doesn’t allow you to decrypt the encrypted password. As a result, it isn’t appropriate for encrypting certain types of data such as credit card numbers. For that type of data, you need to encrypt the data before you store it in the database, and you need to decrypt the data after you retrieve the data from the database.

To do that, you can use the functions in the mcrypt library that’s included with PHP. This library provides functions that support a wide variety of encryption and decryption algorithms. These algorithms are known as *ciphers*.

This topic shows how to use *Advanced Encryption Standard (AES)*, an encryption standard adopted by the U.S. government in 2002. This standard uses the *Rijndael cipher* that was developed by two Belgian cryptographers. The Rijndael ciphers are block ciphers that operate on blocks that have a fixed length.

To control how the cipher operates on a block, you can choose a *mode of operation* such as *cipher-block chaining (CBC)*. CBC was invented by IBM in 1976. In addition, you can use an *initialization vector (IV)* to allow the cipher to produce a unique stream independent from other streams produced by the same encryption key.

### How to encrypt and decrypt data

Figure 21-10 shows the functions, constants, and code for using the Rijndael cipher in CBC mode to encrypt and decrypt data. To start, this code sets up the variables that are needed to encrypt and decrypt a credit card number. For example, the $cipher variable is set to the value of the constant for the Rijndael cipher with a 128-bit key size, and the $mode variable is set to the value of the constant for the CBC mode. Then, the $key variable is set to the raw binary data that’s returned by the sha1 function after it encrypts the specified string for the key. Finally, the $ivs variable is set to the correct size for the initialization vector, and the $iv variable is set to the initialization vector that’s returned by the mcrypt_create_iv function.

After you set up the variables, you can use the mcrypt_encrypt function to encrypt the data. Since this function returns a string of binary data, it’s often helpful to use the base64_encode function to convert the binary data to base64. This increases the size of the data by 33%, but it helps the data survive going through the transport layers.

Conversely, you can use the mcrypt_decrypt function to decrypt the data. However, since this function accepts a string of binary data, you need to use the base64_decode function to convert any base64 data to binary data before you pass it to the mcrypt_decrypt function.

### Some functions from the mcrypt library

| Name | Description |
|------|-------------|
| mcrypt_get_iv_size($cipher, $mode) | Gets the size of the initialization vector (iv). |
| mcrypt_create_iv($ivs) | Creates the initialization vector for the specified size. |
| mcrypt_encrypt($cipher, $key, $data, $mode, $iv) | Encrypts the specified data using the specified cipher, key, mode, and initialization vector. |
| mcrypt_decrypt($cipher, $key, $data, $mode, $iv) | Decrypts the specified data using the specified cipher, key, mode, and initialization vector. |

### Some constants from the mcrypt library

| Name | Description |
|------|-------------|
| MCRYPT_RIJNDAEL_128 | The Rijndael cipher with a 128-bit key size. |
| MCRYPT_RIJNDAEL_192 | The Rijndael cipher with a 192-bit key size. |
| MCRYPT_RIJNDAEL_256 | The Rijndael cipher with a 256-bit key size. |
| MCRYPT_MODE_CBC | The CBC (Cipher-Block Chaining) mode of operation. |

### Two functions for converting between binary and base64

| Name | Description |
|------|-------------|
| base64_encode($data) | Accepts a string of binary data and returns a string of base64 data. |
| base64_decode($data) | Accepts a string of base64 data and returns a string of binary data. |

### Code that encrypts and decrypts data

```
$credit_card_no = '4111111111111111';

// Set up the variables
$cipher = MCRYPT_RIJNDAEL_128;
$mode = MCRYPT_MODE_CBC;
$key = sha1('secretKey', true); // use the sha1 function to generate a key
$ivs = mcrypt_get_iv_size($cipher, $mode);
$iv = mcrypt_create_iv($ivs);

// Encrypt the data
$data = mcrypt_encrypt($cipher, $key, $credit_card_no, $mode, $iv);
$data = base64_encode($data);
echo 'Encrypted data: ' . $data . '<br>';

// Decrypt the data
$data = base64_decode($data);
$credit_card_no = mcrypt_decrypt($cipher, $key, $data, $mode, $iv);
echo 'Decrypted data: ' . $credit_card_no . '<br>';
```

## A class for storing encrypted data

If you intend to encrypt and decrypt data in multiple places in an application, it’s helpful to use a class like the one shown in figure 21-11. That way, you can store the details about the encryption and decryption process in a single location.

The Crypt class begins with a constructor that initializes all of the properties necessary to use the 128-bit version of the Rijndael cipher in CBC mode to encrypt and decrypt data. Then, the encrypt method accepts an unencrypted string of data and returns an encrypted string of base64 data. Conversely, the decrypt method accepts a string of base64 data and returns an unencrypted string.

Once you code the Crypt class, you can use it in multiple places in your application to encrypt or decrypt data with two simple statements. To start, you code the statement that creates the Crypt object from the Crypt class. Then, you call the encrypt or decrypt method to encrypt or decrypt the data.

As you review this code, note that the encrypted data is only safe as long as the hacker isn’t able to access your source code. If the hacker is able to access your source code and the data in the database, he has access to the encryption key that’s needed to decrypt the encrypted data. As a result, it’s important to make sure that hackers won’t be able to access both the data in your database and your source code.

One way to do that is to make sure that the source code and the database aren’t stored in the same location. Another way to do that is to encode your PHP files so that they are difficult to decode even if a hacker can access them. To do that, you can search the Internet for various software products that are designed to encode PHP scripts.
