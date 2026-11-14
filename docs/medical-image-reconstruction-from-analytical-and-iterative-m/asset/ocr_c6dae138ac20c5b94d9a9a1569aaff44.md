which is well known in the world of linear systems and signal processing. This FIR filter is essentially a convolution operator. Therefore, the LDLINE network works well if the input/output relationship is a convolution for a proper filter length n. For other input/output relationships, this network may not work well because this convolution model is not general enough.

![](bbox=[0.172, 0.208, 0.705, 0.315])

Fig. 9.3: A simple ADALINE neural network.

# 9.2.2 Universal approximation

A mathematical foundation is required to justify the use of neural networks. Over the years, many universal approximation theorems were proposed to support the use of neural networks. Here we use a 1D toy example to illustrate the meaning of a universal approximation theorem. Let us consider a continuous function f(x) defined, without loss of generality, on [0, 1]. For prespecified accuracy, we can determine an integer n and divide the [0, 1] into n subintervals such that f(x) can be approximated by a piecewise constant function \(\bar{f}(x)\). The function \(\bar{f}(x)\) is a constant in \(\left( \frac{k}{n}, \frac{k+1}{n} \right)\), with k = 0, 1, 2, ..., n-1 as shown in Figure 9.4. When n is large enough, the approximation is accurate enough. This approximation function \(\bar{f}(x)\) is uniquely determined by n parameters, which are the n values of f(x) at n evenly distributed points:

\(\frac{0.5}{n}, \frac{1.5}{n}, \frac{2.5}{n}, \cdots, \frac{n-0.5}{n}\) (9.3)

in (0, 1).

A piecewise constant function \(\bar{f}(x)\) such as the one shown in Figure 9.4 can be expressed by a summation of weighted unit step functions:

\(\bar{f}(x) = \sum_{k=0}^{n-1} w_k u \left( x - \frac{k}{n} \right),\) (9.4)

where the unit step function is defined as