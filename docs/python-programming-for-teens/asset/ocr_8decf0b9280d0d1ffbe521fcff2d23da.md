```
# Determine whether to make a turn first.
if probability < .01:    # Probability too small to take the turn
    return
if probability < 1:    # Maybe not take the turn
    if not choice(range(100)) in range(0, int(probability * 100)):
        return

# A turn will be made, so the # of degrees is either random or given
if not upper:    # Upper absent, so use lower
    degrees = lower
else:    # Choose a random amount of degrees
    degrees = randint(lower, upper)

if randint(1, 2) == 1:    # Turn left or right with equal prob.
    left(degrees)
else:
    right(degrees)
```

Whew! There is a saying that nothing good comes cheaply, and this function is a case in point. Whenever there is complex logic, you try to handle the easiest cases first. So, here are the cases in this function:

+   1. The probability is less than .01, so you just quit the function.
+   2. The probability is less than 1, so you use it to determine whether to continue. You pick a random number from 0 through 99 and then see if that number is in the range of numbers from 0 through 100 times the probability. If it’s not in that range, you quit the function.
+   3. If you get this far, you’ll be turning the turtle. If the value of upper is not present, the number of degrees will be the value of lower. Otherwise, the number of degrees is a random number from lower through upper.
+   4. Finally, you choose whether to turn left or right, with equal probability.

Note that the function also imports the random function choice for later use in its code.

Even though you have expended a lot of effort on several new function definitions, this effort will be well rewarded. Your top-level code will be simpler and easier to read and manage. Moreover, other programmers will find your code useful, should you decide to share it with them.