# Differential Calculus

```
x=[1,4,9,16]
np.sqrt(x)
```

```
OUT:
array([1., 2., 3., 4.])
```

In this case, the function was applied to each element in the list: $(\sqrt{1}, \sqrt{4}, \sqrt{9}, \sqrt{16})$. Note that every module supports单独. If we attempt this with the math package, it emits an error:

```
x=[1,4,9,16]
math.sqrt(x)
```

```
OUT:
TypeError: must be real number, not list
```

The error indicates that sqrt() from the math package should be applied to a single value.

# 8.3 Differential Calculus

Data science uses models which rely on important properties like the continuity of a function. This is treated with calculus, which belongs to the branch of mathematics called analysis. Next, we will take a quick tour to learn some essential calculus concepts.

# Limit

The concept of a limit, mentioned earlier, is fundamental to analysis. The limit of a sequence can be explained with an example:

Consider the sequence with terms:

> $a_1=1, a_2=\frac{1}{2}, a_3=\frac{1}{3}, \dots, a_n=\frac{1}{n}, \dots$$

As we look terms deeper into the sequence (with larger $n$), they get closer to zero. None of the terms will be equal to zero, but we can get arbitrarily close to zero. In fact, there is a term $a_n$ such that all subsequent terms are sufficiently close to zero. For example, if we wish to be within $1/10$ of zero, then terms $a_{10}=\frac{1}{10}$ will suffice. We can express this notion by saying that as $n$ increases, the terms $a_n$ tend to zero, or that they have a limit of 0. We can also say that the sequence converges to zero, denoted: