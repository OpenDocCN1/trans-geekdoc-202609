```
puts ""
puts [string equal $str1 $str2]
puts [string.equal $str3 $str4]
puts [string equal -nocase $str3 $str4]
```

Here's the output from the program:

```
0
1
0
1
0
1
```

I know, the output isn't very exciting. But the concepts are. Look at the first three lines of output. The first of these lines compares the strings in the two variables `str1` and `str2`. Those two variables both contain the string `Hello`, so they match. Thus, you see a number 0, which is what the `compare` command returns in the event of a match.

The second line of output is the result of comparing `str3` to `str4`. These variables don't match: One has lowercase `bye` in it, and the other has uppercase `BYE` in it. So the `compare` command returns a 1, which means the strings are different.

The third line again compares `str3` and `str4`, but this time adds the option `-nocase`, which tells `compare` to ignore case. In this case, `bye` and `BYE` match, so the output is 0.

Next I write a blank line to keep the output somewhat neat. And then I do the same comparisons, but this time, I use the `equal` command. I get the same results, too, except this time, I get a 1 when the two strings match, and a 0 when they don't match.

Which is better, `compare` or `equal`? Take your pick. They're both great.

# Creating and modifying strings

In this section, I share some words of wisdom on how to create and modify strings. It's nothing too philosophical. Here are the commands you can use:

+   - map
+   - replace