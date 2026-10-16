```
$testvar = "yes";
    echo "Smith<br>";
}
else
{
    echo "$customers[$k], not Smith<br>";
}
$k++;
}
```

These statements display the following on a Web page:

```
Huang, not Smith
Smith
```

The program executes the previous statements as follows:

+   1. Sets the variables before starting the loop: $customers (an array with three values), $testvar (a test variable set to "no"), and $k (a counter variable set to 0).
+   2. Starts the loop by testing whether $testvar != "yes" is true. Because $testvar was set to "no", the statement is true, so the loop continues.
+   3. Tests the if statement. Is $customers[$k] == "Smith" true? At this point, $k is 0, so the program checks $customers[0]. Because $customers[0] is "Huang", the statement is not true. The statements in the if block are not executed, so the program skips to the else statement.
+   4. Executes the statement in the else block. The else block outputs the line "Huang, not Smith". This is the first line of the output.
+   5. Adds one to $k, which now becomes equal to 1.
+   6. Reaches the bottom of the loop.
+   7. Goes to the top of the loop.
+   8. Tests the condition again. Is $testvar != "yes" true? Because $testvar has not been changed and is still set to "no", it is true, so the loop continues.
+   9. Tests the if statement. Is $customers[$k] == "Smith" true? At this point, $k is 1, so the program checks $customers[1]. Because $customers[1] is "Smith", the statement is true. So the loop enters the if block.
+   10. Executes the statements in the if block. Sets $testvar to "yes". Outputs "Smith". This is the second line of the output.
+   11. Adds one to $k which now becomes equal to 2.