examples.

# **Exercise 63.** Evaluate the following expressions:

+   - `(distance-to-0 (make-posn 3 4))`

+   - `(distance-to-0 (make-posn 6 (* 2 4)))`

+   - `(+ (distance-to-0 (make-posn 12 5)) 10)`

by hand. Show all steps. Assume that sqr performs its computation in a single step. Check the results with DrRacket’s stepper.

# **Exercise 64.** The Manhattan distance of a point to the origin considers a path that follows the rectangular grid of streets found in Manhattan. Here are two examples:

![](bbox=[0.111, 0.411, 0.405, 0.595])

![](bbox=[0.59, 0.411, 0.885, 0.595])

The left one shows a “direct” strategy, going as far left as needed, followed by as many upward steps as needed. In comparison, the right one shows a “random walk” strategy, going some blocks leftward, some upward, and so on until the destination—here, the origin—is reached.

Stop! Does it matter which strategy you follow?

Design the function manhattan-distance, which measures the Manhattan distance of the given posn to the origin.