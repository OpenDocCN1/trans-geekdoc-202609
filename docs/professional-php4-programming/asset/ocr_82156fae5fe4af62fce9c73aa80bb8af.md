For example, if we wanted to use the Triple DES algorithm to encrypt a string with a key the following code would do this:

```
```php
<?php
$key = "This is our secret key";
$string = "This is the string that we want to encrypt";

// Encrypt our string
$encrypted_message = mcrypt_ecb(MCRYPT_3DES, $key, $string, MCRYPT_ENCRYPT);
?>
```
```

To decrypt the message we would pass $encrypted_message as the string and use the MCRYPT_DECRYPT constant. The above code works with both mcrypt 2.2.x and 2.4.x. If you are in control of your environment and know mcrypt 2.4.x will always be available then we suggest using the mcrypt 2.4.x specific functions as they give more flexibility.

# ## Asymmetric Encryption

Asymmetric encryption is a type of encryption that has only become available to the general public in the past few years. A good way of thinking of this type of encryption is of a padlock and a box. For example, if Jane has a secret message to send to Alice, Alice can send Jane an open padlock. Jane puts her message into a box and locks it with the padlock that Alice sent her. Now Alice is the only person who can unlock the box and read the message, as she is the only one with the key to the padlock.

When using asymmetric encryption you give out your public key. Think of this as an open padlock. Anyone can then use this open padlock to secure a message and send it to you; you are the only person with your private key and thus the only person who can open the padlock.

This system has become the most common on the Internet – if you have ever bought something over the Internet or used PGP (Pretty Good Privacy), you will have used this system.

PHP provides support for encryption and decryption using this system via the OpenSSL system. It also supports Secure Socket Layer (SSL) connections to remote servers via CURL. The details of the algorithms used are quite complex. A list of places where you can find more information about them is available in the Resources and Further Reading section of this chapter. When possible you should use asymmetric encryption, as generally it is more secure than other forms.

# ## Network Security

When you send information over the Internet it is passed from computer to computer over the network until it reaches its destination. This means that anyone in charge of one of these computers could look at the information you are sending. This if often called packet sniffing. Most of the time this doesn’t matter as the information you are sending, such as the request for a web page, isn’t sensitive. But what happens when we are trying to access a protected area of a web site which requires a password? If we send this password in plain text then there is the possibility that someone else on the network will be able to see this password while it’s traveling from us to the server.