```
<form name="form1" method="get" action="advancedfunc.php">
Your name please?
<input type="text" name="username">
<br>
<input type="submit">
</form>
</body>
</html>
```

When you open this form and subsequently run the PHP program (by clicking the submit button), you see these numbers in the browser if you enter the name Jeff (each number will appear on a separate line):

0 1 4 9 16 25 36 49 64 81

Otherwise, you see these numbers:

0 2 4 6 8 10 12 14 16 18

You can see how this conditional function works; The program defines the Calc function one way if the username is Jeff and another way if the username is not Jeff.

![](bbox=[0.125, 0.495, 0.23, 0.58])

If you're an advanced programmer, you have at your disposal many of these advanced function features that most people probably wouldn't have much use for, such as variable-length argument lists and variable functions. If you're interested in exploring these two topics, you can find them on the PHP site at these three addresses:

+   * www.php.net/functions for conditional functions
+   * www.php.net/manual/en/functions.arguments.php for variable-length functions
+   * www.php.net/manual/en/functions.variable-functions.php for variable functions, which refers to calling a function by name when that name is stored as a string in a variable