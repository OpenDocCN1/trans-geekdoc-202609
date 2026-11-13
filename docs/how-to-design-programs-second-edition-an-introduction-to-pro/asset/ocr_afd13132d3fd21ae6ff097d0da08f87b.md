+   • Design a function that selects the first from a sorted list of pairs.

Consider designing both. Which one do you prefer? Why? ¶

# **Exercise 198.** Design words-by-first-letter. The function consumes a Dictionary and produces a list of Dictionaries, one per Letter.

Redesign most-frequent from exercise 197 using this new function. Call the new function most-frequent.v2. Once you have completed the design, ensure that the two functions compute the same result on your computer’s dictionary:

```
(check-expect
 (most-frequent AS-LIST)
 (most-frequent.v2 AS-LIST))
```

# **Note on Design Choices** For words-by-first-letter you have a choice for dealing with the situation when the given dictionary does not contain any words for some letter:

+   • One alternative is to exclude the resulting empty dictionaries from the overall result. Doing so simplifies both the testing of the function and the design of most-frequent.v2, but it also requires the design of an auxiliary function.

+   • The other one is to include ’() as the result of looking for words of a certain letter, even if there aren’t any. This alternative avoids the auxiliary function needed for the first alternative but adds complexity to the design of most-frequent.v2. End

**Note on Intermediate Data and Deforestation** This second version of the word-counting function computes the desired result via the creation of a large intermediate data structure that serves no real purpose other than that its parts are counted. On occasion, the programming language eliminates them automatically by fusing the two functions into one, a transformation on programs that is also called deforestation. When you know that the language does not deforest programs, consider eliminating such data structures if the program does not process data fast enough. ¶