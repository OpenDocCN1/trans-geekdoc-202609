# if

PHP's if statement has several possible forms. The simplest syntax is:

```
if (condition) statement;
```

condition can be any expression that evaluates to a Boolean (true or false) value. statement only executes if condition evaluates to true. Usually, statements are listed in a block inside curly braces. This is easier to read and allows multiple statements to execute based on the results of a single condition:

```
if ($bIsMorning) {
    $sGreeting = "Good morning";
    echo($sGreeting);
}
```

We often need to specify what should happen if the same condition evaluates to false. One (not very good) possibility would be to use a second if statement with a NOT (!) operator:

```
if ($bIsMorning) {
    $sGreeting = "Good morning";
}
if (!$bIsMorning) {
    $sGreeting = "Hello";
}
echo($sGreeting);
```

Almost all programming languages, including PHP, offer a much better alternative: else. The following example is equivalent to the previous example:

```
if ($bIsMorning) {
    $sGreeting = "Good morning";
} else {
    $sGreeting = "Hello";
}
echo($sGreeting);
```

elseif is used to test additional conditions. An if statement can take as many elseif statements as you like; however, each if statement may only have one else, since else specifies what should be done if no other conditions evaluated to true:

```
if ($bIsMorning) {
    $sGreeting = "Good morning";
} elseif ($bIsAfternoon) {
    $sGreeting = "Good afternoon";
} elseif ($bIsEvening) {
    $sGreeting = "Good evening";
} else {
    $sGreeting = "Hello";
}
echo($sGreeting);
```