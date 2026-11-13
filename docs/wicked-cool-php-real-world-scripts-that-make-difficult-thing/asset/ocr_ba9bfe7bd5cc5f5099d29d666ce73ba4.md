# #22: Protecting Data with a One-Way Hash

This script performs a one-way transformation on data—in other words, it can make a hash signature of someone's password, but you can't ever decrypt it and go back to the original password. Why would you want to do that? The application is in storing passwords. An administrator doesn't need to know users' passwords—in fact, it's a good idea that only the user knows his or her password. The system (and the system alone) should be able to identify a correct password; this has been the Unix password security model for years. One-way password security works as follows:

+   1. When a user or administrator creates or changes an account password, the system hashes the password and stores the result. The host system discards the plaintext password.
+   
+   2. When the user logs in to a system via any means, the entered password is again hashed.
+   
+   3. The host system throws away the plaintext password entered.
+   
+   4. This newly hashed password is compared against the stored hash.
+   
+   5. If the hashed passwords match, then the system grants access.

The host system does this without ever knowing the original password; in fact, the original value is completely irrelevant. As a side effect, should someone break into your system and steal your password database, the intruder will have a bunch of hashed passwords without any way of reversing them to find the originals. Of course, given enough time, computer power, and poorly chosen user passwords, an attacker could probably use a dictionary attack to figure out the passwords. Therefore, don't make it easy for people to get their hands on your password database, and if someone does, have everyone change their passwords.

# ENCRYPTION VS. HASHING

Technically speaking, this process is not encryption. It is a hash, which is different from encryption for two reasons:

+   * Unlike in encryption, data cannot be decrypted.
+   * It's possible (but extremely unlikely) that two different strings will produce the same hash. There's no guarantee that a hash is unique, so don't try to use a hash as something like a unique key in a database.

```
```
function hash_ish($string) {
    return md5($string);
}
```
```

The md5() function returns a 32-character hexadecimal string, based on the RSA Data Security Inc. Message-Digest Algorithm (also known, conveniently enough, as MD5). You can then insert that 32-character string into your database, compare it against other md5'd strings, or just adore its 32-character perfection.