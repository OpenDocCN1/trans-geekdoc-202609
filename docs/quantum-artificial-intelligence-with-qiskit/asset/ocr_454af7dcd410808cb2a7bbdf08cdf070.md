# Amplitude Encoding ■223

![](bbox=[0.193, 0.115, 0.806, 0.313])

Figure 16.1 We build a top-down binary tree that divides the probability of observing $|q_2angle$ on the first level, to the probability of observing $|q_2q_1angle$ on the second level, and finally the probability of observing $|q_2q_1q_0angle$ on the third level representing the required superpositionpsiangle = \sqrt{0.03} \cdot |000angle + \sqrt{0.07} \cdot |001angle + \sqrt{0.15} \cdot |010angle + \sqrt{0.05} \cdot |011angle + \sqrt{0.1} \cdot |100angle + \sqrt{0.3} \cdot |110angle + \sqrt{0.1} \cdot |111angle$. The binary tree is represented by multi-control rotation gates, the multi-control rotation gate are defined over the values indicated by the gray ellipsoids.

# 16.2 TOP-DOWN DIVISION STRATEGY

We build a top-down binary tree that divides the probability of observing $|q_2angle$ on the first level, to the probability of observing $|q_2q_1angle$ on the second level, and finally the probability of observing $|q_2q_1q_0angle$ on the third level representing the required-position $|psiangle$ [8]. The binary tree is represented by multi-control rotation gates (see Figure 16.1) and requires $\log_2 n$ qubits to represent a vector of dimension $n$.

# 16.2.1 Level

The probability of observing $q_2 = 0$ is $\sqrt{0.3}$;

```
$$\sqrt{0.03} \cdot |000\rangle + \sqrt{0.07} \cdot |001\rangle + \sqrt{0.15} \cdot |010\rangle + \sqrt{0.05} \cdot |011\rangle$
```

and probability of observing $q_2 = 1$ is $\sqrt{0.7}$.

We use a parameterized RY gate

```
$R_Y(\theta) = \begin{pmatrix} \cos(&\frac{	heta}{2}) & -sin(&\frac{	heta}{2}) \ \sin(&\frac{	heta}{2}) & \cos(&\frac{	heta}{2}) \end{pmatrix}$
```

to performs rotation of one qubit along the y-axis by the rotation angle $\theta$ (in radiants)

```
$$\theta_0 = 1.98231 = 2 \cdot \arccos(\sqrt{0.3}) \quad (16.2)$
```

with (see Figure 16.1)

```
$RY_{\theta_0}|0\rangle = \sqrt{0.3} \cdot |0\rangle + \sqrt{0.7} \cdot |1\rangle \quad (16.3)$
```