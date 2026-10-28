# A switch statement with a default case

```
switch ($letter_grade) {
    case 'A':
        $message = 'well above average';
        break;
    case 'B':
        $message = 'above average';
        break;
    case 'C':
        $message = 'average';
        break;
    case 'D':
        $message = 'below average';
        break;
    case 'F':
        $message = 'failing';
        break;
    default:
        $message = 'invalid grade';
        break;
}
```

# A switch statement with fall through

```
switch ($letter_grade) {
    case 'A':
    case 'B':
        $message = 'Scholarship approved.';
        break;
    case 'C':
        $message = 'Application requires review.';
        break;
    case 'D':
    case 'F':
        $message = 'Scholarship not approved.';
        break;
}
```

# Description

+   - The *switch statement* starts by evaluating the *switch expression* in the parentheses.
+   - After evaluating the expression, the switch statement transfers control to the *case label* that has the value that matches the value of the expression. Then, it executes the statements for that *case*. It stops executing when it reaches a break statement or the end of the switch statement.
+   - The default case is optional and may be omitted. If included, you can only have one default case. It is usually the last case in the switch statement, but it can be anywhere.
+   - The values in the case label may be literal values or they may be expressions.
+   - If a case doesn’t contain a break statement, execution “falls through” to the next label.
+   - You can nest if statements or other switch statements within the cases of a switch statement.