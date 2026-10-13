
#### Power spectral density

**Definition 2.4**

Given a WSS stochastic process `u[n]`, its *power spectral density* (PSD) (or simply the *power spectrum*) is defined as the Fourier transform of its autocorrelation sequence,

```
r_u(0) r_v(0) ≥ |r_uv(k)|², ∀ k ∈ ℤ.
```

Using the Fourier transform properties, we can recover the autocorrelation sequence via the *inverse Fourier transform* in the following manner:

```
S_u(ω) = Σ_{k=-∞}^{∞} r_u(k) e^{-jωk}
```

```
r_u(k) = (1/2π) ∫_{-π}^{π} S_u(ω) e^{jωk} dω
```

Due to the properties of the autocorrelation sequence, the PSD has some interesting and useful properties, from a practical point of view.

**Properties of the PSD**

*   The PSD of a WSS stochastic process is a *real* and *nonnegative* function of `ω`. Indeed, we have
