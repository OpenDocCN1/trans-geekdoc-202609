
Note that the FIRST constant is declared in the first file and is checked in the 2.php handler. If the constant was not declared, the second file was not included in the first with the help of the include instruction. This means that an attempt to access the file directly is being made.

The if (!defined('FIRST')) exit(); instruction prevents access to the file for editing data by bypassing the HTML authorization form.

## II.7.2. Password Encryption

A convenient way to encrypt the password data is to employ irreversible encryption, that is, to encrypt the data so that it cannot be decrypted. It may seem strange at first, but this type of encryption is used quite often. Functions for irreversible encryption are called hashing functions. They create a unique "fingerprint" of the encoded string. The most common hashing algorithm is MD5, which is implemented using the same-name-function, as follows:

```
string md5(string str [, bool raw_output])
```

The function takes the str string that must be encrypted and returns its unique 128-bit hash code. If the value of the optional argument raw_output is true, a binary 16-character string is returned. The probability of two strings producing the same code approaches zero.

The analogous function md5_file() is often used to create a unique hash code for a file sent over a network. After downloading a file, its integrity can be verified by calculating its MD5 hash code and comparing it against the hash code provided by the developer. This procedure makes it possible to ensure that files transferred over a network are not corrupted. Also, it can be used to prevent the alteration of files and is often employed to protect large software distributions.

![](img/a893312ec68b8170fe567f785e95c06e_278_0.png)

The code for registering users (Listing II.3.30) must be modified by adding code to encrypt their passwords using the md5() function (Listing II.7.3).

![](img/a893312ec68b8170fe567f785e95c06e_278_1.png)

Listing II.7.3 shows only part of the code; the complete user registration code can be found in the scripts/7.7.2/1.php file on the accompanying CD-ROM.

![](img/a893312ec68b8170fe567f785e95c06e_278_2.png)

### Listing II.7.3. The user registration script

```
<?php
/////////////////////////////////////////////////
// The user registration block
/////////////////////////////////////////////////
// Storing the data in a text file
$fd = fopen($filename
fwrite($fd,$str);
close($fd);
...
?>
```

As you can see in Listing II.7.3, the $_POST['pass'] is processed by the md5() function before it is saved in the file.

Now, when passwords are encrypted, the user authorization system (Listings II.7.1 and II.7.2) must be modified. A block in Listing II.7.1 must be modified as shown in Listing II.7.4 in bold.

## Listing II.7.4. The modified user registration code

```php
<?php
if(md5($_POST['pass']) != $temp['password'][$index])
{
    exit("Wrong password!");
}
// If the correct password is entered,
// and displaying the form for editing data
include "2.php"; // The handler of the second HTML form
?>
<table>
<form method="post">
<input type="hidden" name="name"
value='<?php htmlspecialchars($temp['name'][$index]); ?>'>
<input type="hidden" name="pass"
value='<?php htmlspecialchars($_POST['pass]); ?>'>
<input type="hidden" name="edit" value=edit
<tr>
<td>Password:</td>
<td><input type="password" name="passw"
value='<?php htmlspecialchars($_POST['pass]); ?>'></</td>>
</tr>
<tr>
<td>Password:</td>
<td><input type="password" name="pass again"
value='<?php htmlspecialchars($_POST['pass]); ?>'></</td>>
</tr>
<tr>
<td>Email:</td>
<td><input type=text name=email value="<?= htmlspecialchars($temp['email'][$index]); ?>"></</td>>
</tr>
<tr>
<td>URL:</td>
<td><input type=text name='url' value="<?= htmlspecialchars($temp['url'][$index]); ?>"></</td>>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type="submit" value='Edit'></</td>>
</tr>
</form>
</table>
<?php
}
?>
```

In addition, the handler of the editing form must be modified so that it encrypts the new password (Listing II.7.5).

## Listing II.7.5. The modified editing form handler

```php
<?php
///////////////////////////////////////////////////////
// Editing the data file
///////////////////////////////////////////////////////
$arr = file($filename);
$linefile = array();
foreach($arr as $line)
{
    // Breaking the line at dividers
    $data = explode(":", $line);
    if($data[0] == $temp['name'][$index])
    {
        // Building a new string to replace the old one
        $linefile[] = $_POST['name'].":".md5($_POST['passw']).":".$_POST['email'].":".$_POST['url'];
        $_POST['passw'] = $_POST['passw'];
        $temp['email'][$index] = $_POST['email'];
        $temp['url'][$index] = $_POST['url'];
    }
    else
    $linefile[] = trim($line);
}
?>
```

### II.7.3. Guessing a Password

A password is guessed by going through possible combinations of characters, starting with a one-character password and increasing the length by one character after all combinations of the previous length are exhausted. In this case, you know that the password length n is greater than four and that only lowercase letters are used. Because character codes occupy a continuous range from 97 to 122, they are usually generated in a loop. Nevertheless, the script more flexible and allow characters to be used, all possible characters placed into the $pass array. Because the password length is generally not known and can vary, the script is constructed using a recursive function named `decrypt_md5($pass, $answer)`, that accepts two parameters. The first parameter is the encrypted string. The other parameter is used for technical purposes: the current password is sent using it, and its value is a null string when the function is called for the first time. The function returns the guessed password or an empty string if the length of the current password exceeds the specified limit, which is four characters.

### II.7.6. Guessing an MD5 password

```php
<?php
// Setting an unlimited time for the script
set_time_limit(0);

// Reading the passwords from the password file
$pass = file("password");

foreach($pass as $password)
{
  // Timing the password-guessing process
  $begin = time();
  echo decrypt_md5(trim($password));
}

// The password enumeration function
// $pass - The password to guess
// $answer - The current answer (at the first call, an empty string)
function decrypt_md5($pass, $answer)
{
  $arr = array('a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z');
  // Assuming that the password is no longer than four characters
  $max_number = 3;
  if (strlen($answer) > $max_number) return;

  for($j = 0; $j < count($arr); $j++) {
    $temp = $answer.$arr[$j];
    if (md5($temp) == $pass) return $temp;
    // Recursively calling the function to increment the length of the password being guessed
    $result = decrypt_md5($pass, $temp);
    // If the function returns a non-empty string, the password has been guessed and no further search is necessary
    if (strlen($result) > 0) return $result;
  }
}
?>
```

The script may take considerable time to execute; therefore, the limitation on the script-execution time is lifted at the start of the script code by calling the `set_time_limit()` function. The function's only parameter is an integer specifying the new maximum script-execution time. If this parameter equals zero, the execution-time is unlimited.

Afterward, the contents of the `password` file are broken into strings. These are then placed into the `$pass` array, from which they are passed in a loop to the recursive function `decrypt_md5()`.

![](img/a893312ec68b8170fe567f785e95c06e_283_0.png)

> Note that strings from the `$pass` array are passed through the `trim` function to strip them of invisible trailing characters `\r\n`, which may remain in the strings.

The function tries possible password values from `a` to `ab`, `ac`, and to `azzz`. When the value of the `$answer` variable becomes `aaaa`, the function moves to the `b` character and tries all possible combinations from `b` through `bzzz`. In this way, all characters from the `$arr` array are used. As soon as the password is found, the function returns and exits the recursive loop through the `if(strlen($result) > 0) return $result;` check.

In addition to guessing passwords, the script times how long it takes to guess each password. The results of the script's execution are shown in Fig. II.7.1.
As you can see, the later in the alphabet the letter, the longer it takes to guess the password. If it is known that the password owner passwords starting with last letter of the alphabet, the guessing process can be sped up by reversing the `$arr` array.

![](img/a893312ec68b8170fe567f785e95c06e_283_1.png)

Fig. II.7.1. Guessing passwords by character enumeration
