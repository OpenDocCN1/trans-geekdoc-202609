Note
In practice, you usually leave out one of the arguments if it does not need to be set. This
is usually the start statement, as the variable or element that is to be used as a counter
has already been created.

You can write the `for` loop with a colon syntax like the `if` case distinction and then use
`endfor` to end the loop. This allows you to output HTML code in the loop.7 In the follow­
ing example, we include PHP once again within the HTML code, which outputs the
counter variable (see Figure 5.22).

```
<?php
for ($i = 0; $i < 10; $i++):
?>
<p>Output: <?=$i ?></p>
<?php
endfor;
?>
```

Listing 5.25 “for” for the HTML Output (“for_different3.php”)

![](bbox=[0.143, 0.472, 0.842, 0.814])

Figure 5.22 The HTML Code Is Output

7 This also works—as with `if`—with the syntax with curly brackets.