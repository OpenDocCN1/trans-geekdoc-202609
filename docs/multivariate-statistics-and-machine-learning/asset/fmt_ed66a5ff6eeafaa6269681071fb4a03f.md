
where `x`[*i*] is the data point at a given iteration. Stochastic gradient descent improves on the redundancy weakness of batch gradient descent and is therefore much faster, and since it is only required that the gradient be an unbiased estimator of the true gradient, it is not absolutely required to use the full training data. Because of the frequent updates, it can cause rather high variance as the algorithm attempts to arrive at a minimum. Stochastic gradient descent can overshoot the minimum for too large of a learning rate; hence reducing the learning rate is often advised. The algorithm requires less computing resources as well compared to gradient descent for the reason that it does not use all the data at once, which for large-scale problems could have major benefits over gradient descent. Indeed, stochastic gradient descent has been found to be very effective for large-scale machine learning ([Bottou et al., 2018](#ref.xhtml#re_CIT000042)) and is essentially the “workhorse” of most modern machine learning applications. Finally, stochastic gradient descent when applied to nonconvex functions has no guarantee of convergence and can be very sensitive to initial parameter values (Goodfellow et al., [2016](#ref.xhtml#re_CIT000131)).162

*Mini-batch gradient descent* is often seen as a compromise between batch and stochastic methods such that the algorithm performs an update for each “mini-batch” of `n` training examples,

`θ[1]` = `θ[0]` − `η` ⋅ ∇[`θ`]`E`(`θ`;`x`^((`i`; `i` + `n`)))

(2.229)

where now `i` + `n` is the new “mini-batch” added in the updating of `θ[0]` to `θ[1]`. Mini-batch, however, does not always guarantee good convergence and selecting a good learning rate can be challenging.

*Gradient descent with momentum* is yet another derivative of gradient descent that can help accelerate stochastic gradient descent. This and other modifications and adaptations to gradient descent are summarized in [Ruder (2016)](#ref.xhtml#re_CIT000317).

## 2.62 Integral Calculus

Whereas differentiation is about finding the slope of tangents to curves, integral calculus is about finding *areas* under curves. Historically, finding areas of such things as rectangles has been known since the Greeks, but finding areas under more general shapes and curves would take a long time to figure out. Early attempts at computing such areas included that of Eudoxus of Cnidus (400–350 B.C.E.), who attempted to compute areas under curves by successively small rectangles, as illustrated in [Figure 2.21](#c2.xhtml#f2.21).

![Figure 2.21 The method of exhaustion of Eudoxus of Cnidus (400–350 B.C.E.) where successively small rectangles are used to approximate area under a curve.Return to text.⏎](images/fig2.21.jpg)

*Figure 2.21* The method of exhaustion of Eudoxus of Cnidus (400–350 B.C.E.) where successively small rectangles are used to approximate area under a curve.[Return to text.⏎](#c2.xhtml#re_f2.21)

This approach was known as the *method of exhaustion*. Centuries of thinking about the problem culminated with Newton and Leibniz’ (and many others) contribution of the calculus and the integral, where now we could find areas under curves using a more sophisticated method of summation, called the integral ([Figure 2.22](#c2.xhtml#f2.22)).163

![Figure 2.22 The calculation of area under the curve using integral calculus.Return to text.⏎](images/fig2.22.jpg)

*Figure 2.22* The calculation of area under the curve using integral calculus.[Return to text.⏎](#c2.xhtml#re_f2.22)

But how do we go about finding the areas under such “complex” curves? For small changes in `x`, `Δx`, the reader may recall that we can sum these areas, called *Riemann sums*:

$$\\sum\\limits\_{i = 1}^{n}{f\\left( x\_{i} \\right)\\Delta x}$$

(2.230)

As `n`→∞, the definite integral from `a` to `b` is obtained in the limit:

$${\\int\_{a}^{b}{f\\left( x \\right)dx}} = \\lim\\limits\_{n\\rightarrow\\infty}{\\sum\\limits\_{i = 1}^{n}{f\\left( x\_{i} \\right)\\Delta x}}$$

(2.231)

The integral of everyday calculus is known as the *Riemann integral* due to Bernhard Riemann (1826–1866). The Lebesgue integral followed which was applicable to a wider class of functions than the Riemann integral.

Integration is also generally known as *antidifferentiation* for the reason that integration is the reverse process of differentiation (i.e., integration “undoes” the differentiation). That is, if one is given a derivative and wants to know the original function of that differentiated function, one is seeking the antiderivative, which is arrived at through integration. The *fundamental theorem of calculus* encapsulates this idea that one technique is the reverse of the other. As was true for differentiation, not all functions are integrable. In brief, for a function to be integrable, it must be possible to make smaller and smaller pieces of area or volume, and increase the number of those smaller and smaller pieces. Most importantly, it can be shown that every polynomial is integrable over any set of finite volume (since polynomials are *continuous* functions), and hence for many to most functions dealt with in statistics and machine learning, integrability is not a concern. A deeper discussion into integral calculus would bring us into *measure theory*, which formally accounts for conditions of integrability. Much of modern statistics is based in one way or another on foundations in measure theory.164

### 2.62.1 Double and Triple Integrals

Of course, in the multivariable domain, the aforementioned definitions will not suffice, and we need to extend these concepts to multiple dimensions. The double integral is given by

$$\\int{\\int\\limits\_{}{f\\left( x,y \\right)\\, dx\\, dy}}$$

where, instead of integrating with respect to one variable, we are integrating with respect to two (`x` and `y`). The *bivariate density*, for example, featuring the relationship between two variables requires the double integral, as we will see later in the book.

The next step up from a double integral is a triple integral, useful for integrating now in a three-dimensional space, once more corresponding to the volume of the space but in higher dimensions than the dimensionality previously discussed,

$$\\int{\\int{\\int\\limits\_{}{f\\left( x,y,z \\right)dx\\, dy\\, dz}}}$$

Calculus of several variables, whether with regard to differentiation or integration, makes up the subject of *multivariable calculus*. A good reference for single and multivariable calculus is that of [Salas et al.](#ref.xhtml#re_CIT000320) (1998).

## 2.63 Review Exercises

1. 1. Describe the nature of a *derivative* in differential calculus. Why is the *limit* concept necessary to understanding the derivative?

2. 2. In Python, compute the derivative of the function `f`(`x`) = 2`x`² + 10`x`.

3. 3. Discuss the nature of a *composite function* in calculus.

4. 4. What is a *basis function*? Write out a regression equation featuring the use of a basis function.

5. 5. How is a *partial derivative* different from a single-valued derivative?

6. 6. Conduct an online search and distinguish between a *Taylor series* and a *Taylor polynomial*. What function do these serve?

7. 7. Describe how calculus can be used to learn of the *minima* and *maxima* of functions.

8. 8. What is the role of the *learning rate* in seeking an updated value for parameter `θ[0]` (where `θ[1]` is the updated parameter) in gradient descent?

9. 9. Contrast *integral* vs. *differential* calculus. The *fundamental theorem of calculus* relates the two procedures. Brainstorm how the two might be related.

10. 10. Why is the *limit* concept central to integral calculus? Could we still compute areas under curves without the concept of a limit? How so? Explain.

165

# 3 R and Python Software

DOI: [10.4324/9781003376941-5](https://doi.org/10.4324/9781003376941-5)
