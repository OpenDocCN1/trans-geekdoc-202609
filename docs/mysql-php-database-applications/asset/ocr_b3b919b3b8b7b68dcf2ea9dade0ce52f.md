# Logical operators

In addition to comparison operators, you will be using logical operators in your scripts. Table 5-2 lists PHP's logical operators.

| Symbol | Example | Description |
| :--- | :--- | :--- |
| and | if ($a ==0 and $b==1) | Checks both conditions. |
| && | if ($a ==0 && $b==1) | Same as the previous symbol, but has a higher precedence (see Note below). |
| or | if ($a ==0 or $b ==1) | Determines if one or the other operand meets the condition. |
| || | if ($a ==0 || $b ==1) | Same as the previous symbol, but has a higher precedence (see Note below). |
| xor | if ($a ==0 xor $b==1) | This is known as exclusive or. It determines if one of the two operands is true but not both. If both of these conditions are true, the overall test will be false. |
| ! | if (!empty($a)) | Determines if something is not the case. In this example the condition will be true if $a is not empty. |

> The difference between && and and, and between | and or, is the order of precedence. PHP must determine which operators to compare first. It does this according to the list found at http://php.net/operators. Don't forget, though, that parentheses override the order of precedence. The contents of inner parentheses get evaluated before those of outer parentheses.

# Complex if statements

Using the operators in Table 5-1 and 5-2, you can create if statements that are a bit more complex than the basic one at the beginning of this chapter.