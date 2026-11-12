```
set num 2
while ($num < 65537) {
    set num [expr $num * 2]
    if ($num == 4096) {
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

Notice that 4096 (which normally would have shown up) isn't in the list.
That's because in the program I compare the num variable to 4096, and if it
matches, I skip the rest of the iteration and go on to the next one.

A common mistake with the continue command is to forget to do whatever
is necessary to move on to the next iteration. For example, in the preceding
program, I made sure to multiply the num variable by 2 before continuing
with the next iteration. If I first checked for 4096 and didn't multiply by 2,
the next iteration would also be 4096, and the next iteration would be 4096,
and so on, and the program would just keep running forever (or least until
you interrupted it).

Here's an example of the break command:

```
set num 2
while ($num < 65537) {
    puts $num
    gets stdin choice
    if {$choice == "n"} {
        break
    }
    set num [expr $num * 2]
}
```