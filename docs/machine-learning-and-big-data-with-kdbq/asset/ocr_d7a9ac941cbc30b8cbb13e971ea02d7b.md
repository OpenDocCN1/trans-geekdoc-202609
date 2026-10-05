# 76

# LANGUAGE FUNDAMENTALS

The err expression can be a function whose first argument will be the error as a string:

```
mult{.;*(x;y); {"Error is: ",x]}
```

```
mult[4;"toto"]
```

```
"Error is: type"
```

# 3.5 VECTOR OPERATIONS

Until now, we have covered a number of native q functions and shown how to define our own. In this section, we will present a few more native functions which cover basic series operations. We split the functions into two classes: aggregators and uniform functions.

# 3.5.1 Aggregators

# 3.5.1.1 Simple Aggregators

The first class are our basic aggregators: min, max, avg, med, var, dev

```
min 3 1 4 1 6 7 4 3 8 9 1 2f / minimum
```

```
1f
```

```
max 3 1 4 1 6 7 4 3 8 9 1 2f / maximum
```

```
9f
```

```
avg 3 1 4 1 6 7 4 3 8 9 1 2f / average
```

```
4.083333
```

```
med 3 1 4 1 6 7 4 3 8 9 1 2f / median
```

```
3.5
```

```
var 3 1 4 1 6 7 4 3 8 9 1 2f / variance
```

```
7.243056
```