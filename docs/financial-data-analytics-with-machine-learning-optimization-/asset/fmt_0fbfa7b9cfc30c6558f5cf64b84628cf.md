
The constant `1/2` is included to make the total variation distance `d_TV` take values between 0 and 1. If `d_TV(ν^(1), ν^(2)) = 0`, then `ν^(1) = ν^(2)`. For the other extreme case where `d_TV(ν^(1), ν^(2)) = 1`, `ν^(1)` and `ν^(2)` are singular to each other in the sense that `S` can be partitioned into two disjoint subsets `S'` and `S''` such that `ν^(1)` puts all of its probability mass on `S'` while `ν^(2)` puts all of its probability mass on `S''`. If `ν^(1), ν^(2), ...`, and `ν` are probability distributions on `S`, then we say that `ν^(n)` converges to `ν` in total variation as `n → ∞` if

```
lim_{n → ∞} d_TV(ν^(n), ν) = 0.
```

The total variation distance also has the natural interpretation of being the maximal absolute difference between the probabilities that the two distributions assign to any one event:
