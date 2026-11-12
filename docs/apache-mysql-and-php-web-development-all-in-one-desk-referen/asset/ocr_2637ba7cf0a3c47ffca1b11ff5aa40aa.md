+   - >= means greater than or equal to.
+   - == means equal to. (Yes, that’s two equal signs in a row.)
+   - != means not equal to.

These operators are all used for comparing numbers. In a later section, “Comparing strings,” I show you how to — you guessed it — compare strings.

# Evaluating conditions inside an if block

If you read Book II, Chapter 2, you know that you can test whether a string is a valid integer. When you read text from the command line, it comes in as a string. Thus, say that you have a line like this:

```
gets stdin a
```

Your variable a can contain anything the user might type in, not just numbers. What if you want to just get numbers? Then you can use a fancy if statement in conjunction with some of the string-processing commands. Here’s the string command you want to use here:

```
[string is integer $a]
```

If you remember how substitution works, you can logically figure out that you can put this string command inside an if block like so:

```
gets stdin a
if {[string is integer $a]} {
    if {$a > 50} {
        puts "a > 50"
    } else {
        puts "a <= 50"
    }
} else {
    puts "Sorry, that's not a number"
}
```

See how I put the string command right inside the if statement’s expression area? And it works! Here’s a sample session of this program; I typed in the abc part when I ran the program:

```
$tclsh if2.tcl
abc
Sorry, that's not a number
```