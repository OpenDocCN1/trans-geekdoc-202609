
where `t`^(*l*), `t`^(*r*), `a`^(*l*) and `a`^(*r*) are the four learnable real number parameters (initialized as `a`^(*l*) = 0, `t`^(*l*) = 0, and `t`^(*r*) = `maxInput`, where `maxInput` is a hyperparameter). SReLU’s rather large number of parameters results in high representation power.

The gradients of SReLU are given by  

$\frac{dy_{i}}{dx_{i}} = f\prime\left( x_{i} \right) = \left\{ \begin{matrix} {a^{l}, x_{i} < t^{l}} \\ {1, t^{l} \leq x_{i} \leq t^{r}} \\ {a^{r}, x_{i} > t^{r}} \end{matrix} \right.$,   

$$\frac{dy_{i}}{da^{l}} = \left\{ \begin{matrix} {x_{i} - t^{l}, x_{i} < t^{l}} \\ {0, x_{i} \geq t^{l}} \end{matrix} \right.,\text{and}$$  

$\frac{dy_{i}}{dt^{l}} = \left\{ \begin{matrix} {1 - a^{l}, x_{i} < t^{l}} \\ {0, x_{i} \geq t^{l}} \end{matrix} \right..$  

## 5.2.7 APLU

Adaptive Piecewise Linear Unit (APLU) \[21\] is defined as  

$$y_{i} = \operatorname{}ReLU\left( x_{i} \right) + \sum_{c = 1}^{n}a_{c}\max\left( {0, - x_{i} + b_{c}} \right)$$  

where `a`[c] and `b`[c] are real numbers, each different for each channel of the input. `APLU` is a linear piecewise function able to approximate, as noted in the Introduction, any continuous function on a compact set.

The gradient of APLU is given by the sum of the gradients of ReLU and of the functions contained in the sum. With respect to the parameters, `a`[c] and `b`[c], the gradients are  

$$\frac{df\left( {x,a} \right)}{da_{c}} = \left\{ \begin{matrix} {- x + b_{c}, x < b_{c}} \\ {0, x \geq b_{c}} \end{matrix}\text{and}\frac{df\left( {x,a} \right)}{db_{c}} = \left\{ \begin{matrix} {- a_{c}, x < b_{c}} \\ {0, x \geq b_{c}} \end{matrix} \right.}$$  

In this study, the parameters `a`[c] were initialized to 0, while the points were randomly initialized. Added was a 0.001 `L`² -penalty on the norm of the parameters `a`[c]. Thus, another term was included in the loss function, which is defined as  

$$L^{reg} = \sum_{c = 1}^{n}\left| a_{c} \right|^{2}L^{reg} = \sum_{c = 1}^{n}\left| a_{c} \right|^{2}$$  

A relative learning rate was also added to these parameters: `maxInput` times the smallest used for the rest of the network. Thus, if `λ` is the global learning rate, the learning rate `λ`^(\*) of the parameters `a`[c] would be  

$\lambda^{\text{\*}} = \frac{\\lambda}{maxInput}\\lambda^{\\text{\*}} = \\frac{\\lambda}{maxInput}.$  

## 5.2.8 MeLU

To understand the Mexican ReLU (MeLU) \[25\], let `ϕ`^(*a*, *λ*)(*x*)= max (*λ*−|*x*−*a*|,0) be a “Mexican hat type” function, where `a` and `λ` are real numbers. When |*x*−*a*| > *λ*, the function `ϕ`^(*a*, *λ*)(*x*) is null but constantly increases with a derivative of 1 and between *a* and *a*−*λ* and decreases with a derivative of −1 between *a* and *a* + *λ*.

The aforementioned functions serve as the building blocks of MeLU, which is defined as  

$$y_{i} = \\text{MeLU}\\left( x_{i} \\right) = \\text{PReLU}^{c\_{0}}\\left( x_{i} \\right) + \\sum_{j = 1}^{k - 1}c_{j}\\phi^{a\_{j},\\lambda\_{j}}\\left( x_{i} \\right),$$  

where `k` is the number of learnable parameters for each channel (one parameter for PReLU and `k`−1 parameters for the coefficients in the sum of the Mexican hat functions; `k` = 4, 8 here), `c`[j] are the learnable parameters, `c`[0] is the vector of parameters in PReLU, and `a`[j] and `λ`[j] are both fixed and chosen recursively.

Initially, the parameter `maxInput` is set. The first Mexican hat function has its maximum in 2 ⋅ `maxInput` and is equal to zero in 0 and 4 ⋅ `maxInput`. The next two functions are chosen to be zero outside the interval \[0, 2 ⋅ `maxInput`\] and \[2 ⋅ `maxInput`, 4 ⋅ `maxInput`\], with the requirement being that they have their maximum in `maxInput` and 3 ⋅ `maxInput` (Table 5.1).

TABLE 5.1 Fixed Parameters of MeLU with `maxInput` = 256  

| `j` || **1** || **2** || **3** || **4** || **5** || **6** || **7** |

| --- | --- | --- | --- | --- | --- | --- | --- |

| `a`[j] || 512 || 256 || 768 || 128 || 384 || 640 || 896 |

| --- | --- | --- | --- | --- | --- | --- | --- |

| `λ`[j] || 512 || 256 || 256 || 128 || 128 || 128 || 128 |

Since Mexican hat functions are continuous and piecewise differentiable, so is MeLU. If all the `c[i]` learnable parameters are initialized to zero, MeLU coincides with ReLU, a property that is helpful in transfer learning when the network is pretrained with ReLU (in which case MeLU can simply be substituted; of course, MeLU can also be substituted for networks trained with Leaky ReLU and PReLU). Another important property derives from the fact that the Mexican hat functions are a Hilbert basis on a compact set with the `L²` norm; thus, they can approximate every function in `L²([0, 1, 024])` as `k` goes to infinity.

MeLU is similar to SReLU and APLU in having multiple learnable parameters, but this number is larger in APLU. MeLU is also similar to APLU in that it can approximate the same set of piecewise linear functions equal to identity when `x` is large enough, but how this is done is different for each function. Given the right choice of the parameters, APLU can be equal to any piecewise linear function because the points of nondifferentiability are learnable, but MeLU is more efficient because it can represent every piecewise linear function by exploiting only the joint optimization of the weight matrix and the biases. Moreover, the gradients of the two activations with respect to the learnable parameters are different. The optimization of a neural network depends in large part on two factors: the output of every hidden layer and the gradient of that output with respect to the parameters.

Unlike APLU, MeLU changes the activation where it is needed, making optimization easier. The difference between the basis functions of MeLU and APLU is illustrated in Figure 5.2. Moreover, as noted in Section 5.2.7, the coefficients in APLU must be regularized with an `L²` penalty and benefits from a low learning rate; MeLU does not need any regularization.

![FIGURE 5.2 Partial derivatives of MeLU and APLU.](img/fig5_2.jpg)

FIGURE 5.2 Partial derivatives of MeLU and APLU.

In this study, the learnable parameters in MeLU are initialized to zero, so the activation starts off as ReLU, thereby exploiting all the nice properties of ReLU at the beginning.

### 5.2.9 GaLU

Gaussian ReLU (GaLU), proposed here, is based on MeLU and possesses the same desirable properties. To define GaLU, let `ϕg(x) = max(λ - |x - a|, 0) + min(|x - a - 2λ| - λ, 0)` be a Gaussian type function, where `a` and `λ` are real numbers. In Figure 5.3, a standard Gaussian wavelet function is compared with a Gaussian type with `a = 1`, `λ = 1`.

![FIGURE 5.3 Gaussian wavelet (a) and our Gaussian type (b).](img/fig5_3.jpg)

FIGURE 5.3 Gaussian wavelet (a) and our Gaussian type (b).

GaLU is defined, similarly to MeLU, as

$y_{i} = \text{GaLU}(x_{i}) = \text{PReLU}^{c_{0}}(x_{i}) + \sum_{j = 1}^{k - 1}c_{j}\phi_{g}^{a_{j},\\lambda_{j}}(x_{i}).$

As shown in Ref. \[31\], piecewise linear odd functions constructed of many linear pieces approximate nonlinear functions better than ReLU does. The rationale behind GaLU is to add more linear pieces than is the case with MeLU.

Like MeLU, GaLU has a set of fixed parameters (see Table 5.2 where the fixed parameters of GaLU and MeLU with `maxInput = 1` are compared).

TABLE 5.2 Comparison of the Fixed parameters of GaLU and MeLU with `maxInput = 1`

|  || `j` || **1** || **2** || **3** || **4** || **5** || **6** || **7** |

| --- | --- | --- | --- | --- | --- | --- | --- |

| MeLU || `a[j]λ[j]` || 22 || 11 || 31 || 0.50.5 || 1.50.5 || 2.50.5 || 3.50.5 |

| --- | --- | --- | --- | --- | --- | --- | --- |

| GaLU || `a[j]λ[j]` || 11 || 0.50.5 || 2.50.5 || 0.250.25 || 1.250.25 || 2.250.25 || 3.250.25 |

## 5.3 Experimental Results
