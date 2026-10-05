# Part II: Solutions

```
$temp = $answer.arr[$j];
// Checking whether a new password was found
for($i = 0; $i < count($pass['pass']); $i++) {
    if (md5($pass['pass'][$i]) == $pass['answer']) {
        $pass['answer'][$i] = $temp;
}
    // Recursively calling the function to increment
    // the length of the password being guessed
    decrypt_md5($temp);
}
?
```

As can be seen in Listing II.7.8, not a single password but a two-dimensional array of values is passed to the function as the parameter. Moreover, the parameters are passed by reference, which makes it possible to preserve their values after the function is called. Each newly-generated password hash code is compared with the hash code of each password being guessed. The recursive loop is exited when all elements of the $pass['answer'] array hold nonzero values. The script's operation are shown in Fig. II.7.4.

![](bbox=[0.175, 0.67, 0.965, 0.89])

Fig. II.7.4. Guessing four-character passwords in a batch