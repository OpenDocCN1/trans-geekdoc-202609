# 68

# LANGUAGE FUNDAMENTALS

The over advert is often called fold when the function has two arguments. The expression f[/x;y;z] computes expression f[f..f[x;y_0];y_1;z_1]:..y_{n-2};z_{n-2}];y_{n-1};z_{n-1}].

```
{{x-y xexp 2)}/(1 3f; 4f; 2f)
```

computes

```
( 2f + (2f+1f-4f xexp 2) - 5f xexp 2; 2f + (2f+3-4f xexp 2) - 5f xexp 2)
```

and returns:

```
-36 -34f
```

The advert can also be thought of in a map-reduce context, where we fold, i.e. reduce, the result. A very useful built-implementation of this is the function raze, which folds the input list into a single element:

```
raze (1 2 3;4 5 6)
```

Examining the implementation of raze reveals that it is the comma-join with the advert fold:

```
raze
```

```
/
```

and

```
(,/) (1 2 3;4 5 6)
```

+   1 2 3 4 5 6

# 3.2.5 Scan

The scan behaves as the over advert except that intermediary results are shown after each accumulation. Hence, f \y iteratively computes expression f[f..f[x;y_0];y_1;..y_{n-2}];y_{n-1}] and displays each intermediary result (x;f[x;y_0];y_1;..f[x;y_0];y_1];..f[f..f[x;y_0];y_1];..y_{n-2}];y_{n-1}]).

We saw in our previous example that

```
{(x-y xexp 2)}/(5 6 7f)
```

only returns the final result of the computation, i.e. (5f - 6f xexp 2)-7f xexp 2 -80f

while

```
{(x-y xexp 2)\}(5 6 7f)
```