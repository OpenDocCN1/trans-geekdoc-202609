# Combined Assignment Operators

In addition to the simple assignment, there is a set of combined assignment operators. Each of them is a shorthand of performing another operation on a variable and assigning the result back to that variable. For example,

$a += 5;

This is equivalent to writing

$a = a + 5;

Combined assignment operators exist for each of the arithmetic operators and for the string concatenation operator. A summary of all the combined assignment operators and for the is shown in Table 1.2.

| Operator | Use | Equivalent To |
| --- | --- | --- |
| += | $a += $b | $a = a + $b |
| -= | $a -= $b | $a = a - $b |
| *= | $a *= $b | $a = a * $b |
| /= | $a /= $b | $a = a / $b |
| %= | $a %= $b | $a = a % $b |
| .= | $a .= $b | $a = a . $b |

# Pre- and Post-Increment and Decrement

The pre- and post-increment (++) and decrement--) operators are similar to the ++ and -- operators, but with a couple of twists.

All the increment operators have two effects: they increment and assign a value. Consider the following:

```
$a=4;
echo ++$a;
```

The second line uses the pre-increment operator, so called because the ++ appears before the $a. This has the effect of first increment $a by 1 and returning the incremented value. In this case, $a is incremented to 5, and the value 5 is returned. The value of this whole expression is 5. (Notice that the actual value stored in $a is changed: It is not just returning $a + 1.).

If the ++ is after the $a, however, you are using the post-increment operator. It has a different effect. Consider the following:

```
$a=4;
echo $a++;
```