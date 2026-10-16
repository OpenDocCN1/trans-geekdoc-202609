```
$counter=0;
$counter++;
echo $counter;
```

This echo statement also outputs 1 because ++ adds 1 to the current value of $counter. Or you can use the following statement:

```
$counter--;
```

This statement subtracts 1 from the current value of $counter.

Sometimes you may want to do a different arithmetic operation. You can use any of the following shortcuts:

```
$counter+=2;
$counter-=3;
$counter*=2;
$counter/=3;
```

These statements add 2 to $counter, subtract 3 from $counter, multiply $counter by 2, and divide $counter by 3, respectively.

# Using exit

Sometimes you want the program to stop executing — just stop at some point in the middle of the program. For instance, if the program encounters an error, often you want it to stop rather than continue with more statements. The exit statement stops the program. No more statements are executed after the exit statement. The format of an exit statement is

```
exit("message");
```

The message is a message that is output when the program exits. For instance, you might use the statement

```
exit("The program is exiting");
```

You can also stop the program with the die statement, as follows:

```
die("The program is dying");
```

The die statement is the same as the exit statement. die is just another name for exit. Sometimes it's just more fun to say die.