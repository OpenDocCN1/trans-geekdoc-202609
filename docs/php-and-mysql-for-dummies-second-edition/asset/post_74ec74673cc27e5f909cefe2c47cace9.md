
✓ do..while loop: Sets up a condition; executes a block of statements; checks the condition; if the condition is true, repeats the block of statements

I describe each of these loops in detail in the following few sections.

## Using for loops

The most basic for loops are based on a counter. You set the beginning value for the counter, set the ending value, and set how the counter is incremented. The general format is

```
for (startingvalue;endingcondition;increment)
{
    block of statements;
}
```

Fill in the following values:

- *startingvalue*: A statement that sets up a variable to be your counter and sets it to your starting value. For instance, the statement `$i=1;` sets `$i` as the counter variable and sets it equal to 1. Frequently, the counter variable is started at 0 or 1. The starting value can be a combination of numbers (2 + 2) or a variable.
- *endingcondition*: A statement that sets your ending value. As long as this statement is true, the block of statements keeps repeating. When this statement is not true, the loop ends. For instance, the statement `$i<10;` sets the ending value for the loop to 10. When `$i` is equal to 10, the statement is no longer true (because `$i` is no longer less than 10), and the loop stops repeating. The statement can include variables, such as `$i<$size;`.
- *increment*: A statement that increments your counter. For instance, the statement `$i++;` adds 1 to your counter at the end of each block of statements. You can use other increment statements, such as `$i+=1;` or `$i--;`.

The basic for loop sets up a variable — for example, a variable called $i, — that is a counter. This variable has a value during each loop. The variable $i can be used in the block of statements that is repeating. For instance, the following simple loop displays Hello World! three times:

```
for ($i=1;$i<=3;$i++)
{
echo "$i. Hello World!<br>";
}
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_192_0.png)

The statements in the block do not need to be indented. PHP doesn't care whether they're indented. However, indenting the blocks makes it much easier for you to understand the program.

The output from these statements is

```
1. Hello World!
2. Hello World!
3. Hello World!
```

For loops are particularly useful to loop through an array. Suppose that you have an array of customer names and want to display them all. You can do this easily with a loop:

```
for ($i=0;$i<100;$i++)
{
    echo "$customerNames[$i]<br>";
}
```

The output displays a Web page with a list of all the customer names, one on each line. In this case, you know that you have 100 customer names, but suppose that you don't know how many customers are in this list. You can ask PHP how many values are in the array and use that value in your for loop. For example, you can use the following statements:

```
for ($i=0;$i<sizeof($customerNames);$i++)
{
    echo "$customerNames[$i]<br>";
}
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_192_1.png)

## Advanced for loops

The structure of a for loop is quite flexible and allows you to build loops for almost any purpose. A for loop has this general format:

```
for ( beginning statements;
    conditional statements;
    ending statements)
{
    block of statements;
}
```

Where

- The beginning statements execute once at the start of the loop.
- The conditional statements are tested for each iteration of the loop.
- The ending statements execute once at the end of the loop.

Each of the statement sections is separated by a semicolon (;). Each section can contain as many statements as needed, separated by commas. Any section can be empty.

The following loop has statements in all three sections:

```
for ($i=0,$j=1;$t<=4;$i++,$j++)
{
  $t = $i + $j;
  echo "$t<br>";
}
```

The output of these statements is

1
3
5

The loop is executed in the following order:

- 1. The beginning section containing two statements is executed; $i is set to 0, and $j is set to 1.
- 2. The conditional section containing one statement is evaluated. Is $t less than or equal to 4? Yes, so the statement is true. The loop continues to execute.
- 3. The statements in the statement block are executed. $t becomes equal to $i plus $j, which is 0 + 1, which equals 1. Then $t is echoed to give the output 1.
- 4. The ending section containing two statements is executed — $i++ and $j++. One is added to $i so it equals 1, and 1 is added to $j so that it now equals 2.
- 5. The conditional section is evaluated. Is $t less than or equal to 4? Because $t is equal to 1 at this point, the statement is true. The loop continues to execute.
- 6. The statements in the statement block are executed. $t becomes equal to $i plus $j, which is 1 + 2, which equals 3. Then $t is echoed to give the output 3.
- 7. The ending section containing two statements is executed — $i++ and $j++. One is added to $i so it equals 2, and 1 is added to $j so that it equals 3.
- 8. The conditional section is evaluated. Is $t less than or equal to 4? Because $t now equals 3, the statement is true. The loop continues to execute.
- 9. The statements in the statement block are executed. $t becomes equal to $i plus $j, which is 2 + 3, which equals 5. Then $t is echoed to give the output 5.
- 10. The ending section containing two statements is executed — $i++ and $j++. One is added to $i so it equals 3, and one is added to $j so that it equals 4.
- 11. The conditional section is evaluated. Is $t less than or equal to 4? Because $t now equals 5, the statement is not true. The loop does not continue to execute. The loop ends, and the program continues to the next statement after the end of the loop.

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

- 1. Sets the variables before starting the loop: $customers (an array with three values), $testvar (a test variable set to "no"), and $k (a counter variable set to 0).
- 2. Starts the loop by testing whether $testvar != "yes" is true. Because $testvar was set to "no", the statement is true, so the loop continues.
- 3. Tests the if statement. Is $customers[$k] == "Smith" true? At this point, $k is 0, so the program checks $customers[0]. Because $customers[0] is "Huang", the statement is not true. The statements in the if block are not executed, so the program skips to the else statement.
- 4. Executes the statement in the else block. The else block outputs the line "Huang, not Smith". This is the first line of the output.
- 5. Adds one to $k, which now becomes equal to 1.
- 6. Reaches the bottom of the loop.
- 7. Goes to the top of the loop.
- 8. Tests the condition again. Is $testvar != "yes" true? Because $testvar has not been changed and is still set to "no", it is true, so the loop continues.
- 9. Tests the if statement. Is $customers[$k] == "Smith" true? At this point, $k is 1, so the program checks $customers[1]. Because $customers[1] is "Smith", the statement is true. So the loop enters the if block.
- 10. Executes the statements in the if block. Sets $testvar to "yes". Outputs "Smith". This is the second line of the output.
- 11. Adds one to $k which now becomes equal to 2.

The output of these statements in a browser is

```
Huang, not Smith
Smith
```

This is the same output shown for the while loop example. The difference between a while loop and a do..while loop is where the condition is checked. In a while loop, the condition is checked at the top of the loop. Therefore, the loop will never execute if the condition is never true. In the do..while loop, the condition is checked at the bottom of the loop. Therefore, the loop always executes at least once even if the condition is never true.

For instance, in the preceding loop that checks for the name Smith, suppose the original condition is set to yes, instead of no, by using this statement:

```
$testvar = "yes";
```

The condition would test false from the beginning. It would never be true. In a while loop, there would be no output. The statement block would never run. However, in a do..while loop, the statement block would run once before the condition was tested. Thus, the while loop would produce no output, but the do..while loop would produce the following output:

```
Huang, not Smith
```

The do..while loop produces one line of output before the condition is tested. It does not produce the second line of output because the condition tests false.

## Infinite loops

You can easily set up loops so that they never stop. These are infinite loops. They repeat forever. However, seldom does anyone create an infinite loop intentionally. It is usually a mistake in the programming. For instance, a slight change to the program that sets up a while loop can make it into an infinite loop.

Here is the program shown in the section, “Using while loops,” earlier in this chapter:

```
$customers = array ( "Huang", "Smith", "Jones" );
$testvar = "no";
$k = 0;
while ( $testvar != "yes" )
{
    if ($customers[$k] == "Smith" )
    {
```
