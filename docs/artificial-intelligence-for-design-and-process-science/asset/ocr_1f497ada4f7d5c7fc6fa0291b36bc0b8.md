# $U(n,p,q)$

```
$e^{i[q+n(-p)]t_1} \quad e^{i[q+n(-p)]t_2} \quad e^{i[q+n(-p)]t_{N-1}} \quad e^{i[q+n(-p)]t_N}$$
$$egin{bmatrix} [q+n(-p)]^2 & [q+n(-p)]^2 & [q+n(-p)]^2 & [q+n(-p)]^2 \ \vdots & \vdots & \vdots & \vdots \ e^{i[q+n(-p+1)]t_1} & e^{i[q+n(-p+1)]t_2} & e^{i[q+n(-p+1)]t_{N-1}} & e^{i[q+n(-p+1)]t_N} \end{bmatrix}$$
$$[q+n(-p+1)]^2 [q+n(-p+1)]^2 [q+n(-p+1)]^2 [q+n(-p+1)]^2$$$
$$\vdots & \vdots & \vdots & \vdots \ e^{i[q+n(-1)]t_1} & e^{i[q+n(-1)]t_2} & e^{i[q+n(-1)]t_{N-1}} & e^{i[q+n(-1)]t_N}$$
$$[q+n(-1)]^2 [q+n(-1)]^2 [q+n(-1)]^2 [q+n(-1)]^2$$$
$$\vdots & \vdots & \vdots & \vdots \ e^{i[q+n(0)]t_1} & e^{i[q+n(0)]t_2} & e^{i[q+n(0)]t_{N-1}} & e^{i[q+n(0)]t_N}$$
$$[q+n(0)]^2 [q+n(0)]^2 [q+n(0)]^2 [q+n(0)]^2$$$
$$\vdots & \vdots & \vdots & \vdots \ e^{i[q+n(1)]t_1} & e^{i[q+n(1)]t_2} & e^{i[q+n(1)]t_{N-1}} & e^{i[q+n(1)]t_N}$$
$$[q+n(1)]^2 [q+n(1)]^2 [q+n(1)]^2 [q+n(1)]^2$$$
$$\vdots & \vdots & \vdots & \vdots \ e^{i[q+n(-p-1)]t_1} & e^{i[q+n(-p-1)]t_2} & e^{i[q+n(-p-1)]t_{N-1}} & e^{i[q+n(-p-1)]t_N}$$
$$[q+n(-p-1)]^2 [q+n(-p-1)]^2 [q+n(-p-1)]^2 [q+n(-p-1)]^2$$$
$$\vdots & \vdots & \vdots & \vdots \ e^{i[q+n(p)]t_1} & e^{i[q+n(p)]t_2} & e^{i[q+n(p)]t_{N-1}} & e^{i[q+n(p)]t_N}$$
$$[q+n(p)]^2 [q+n(p)]^2 [q+n(p)]^2 [q+n(p)]^2$$$
$(2b)$
```

This matrix, which we term the U-matrix, is a unique nonstationary state matrix, in which each term in the matrix is nonstationary.

For example, the Fourier series representing the “polygon” in will 1 will specifically be:

```
$u_{5,1}(p,t) = \sum_{l=-p}^p e^{i(1+5l)t} \quad (3)$
```

Using MATLAB and the Fourier series we plotted the directed graph as represented in Fig. 2. Note that Fig. 2 is produced from the error content graph representation, and it is an analytical representation of noise in the communication channel. However, Fig. 2 is a simple directed graph produced from Shannon’s channel representation scheme. The biological significance of the quantum Fourier representation depicted in Fig. 2 is that each directed “edge” is a mathematical computation. That is that electronic, atomic, molecular, and larger assemblies can be expressed as a series of computations in complex domain. This computational representation also connects the communication channel formalism to quantum electrodynamics (QED) [6].