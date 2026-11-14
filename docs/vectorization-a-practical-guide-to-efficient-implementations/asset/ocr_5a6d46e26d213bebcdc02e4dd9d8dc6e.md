which seems to be slow (on my M1 MacBook Pro)

```
```
32.3 ms ± 390 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)
```
```

Using list comprehension

```
```
[0 for _ in range(1_000_000)]
```
```

seems to improve the performance

```
```
17.3 ms ± 586 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```
```

We can also use a one-liner with Python's syntax candy operator * on the list

```
```
[0] * 1_000_000
```
```

which is much faster

```
```
2.69 ms ± 66.6 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```
```

Still, none of the above beats the performance of the NumPy function np.zeros

```
```
np.zeros(1_000_000)
```
```

which is the fastest

```
```
537 µs ± 39.8 µs per loop (mean ± std. dev. of 7 runs, 1,000 loops each)
```
```

By using np.zeros, we can also easily create a multi-dimensional tensor (not just a 1-D vector), which then helps us perform additional downstream vectorized operations.

But why pre-allocate or initialize a vector at all? This again has something to do with performance. It can be said that extending an array on the fly is more costly than pre-allocating a portion of the memory for our computations. Let's show this