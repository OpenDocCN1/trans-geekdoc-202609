The recursive summation function developed in this section might seem elegant and graceful to the eye, but each call at runtime requires an extra chunk of computer memory to support the storage for the arguments and return values. Thus, the amount of memory required to run this function grows as a linear function of the size of the range of numbers being summed. For small ranges, this is not a significant problem, but for large ranges, a loop-based summation provides a better alternative.

The loop-based version of the summation function uses a for loop with the range function and adds each value to an ongoing total. The total is initially set to 0 and is returned when the loop finishes. Here is the code:

```
def summation(low, high):
    """Returns the summation of the integers
    from low to high.
    Precondition: low <= high."""
    total = 0
    for number in range(low, high + 1):
        total += number
    return total
```

Why is the runtime performance of this version better than the recursive version? The loop-based function is called just once, with memory allocated for the two arguments low and high and for the temporary variables total and number. On each pass through the loop, the values in this storage are reset, but no new storage is ever added or ever needed.

So now you might ask, “Why do I need to bother with recursion at all, if a loop-based function seems to perform better than a recursive one?” There are two cases in which you might still prefer a recursive alternative.

The first reason you might prefer recursion is that it allows you to write some recursive functions that do not result in growth of memory usage at runtime. These functions are called tail-recursive functions. In a tail-recursive function, no operation is performed after a recursive call. The recursive summation function defined earlier is not, on this definition, tail recursive. After each recursive call of summation returns, its total is added to the previous value of the low argument, in the following statement:

```
return low + summation(low + 1, high)
```

To convert such a function to a tail-recursive function, you need to think of a way of passing the total as an extra argument to each function call. Then you can increase the total at runtime before each recursive call, rather than after. In the case of the summation function,