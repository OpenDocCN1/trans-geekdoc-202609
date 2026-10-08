# Understanding Precedence and Associativity

It also uses the number_format () to format the totals as strings with two decimal places. This is a function from PHP's Math library.

If you look closely at the calculations, you might ask why the calculations were performed in the order they were. For example, consider this statement:

```
$totalamount = $tireqty * TIREPRICE
 + $oilqty * OILPRICE
 + $sparkqty * SPARKPRICE;
```

The total amount seems to be correct, but why were the multiplications performed before the answers? The answer lies in the precedence of the operators—that is, the order in which they are evaluated.

# Understanding Precedence and Associativity

In general, operators have a set precedence, or order, in which they are evaluated. Operators also have associativity, which is the order in which operators of the same precedence are evaluated. This order is generally left to right (called left for short), right to left (called right for short), or not relevant.

Table 1.7 shows operator precedence and associativity in PHP. In this table, operators with the lowest precedence are at the top, and precedence increases as you go down the table.

Table 1.7 Operator Precedence in PHP

| Associativity | Operators |
| --- | --- |
| left | Or |
| left | Xor |
| left | And |
| right | Print |
| left | = += - *= = / % = && | ^ <= <= >> |
| left | ? |
| left | || |
| left | && |
| left | | |
| left | ^ |
| left | & |
| n/a | == != === !== |