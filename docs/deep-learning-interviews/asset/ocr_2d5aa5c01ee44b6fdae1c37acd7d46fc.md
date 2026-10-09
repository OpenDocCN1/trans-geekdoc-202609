terms of finding the MLE \hat{\gamma}, since ln is a monotonically increasing function. Often, we maximize \ln(f(\gamma)) instead of the f(\gamma). A common example is when L(\gamma) is comprised of normally distribution random variables . Formally, if X _{1}, \cdots, X_{n} are i.i.d. each with probability mass function (PMF) of f _{X_{i}}(x_{i} | \gamma), then

\begin{align}
 & f(\gamma)=\prod_{i=1}^{n} f _{X_{i}}\left(x_{i} | \gamma\right), \\ & \ln(f(\gamma))=\sum_{i=1}^{n} \ln f _{X_{i}}\left(x_{i} | \gamma\right).
\end{align}

(3.54) \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (3.55)

SOL-53 CH.SOL- 3.24.

The general procedure for finding the MLE, given that the likelihood function is differentiable, is as follows:

+   1 Start by differentiating the log-likelihood function \ln\left(L(\gamma)\right) with respect to a parameter of interest \gamma .
2 Equate the result to zero .
3 Solve the equation to find \hat{\gamma} that holds:.
4 Compute the second derivative to verify that you indeed have a maximum . rather than a minimum .

\begin{align}
 & \frac{\partial \ln L\left(\hat{\gamma} | x_{1}, \cdots x_{n}\right)}{\partial \gamma}=0
\end{align}

(3.56)

SOL-54 CH.SOL- 3.25.

The first derivative of the log-likelihood function is commonly known as the Fisher score function , and is defined as: