# 302 APPENDIX | A Greeks for Vanilla European Options

We have

```
$$\frac{\partial d_2}{\partial S} = \frac{\partial d_1}{\partial S}-\frac{1}{S\sqrt{T-t}}, \quad (A.1.6)$
```

```
$$\frac{\partial d_2}{\partial \sigma} = \frac{\partial d_1}{\partial \sigma}-\sqrt{T-t}, \quad (A.1.7)$
```

```
$$\frac{\partial d_1}{\partial r} = \frac{\partial d_2}{\partial r}-\frac{\sqrt{T-t}}{\sigma}, \quad (A.1.8)$
```

```
$$\frac{\partial d_2}{\partial t} = \frac{\partial d_1}{\partial t}-\frac{\sigma}{2(T-t)}, \quad (A.1.9)$
```

Also

```
$n(d_2) = \frac{1}{\sqrt{2\pi}}exp(-d_2^2/2)\n= \frac{1}{\sqrt{2\pi}}exp(-d_1^2/2)\exp\{d_1\sqrt{T-t}-\sigma^2(T-t)/2\}\n= n(d_1)\exp\{log(S/E)+(r-q+\sigma^2/2)(T-t)-\sigma^2(T-t)/2\}$
```

so

```
$n(d_2) = \frac{S}{E}n(d_1)\exp(r(T-t))exp(-q(T-t)).\quad (A.1.110)$
```

We note that

```
$$\frac{\partial N(d_1)}{\partial S} = \frac{\partial N(d_1)}{\partial d_1}\frac{\partial d_1}{\partial S} = n(d_1)\frac{1}{S\sqrt{T-t}}$
```

This technique will be used for computing the Greeks.

# A.2 GAMMA

Gamma is defined as the second derivative of the option value with respect to the underlying stock price. This means (see Appendix A.3) it is the rate of change of delta with the underlying stock price.\nFor a European call, the value of gamma is

```
$$\Gamma_c = \frac{\partial^2\Delta_c}{\partial S^2}=\frac{\partial\Delta_c}{\partial S}\frac{\partial}{\partial S}\{N_1(d_1)\exp(-q(T-t))},\$
```

the value of $\Delta_c$ is given in Appendix A.3. So

```
$$\Gamma_c = exp(-q(T-t))\frac{\n(d_1)}{\partial S}\frac{\partial d_1}{\partial S}.\quad (A.2.1)$
```

Therefore,

The value of gamma for a European call can be calculated similarly

```
$$\Gamma_p = \frac{\partial^2p}{\partial S^2}=\frac{\partial\Delta_p}{\partial S}\frac{\partial}{\partial S}\{(N_1(d_1)-1)exp(-q(T-t))},\$
```