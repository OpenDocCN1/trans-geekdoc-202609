This prints out a random floating point value somewhere between 0 and 500. (Theoretically, it may print out 0.0, or it may print out 500.0, although the chances are slim.) Here's the number I saw when I ran it:

```
253.204345703125
```

If you're trying to debug a program that uses a random-number generator, you can try this little trick: seeding the random-number generator with a constant value. Debugging is difficult when dealing with random situations because you might not have the same sequence of events happen each time you run your program. For example, suppose you're writing a card game that will shuffle the cards using a random-number generator. The cards will be shuffled differently each time you run the program (if you use the `time` function to start out the random-number generator). But what if while debugging you want the cards to be shuffled the same each time? You can start the random-number generator with a fixed number of your choice, rather than the time, like so:

```
srand 10000;
```

The first number you get won't be 10000; instead, it will be a floating point number within the range you specify. Each time you run the program, that first random number will be the same. When you're finished debugging, you can replace the `10000` with the `time` function.

Starting with version 5.004 of Perl (no, that doesn't include version 5.0), you don't need to call `srand` because Perl automatically calls it the first time you call `rand`. But the earlier versions of Perl don't call `srand` automatically, so you won't get a new seed each time. Personally, I like to always call `srand` when my program starts (if I'll be using random numbers, that is), just to be on the safe side.

# Searching and Replace Substrings

Perl has three functions for searching for a substring within a string:

+   - `substr`
+   - `index`
+   - `rindex`

The first of these functions, `substr`, is multifaceted. You can use it to extract a substring from a string based on position; and you can use it to replace a substring. Here's an example: