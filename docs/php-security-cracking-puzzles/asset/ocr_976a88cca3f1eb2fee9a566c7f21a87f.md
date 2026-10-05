Increasing the number of characters in the possible character set increases the guessing time significantly. However, the guessing time increases even more when the password length is increased. Thus, the password-guessing time of the script in Listing II.7.6 — using only the lowercase English letters — increases by an order of magnitude when the password length is increased by only one place, to five characters (Fig. II.7.3).

![](bbox=[0.166, 0.273, 0.952, 0.467])

> Fig. II.7.3. Guessing five-character passwords

When than one password must be guessed, the password-guessing time can be saved by checking each possible combination against all unknown-words instead of running through all possible character combinations for each password. A script for processing at all possible time four passwords from the password file of Listing II.7.6 is shown in Listing II.7.8.

# II.7.8. The modified password-guessing script

```
<?php
// Setting an unlimited execution time for the script
set_time_limit(0);

// Reading the passwords from the password file
$temp = file("password");
// Timing the password guessing process
$begin = time();
$i = 0;
foreach($temp as $password) {
    $pass['password']][$i] = trim($password);
```