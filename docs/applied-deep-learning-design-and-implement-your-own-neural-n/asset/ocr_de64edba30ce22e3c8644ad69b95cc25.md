Where a, b, c, and d are the rows of the data set, and the dimension of the data set is '. Here, we will find out the similarity between two rows of the data set, say the similarity between a and b as follows:

```
Sim(a,b)
```

It lies in the range of 0 to 1, that is,

```
Sim(a,b) ∈ [0,1]
```

Now, let us say the data set is D. For all values of a, which belong to D, that is,

```
∀a ∈ D
```

The similarity between a and a is 1 for the case of two identical rows in a data set, as shown in figure 7.26:

| | 1 | 2 | ..... | d |
|---|---|---|---|---|
| a | | | | |
| b | | | | |
| c | | | | |
| d | | | | |
| a | | | | |

Figure 7.26: Two identical rows in the considered data set

```
Sima,a=1
```

And for all values of a and b, which belong to D, that is,

```
∀a,b∈D
```

Here, if a and b are completely different, then

```
Sim(a, b) = 0
```

Similarly, for all values of a, b and c, which belong to D, that is,

```
∀a, b, c ∈ D
```

If we have the following condition:

```
Sim(a, b) < Sim(a, c)
```