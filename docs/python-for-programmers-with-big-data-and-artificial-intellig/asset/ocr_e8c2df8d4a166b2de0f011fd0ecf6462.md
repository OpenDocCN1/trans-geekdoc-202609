passing the tuple to the built-in sum function—like a list, a tuple is a sequence.

Note that functions `roll_dice` and `display_dice` each begin their blocks with a docstring that states what the function does. Also, both functions contain local variables `die1` and `die2`. These variables do not “collide,” because they belong to different functions’ blocks. Each local variable is accessible only in the block that defined it.

# First Roll

When the script begins executing, lines 16–17 roll the dice and display the results. Line 20 calculates the sum of the dice for use in lines 22–29. You can win or lose on the first roll or any subsequent roll. The variable `game_status` keeps track of the win/loss status.

# The `in` operator in line 22

```
sum_of_dice in (7, 11)
```

tests whether the tuple `(7, 11)` contains `sum_of_dice`’s value. If this condition is `True`, you rolled a 7 or an 11. In this case, you won on the first roll, so the script sets `game_status` to `'WON'`. The operator’s right operand can be any iterable. There’s also a `not in` operator to determine whether a value is _not_ in an iterable. The preceding concise condition is equivalent to

lick here to view code image

```
(sum_of_dice == 7) or (sum_of_dice == 11)
```

# Similarly, the condition in line 24

```
sum_of_dice in (2, 3, 12)
```

tests whether the tuple `(2, 3, 12)` contains `sum_of_dice`’s value. If so, you lost on the first roll, so the script sets `game_status` to `'LOST'`.

For any other sum of the dice (4, 5, 6, 8, 9 or 10):

+   - line 27 sets `game_status` to `'CONTINUE'` so you can continue rolling