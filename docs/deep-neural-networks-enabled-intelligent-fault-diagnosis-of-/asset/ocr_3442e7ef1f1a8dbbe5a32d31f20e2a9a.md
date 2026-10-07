method, synchroqueezing transform (SST), etc., and has low time complexity. Thus, SET is a powerful tool for characterizing inherent features of time-varying nonlinear signal in the time domain and frequency domain simultaneously. This work utilizes SET to transform one-dimensional (1D) fault vibration signals into 2D TF maps suitable for deep convolutional neural network (DCNN) and improve diagnostic accuracy, especially for harsh working conditions. SET comprises the following steps:

For a signal $x(u)$, its regular STFT is defined as

```
$G_x(\tau,w) = \int_{-\infty}^{+\infty} x(u) \cdot g(u-\tau) \cdot e^{-iw\tau} du \eqno(10.2)$
```

$g(u-\tau)$ indicates a window function (WF) with the center at $	au$, $w$ is the frequency, $u$ and $	au$ denote the time parameter.

In considering a phase shift $e^{iw\tau}$, Eq. (10.2) is rewritten as:

```
$G_x(\tau,w) = \int_{-\infty}^{+\infty} x(u) \cdot g(u-\tau) \cdot e^{-iw(u-\tau)} du \eqno(10.3)$
```

According to the derivative of $G_r(\tau,w)$, the intrinsic IF $v_G(\tau,w)$ at each TF position be obtained in:

```
$v_G(\tau,w) = \frac{\partial}{\partial\tau}arg(G_r(\tau,w)) = i \cdot G_r^{-1}(\tau,w) \cdot G_r'(\tau,w) + w \eqno(10.4)$
```

where $g'$ is the derivative of the WF $g(u-\tau)$ regarding time $	au$.

A new TF plane reconstructed by TF coefficients of $G_r(\tau,w)$ at IF positions, is expressed as:

```
$SET_r(\tau,w) = G_r(\tau,w) \cdot \delta(w-v_G(\tau,w)) \eqno(10.5)$
```

where $SET_r(\tau,w)$ are the TF results of SET, $\delta(.)$ is the Dirac function, and $\delta(w-v_G(\tau,w))$ denotes the synchro-extracting operator (SEO). Considering that SEO's real part is utilized in practice, $SEO(\tau,w)$ is rewritten as:

```
$SEO(\tau,w) = \begin{cases} 1, & Re[G_r^{-1}(\tau,w) \cdot G_r'(\tau,w)] < \Delta w/2 \ 0, & \text{otherwise} \end{cases} \eqno(10.6)$
```

where $\Delta w$ is the frequency interval and it can adjust the SET's frequency resolution, $Re()$ indicates taking the real part.

In this chapter, $\Delta w$ is set to 1, and the $g(u-\tau)$ is a Gaussian WF with a window length of 128. After the above set, the 1D time-domain signal is converted to 2D TFR, which will be used as the input of the subsequent model.