# 72

# LANGUAGE FUNDAMENTALS

```
f: { 1+rand x };
```

and

```
f\[5"
```

repeatedly calls f with parameter f[x_i - 1], and x_0 = 5, until two consecutive repeat, giving:

5 4 3

Passing in a float, we will observe convergence within a tolerance:

```
rand\[e-18\]
```

```
1e-18 2.58051e-19 2.22863e-19 1.703674e-19 1.495538e-19 9.947239e-20
1.440335e-20...
```

In q, float tolerance for two numbers x and y is defined as the ε, for which (x - y) < ε × max(x,y).

# 3.3 APPLY

The verbs @ and . apply a multivariate mapping to a list of arguments, written in prefix or infix form. Sections 3.3.1 and 3.3.2 describe the differences between the two notations.

# 3.3.1 @apply

The verb @ is used to apply a monadic function f on indices I of a list L. The following expression applies the function cosine on the first and third elements of the list; the second element 1.570796 being left unchanged:

```
@[(0.7853982; 1.570796; 3.141592654); 2; cos)]
```

It returns cos 0.7853982; 1.570796; cos 3.141592654:

```
0.707108 1.570796 -1
```

When applied to dyadic, @[L; f; a] applies a dyadic function f on the I-th elements of list L with second argument a. Example:

```
@[1 2 3 4f; 0; {x+2y}; 6 7f]
```

applies the function x+2*y on the first and third elements of 1 2 3 4f, namely 1 and 3 and the second argument 6 7f. The values of L=1 2 3 4f for all elements not in Ø 2 are returned, i.e. L@1=2 and L@3=4f. The expression computes 1+2+6f 2+3*7f 4f:

13 2 17 4f