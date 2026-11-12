Using the pizza.txt file I described earlier, you can run the code like this:

```
perl last.pl pizza.txt
```

Because the first line in the pizza.txt file contains some pizza, the program doesn't even make it to the first print statement. All you see in the output is the output from the code that follows the while loop:

All done!

# Subroutines

One of the best ways to write software is to divide your code into different parts called subroutines. And the best way to understand what I mean by this is through an example. Take a look at this code:

```
sub dosomething {
    print "Inside the subroutine!\n":
}
```

```
print "Starting!\n";
dosomething();
print "Finishing!\n";
```

The first three lines are a subroutine and don't run at first. Instead, the flow skips to the first line after the subroutine, which is print "Starting!\n". Then the next line, dosomething(), calls the subroutine, which diverts the flow of the program to start running the lines inside the subroutine.

In this case, the subroutine has only one line inside it:

```
print "Inside the subroutine!\n";
```

After running this line of code, the program returns to where it left off before entering the subroutine and runs the final line, print "Finishing!\n":. When you run the program, you see this output:

```
Starting!
Inside the subroutine!
Finishing!
```

Think of subroutines like this: Suppose you're going to run some errands. You may first go to the bank, then head for the grocery store, and then drop off the recycling. In this scenario, you have divided your process (running