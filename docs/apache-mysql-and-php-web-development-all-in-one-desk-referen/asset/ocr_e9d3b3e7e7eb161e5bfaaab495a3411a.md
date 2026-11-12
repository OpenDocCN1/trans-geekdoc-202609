```
8000.25
I cannot vouch for the book's accuracy
$tclsh or.tcl
Ernest Hemingway
.05
Sounds like a bargain!
```

# Using many ifs and elses

If you want to test for more than one condition, you can pile a bunch of if and else statements within a single giant if block. Here's an example that shows how this works:

```
gets stdin a
if {$a > 50} {
    puts "a > 50"
} elseif {$a == 50} {
    puts "a == 50"
} else {
    puts "a <= 50"
}
```

I put the command elseif after the closing brace of the initial if block, and I added the expression $a == 50. This big block of code reads data from the console and stores it in the variable a. Then the code tests if a is greater than 50, and if so, it writes out a message. Otherwise, the code tests if a equals 50, and if so, it writes out a message. But if neither condition is true, the code writes out a final message.

Here are some sample sessions:

```
$tclsh ifelseif.tcl
25
a <= 50
```

```
$tclsh ifelseif.tcl
50
a == 50
```

```
$tclsh ifelseif.tcl
60
a > 50
```

# Selecting from many conditions with switch

If you want to compare a single variable or expression to several possibilities, instead of piling a bunch of if and elseif statements together, you can use a switch statement.