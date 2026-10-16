+   - We used accuracy to evaluate the performance.
+   - We didn’t try different numbers of neighbors.
+   - We only compared two simple models.

Additionally, linear regression is quite sensitive to using standardized data. While *diabetes* came to us prestandardized, we need to keep in mind that *we* might be responsible for that step in other learning problems. Another issue is that we can often benefit from restricting the weights—the {m, b} or w—that a linear regression model can use. We’ll talk about why that is the case and how we can do it with `sklearn` in Section 9.1.

# 4.6.2 Summary

Wrapping up our discussion, we’ve seen several things in this chapter:

+   1. *diabetes*: a simple real-world dataset
+   2. Linear regression and an adaptation of nearest-neighbors for regression
+   3. Different measures of center—the mean and median
+   4. Measuring learning performance with root mean squared error (RMSE)

# 4.6.3 Notes

The *diabetes* data is from a paper by several prominent statisticians which you can read here: http://statweb.stanford.edu/~tibs/ftp/lars.pdf.

# 4.6.4 Exercises

You might be interested in trying some classification problems on your own. You can follow the model of the sample code in this chapter with another regression dataset from `sklearn`: `datasets.load_boston` will get you started!