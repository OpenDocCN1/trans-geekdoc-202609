local version. Thus, if you are ever in doubt, design with `local` first and then convert this tested version into one that uses `lambda`. Keep in mind, however, that `lambda` is not a cure-all. The locally defined function comes with a name that explains its purpose, and, if it is long, the use of an abstraction with a named function is much easier to understand than one with a large `lambda`.

The following exercises request that you solve the problems from chapter 16.7 with `lambda` in ISL+.

# **Exercise 285.** Use `map` to define the function `convert-euro`, which converts a list of US$ amounts into a list of € amounts based on an exchange rate of US$1.06 per €.

Also use `map` to define `convertFC`, which converts a list of Fahrenheit measurements to a list of Celsius measurements.

Finally, try your hand at `translate`, a function that translates a list of Posns into a list of lists of pairs of numbers.

# **Exercise 286.** An inventory record specifies the name of an inventory item, a description, the acquisition price, and the recommended sales price.

Define a function that sorts a list of inventory records by the difference between the two prices.

# **Exercise 287.** Use `filter` to define `eliminate-exp`. The function consumes a number, `ua`, and a list of inventory records (containing name and price), and it produces a list of all those structures whose acquisition price is below `ua`.

Then use `filter` to define `recall`, which consumes the name of an inventory item, called `ty`, and a list of inventory records and which produces a list of inventory records that do not use the name `ty`.

In addition, define `selection`, which consumes two lists of names and selects all those from the second one that are also on the first.

# **Exercise 288.** Use `build-list` and `lambda` to define a function that

+   1. creates the list `(list 0 ... (- n 1))` for any natural number `n`;
+   2. creates the list `(list 1 ... n)` for any natural number `n`;
+   3. creates the list `(list 1 1/2 ... 1/n)` for any natural number `n`;
+   4. creates the list of the first `n` even numbers; and
+   5. creates a diagonal square of `0`s and `1`s; see exercise 262.