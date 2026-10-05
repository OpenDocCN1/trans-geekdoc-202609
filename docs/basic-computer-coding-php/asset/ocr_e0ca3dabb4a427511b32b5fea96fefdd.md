# non_static.php

Static Variable is a variable that has been allocated “statically”, meaning that its lifetime (or "extent") is the entire run of the program.

```
<?php

function nonstatic() {

  $value = 0;
  $value += 1;

  return $value;
}

nonstatic();
nonstatic();
nonstatic();
nonstatic();

echo nonstatic(), "\n";

?>
```

In the above example, we have a normal, non-static variable. We increment the variable each time the function is called. We call the function 5 times. However, non-static variables are initiated for each call of the function. After 5 function calls the $value equals to 2.
The static variables are initiated only once, when the function is first called. They retain their value afterwards.

# static.php

```
<?php

function staticfun() {
```