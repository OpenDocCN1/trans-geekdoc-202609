You may be wondering how this formula works. Sometimes, I think IFS are overkill. This formula works by using a Boolean expression. First, it tests if the feature equals a certain value. This will return a TRUE or FALSE in Excel. What’s interesting (or perhaps weird, depending upon who you ask), is that Excel can’t immediately translate those TRUEs and FALSEs into 1s and 0s without a mathematical operation that converts them. Multiplying by 1 quickly converts the result from a Boolean into a number. Many Excel gurus use this shorthand to convert Booleans.

The same goes for values “F” in the Female column, “H” in the Home column, and “A” in the Apt column. In all, your column formulas should look like this:

```
Male: = (CustomerData[@[Implied Gender]]="M") * 1
Female: = (CustomerData[@[Implied Gender]]="F") * 1
Home: = (CustomerData[@[Home/Apt/ PO Box]]="H") * 1
Apartment: = (CustomerData[@[Home/Apt/ PO Box]]="A") * 1
```

Because we’re dealing with an Excel Table, the formulas automatically copy all the way down (see Figure 6.3). You can use the format painter to copy the conditional formatting from another column to make the ones pop more than the zeros.

![](bbox=[0.135, 0.46, 0.43, 0.72])

Figure 6.3: Training data with dummy variables populated

# Let's Bake Our Own Linear Regression

Every time I say this, a statistician loses its wings, but I’m going to say it anyway—if you’re ever shoved a trend line through a cloud of points on a scatter plot, then you’ve built an AI model. Maybe not a good one, but you still did it.