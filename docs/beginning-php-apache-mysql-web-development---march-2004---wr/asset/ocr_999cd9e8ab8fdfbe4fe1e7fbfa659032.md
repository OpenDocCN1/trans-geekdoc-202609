# Chapter 2

In addition, while there may be more than one syntax for accomplishing the goal, good coders will be consistent throughout their code with whichever method they choose. For example, as far as PHP is concerned, the two snippets of code mean the same thing:

```
```php
// php code goes here;
?>
```
```php
<?php
// php code goes here;
?>
```
```

You should simply pick one and stick with it throughout your program.

+   - Frequent comments: The more you use comments throughout your code, the better off you will be. It's not important in smaller, simpler programs, when your programs become more and complex, it will be hard for you to remember what you did, where you did it, and why you did it the way you did.

+   - The use of line numbers: Some editors insert line numbers for you, but others do not. We discuss editors later in this chapter, but you should know that it is important to denote line numbers somewhere in your code, if they are not provided for you, because PHP lets you when your program generates errors, and notifies you of the line number in which the error occurs. If you have to count the lines manually time you encounter an error, you can imagine time consuming and inefficient your debugging will be.

# Why Should You Care About What Your Code Looks Like?

It's important to follow good coding practices for three reasons:

+   - For efficiency: The easier your code is to read and follow, the easier it will be to keep track of where you are with your code, and the quicker it will be to pick up where you left off after a break.

+   - For debugging: Knowing where your problem lies is a major debugging tool. If you have comments, you can easily follow your logic, and if you have line numbers and consistent formatting, you can easily scan your document to pinpoint a trouble area.

+   - For future expansions and modifications: Using comments in your code is especially important for future changes, not all of us can remember the logic behind the code that was written years or even months ago. Also, if you are working on a project that involves a team, if everyone is using the same coding styles, it will be much easier to make changes or additions to someone else's work down the road.

now enough preaching about code—let's get to it.

# Creating Your First Program

You can't get much simpler than this first program, but try out to get a feel for what the results like. The PHP function echo, seen in the material that follows, is one of the most commonly used PHP functions and that, undoubtedly, will become intimate with it. It is used to send text (or variable values or varieties of other things) to the browser.