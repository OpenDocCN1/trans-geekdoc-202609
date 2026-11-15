The while loop, on the other hand, is used to repeat the execution of a code block only if the condition we set is still true. Therefore, when the condition is no longer met, the loop will break and the application will continue with the next lines of code. Here's a while loop in action:

```
x = 1
while x < 10:
    print(x)
    x += 1
```

The x variable is declared as an integer and then we instruct the program that as long as x is less than ten, the result should be printed. Take note that if you do not continue with any other statement at this point you will create an infinite loop and that is not something you want. The final statement makes sure that the application will print the new value with one added to it with every execution. When the variable stops being less than ten, the condition will no longer be met and the loop will break, allowing the application to continue executing any code that follows.

Keep in mind that infinite loops can easily happen due to mistakes and oversight. Luckily, Python has a solution, namely the “break” statement which should be placed at the end of the loop. Here's an example:

```
while True:
    answer = input (“Type command:”)
    if answer == “Yes”:
        break
```

Now the loop can be broken by typing a command.

# Functions

As a beginner machine learner this is the final Python component you need to understand before learning the cool stuff. Functions