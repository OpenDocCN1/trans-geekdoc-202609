# "elseif"

In practice, there is often not just one alternative, but several. One possible solution is to simply write several if case distinctions one after the other:

```
if ($age > 3) {
    echo "At $age, the child has outgrown infancy.";
}
if ($age >= 2) {
    echo "The $age year old baby can speak a little.";
}
```

What happens if the variable $age has the value 6? Because the two if case distinctions have nothing to do with each other, both are checked separately. Because both conditions are met, PHP executes both statements (see Figure 5.11).

![](bbox=[0.139, 0.355, 0.86, 0.485])

Figure 5.11 A Six-Year-Old Baby Who Can Only Speak a Little? That Does Not Work.

To check several conditions in a case differentiation, there is elseif:

```
if (condition) {
    statements;
} elseif (condition) {
    statements;
}
```

The elseif statement block is only executed if the if condition was not fulfilled and the elseif condition is fulfilled. The next example uses elseif instead of the two if statements in the last example.

```
$age = 6;
if ($age > 3) {
    echo "At $age years old, the child has outgrown infancy.";
} elseif ($age >= 2) {
    echo "The $age years old baby can speak a little.";
}
```

Listing 5.9 Check Alternatives with "elseif" ("elseif.php")