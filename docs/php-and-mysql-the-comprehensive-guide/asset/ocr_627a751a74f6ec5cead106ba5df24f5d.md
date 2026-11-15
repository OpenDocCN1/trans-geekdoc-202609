# More Complex Tests

In the previous examples, `match` was used for simple value checks. However, more complex checks are also conceivable. In this case, the truth value `true` is used as the variable:

```
$result = match (true) {
```

In the respective line for this case, we then replace the value with a check that returns a truth value as the result:

```
$age >= 10 && $age < 30 => "You are between 10 and 29.",
```

As soon as this check returns `true` for a line, `match` strikes and accepts the return value for this line—that is, for the following line in the example:

```
$age >= 50 && $age < 70 => "You are between 50 and 69.",
```

> **Note**
> The actual test is moved to the test line here. This also means that you can test at this point without strict typing. In our case, `>` and `<` are used as operators. This means that the check would also return `true` if `$age` were a string instead of an integer.

The following lines are ignored, even if their checks would also return `true`.

```
$age = 55;
$result = match (true) {
    $age >= 10 && $age < 30 => "You are between 10 and 29.",
    $age >= 30 && $age < 50 => "You are between 30 and 49.",
    $age >= 50 && $age < 70 => "You are between 50 and 69.",
    default => "You do not fit into any of the categories."
};
echo $result;
```

Listing 5.20 "match" with Complex Checks ("match_true.php")

![](bbox=[0.13, 0.71, 0.86, 0.86])

Figure 5.19 The Complex Check Has Found the Correct Value