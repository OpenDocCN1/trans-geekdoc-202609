When a `break` statement is encountered, execution of the `switch` statement is halted and is resumed past the `switch` statement's close curly brace.

Once a `case` label is found that matches the value in question, no other `case` labels will be evaluated, so omitting the `break` statement at the end of a case causes execution to fall through to all subsequent cases, even though those values do not match. It is a common mistake for beginners to accidentally omit `break` and end up with the results of multiple cases. However, "fall through" isn't a bug; it's a feature. It allows the programmer to produce the same results for more than one case:

```
switch ($sLangCode) {
case "fr": // Fall through:
case "es":
    echo("Romance language");
    break;

case "en": // Fall through:
case "de":
    echo("Germanic language");
    break;

case "ru":
    echo("Slavic language");
    break;

default:
    echo("Language not recognized in system.");
}
```

It is good programming practice to include comments like those in the example above to make it clear that the omission of the `break` statement is intentional. In this example, "Romance language" will print whether the value is `fr` or `es`, so the effect is similar to that of using an OR (`||`) operator in an `if` statement.

In other instances, however, fall through is even more flexible than OR. In the following example, both `statement1` and `statement2` will execute if `$sLangCode`'s value is `fr`, but only `statement2` will execute if the value is `es`:

```
switch ($sLangCode) {
case "fr":
    statement1; // Fall through:
case "es":
    statement2;
    break;
}
```

In the examples above, we use literal values for our case labels. In PHP, unlike most other languages, case labels may themselves be variables. Not even JavaScript (which is pretty liberal as far as programming languages go) is that flexible. Arrays and objects are the only data types that are not legal as case labels in PHP.