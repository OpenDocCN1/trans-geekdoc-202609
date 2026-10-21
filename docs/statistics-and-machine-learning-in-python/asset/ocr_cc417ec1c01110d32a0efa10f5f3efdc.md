```
[33.  1.  2.  3.  4.  5.  6.  7.  8.  9.]
[[0.  1.  2.  3.  4.]
 [5.  6.  7.  8.  9.]]
```

Ravel: returns a view of the original array whenever possible.

```
arr_flt = arr.ravel()
arr_flt[0] = 33
print(arr_flt)
print(arr)
```

Out:

```
[33.  1.  2.  3.  4.  5.  6.  7.  8.  9.]
[[33.  1.  2.  3.  4.]
 [ 5.  6.  7.  8.  9.]]
```

# 4.4 Stack arrays

Stack flat arrays in columns

```
a = np.array([0, 1])
b = np.array([2, 3])

ab = np.stack((a, b)).T
print(ab)

# or
np.hstack((a[:, None], b[:, None]))
```

Out:

```
[[0 2]
 [1 3]]
```

# 4.5 Selection

Single item

```
arr = np.arange(10, dtype=float).reshape((2, 5))

arr[0]      # 0th element (slices like a list)
arr[0, 3]   # row 0, column 3: returns 4
arr[0][3]   # alternative syntax
```

# 4.5.1 Slicing

Syntax: start:stop:step with start (default 0) stop (default last) step (default 1)