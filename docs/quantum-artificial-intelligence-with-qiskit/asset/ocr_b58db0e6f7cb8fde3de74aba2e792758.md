# 4.4.2 RY Gate - RY

qc.ry(theta,qubit)

The RY gate performs a rotation of one qubit along the $y$-axis by the rotation angle $	heta$. The rotation angle is in radians.

With $	heta = \pi$

```
$RY|0\rangle \rightarrow |1\rangle \quad RY|1\rangle \rightarrow -|0\rangle$
```

With $	heta = \pi/2$

```
$RY|0\rangle \rightarrow \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle \quad RY|1\rangle \rightarrow \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle$
```

The RY gate defines a quantum gate on one qubit and can be represented by a unitary matrix $RX$ in Hilbert space $\mathcal{H}_2$

```
$R_Y(\theta) = \begin{pmatrix} \cos(\\frac{	heta}{2}) & -sin(\\frac{	heta}{2}) \ \sin(\\frac{	heta}{2}) & \cos(\\frac{	heta}{2}) \end{pmatrix}$
```

# 4.4.3 RZ Gate - RZ

qc.rz(phi,qubit)

The RZ gate performs a rotation of one qubit along the $z$-axis by the rotation angle $\phi$. The rotation angle is in radians.

With $\phi = \pi$

```
$RZ|0\rangle \rightarrow -i|0\rangle \quad RZ|1\rangle \rightarrow i|1\rangle$
```

With $\phi = \pi/2$

```
$RZ|0\rangle \rightarrow \frac{1}{\sqrt{2}} - \frac{i}{\sqrt{2}}|0\rangle \quad RZ|1\rangle \rightarrow \frac{1}{\sqrt{2}} + \frac{i}{\sqrt{2}}|1\rangle$
```

The RZ gate defines a quantum gate on one qubit and can be represented by a unitary matrix $R_Z(\phi)$ in Hilbert space $\mathcal{H}_2$

```
$R_Z(\phi) = \begin{pmatrix} e^{-i\frac{\phi}{2}} & 0 \ 0 & e^{i\frac{\phi}{2}} \end{pmatrix}$
```

# 4.4.4 U Gate - U

U gate is a single-qubit rotation gate with 3 Euler angles.

qc.u(theata, phi, lambda, qubit)