And letting $f_1 = (|0\rangle |++\rangle + |1\rangle |--\rangle)^{\otimes 2}$ and $f_2 = (|0\rangle |++\rangle - |1\rangle |--\rangle)^{\otimes 2}$, we have the above equal to:

```
$(H \otimes I^{\otimes 7}) CNOT_{ms} (\alpha |0\rangle + \beta |1\rangle)_m \otimes \left( \frac{1}{2\sqrt{2}} |0\rangle_s \otimes f_1 + \frac{1}{2\sqrt{2}} |1\rangle_s \otimes f_2 \right)
= (H \otimes I^{\otimes 7}) CNOT_{ms} \left[ \frac{\alpha}{2\sqrt{2}} |00\rangle_{ms} \otimes f_1 + \frac{\alpha}{2\sqrt{2}} |01\rangle_{ms} \otimes f_2 + \frac{\beta}{2\sqrt{2}} |10\rangle_{ms} \otimes f_1 + \frac{\beta}{2\sqrt{2}} |11\rangle_{ms} \otimes f_2 \right]
= (H \otimes I^{\otimes 7}) \left[ \frac{\alpha}{2\sqrt{2}} |00\rangle_{ms} \otimes f_1 + \frac{\alpha}{2\sqrt{2}} |01\rangle_{ms} \otimes f_2 + \frac{\beta}{2\sqrt{2}} |11\rangle_{ms} \otimes f_1 + \frac{\beta}{2\sqrt{2}} |10\rangle_{ms} \otimes f_2 \right]
= \frac{\alpha}{4} (|00\rangle + |10\rangle)_{ms} \otimes f_1 + \frac{\alpha}{4} (|01\rangle + |11\rangle)_{ms} \otimes f_2 + \frac{\beta}{4} (|01\rangle - |11\rangle)_{ms} \otimes f_1 + \frac{\beta}{4} (|00\rangle - |10\rangle)_{ms} \otimes f_2
= |00\rangle_{ms} \otimes \left( \frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2 \right) + |01\rangle_{ms} \otimes \left( \frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2 \right) + |10\rangle_{ms} \otimes \left( \frac{\alpha}{4} f_1 - \frac{\beta}{4} f_2 \right) + |11\rangle_{ms} \otimes \left( -\frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2 \right)
```

where we get $\frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2, \frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2, \frac{\alpha}{4} f_1 - \frac{\beta}{4} f_2$ or $-\frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2$ (with equal probability, i.e. 1/4) depending on the outcome of the measurement, i.e. when we measure the qubits m and s with respect to the computational basis. Suppose the measurement yielded $|00\rangle_{ms}$, then we transmit the 6-qubit cluster state:

```
$|r'\rangle = \frac{\frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2}{\sqrt{1/4}} = \frac{\alpha}{2} f_1 + \frac{\beta}{2} f_2$, which is
```

```
$\frac{\alpha}{2} (|0\rangle |++\rangle + |1\rangle |--\rangle) \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle)
+ \frac{\beta}{2} (|0\rangle |++\rangle - |1\rangle |--\rangle) \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle)$
```

containing the quantum information to be transmitted (i.e. the amplitudes $\alpha$ and $\beta$). How is this more robust to transmission losses? From the example in Borregaard et al. [2020], suppose some of the qubits are lost during the