
set x 100
if {$x == 100} {
    set y 200
    if {$y == 200} {
        puts "Works!"
    }
}

The following program reads the indenttest.txt file, indents each line four spaces, and prints out the results. Then it reduces the indention of each line a couple spaces and prints out the new results:

```
package require textutil
set f [open "indenttest.txt"]
set t [read $f]
close $f
set res [::textutil::indent $t "  "]
puts $res
puts ""
set res2 [::textutil::indent $res "  "]
puts res2
```

Notice how I make use of the textutil package and then access the indent command using ::textutil::indent. First, I open a file and read in the file's contents into the t variable. Then I try indenting the whole file with several spaces and printing out the results. Next, I try indenting again, but with fewer spaces, and again print out the results. Here's the output; notice that the second block is indented less than the first block:

```
set x 100
if {$x == 100} {
    set y 200
    if {$y == 200} {
        puts "Works!"
    }
}
```

```
set x 100
    if {$x == 100} {
        set y 200
        if {$y == 200} {
            puts "Works!"
        }
    }
}
```

## Reformatting text

Often when working with online text you need to reformat text to fit within a certain width. Many e-mail programs perform this function, and the textutil package includes a command called adjust that squeezes down the text. (If the text is already narrow, no changes are made, even if the text is extremely narrow.) In the following example, I have included a long string with no newlines; I then call the adjust function with a parameter of 60 to reformat the text. This adds newlines where necessary to fit each line within 60 characters. Then I try the same thing again but with a parameter of 40, limiting each line to 40 characters. Here's the code:

```
package require textutil

set address "Four score and seven years ago our fathers
brought \
forth on this continent a new nation, conceived in \
liberty and dedicated to the proposition that all men \
are created equal. Now we are engaged in a \
great civil war, testing whether that nation or any \
nation so conceived and so dedicated can long endure. \
We are met on a great battlefield of that war. We have \
come to dedicate a portion of that field as a final \
resting place for those who here gave their lives that \
that nation might live..."
set formatted [::textutil::adjust $address -length 60]
puts $formatted
puts ""
set formatted [::textutil::adjust $address -length 40]
puts $formatted
puts ""
```

## Building Advanced Data Structures

The tcllib includes several handy data structures for advanced data processing. The three that I look at here are common structures used in many programs:

- **queue**: Implements a first-in-first-out (FIFO) data structure. This is a list that behaves much like people waiting in line.
- **stack**: Implements a last-in-first-out (LIFO) data structure. This is a list that behaves much like a stack of papers.
- **record**: Allows you to build data types consisting of several parts. (This is much like struct in C and C++ and record in Pascal.)

![](img/3f967ab8a8fddc723173059f56621648_315_0.png)

To use these data structures, you need to include the following line near the beginning of your program:

```
package require struct
```

You then access a command by typing two colons, the word `struct`, two more colons, and then the command name. Here are two examples: `::struct::queue` and `::struct::stack`.

### Standing in line with a queue

A _queue_ is a data structure that behaves like people standing in line. You can keep adding more and more to the data, and this data goes at the end of the line. You can then take data off one by one, and the data comes from the front of the line. For example, if you put a 100 in a queue, then a 200 in the queue, then a 300 in the queue, the queue will look like this:

(front of the line) 100 200 300 (back of the line)

If you take off an item, you'll have to take the first in the queue. The first item you take off, then, is a 100, leaving the queue like this:

(front of the line) 200 300 (back of the line)

The next item you take off is a 200, leaving the queue like this:

(front of the line) 300 (back of the line)

... and so on. A queue is commonly used in situations where you have several data items trying to access a single device. What kind of device? A printer is an example. The program running the printer can take several print jobs, but then puts them all in a queue, printing them one by one. The following program demonstrates a queue. This approach is usually called FIFO, which stands for First In, First Out.

```
package require struct

::struct::queue myqueue
myqueue put 50
myqueue put 60
myqueue put "Hello"
set x [myqueue get]
puts $x
set x [myqueue get]
puts $x
```

Notice the strange syntax here. You first create the queue using the `::struct::queue` command, passing a name for your queue. Oddly, this name then becomes a command, which you can use to manipulate your new queue, by passing a subcommand (in this first case, the subcommand is `put`). First I call `put` to add a 50 to the queue. Then I `put` a 60, and then I `put` the string `Hello`.

Next, I take something off the queue using the `get` subcommand and print it out; then I take something else off the queue and print that out. Here's the output, verifying that the first item I put in was the first item I got back:
50
60

### Gathering papers with a stack

A *stack* is a data structure that works like a stack of papers on your desk: The most recent addition to the list is the first item you can retrieve from it. Let's say you put something on the stack, say a 1. Then you put something else on it, say a 2. And then you put a 3. Now, because this is a stack, when you take items off, you can take them only off the top. Thus, you first take the 3 off the stack, leaving the 1 and 2 behind. Next, you take off the 2 from the stack, leaving the 1 behind. Finally, you can take off the 1, leaving an empty stack.

A common use of a stack is in how the computer keeps track of your function calls: Each time you call a function, the computer saves the function on a stack. Then when your program returns from the function, the computer pops the top off the stack, and whatever is underneath is the function to return to. This is usually called First In, Last Out, or FILO. Or, sometimes Last In, First Out, or LIFO.

Here's a sample program that creates and manipulates a stack:

```
package require struct

::struct::stack mystack
mystack push 100
mystack push "Hi"
mystack push 250
set x [mystack pop]
puts $x
set x [mystack pop]
puts $x
```

This code creates a new stack using the `::struct::stack` command. Then the code pushes a 100 onto the stack using the `push` command. (_Push_ is the correct term for putting something on the stack.) Next, I push a string `Hi` on the stack, and then I push 250. Now I have a 100 at the bottom, a `Hi` string in the middle, and a 250 on top.

To retrieve an item from the top of the stack, you use the `pop` command. So, next I use the `pop` command to pop something off the stack. What will I pop off? The item on top, which is 250. Then if I pop something else off the stack, I'll get the string Hi. Here's the output:

250
Hi

### Grouping data in a record

A *record* is a handy way to collect data that's divided up into subdata, so to speak, thereby allowing you to group related data together. For example, I may want to create a data structure that's made up of a *name*, an *e-mail* address, and a *company*. Using the *record* structure, I can group those three items together into a single entity that I will call *emailinfo*.

After the record is defined, I can create a new instance of my *emailinfo* structure; I can set the *name* for the instance, the *e-mail* for the instance, and the *company*. Using this definition, I can create unlimited instances of the *emailinfo* structure, and again set the name, e-mail, and company. Here's an example:

```
package require struct

::struct::record define emailinfo {
    name
    email
    company
}

emailinfo friend
friend config -name "Jeff" -email "jeff@me.com" \\
   -company "Me, Inc."
emailinfo friend2
friend2 config -name "Suzy" -email "suzy@me.com" \\
   -company "Me, Inc."

puts [friend cget -name]
puts [friend cget -email]
puts [friend cget -company]

puts [friend2 cget -name]
puts [friend2 cget -email]
puts [friend2 cget -company]
```

Notice how I specify the structure; I use the ::struct::record command and the define subcommand. Then I provide the name for my structure. And then inside braces I give the names of the items making up the structure.
