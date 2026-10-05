# Dictionaries and Tables: The q Fundamentals

Similar to vectors, indexing dictionaries outside their domain does not result in an error, but returns the null element:

```
d1 "d"
```

```
0Ni
```

```
d2`d
```

```
" "
```

```
vector 4
```

```
0N
```

Even the following is a dictionary:

```
m1:(1 2 3f;4 5 6f);
m2:(10 20f;30 40f);
(m1;m2)!(count m1;count m2)
```

```
1 2 3 4 5 6 2
10 20 30 40 2
```

therefore:

```
matdict:(m1;m2)!(count m1;count m2);
matdict:(10 20f;30 40f)
```

2

> More specifically, dictionaries in q define what is known as an algebraic map which is a partial function. It is worth mentioning this since uniqueness of key is not guaranteed in q:

```
isThisAllowed: `a`b`a`atil 4
isThisAllowed`a
```

```
0
```

The values of repeated entries for a key cannot be accessed.
The type of a dictionary is 99h as can be seen from:

```
type dict
```