
The benefit of `sum()` is that like with other NumPy aggregation functions, this summation can be done along rows or columns as well:

```
In [17]:
# how many values less than 6 in each row?
np.sum(x < 6, axis=1)
Out[17]:
array([4, 2, 2])
```

This counts the number of values less than 6 in each row of the matrix.

If we're interested in quickly checking whether any or all the values are true, we can use (you guessed it) `np.any` or `np.all`:

```
In [18]:
# are there any values greater than 8?
np.any(x > 8)
Out[18]:
True
```

```
In [19]:
# are there any values less than zero?
np.any(x < 0)
Out[19]:
False
```

```
In [20]:
# are all values less than 10?
np.all(x < 10)
Out[20]:
True
```

```
In [21]:
# are all values equal to 6?
np.all(x == 6)
Out[21]:
False
```

`np.all` and `np.any` can be used along particular axes as well. For example:

```
In [22]:
# are all values in each row less than 8?
np.all(x < 8, axis=1)
Out[22]:
array([True, False, True], dtype=bool)
```

Here all the elements in the first and third rows are less than 8, while this is not the case for the second row.

Finally, a quick warning: as mentioned in [Aggregations: Min, Max, and Everything In Between](https://jakevdp.github.io/PythonDataScienceHandbook/02.04-computation-on-arrays-aggregates.html), Python has built-in `sum()`, `any()`, and `all()` functions. These have a different syntax than the NumPy versions, and in particular will fail or produce unintended results when used on multidimensional arrays. Be sure that you are using `np.sum()`, `np.any()`, and `np.all()` for these examples.

## Boolean operators

We've already seen how we might count, say, all days with rain less than four inches, or all days with rain greater than two inches. But what if we want to know about all days with rain less than four inches and greater than one inch? This is accomplished through Python's bitwise logic operators, `&`, `|`, `^`, and `~`. Like with the standard arithmetic operators, NumPy overloads these as ufuncs which work element-wise on (usually Boolean) arrays.

For example, we can address this sort of compound question as follows:

```
In [23]:
np.sum((inches > 0.5) & (inches < 1))
Out[23]:
29
```

So we see that there are 29 days with rainfall between 0.5 and 1.0 inches.

Note that the parentheses here are important–because of operator precedence rules, with parentheses removed this expression would be evaluated as follows, which results in an error:

`inches > (0.5 & inches) < 1`

Using the equivalence of `A AND B` and `NOT (NOT A OR NOT B)`, we can compute the same result in a different manner:

```
In [24]:
np.sum(~((inches <= 0.5) | (inches >= 1)))
Out[24]:
29
```

Combining comparison operators and Boolean operators on arrays can lead to a wide range of efficient logical operations.

The following table summarizes the bitwise Boolean operators and their equivalent ufuncs:

| Operator | Equivalent ufunc |
| :--- | :--- |
| `&` | `np.bitwise_and` |
| `|` | `np.bitwise_or` |
| `^` | `np.bitwise_xor` |
| `~` | `np.bitwise_not` |

Using these tools, we might start to answer the types of questions we have about our weather data. Here are some examples of results we can compute when combining masking with aggregations:

```
In [25]:
print("Number days without rain:      ", np.sum(inches == 0))
print("Number days with rain:         ", np.sum(inches != 0))
print("Days with more than 0.5 inches:", np.sum(inches > 0.5))
print("Rainy days with < 0.2 inches  :", np.sum((inches > 0) &
(inches < 0.2)))
Number days without rain:      215
Number days with rain:         150
Days with more than 0.5 inches: 37
Rainy days with < 0.2 inches: 75
```

## Boolean Arrays as Masks

A more powerful pattern is to use Boolean arrays as masks, to select particular subsets of the data themselves. Returning to our `x` array from before, suppose we want an array of all values in the array that are less than, say, 5:

```
In [26]:
x
Out[26]:
array([[5, 0, 3, 3],
       [7, 9, 3, 5],
       [2, 4, 7, 6]])
```

We can obtain a Boolean array for this condition easily, as we've already seen:

```
In [27]:
x < 5
Out[27]:
array([[False, True,  True,  True],
       [False, False, True, False],
       [True,  True, False, False]], dtype=bool)
```

Now to select these values from the array, we can simply index on this Boolean array; this is known as a masking operation:

```
In [28]:
x[x < 5]
Out[28]:
array([0, 3, 3, 3, 2, 4])
```

What is returned is a one-dimensional array filled with all the values that meet this condition; in other words, all the values in positions at which the mask array is `True`.

We are then free to operate on these values as we wish. For example, we can compute some relevant statistics on our Seattle rain data:

```
In [29]:
# construct a mask of all rainy days
rainy = (inches > 0)
# construct a mask of all summer days (June 21st is the 172nd day)
days = np.arange(365)
summer = (days > 172) & (days < 262)
print("Median precip on rainy days in 2014 (inches):  ",
np.median(inches[rainy]))
print("Median precip on summer days in 2014 (inches): ",
np.median(inches[summer]))
print("Maximum precip on summer days in 2014 (inches):",
np.max(inches[summer]))
print("Median precip on non-summer rainy days (inches):",
np.median(inches[rainy & ~summer]))
Median precip on rainy days in 2014 (inches):   0.194881889764
Median precip on summer days in 2014 (inches):  0.0
Maximum precip on summer days in 2014 (inches): 0.850393700787
Median precip on non-summer rainy days (inches): 0.200787401575
```

By combining Boolean operations, masking operations, and aggregates, we can very quickly answer these sorts of questions for our dataset.

## Aside: Using the Keywords and/or Versus the Operators &/|

One common point of confusion is the difference between the keywords `and` and `or` on one hand, and the operators `&` and `|` on the other hand. When would you use one versus the other?

The difference is this: `and` and `or` gauge the truth or falsehood of entire object, while `&` and `|` refer to bits within each object.

When you use `and` or `or`, it's equivalent to asking Python to treat the object as a single Boolean entity. In Python, all nonzero integers will evaluate as `True`. Thus:

```
In [30]:
bool(42), bool(0)
Out[30]:
(True, False)
```

```
In [31]:
bool(42 and 0)
Out[31]:
False
```

```
In [32]:
bool(42 or 0)
Out[32]:
True
```

When you use `&` and `|` on integers, the expression operates on the bits of the element, applying the `and` or the `or` to the individual bits making up the number:

```
In [33]:
bin(42)
Out[33]:
'0b101010'
```

```
In [34]:
bin(59)
Out[34]:
'0b111011'
```

```
In [35]:
bin(42 & 59)
Out[35]:
'0b101010'
```

```
In [36]:
bin(42 | 59)
Out[36]:
'0b111011'
```

Notice that the corresponding bits of the binary representation are compared in order to yield the result.

When you have an array of Boolean values in NumPy, this can be thought of as a string of bits where `1 = True` and `0 = False`, and the result of `&` and `|` operates similarly to above:

```
In [37]:
A = np.array([1, 0, 1, 0, 1, 0], dtype=bool)
B = np.array([1, 1, 1, 0, 1, 1], dtype=bool)
A | B
Out[37]:
array([ True,  True,  True, False,  True,  True], dtype=bool)
```

Using `or` on these arrays will try to evaluate the truth or falsehood of the entire array object, which is not a well-defined value:

```
In [38]:
A or B
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-38-5d8e4f2e21c0> in <module>()
----> 1 A or B
ValueError: The truth value of an array with more than one element is ambiguous. Use a.any() or a.all()
```

Similarly, when doing a Boolean expression on a given array, you should use `|` or `&` rather than `or` or `and`:

```
In [39]:
x = np.arange(10)
(x > 4) & (x < 8)
Out[39]:
```
