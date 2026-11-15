```
{ 2 * } double WORD
{ 2 4 6 8 } double MAP ( → { 4 8 12 16 })
```

The sum of a list numbers can be obtained by using a fold left operation:⁴

```
0 2 4 6 8 + FOLDL ( → 20)
```

Note how the fold operation results in a single value, while the map operation alters all values in a list.

³Please refer to the Functions & Abstractions chapter.

⁴In functional programming, fold left and fold right functions are known as list reducers, as they fold each item of a list into the initial value, at right or left respectively.

# 16.3 RANDOM ACCESS & SORTED LIST

With connectedness strictly required, a list must be traversed in order to access any element. However, it is more expedient to access an element directly by its index number, without traversal. To do so, we relax the connectedness property with a variation on List called a random access list.⁵

A random access list may be illustrated as an array of elements.