In the normal course of our application, this might be the fifth call made to `get_constant()`, so `MY_CONSTANT` would end up being defined as 32768. But suppose you want to watch for `MY_CONSTANT` somewhere else, such as in a debugging function. You can put the same call to `get_constant()` in the header file of your application:

```
$global_variable = get_constant('MY_CONSTANT');
```

This is the first call to `get_constant()` that is executed, so `MY_CONSTANT` will be defined as 2048. The point is, it doesn’t matter. It’s the same value that will be returned inside the `foo()` function when it makes its `get_constant()` call. As long as `MY_CONSTANT` represents the same value everywhere in the application, that’s what counts.

# # Summary

If you would like to see how the rest of the code comes together, take a look at the accompanying CD. The other files are well commented and should be relatively easy to follow.

You should come away from this chapter with an understanding of two concepts:

+   - First, recursion. Recursion is a nifty tool that can be very helpful at times.
+   - Second, the way we went about organizing the data. We didn’t follow a strict normalization procedure, like the one described in Chapter 1. Here we were more concerned with what gets the job done. In the end that’s what all application developers are trying to do, right?

Finally, we covered how to set up your own error handler, and some of the uses to which you might put it. As with the HTML functions, you might decide that you want to use a different approach. If so, feel free to ignore our example.