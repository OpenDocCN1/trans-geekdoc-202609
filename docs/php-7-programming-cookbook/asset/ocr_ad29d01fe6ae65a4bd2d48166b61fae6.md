7. To perform encryption, use `openssl_encrypt()`. Here are the parameters that should be passed:

| Parameter | Notes |
| :--- | :--- |
| Data | Plain text you need to encrypt. |
| Method | One of the methods you identified using `openssl_get_cipher_methods()`. Identified as follows:*method_key_size-cipher_mode*<br><br>So, for example, if you want a method of AES, a key size of 256, and GCM mode, you would enter `aes-256-gcm`. |
| Password | Although documented as *password*, this parameter can be viewed as a *key*. Use `random_bytes()` to generate a key with a number of bytes to match the desired key size. |
| Options | Until you gain more experience with openssl1 encryption, it is recommended you stick with the default value of 0. |
| IV | Use `random_bytes()` to generate an IV with a number of bytes to match the cipher method. |

8. As an example, suppose you wanted to choose the AES cipher method, a key size of 256, and XTS mode. Here is the code used to encrypt:

```
```
$plainText = 'Super Secret Credentials';
$key = random_bytes(16);
$method = 'aes-256-xts';
$cipherText = openssl_encrypt($plainText, $method, $key, 0, $iv);
```
```

9. To decrypt, use the same values for $key and $iv, along with the `openssl_decrypt()` function:

```
```
$plainText = openssl_decrypt($cipherText, $method, $key, 0, $iv);
```
```

# How it works...

In order to see which cipher methods are available, create a PHP script called `chap_12_openssl1_encryption.php` and run this command:

```
```
<?php
  echo implode(',', openssl_get_cipher_methods());
```
```