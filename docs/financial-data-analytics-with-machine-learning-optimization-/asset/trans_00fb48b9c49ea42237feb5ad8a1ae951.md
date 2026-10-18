

[(14.13)](#c14.xhtml#R_c14-disp-0039)

```math
\begin{aligned}
&\hat{f}_x(x) = \frac{1}{n h_n} \sum_{i=1}^{n} K\left(\frac{x - x_i}{h_n}\right) \\
&= \frac{1}{h_n} K\left(\frac{x - x}{h_n}\right) \\
&= \int_{\mathbb{R}} \frac{1}{h_n} K\left(\frac{x - u}{h_n}\right) f_x(u) \, du \\
&= \int_{\mathbb{R}} K(z) f_x(x + h_n z) \, dz \\
&= \int_{\mathbb{R}} K(z) f_x(x) \, dz + o(1) \\
&= f_x(x) + o(1)
\end{aligned}
```

where to obtain the second last equality, the integral

```math
\int_{\mathbb{R}} K(z) f_x(x + h_n z) \, dz
```

has an integrand such that

```math
f_x(x + h_n z) = f_x(x) + o(1)
```

locally uniformly as

```math
h_n \to 0
```

if we assume (i) `f_x` is globally Lipschitz, and (ii)

```math
\int_{\mathbb{R}} |z| K(z) \, dz
```

is finite, the integral is certainly equal to

```math
\int K(z) f_x(x) \, dz + o(1)
```

