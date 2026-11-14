```
\(\phi(y) = T\omega(y) = yB_0T + y\gamma G_y T.\)
```

Recall that the function f(x, y) is complex with a magnitude and a phase and can be expressed as

```
\(f(x, y) = |f(x, y)|e^{i\varphi(x,y)}.\)
```

After a phase change of \(\phi(y)\), f(x, y) becomes

```
\(|f(x, y)|e^{i\varphi(x,y)}e^{-i\phi(y)} = f(x, y)e^{-i(yB_0T + pyG_yT)}.\)
```

We can ignore the first term \(yB_0T\) in the exponent because it introduces the same phase change to all y-positions and carries no information of the image.

The function f(x, y) is now encoded by the phase-changing factor as

```
\(f(x, y)e^{-i2\pi pyG_yT},\)
```

which is the signal that we try to read out. Therefore, the readout signal is

```
\(\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} [f(x, y)e^{-i2\pi pyG_yT}] \cos(2\pi x X G_x t) \, dx dy.\)
```

The MRI machines use quadrature data acquisition, which has two outputs at 90° out of phase. One output gives

```
\(\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} [f(x, y)e^{-i2\pi pyG_yT}] \cos(2\pi x X G_x t) \, dx dy,\)
```

and the other gives

```
\(\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} [f(x, y)e^{-i\pi ryG_yT}] \sin(2\pi x X G_x t) \, dx dy.\)
```

We can combine them into a complex signal, with one output as the real part and the other output as the imaginary part,

```
\(\text{signal (}t) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y)e^{-i2\pi pyG_yT} e^{-i2\pi pyG_x t} \, dx dy.\)
```

If we rewrite it as

```
\(\text{signal}_{G_y} (t) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y)e^{-i2\pi [x(yG_x t) + y(yG_y T)]} \, dx dy,\)
```

we immediately recognize it as the 2D Fourier transform of f(x,y):