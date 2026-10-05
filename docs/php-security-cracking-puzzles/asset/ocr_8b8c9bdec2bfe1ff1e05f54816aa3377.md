```
// Reading the passwords from the password file
$pass = file("password");
foreach($pass as $password) {
    // Decrypting the password guessing process
    $begin = time();
    echo decrypt_md5(trim($password));
    $end = time();
    echo " (The password was guessed in ".$end - $begin.")") seconds.<br>";
}
```

```
// The password character enumeration function
//$pass - The password to guess
// $answer - The current answer (at the first call, an empty string)
function decrypt_md5($password) {
    // Moving the contents of the dictionary into an array
    $dict = file("linux.words");
    // Looping guessing of the password
    foreach($dict as $word) {
        if(md5(trim(strtolower($word))) == $pass) return strtolower($word);
    }
}?
```

As you can see in Listing II.7.9, a chain of functions (strtolower(), trim(), and md5() ) is used to convert a dictionary word to lowercase, remove leading and trailing spaces, and obtain its MD5 hash code. The results of the script's execution are shown in Fig. II.7.6.

As you can see in Fig. II.7.6, even though the dictionary contains almost half a megabyte of data, it takes almost no time to crack all of the passwords. Of course, real passwords that are this simple are rare, the dictionary can easily be expanded to include longer and more complex passwords. Adding words in one language entered using another language keyboard is easy. The latter option is also used when cracking passwords.