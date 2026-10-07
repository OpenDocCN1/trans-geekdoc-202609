# Inverter-based memristive neuromorphic circuit 279

Also, we define $net_j^i = \sum_k g(	heta_{jk}^i)O_{kp}^{-1} + g(	heta_{jk}^i)O_{kn}^{-1} + eta_j^i b_p' + eta_j^i b_n'$ as the weighted sum of the inputs of the $j$th neuron in $i$th layer. Therefore, the weight gradient by considering the proposed weight mapping functions is defined as

```
$$\frac{\partial J}{\partial \theta_{jk}^i} = \frac{\partial J}{\partial f_j^i} \frac{\partial f_j^i}{\partial net_j^i} \frac{\partial net_j^i}{\partial \theta_{jk}^i} = (11.26)$
```

where

```
$$\frac{\partial net_j^i}{\partial \theta_{jk}^i} = \frac{\partial(\theta_{jk}^i)O_{kp}^{-1}}{\partial \theta_{jk}^i} \cdot \frac{\partial(g_2)O_{kn}^{-1}}{\partial \theta_{jk}^i} = (11.27)$
```

```
$$\frac{\partial g_1(\theta_{jk}^i)}{\partial \theta_{jk}^i} = \frac{1}{K}g_1(\theta_{jk}^i)[K - g_1(\theta_{jk}^i)] = (11.28)$
```

```
$$\frac{\partial(g_2)O_{kn}^{-1}}{\partial g_1} = (O_{kn}^{-1})$
```

```
$$\sum_{m=1}^N (g_1(\theta_{km}^m) + g_1(\theta_{km}^n)) = - \frac{1}{2} \sum_{m=1}^N O_m^{-1} \times g_1(\theta_{km}^p) = (11.29)$
```

After the training phase, the weights should be written to the memristive crossbar. In this chapter, the scheme of [43] is assumed to be implemented in the programming interface for writing the memristors. It solves the problems of device variation and stochastic write and has the relative accuracy of 1%. Also, the memistor model proposed in [24] for the device of [39] which has a good endurance and retention is utilized. In this model, the $I - V$ characteristic (and hence the conductance) of the memristor is determined by its state variable. Therefore, the extracted conductance values should be mapped to the corresponding state of the memristor for the use in the SPICE simulations. The $I - V$ characteristic of the memristor model is formulated as [24]:

```
$I(t) = \begin{cases} a_1.x(t) \sinh(b.V(t)), & V(t) \ge 0 \ a_2.x(t) \sinh(b.V(t)), & V(t) < 0 \end{cases} = (11.30)$
```

where $b$, $a_1$, and $a_2$ are the fitting parameters and $x(t)$ is the state variable. For this element, the $I - V$ relation is not linear making the mapping of the conductance $\sigma$ to the state variable not exact $\sigma(t) = I(t)/V(t)$. To simplify the extraction of $x$ from $\sigma$, we suggest employing the first two terms of the Taylor series of (11.30). Based on this approximation which has a maximum error of only $0.1\%$, $I(t)$ may be expressed as

```
$I(t) = \begin{cases} a_1x(t)(b(t) + \frac{b^3V(t)^3}{6}), & V(t) \ge 0 \ a_2x(t)(b(t) + \frac{b^3V(t)^3}{6}), & V(t) < 0 \end{cases} = (11.31)$
```