In this case, the code simply outputs the value of $count for each pass of the loop.

# Compound Operators

Compound operators provide a handy shortcut when you want to apply an arithmetic operation to an existing variable. The following example uses the compound addition operator to add six to the current value of $count :

```
$count += 6;
```

The effect of this is to take the initial value of $count , add six to it, and then assign it back to $count . In fact, the operation is equivalent to doing the following:

```
$count = $count + 6;
```

All the basic arithmetic operators have corresponding compound operators, as shown in Table 5.1 .

# Table 5.1. Compound Operators

| Operator | Equivalent To |
| :--- | :--- |
| $a += $b | $a = $a + $b; |
| $a -= $b | $a = $a - $b; |
| $a *= $b | $a = $a * $b; |
| $a /= $b | $a = $a / $b; |
| $a %= $b | $a = $a % $b; |

# Operator Precedence

The rules governing operator precedence specify the order in which expressions are evaluated. For example, the following statement is ambiguous:

```
echo 3 * 4 + 5;
```