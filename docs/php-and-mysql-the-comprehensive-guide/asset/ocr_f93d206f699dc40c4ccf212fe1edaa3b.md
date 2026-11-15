```
class Travel {
public ?DateTime $start = null;
}
```

This object is not created here because it was intentionally commented out:

```
//$travel->start = new DateTime();
```

In this case, the nullsafe operator intervenes, determines that the second operand, start, has the value null, and thus ends the check:

```
$arrival = $travel?->start?->format('d.m.Y');
```

The result is the output of NULL as the value.

Here is the complete code:

```
<?php
class Travel {
public ?DateTime $start = null;
}

$travel = new Travel();
$travel->start = new DateTime();

$arrival = $travel?->start?->format('d.m.Y');
var_dump($arrival);
?>
```

# Listing 5.7 The Nullsafe Operator ("nullsafe_operator.php")

![](bbox=[0.145, 0.62, 0.855, 0.75])

# Figure 5.9 The "DateTime" Object Is Null

The differentiation from the conditional operator with null check is not entirely straightforward; both can be used across the board for some applications. Therefore, here is a brief overview of the most important differences: