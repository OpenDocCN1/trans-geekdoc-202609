When I typed in abc, the first if statement checked whether my input was a number. Because I didn't type in a number, the code inside the else block ran, printing the Sorry message.

You can also use the expr command for more complex expressions, again using the brackets for substitution. Here's a pretty cool numerical analysis program:

```
gets stdin a
set pi [expr acos(-1)]
set a [expr $a * $pi / 180]
if {abs(cos($a)) < 1e-5} {
    puts "That's a good angle!"
} else {
    puts "No good..."
}
```

This program figures out a good value for pi, then converts an angle from degrees to radians, and then tests if the angle's cosine is within a certain error level around the value 0. If so, the angle is either plus or minus 90 degrees. Here are some sample sessions:

```
$tcsh if3.tcl
90
That's a good angle!

$tcsh if3.tcl
-90
That's a good angle!

$tcsh if3.tcl
180
No good...

$tcsh if3.tcl
45
No good...
```

# Comparing strings

If you are using Tcl version 8.4 or above, and if you want to compare strings in an if command, don't use the comparison operators (<, >, and so on) that you use for numbers. Instead, use the following commands:

+   - eq to test if two strings are equal
+   - ne to test if two strings are not equal