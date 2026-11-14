paste this line directly into a cell, you will likely get a #CALC! error. That's because you have a generic function with nothing passed in. To test your LAMBDA, you simply add parentheses to the end of the function (it's as if the LAMBDA declaration is the function name). Take a look at Figure 8.4 to see this up close.

![](bbox=[0.151, 0.222, 0.696, 0.372])

# Figure 8.4: Testing the LAMBDA by sending in parameters

As you can see, B2 is passed into the LAMBDA as the current_row parameter. It's then run through the OFFSET function. But where LAMBDA really take off is when they allow us to assign them to a named range. So, you can take the formula defined earlier (without the additional parenthesis passing anything through) and assign it to a named range. With the formula copied, go to the Formulas tab and click Define Name. Give it a name like GetPreviousPeriod and paste in the LAMBDA function in the Refers To field (see Figure 8.5). Click OK when you're ready.

![](bbox=[0.151, 0.591, 0.452, 0.782])

# Figure 8.5: Assigning a LAMBDA to a named range

From here on out, the LAMBDA can be treated like a new Excel function. Simply use =GetPreviousPeriod(cell_reference). Because this isn't a programming book, we won't use LAMBDAS specifically in this chapter, but hopefully you can see how they're useful in your analysis as you go through this chapter. And perhaps in your own work as well.