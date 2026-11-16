![](bbox=[0.17, 0.11, 0.83, 0.42])

Figure 1.2. (a) Channel-III ECG signal of normal, (b) Channel-V3 ECG signal of normal, (c) Channel-V5 ECG signal of normal, (d) Channel-III ECG signal of HPT, (e) Channel-V3 ECG signal of HPT (f) Channel-V5 ECG signal of HPT.

The frequency response of LPF \(K(\omega')\) is given as

```
\(K(\omega') = \left\{ \begin{array}{ll} (s_1 s_2)^2, & |\omega'| < \omega_{ph} \\ (s_1 s_2) 2 \frac{1}{\theta} . \frac{\omega' - \omega_{ph}}{\omega_s - \omega_{ph}}, & \omega_{ph} \leqslant \omega' \\ (s_1 s_2) \frac{1}{2} \theta . \frac{\pi - \omega' + \omega_{ph}}{\omega_s - \omega_{ph}}, & -\omega_s \leqslant \omega' \leqslant -\omega_{ph} \\ 0, & |\omega'| \geqslant \omega_s \end{array} \right.\) (1.1)
```

The frequency response of HPF \(H(\omega')\) is given as,

```
\(H(\omega') = \left\{ \begin{array}{ll} (2 s_3 s_4)^{1/4} \theta . \frac{\pi - \omega' - \omega_0}{\omega_s - \omega_{ph}}, & \omega_0 \leqslant \omega' < \omega_1 \\ (2 s_3 s_4)^{\frac{1}{2}}, & \omega_1 \leqslant \omega' < \omega_2 \\ (2 s_3 s_4)^{\frac{1}{2}} \frac{1}{\theta} . \frac{\omega' - \omega_2}{\omega_3 - \omega_2}, & \omega_2 \leqslant \omega' \leqslant \omega_3 \\ 0, \omega' \epsilon [0, \omega_0) \bigcup (\omega_3, 2 \pi) & \end{array} \right.\) (1.2)
```

where, phase frequency \((\omega_{ph})\) is given as,

```
\(\omega_{ph} = \frac{(1 - \beta) \pi}{s_1} + \frac{\epsilon}{s_1}\) (1.3)
```