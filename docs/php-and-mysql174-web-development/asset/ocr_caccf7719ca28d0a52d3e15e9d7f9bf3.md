As well as the for loop, there is a foreach loop, designed specifically for use with arrays. We discuss how to use it in Chapter 3.

# do..while Loops

The final loop type we describe behaves differently. The general structure of
a do..while statement is

```
do
expression;
while (condition);
```

A do..while loop differs from a while loop because the condition is tested at the end. This
means that in a do..while loop, the statement or block within the loop is always executed at
least once.

Even if you consider this example in which the condition is false at the start and can
never become true, the loop will be executed once before checking the condition and ending:

```
$num = 100;
d{
echo $num.*<br />;
}while ($num < 1) {

```

# Breaking Out of a Control Structure or Script

If you want to stop executing a piece of code, you can choose from three approaches,
ending on the effect you are trying to achieve.

If you want to stop executing a loop, you can use the break statement as previously discussed
in the section on switch. If you use the break statement in a loop, execution of the script will
continue at the next line of the script after.

If you want to jump to the next iteration, you can instead use the continue statement.
If want to finish executing the entire PHP script, you can use exit. This approach is
typically useful when you are performing error checking. For example, you could modify the
asas follows:

```
if($totalqty == 0) {
echo "You did not order anything on the previous page<br />";
exit;
}
```

The call to exit stops PHP from executing the remainder of the script.