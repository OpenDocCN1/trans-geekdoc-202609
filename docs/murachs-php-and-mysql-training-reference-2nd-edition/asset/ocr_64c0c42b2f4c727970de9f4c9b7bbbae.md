# ## Functions that generate random numbers

| Function | Description |
|---|---|
| `getrandmax()` | Returns the largest integer the rand function can return. This may be a relatively small number (about 32000) on some systems. |
| `rand()` | Returns a random integer between 0 and getrandmax(). |
| `rand($lo, $hi)` | Returns a random integer between $lo and $hi. |
| `mt_getrandmax()` | Returns the largest integer the mt_rand function can return. This number is typically PHP_INT_MAX. |
| `mt_rand()` | Returns a random integer between 0 and mt_getrandmax(). This function uses the Mersenne Twister algorithm which is faster and “more random” than the algorithm used by the rand function. |
| `mt_rand($lo, $hi)` | Returns a random integer between $lo and $hi using the Mersenne Twister algorithm. |

# ## How to simulate a random dice roll

```
```php
$dice = mt_rand(1, 6);
```
```

# ## How to generate a random value between 0 and 1 with 5 decimal places

```
```php
$number = 0;
$places = 5;                 // Number of decimal places
for($i = 0; $i < $places; $i++) {
    $number += mt_rand(0,9);          // Add the random number
    $number /= 10;                    // Increase the number of decimal places
}
echo $number;                         // For example 0.46073
```
```

# ## How to generate a random password

```
```php
$password_length = 8;

// Add a symbol to the password
$symbols = '~!@#$%^&*()_-+=[]{}:;,.<>?';       // Symbols to pick from
$symbol_count = strlen($symbols);
$index = mt_rand(0, $symbol_count - 1);       // Choose a random position
$password = substr($symbols, $index , 1);     // Add the symbol

$password .= chr(mt_rand(48, 57));            // Add a number
$password .= chr(mt_rand(65, 90));            // Add an uppercase letter

// Add lowercase letters to reach the specified length
while (strlen($password) < $password_length) {
    $password .= chr(mt_rand(97, 122));
}

$password = str_shuffle($password);           // Shuffle the characters
echo $password;                               // For example, 'd7Vkg-Hf'
```
```

Figure 9-11  How to generate random numbers