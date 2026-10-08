The condition $totalqty == 0 will be true if $totalqty is equal to zero. If $totalqty is not equal to zero, the condition will be false. When the condition is true, the echo statement will be executed.

# Code Blocks

Often you have more than one statement you want executed according to the actions of a conditional statement such as if. You can group a number of statements together as a block. To declare a block, you enclose it in braces:

```
if ($totalqty == 0) {
echo '<p style="color:red">';
echo 'You did not order anything on the previous page!';
echo '</p>';
}
```

The three lines enclosed in curly braces are now a block of code. When the condition is true, all three lines are executed. When the condition is false, all three lines are ignored.

> Note As mentioned, PHP does not know how you lay out your code. However, you should indent your code for readability purposes. Indenting is useful to enable you to see at a glance which lines will be executed only if conditions are met, which statements are grouped into blocks, and which statements are parts of loops or functions. In the previous examples, you can see that the statement depending on the if statement and the statements making up the block are indented.

# else Statements

An else statement allows you to define an alternative action to be taken when the condition in an if statement is false. Say you want to Bob's customers when they do not order anything. On the other hand, if they make an order, instead of a warning, you want to show them what they ordered.

If you rearrange the code and add an else statement, you can display a warning or a summary:

```
if ($totalqty == 0) {
echo 'You did not order anything on the previous page!<br />';
} else {
echo htmlspecialchars($tireqty).' tires<br />';
echo htmlspecialchars($oilqty).' bottles of oil<br />';
echo htmlspecialchars($sparkqty).' spark plugs<br />';
}
```