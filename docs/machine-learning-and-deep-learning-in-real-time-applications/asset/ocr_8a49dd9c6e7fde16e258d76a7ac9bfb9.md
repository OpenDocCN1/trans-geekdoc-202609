# Deep Learning Using Keras

Figure 5. Input layer, hidden layer and output layer in digit recognition model

![](bbox=[0.213, 0.1785, 0.7935, 0.5035])

```
$WX + b = \begin{cases} (ja + kd + lg) + s & (jb + ke + lh) + s & (jc + kf + li) + s \ (ma + nd + og) + t & (mb + ne + oh) + t & (mc + nf + oi) + t \ (pa + qd + rg) + u & (pb + qe + rh) + u & (pc + qf + ri) + u \end{cases}$
```

```
$Z^{[l]} = W^{[l]}A^{[l-1]} + b^{[l]}$
```

```
$\sigma(Z) = \sigma(WA + b) = \frac{1}{1 + e^{[WA+b]}}$
```

+   3. Compute the loss,

Error$_n$ = Actual Output – Desired Output

+   4. Implement the backward propagation module: Travel back from the output layer to the hidden layer to adjust the weights such that the error is decreased.