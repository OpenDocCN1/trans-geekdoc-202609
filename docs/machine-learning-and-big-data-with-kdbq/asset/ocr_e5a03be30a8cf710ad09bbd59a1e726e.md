# 78

# LANGUAGE FUNDAMENTALS

# Example

```
maxs 3 1 4 1 6 7 4 3 8 9 1 2 f
```

returns:

```
3 3 4 6 7 7 7 8 9 9 9 f
```

The outcome is thus a vector of the same length.

# 3.5.2.2 Window Functions

The last class of functions focuses on calculating a “running” function over a moving window of fixed length. Unlike the previous case, in which the current value was the running total, the functions listed below forget observations which are too far from current observation and only focus on a fixed window.

Each function takes two arguments: the first argument is an integer k representing memory and the second argument is a vector x1;x2;x3;x4;...xN, which is used to iteratively apply the calculation of the function. Namely, the core function is applied on vectors of length k. For the first k1 elements, the list is truncated as there is no full memory. The first iterations are therefore applied on: enlist x1, (x1;x2), (x1;x2, x3), and once the full memory is available, the memory steps in and sub-vectors look as: (x2;x3;...x(k+1)) etc.

+   - mavg - The function is applied on a vector and returns the running average, avg, over a sub-vector of fixed length.
- mdev - The function is applied on a vector and returns the running standard deviation, dev, over a sub-vector of fixed length.
- mcount - The function is applied on a vector and returns a counter of non-missing elements, count, over a sub-vector of fixed length.
- mmax - The function is applied on a vector and returns the running maximum, max, over a sub-vector of fixed length.
- mmin - The function is applied on a vector and returns the running minimum, min, over a sub-vector of fixed length.
- msum - The function is applied on a vector and returns the running sum, sum, over a sub-vector of fixed length.

```
xmax[3; 3 1 4 1 6 7 4 3 3 3 8 9 1 2 f]
```

```
3 3 4 6 7 7 7 4 3 8 9 9 9 f
```

and using infix notation

```
3 mcount 3 3 4 6 7 7 7 4 3 8 9 0 9 f
```

```
1 2 3 3 3 3 3 3 3 3 3 2 2
```