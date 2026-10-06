# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

```
for num in 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
sq_num = num * num
print "The square of num " is " sq_num
```

**Figure 11-3.** Pseudocode for a simple loop that prints the squares of the first ten numbers

The type of loop shown here is the *for loop*, where the basic structure is for a value in list of values, where the number of times the loop will run is the same as the number of elements in the list, with each run having the value one of the values in the list. We always know how many times this kind of loop will run.

Another type of loop is the *while loop*, which will run over and over until a predefined condition is no longer met. This would look something like the pseudocode in Figure 11-4. In this case, we start with a named num and increase it each the loop runs and stop when the number gets to 10. As long as the condition after the while is, the loop will continue. Additionally, you can also use the keyword break to exit a while loop at that point in the code.

```
num = 0
while num < 10
sq_num = num * num
print "The square of num " is " sq_num
increase num by 1
```

**Figure 11-4.** Pseudocode for a while loop that prints the squares of the first ten numbers

Note that most programmers prefer for for loops over while loops because it's easy to have a bug in your while loop that means it runs forever (if you forget to increase num by 1 in the Figure 11-4 example, it would never exit). This is obviously an easy fix, but it would still be a hassle the first time you run it with the bug.