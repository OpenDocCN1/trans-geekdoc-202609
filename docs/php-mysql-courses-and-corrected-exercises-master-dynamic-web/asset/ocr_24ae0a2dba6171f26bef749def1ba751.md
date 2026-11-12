```
declare(strict_types=1);

function add(int $a, int $b): int {
    return $a + $b;
}
```

To declare the type of parameters, simply specify the desired type in front of each parameter, and to specify the type of value returned by a function, simply addition a colon (:) after the list of parameters, followed by the expected return type.

Let's modify the previous example by specifying the parameter types and the output type: