In [18]:

```
values = np.array([5, -3, 2, 1])
squares = values * values # element-wise multiplication
print(squares,
    np.sum(squares),  # sum of squares. ha!
    np.dot(values, values), sep="\n")
```

[25  9  4  1]
39
39

If I wrote this mathematically, it would look like: dot(values,values) = ∑ᵢ vᵢ vᵢ = ∑ᵢ vᵢ².

# 2.5.3 Sum of Squared Errors

There is another very common summation pattern, the sum of squared errors, that fits in here nicely. In this case of mathematical terminology, the red herring is both red and a herring. If I have a known value actual and I have your guess as to its value predicted, I can compute your error with error = predicted - actual.

Now, that error is going to be positive or negative based on whether you over- or underestimated the actual value. There are a few mathematical tricks we can pull to make the errors positive. They are useful because when we measure errors, we don’t want two wrongs—overestimating by 5 and underestimating by 5—to cancel out and make a right! The trick we will use here is to square the error: an error of 5 → 25 and an error of −5 → 25. If you ask about your total squared error after you’ve guessed 5 and −5, it will be 25 + 25 = 50.

In [19]:

```
errors = np.array([5, -5, 3.2, -1.1])
display(pd.DataFrame({'errors':errors,
    'squared':errors*errors}))
```

|  | errors | squared |
|---|---|---|
| 0 | 5.0000 | 25.0000 |
| 1 | -5.0000 | 25.0000 |
| 2 | 3.2000 | 10.2400 |
| 3 | -1.1000 | 1.2100 |

So, a squared error is calculated by error² = (predicted − actual)². And we can add these up with ∑ᵢ(predictedᵢ − actualᵢ)² = ∑ᵢ errorᵢ². This sum reads left to right as, “the sum of (open paren) errors which are squared (close paren).” It can be said more succinctly: the sum of squared errors. That looks a lot like the dot we used above: