| AND | && | $a && $b | AND: Returns true if $a and $b are true (true) |
| --- | --- | --- | --- |
| OR | || | $a || $b | OR: Returns true if at least $a or $b is true. |
| XOR | XOR | $a XOR $b | Returns true if only $a is true or if only $b is true |
| Denial | ! | !$a | Returns the inverse of a boolean expression |

AND operator (&& or and): The AND operator returns true if all Boolean expressions combined are true.

+   * True && True gives True
+   * True && False gives False
+   * False && True gives False
+   * False && False gives False

# Example:

```
<?php
$a = 10 > 2;
$b = 5 < 1;
$result = ($a && $b); // $result is false because $b is false
echo $result;
```