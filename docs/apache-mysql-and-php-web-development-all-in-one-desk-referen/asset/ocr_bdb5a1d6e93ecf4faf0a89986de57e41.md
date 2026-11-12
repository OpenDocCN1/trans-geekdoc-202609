In this chapter, I take you through the different ways you can control the structure of your program. The structure refers to the way the program is organized, which affects the flow of the program. The flow of the program is the step-by-step sequence the program takes through your code, however simple or complex it may be.

# Looping

Often when you're developing programs, you need to repeat a group of instructions over and over. Sometimes you need to repeat these instructions a specific number of times; sometimes they must be repeated as long as a certain condition is true. (Such conditions are within the computer, however. I don't mean conditions like “while my boss is still paying me” or “while I still have caffeine inside of me.”) For example, you may be reading in lines from a text file, and you want to process (print out, remove the HTML, or whatever) each line. You want to do this for each line in the file. Or, another example: You may be reading information coming down over the Internet, and you will keep reading as long as more information arrives, only stopping your reading when the data ends.

Both of these examples share a common element: They both perform a certain task over and over. In the sections that follow, I show you how you can make things happen over and over using — you guessed it — Perl.

# Looping for each item in a list: foreach loops

The easiest way to repeat a sequence of instructions over and over is by using a foreach loop. The foreach loop operates in the way that its name implies. This example shows you what I mean by that:

```
foreach (0,1,1,2,3,5,8,13,21) {
    print "$_\n";
}
```

This foreach loop runs the code inside the braces once for each number inside the list. Each time the loop runs, the default variable ($_ ) takes on the value of the current item from the list. During the first iteration through the loop, $_ is 0. Then the loop goes through another iteration, but this time, $_ is 1. Then it's 1 again, then 2, then 3, then 5, and so on. Here's the output:

```
0
1
```