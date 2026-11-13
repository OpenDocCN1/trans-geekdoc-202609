| # of occurrences | sensible | irrelevant |
|---|---|---|
| size | finite but arbitrary | finite or infinite |

The last row in this table presents a new idea, though an obvious one, too. Many of the sets mentioned in this book are infinitely large, for example, Number, String, and also List-of-strings. In contrast, a list is **always** finite though it may contain an arbitrarily large number of items.

In sum, this section explains the essential differences between sets and lists and how to represent finite sets with finite lists in two different ways. BSL is not expressive enough to represent infinite sets; exercise 299 introduces a completely different representation of sets, a representation that can cope with infinite sets, too. The question of how actual programming languages represent sets is beyond the scope of this book, however.

Exercise 160. Design the functions `set+.L` and `set+.R`, which create a set by adding a number x to some given set s for the left-hand and right-hand data definition, respectively.