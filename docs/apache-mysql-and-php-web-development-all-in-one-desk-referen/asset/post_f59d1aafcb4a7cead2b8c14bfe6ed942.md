
In the first iteration, the item variable gets the value 5. In the next iteration, the item variable gets the value 10, then 25, and then 500. Here's the output:

```
5
10
25
500
```

If you want to count a range of numbers — such as 0, 1, 2, 3, up to, for example, 100 — use a regular for loop. But if you want to count a particular set of numbers — such as 5, 10, 25, and 500 — the foreach loop is better, as demonstrated in the preceding example.

Tcl also has an interesting feature that enables you to move through a list but store the list in pairs. Take a look at this example:

```
foreach {item1 item2} {5 10 25 500} {
    puts "item1=$item1 item2=$item2"
}
```

The first line is just like the previous example, but this time, I added two counter variables, item1 and item2. (Don't use a comma between any of these variables, or you'll get strange errors that are almost impossible to figure out. I speak — ahem — from experience.)

In the first iteration of this loop, item1 gets 5, and item2 gets 10; these are the first two items in the loop. In the next iteration, item1 gets 25, and item2 gets 500; these are the next two items in the list. In other words, you move through the list in groups of two rather than one. Here's the output:

```
item1=5 item2=10
item1=25 item2=500
```

But notice I have an even number of items in the list, and that works out nice and neat. What if you try to fake out the loop and put an odd number of items in the list? What will happen? Here's an example:

```
foreach {item1 item2} {5 10 25 500 600} {
    puts "item1=$item1 item2=$item2"
}
```

In the first iteration, you have 5 and 10 in item1 and item2, respectively. Then you get 25 and 500. But what about the third iteration? The loop has only one number left, 600. Here's the output so you can see what happens:

```
item1=5 item2=10
item1=25 item2=500
item1=600 item2=
```

In the final iteration, the 600 goes in the first variable, item1. The other variable, item2, simply gets an empty value, which prints as nothing.

Sometimes putting all the elements in a single list can be confusing because you might forget which item goes with which variable. Here's an alternative form:

```
foreach item1 {1 2 3} item2 {10 20 30} {
    puts "item1=$item1 item2=$item2"
}
```

This loop runs through three iterations. In the first iteration, item1 gets 1 (taken from the first list, {1 2 3}), and item2 gets 10 (taken from the second list, {10 20 30}). In the second iteration, item1 gets 2, and item2 gets 20. And in the third and final iteration, item1 gets 3, and item2 gets 30.

### Looping while something is true

The simplest way to loop is to simply loop while something is true. In other words, you set up some initial conditions, and you run a loop over and over while a certain condition is true. Here's an example using the while loop:

```
set num 2
while {$num < 65537} {
    puts $num
    set num [expr $num * 2]
}
```

This code first stores 2 in the variable num. Then the code keeps running over and over as long as num is less than 65537. When num is not less than 65537, the loop ends.

Each iteration of this loop first prints out the value in num. Then the code stores twice the value of num in num by calling the expr command. (I know, that's kind of a complex way to do it. Other languages might use something simple like num = num * 2, but alas that isn't possible with Tcl.)

### Breaking out and continuing again

Regardless of the kind of loop you use (for, foreach, or while), you may want to write some code where if something happens, you want to break out of the loop and continue with code that follows the loop. Or you might want to stop in the middle of the current iteration and immediately continue with the next iteration. For these situations, you use the break command and continue command, respectively.

Here's an example of the continue statement:

```
set num 2
while {$num < 65537} {
    set num [expr $num * 2]
    if {$num == 4096} {
        continue
    }
    puts $num
}
```

4
8
16
32
64
128
256
512
1024
2048
8192
16384
32768
65536
131072

Notice that 4096 (which normally would have shown up) isn't in the list. That's because in the program I compare the num variable to 4096, and if it matches, I skip the rest of the iteration and go on to the next one.

A common mistake with the continue command is to forget to do whatever is necessary to move on to the next iteration. For example, in the preceding program, I made sure to multiply the num variable by 2 before continuing with the next iteration. If I first checked for 4096 and didn't multiply by 2, the next iteration would also be 4096, and the next iteration would be 4096, and so on, and the program would just keep running forever (or at least until you interrupted it).

Here's an example of the break command:

```
set num 2
while {$num < 65537} {
    puts $num
    gets stdin choice
    if {$choice == "n"} {
        break
    }
    set num [expr $num * 2]
}
```

In this example, you have the option to continue with the rest of the loop or break out of it, depending on what you type into the console. I call the gets command to read a string from the console, and then I compare the input to the string n. If it matches, I break out of the loop. Here's some sample output:

2
y
4
y
8
y
16
n

The y and n letters are what I typed in; the program wrote out the numbers. Remember, however, that I didn't have to type y to continue; I could have typed anything except an n. That's because the program only tests whether I typed in an n, and if so, it breaks out of the loop.

## Chapter 4: Building Procedures

### In This Chapter

- Creating a procedure
- Passing a parameter to a procedure
- Returning a value from a procedure
- Creating local and global variables
- Passing multiple parameters to a procedure

Tcl provides you with a whole set of commands, but you can also make your own commands with the proc command. By using proc, you can make your own procedures, which become commands within your program.

If you're familiar with other languages such as Perl or PHP, what I'm describing here are simply procedures and functions. However, Tcl programmers think in terms of commands, so calling a new procedure is akin to creating a new command. In this chapter, I refer to the process as creating a procedure, not a command, because the command is called proc, which stands for (drum roll) procedure.

### Creating a Simple Procedure

To create a procedure, you use the proc command, as I do in this example program:

```
proc MyProc {} {
    puts "Hi!"
}
MyProc
MyProc
MyProc
```

When you run this program, here's the output you see:

```
Hi!
Hi!
Hi!
```

The first line of the program declares a new procedure called MyProc; notice the word proc followed by the name, MyProc. Don't worry yet about the empty braces that follow. Then comes an open brace, some more code, and finally a closing brace. The code inside the braces makes up the new procedure called MyProc.

Then on the following lines, I test out the new procedure by _calling_ it three times. Each time the program runs a MyProc line, the program instead runs the code inside the MyProc procedure, which is this line:

```
puts "Hi!"
```

Thus, this puts line runs three times, resulting in the output of three lines of Hi!.

Here's another example:

```
proc MyProc {} {
    puts "Hi!"
    puts "Goodbye"
}

MyProc
MyProc
```

This time the MyProc procedure has two lines of code in it. I call the procedure twice, and I get the following output:

```
Hi!
Goodbye
Hi!
Goodbye
```

The first two lines of output are from the first call to MyProc. The final two lines of output are from the second call to MyProc. If you're curious about the two empty braces in the proc line, I take that up in the next section.

### Passing Parameters to a Procedure

A procedure isn't particularly useful unless you can supply the procedure with information. For example, suppose you want a procedure that takes a temperature in Fahrenheit (thank goodness for spell-checkers) and writes out the same temperature in Celsius. (But don't say centigrade. That's a holdover from when the U.S. government tried to convert the country to the metric system.) To create a procedure that converts a Fahrenheit number to a
