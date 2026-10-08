```
<table style="border: 0px; padding: 3px">
<tr>
<td style="background: #cccccc; text-align: center;">Distance</td>
<td style="background: #cccccc; text-align: center;">Cost</td>
</tr>
<tr>
<td style="text-align: right;">50</td>
<td style="text-align: right;">5</td>
</tr>
<tr>
<td style="text-align: right;">100</td>
<td style="text-align: right;">10</td>
</tr>
<tr>
<td style="text-align: right;">150</td>
<td style="text-align: right;">15</td>
</tr>
<tr>
<td style="text-align: right;">200</td>
<td style="text-align: right;">20</td>
</tr>
<tr>
<td style="text-align: right;">250</td>
<td style="text-align: right;">25</td>
</tr>
</table>
</body>
</html>
```

Rather than an easily bored human—who must be paid for his time—to type the HTML, having a cheap and tireless computer do it would be helpful.

Loop statements tell PHP to execute a statement or block repeatedly.

# while Loops

The simplest kind of loop in PHP is the while loop. Like an if statement, it relies on a condition. The difference between a while loop and an if statement is that an if statement executes the code that follows only once if the condition is true. A while loop executes the block repeatedly as long as the condition is true.

You generally use a while loop when you don't know how many iterations will be required to make the condition true. If you require a fixed number of iterations, consider using a for loop.

The basic structure of a while loop is

```
while ( condition ) expression;
```