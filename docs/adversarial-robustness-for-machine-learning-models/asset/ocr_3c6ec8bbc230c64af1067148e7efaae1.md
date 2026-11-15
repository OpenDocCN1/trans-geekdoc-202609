# **Algorithm 7** MINE–based MinMax attack algorithm.

```
1: **Require**: data sample x, attack criterion f_x, step sizes α and β, perturbation bound ε, # of iterations T
2: Initialize δ_0 = 0, c_0 = 0, δ* = null, I_Θ* = -∞, t = 1
3: for t in T iterations do
4: δ_{t+1} = δ_t - α \cdot (c \cdot 
abla f_x^+(x + δ_t) - 
abla I_Θ(x, x + δ_t))
5: Project δ_{t+1} to [-ε, ε] via clipping
6: Project x + δ_{t+1} to [0, 1] via clipping
7: Compute I_Θ(x, x + δ_{t+1})
8: Perform c_{t+1} = (1 - \frac{β}{t^{7/4}}) \cdot c_t + β \cdot f_x^+(x + δ_{t+1})
9: Project c_{t+1} to [0, ∞]
10: if f_x(x + δ_{t+1}) \le 0 and I_Θ(x, x + δ_{t+1}) > I_Θ* then
11: update δ* = δ_{t+1} and I_Θ* = I_Θ(x, x + δ_{t+1})
12: end if
13: end for
14: Return δ*, I_Θ*
```

ples (MINE-UAEs). In what follows, we show novel applications of MINE-UAEs as a simple plug-in data augmentation tool to boost the model performance of several unsupervised machine learning tasks. We provide a brief summary of the datasets:

+   • MNIST consists of grayscale images of hand-written digits. The numbers of training/test samples are 60K/10K.
+   • SVHN is a color image dataset set of house numbers extracted from Google Street View images. The number of training/test samples are 73257/26302.
+   • Fashion MNIST contains grayscale images of 10 clothing items. The numbers of training/test samples are 60K/10K.
+   • Isolet consists of preprocessed speech data of people speaking the name of each letter of the English alphabet. The numbers of training/test samples are 6238/1559.
+   • Coil-20 contains grayscale images of 20 multiviewed objects. The numbers of training/test samples are 1152/288.
+   • Mice protein consists of the expression levels (features) of 77 protein modifications in the nuclear fraction of cortex. The numbers of training/test samples are 864/216.