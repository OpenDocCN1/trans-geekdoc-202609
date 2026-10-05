# Functions

and returns:

```
-21 -32 -45
-20 -31 -44
-19 -30 -43
```

The built-in operator cross computes the Cartesian product between two objects. For lists, cross y is equivalent to raze x/:\y.

```
(4 5 6f) cross (5 6 7f)
```

returns

+   4 5
4 6
4 7
5 5
5 6
5 7
6 5
6 6
6 7

# 3.2.1.5 Each-both

The more general each-both adverb modifies dyadic functions and verbs to apply to the items of lists instead of the lists themselves. The cardinality of both lists must be the same. The expression:

```
(`a``b`;`c`),(`4;5;6)
```

applies the each-both adverb ` to the dyadic function , on the two lists (`a`;`b`;`c`) and (4;5;6) resulting:

+   `a 4
`b 5
`c 6

> Note that the cardinality of both lists must be the same, otherwise a `length error returned:

```
(`a``b`),(`a``b``c`)
```

returns the error message:

```
`length
```