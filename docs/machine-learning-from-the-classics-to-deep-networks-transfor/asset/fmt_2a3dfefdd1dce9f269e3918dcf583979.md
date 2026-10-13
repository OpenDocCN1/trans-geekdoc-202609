
*y*[*n*] = *θ*[0] + *θ*[1]*x*[*n*] + *θ*[2]*x*[*n*]² + *θ*[3]*x*[*n*]³ + *θ*[5]*x*[*n*]⁵ + *η*[*n*], *n* = 1, 2, …, *N*,

where *η*[*n*] are i.i.d. noise samples drawn from a zero mean Gaussian with variance *σ*[*η*]². Samples *x*[*n*] are equidistant points in the interval [0, 2]. The goal of the task is to predict the value *y* given a measured value *x*, using Eq. (12.22). The parameter values used to generate the data were equal to:

*θ*[0] = 0.2, *θ*[1] = −1, *θ*[2] = 0.9, *θ*[3] = 0.7, *θ*[5] = −0.2.

### (a)

In the first set of experiments, a Gaussian prior for the unknown **θ** was used with mean **θ**[0] equal to the previous true set of parameters and *Σ*[*θ*] = 0.1*I*. Also, the true model structure was used to construct the matrix Φ.

Fig. 12.1A shows the points (*y*, *x*) in red together with the error bars, as measured by the computed *σ*[*y*]², for the case of *N* = 20 training points and *σ*[*η*]² = 0.05. Fig. 12.1B demonstrates the obtained improvement when the training points are increased to *N* = 500, while keeping the values of the other two parameters unchanged. Fig. 12.1C corresponds to the latter case, where the noise variance is increased to *σ*[*η*]² = 0.15.

![Figure 12.1 Each one of the red points (y, x) indicates the prediction (y) corresponding to the input value (x). The error bars are dictated by the computed variance, \sigma_{y}^{2}. The mean values used in the Gaussian prior are equal to the true values of the unknown model. (A) \sigma_{\eta}^{2} = 0.05, N = 20, \sigma_{\theta}^{2} = 0.1. (B) \sigma_{\eta}^{2} = 0.05, N = 500, \sigma_{\theta}^{2} = 0.1. (C) \sigma_{\eta}^{2} = 0.15, N = 500, \sigma_{\theta}^{2} = 0.1. Observe that the larger the data set is, the better the predictions are, and the larger the noise variance is, the larger the error bars become.](images/B9780443292385000184/gr001.jpg)
