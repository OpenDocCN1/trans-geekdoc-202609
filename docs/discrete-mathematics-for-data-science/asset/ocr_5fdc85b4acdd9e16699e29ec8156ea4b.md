sorting were applicable. Once drawn from the bag, elements can be processed into more restrictive collections by data type as needed.

Therefore, we should be able to construct a bag mixed of numbers and characters, such as:

```
{ a 3 b b } bag₀ LIST
```

Typical bag and set operations include:

+   • Inserting or adding elements.
+   • Removing certain elements.
+   • Verifying that certain elements exist.
+   • Counting some or all elements.

# 15.2 RANDOM SELECTIONS OF DATA

Due to the unordered nature of bags and sets, adding, removing, and searching bag and set data entails a random function. Randomly searching a bag is less efficient than searching a list if element removal is not part of the selection operation. This is because the random aspect of bag retrieval occasionally results in selecting the same elements, while random selection from a list can still be limited to a range of indices.

In computer programs, the selection of elements at random depends on a function that generates numbers at random. To be practical, such a random number generator must be limited to a range of integers. Numbers outside of a reasonable range may be too large or too small to apply to the problem at hand.

Here is an example number generating function:

```
{ -10 10 RAND } rng WORD
rng ( → 4)
rng ( → -2)
```