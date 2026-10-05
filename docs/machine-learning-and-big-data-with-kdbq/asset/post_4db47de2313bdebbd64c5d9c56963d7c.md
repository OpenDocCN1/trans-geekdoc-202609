
## Functions

## 3.2.1.1 Each

The each adverb modifies a monadic function so that it applies to each item in a list rather than to the list as a whole. Hence, the ad each in the following code list applies the monadic function to each single element of the nested list.

```
reverse ((`a`b`c);(``d`e`f))
```

| c b a |
| f e d |

Without introducing the verb each, the two sublists would be inverted:

```
reverse ((`a`b`c);(``d`e`f))
```

returns

| d e f |
| a b c |

## 3.2.1.2 Each-left \

The each adverb \ modifies a dyadic function so that it applies the second argument on each item of the first argument. In other words, x f \ y f between y and items of x. The following expression:

```
(4 5 6) { x-y xexp 2 }:(5 6 7)
```

- 4-5 xexp 2 4-6 xexp 2 4-7 xexp 2
- 5-5 xexp 2 5-6 xexp 2 5-7 xexp 2
- 6-5 xexp 2 6-6 xexp 2 6-7 xexp 2
namely:

```
-21 -32 -45
-20 -31 -44
-19 -30 -43
```

Note the above can be rewritten using a combination of a projection and the unary each in one call:

```
{ x-y xexp 2 };[5 6 7f]each 4 5 6
```

```
-21 -32 -45
-20 -31 -44
-19 -30 -43
```

The outer product between two vectors u ⊗ v = uvᵀ can be written as:

```
.quantQ.outer:{x *:\y}
```

where we have defined the function within the book’s namespace.

## 3.2.1.3 Each-right /:

The each-right adverb :/ modifies a dyadic function so that it applies the first argument to each item of the second argument. Applying the each-right adverb to the same x–y xexp 2 function and the same arguments:

```
(4 5 6) { x-y xexp 2 }\:(5 6 7f)
```

returns:

```
-21 -20 -19
-32 -31 -30
-45 -44 -43
```

Moreover, similarly to the left-left case, this can alternatively be written as

```
{ x-y xexp 2 }[4 5 6];each (5 6 7f)
```

```
-21 -20 -19
-32 -31 -30
-45 -44 -43
```

The identity matrix can be built with each-left or each-right adverbs as follows:

```
quant.identity:[:n]) `float($til)=:til n
```

It checks whether each element of til namely 0, 1, 2, ..., n-1 is equal to each element of til on the right-hand side.

```
quant.Q identity[4]
```

returns:

```
1 0 0 0
0 1 0 0
0 0 1 0
0 0 0 1
```

## 3.2.1.4 Cross Product / ::

The cross product or Cartesian product is the composition of an each-right with an each-left. It pairs each item on the left with each item on the right:

```
(4 5 6) { x-y xexp 2 }\:(5 6 7f)
```

It equivalent to:

```
(4 { x -y xexp 2}\:(5 6 7f); 5 { x -y xexp 2}\:(5 6 7f); 6 { x -y xexp 2}\:(5 -6 7f))
```

## Functions

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

4 5
4 6
4 7
5 5
5 6
5 7
6 5
6 6
6 7

## 3.2.1.5 Each-both

The more general each-both adverb modifies dyadic functions and verbs to apply to the items of lists instead of the lists themselves. The cardinality of both lists must be the same. The expression:

```
(`a``b`;`c`),(`4;5;6)
```

applies the each-both adverb to the dyadic function , on the two lists (`a`;`b`;`c`) and (4;5;6) resulting:

- `a` 4
- `b` 5
- `c` 6

> Note that the cardinality of both lists must be the same, otherwise a `length returned:

```
(`a``b`),(`a``b``c`)
```
returns the error message:

```
`length
```

## LANGUAGE FUNDAMENTALS

The each-adverb can be used to add columns to tables as tables are the list of records.

```
tbl1::[]c1::`a`b`c);
tbl2::[]c2
```

joins the column of tbl1 with the column of tbl2:

```
c1
b
c
```

The * can be applied to user-defined functions:

```
(4 5 6f) {x*y}(5 6f)
```

The code applies the adverb * on the function x*y with arguments (4 5 6f) and (5 6f). In this trivial example, it is equivalent to calling the dyadic function x*y on the two lists ((4 5 6f); (5 6f)) with the dot notation:

## Functions

## The dot product

Note that in many cases, the native functions will be sufficient to apply the each or each-both adverbs. For example, the dot product between two vectors,

| a1 | b1 |
| a2 | b2 |
| ... | ... |
| an | bn |

need to be defined as:

```
x: 1 2 3
y: 3 4 5
```

since the native multiplication operator already applies on two vectors, So the above can be simplified to

sum x * y.

Moreover, for dot product, there is a built-in function, as we saw in Chapter 1: A complex example, which better illustrates a case where we can use each-both, when we have a more complicated, and therefore makes sense to be applied over the element of the two lists in pairwise manner.

Here we have a table where calc is a nested column, each entry in a is a vector. The first argument applies to a vector, whereas the second is scalar. Each of the two inputs, the vector and a scalar, could be the first record in our table t, e.g.-1.011575 0.383739 0.188203 and 7.

Let's assume our calc function is also piecewise, thus differently based on a condition:

```
calc: { $[ all ø < x; x recip y; x recip y }
```

and

```
calc[-1.011575 0.383739 0.188203; 7];
```

```
-1.083894 0.001225324 8.557739e-06
```

## LANGUAGE FUNDAMENTALS

How to pass this function from all entries (records) of table?

```
r: update c = calc'[a;b] from t;
r
```

| a | b | c |
|---|---|---|
| -0.11575 | 0.387398 | 0.188203 |
| -7 -108391 | 0.001225324 | 8.557739e-06 |
| -0.4292475 | -0.1388364 | 0.117361 |
| 0.6093965 | -0.7769351 | -2.282934 |
| -2.147298 | 2.101333 | -2.305268 |
| 1.372702 | 1.740763 | 0.139957 |
| -1.452881 | -2.820678 | 0.0950256 |
| -2.138477 | -2.430328 | -2.169664 |
| 0.351839 | -1.361123 | 0.8741012 |
| 0.2354421 | -2.222245 | -2.128178 |
| 2.325267 | -0.3603932 | -1.23661 |
| 0.742755 | -2.097245 | 0.834178 |
| 1.872449 | -2.141622 | -0.290992 |
| -1.538376 | 2.1160815 | -2.275455 |
| -0.3917162 | 1.8033989 | -0.3954571 |

## 3.2.2 Each-prior '

The each-prior adverb : performs a dyadic operation on each list of items with its predecessor. Let us consider an example:

```
4 (x-y xexp 2); (5 6 xexp 2)
```

which applies the function x-y xexp does each item of the list 5 6 xexp and its predecessor. Hence, the expression is equivalent to:

```
(5 - 4 xexp 2; 6-5 xexp 2; 7 - 6 xexp 2)
```

and returns:
The monadic version of the each-prior adverb does not choose an initial value:

```
((x-y xexp 2)')(5 6 xexp 2)
```

It is equivalent to:

```
(5f-0nxexp 2; 6-5f xexp 2; 7 - 6 xexp 2)
```

and returns:

```
Øn -19 -29
```
