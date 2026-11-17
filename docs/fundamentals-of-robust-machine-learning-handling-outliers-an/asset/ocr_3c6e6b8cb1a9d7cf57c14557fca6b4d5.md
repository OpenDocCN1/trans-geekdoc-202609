then it follows that the **reverse MLE procedure** would require that

$$f_X(x) = \frac{1}{\kappa}e^{-\rho(x)},$$ (3.5.1)

where $\kappa$ is a normalization coefficient. Here, $f_X(x)$ is the PDF we seek. We should keep in mind that the distribution associated with a loss function must be centered at 0; in other words, we expect it to be symmetric about 0. Hence, the mean of the distribution is 0, or mathematically $\mathbb{E}[X] = 0$. The reverse MLE procedure can be applied to well-known loss functions, such as $L_1$, $L_2$, and Huber. We illustrate the steps for $L_1$ and $L_2$ in the following examples and leave the derivation of the Huber distribution as an exercise for the reader.

**Example**: To find the distribution associated with the $L_1$ loss function, we begin with the term

$$ho_{L_1}(x) = |x|.$$

Then we apply the reverse MLE rule above to obtain

$$f_X(x) = \frac{1}{\kappa}e^{-|x|}.$$

We can find $\kappa$ as follows:

$$\kappa = \int_{-\infty}^{\infty} e^{-|x|} dx = 2.$$

Hence, the basic form of the distribution for the $L_1$ loss is

$$f_X(x) = \frac{1}{2}e^{-|x|},$$ (3.5.2)

which is called the *Laplace distribution*.

**Example**: To find the distribution associated with the $L_2$ loss function, we begin with the term

$$ho_{L_2}(x) = x^2/2.$$

Then we apply the reverse MLE rule above to obtain

$$f(x) = \frac{1}{\kappa}e^{-x^2/2}.$$

We can find $\kappa$ as follows:

$$\kappa = \int_{-\infty}^{\infty} e^{-x^2/2} dx = \sqrt{2\pi}.$$

Hence, the basic form of the distribution for the $L_2$ loss function is

$$f_X(x) = \frac{1}{\sqrt{2\pi}}e^{-x^2/2},$$ (3.5.3)

which is, of course, the Gaussian distribution.

If we now apply the reverse MLE rule to the log-cosh loss, we start with

$$\rho_{LC}(x) = \log(\cosh(x)).$$