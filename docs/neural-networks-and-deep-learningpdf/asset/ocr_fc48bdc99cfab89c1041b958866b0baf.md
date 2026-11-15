![](bbox=[0.135, 0.095, 0.545, 0.295])

Implicitly, we're studying some real-world phenomenon here, with x and y representing real-world data. Our goal is to build a model which lets us predict y as a function of x. We could try using neural networks to build such a model, but I'm going to do something even simpler: I'll try to model y as a polynomial in x. I'm doing this instead of using neural nets because using polynomials will make things particularly transparent. Once we've understood the polynomial case, we'll translate to neural networks. Now, there are ten points in the graph above, which means we can find a unique 9th-order polynomial y = a0x^9 + a1x^8 + ... + a9 which fits the data exactly. Here's the graph of that polynomial*:

> * I won't show the coefficients explicitly, although they are easy to find using a routine such as Numpy's polyfit. You can view the exact form of the polynomial in the source code for the graph if you're curious. It's the function p (x) defined starting on line 14 of the program which produces the graph.

![](bbox=[0.135, 0.565, 0.545, 0.78])

That provides an exact fit. But we can also get a good fit using the linear model y = 2x: