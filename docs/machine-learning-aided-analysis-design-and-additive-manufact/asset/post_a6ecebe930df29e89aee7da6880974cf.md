
## 5.2.5 Solving procedure

The Lagrangian energy function under general boundary conditions can be expressed as:

```
$L = U_s + U_{ip} + U_g - T - W_f \quad (5.30)$
```

Substituting Eq. (5.13), (5.14), and (5.16)–(5.18) into Eq. (5.30) and performing variational operations on the unknown coefficients, a linear equation system can be yielded, which can be sorted and matrixed to obtain the vibration characteristics of the system, namely:

```
$(\mathbf{K} - \omega^2\mathbf{M})mathbf{Q} = F \quad (5.31)$
```

where **M** stands for the matrix of FGP shallow shells, **K** is the stiffness matrix, **F** represents the external excitation force vector acting on the shallow shell. **Q** represents the generalized coordinate vector. When no external force is applied to the shallow shell (i.e., the force vector in Eq. (5.31) is set as the zero vector), the generalized eigenvalue Eq. (5.30) required for free vibration analysis can then be obtained. The related dynamic equation can be stated as:

```
$(\mathbf{K} - \omega^2\mathbf{M})mathbf{Q} = 0 \quad (5.32)$
```

In this study, four types of loads including the rectangular, triangular, half-sine, and exponential pulse are mainly considered for the forced vibration analysis, the mathematical definition of which can be written as [47]:

```
$Rectangular: F_r(t) = \begin{cases} f_r & 0 \le t \le \tau \\ 0 & t > \tau \end{cases}$
```

```
$Triangular: F_t(t) = \begin{cases} \frac{2t}{\tau}f_t & 0 \le t \le \frac{\tau}{2} \\ -2(\frac{t}{\tau} - 1)f_t & \frac{\tau}{2} \le t \le \tau \\ 0 & t \ge \tau \end{cases}$
```

```
$Half-sine: F_s(t) = f_s\sin(\frac{\pi t}{\tau}) \begin{cases} & 0 \le t \le \tau \\ 0 & t > \tau \end{cases}$
```

```
$Exponential: F_e(t) = \begin{cases} f_ee^{-\frac{t}{\tau}} & 0 \le t \le \tau \\ 0 & t > \tau \end{cases} \quad (5.33)$
```

where $f_t$ and $\tau$ are respectively the amplitude and pulse width of the load acting on the shallow shell, $t$ stands for the time variable. $\xi$ denotes the constant term. On the basis of the previous derivation, the transient dynamic analysis of the shallow shell can be further carried out. The basic equation of motion can be expressed as:

## $\mathbf{M}\ddot{\mathbf{u}} + \mathbf{C}_u\dot{\mathbf{u}} + \mathbf{K}\mathbf{u} = \mathbf{F}$

where $\mathbf{M}$, $\mathbf{K}$, and $\mathbf{F}$ are consistent with the previous formulation, $\ddot{\mathbf{u}}$, $\dot{\mathbf{u}}$, and $\mathbf{u}$ represent the acceleration vector, the velocity vector, and the displacement vector, $\mathbf{C}_R$ is the damping matrix of the structure, which can be defined as [15].

## $\mathbf{C}_R = \beta_1\mathbf{M} + \beta_2\mathbf{K}$

$\beta_1$ and $\beta_2$ stand for the Rayleigh damping coefficients. For the current investigation, the damping is not taken into account, that is, $\mathbf{C}_R=0$.

In order to obtain the response of FGP shallow shell, the Newmark-$\beta$ method is employed to solve the transient dynamic equation. According to Newmark-$\beta$, the recursive relationship between displacement $\mathbf{u}_i$ and velocity $\dot{\mathbf{u}}_i$ for the response of FGP shallow shell can be obtained and the transient response at an arbitrary moment can be computed.

```
$$\mathbf{u}_{i+\Delta t} = \mathbf{u}_i + (1-\delta)\dot{\mathbf{u}}_i\Delta t + \frac{\delta}{2}\ddot{\mathbf{u}}_{i+\Delta t}\Delta t^2$$
$$\dot{\mathbf{u}}_{i+\Delta t} = \dot{\mathbf{u}}_i + \ddot{\mathbf{u}}_i\Delta t + (\frac{1}{2}-\alpha)(\ddot{\mathbf{u}}_i + \ddot{\mathbf{u}}_{i+\Delta t})\Delta t^2$$
```

From Eq. (5.37), it can be deduced that the calculation formulas of acceleration and velocity at $t_{i+1}$ are as follows:

```
$$\ddot{\mathbf{u}}_{i+1} = a_0(\dot{\mathbf{u}}_{i+1} - \dot{\mathbf{u}}_i) + a_2(\mathbf{u}_{i+1} - \mathbf{u}_i)$$
$$\dot{\mathbf{u}}_{i+1} = a_1(\dot{\mathbf{u}}_{i+1} - \dot{\mathbf{u}}_i) + a_4(\mathbf{u}_{i+1} - \mathbf{u}_i)$$
```

where

```
$a_0 = \frac{1}{\alpha\Delta t^2}, a_1 = \frac{\delta}{\alpha\Delta t}, a_2 = \frac{-1}{\alpha}, a_3 = \frac{1}{2\alpha}, a_4 = \frac{-1}{2\alpha}, a_5 = \frac{\Delta t}{2}(\frac{1}{\alpha}-1)$
```

where $\alpha=\frac{1}{2}$ and $\delta=\frac{1}{2}$. According to Eq. (5.34), the equation of motion at $t_{i+1}$ can be obtained:

```
$$\mathbf{M}\ddot{\mathbf{u}}_{i+1} + \mathbf{C}_R\dot{\mathbf{u}}_{i+1} + \mathbf{K}\mathbf{u}_{i+1} = \mathbf{F}_{i+1}$$
```

Free and forced vibrations of functionally graded porous shells on elastic foundation 153

Combining Eqs. (5.36)–(5.38) yields the displacement, acceleration, and velocity at time $t_{i+1}$.

## 5.3 Analysis and discussion

Based on the dynamic model developed above, the object of this section is to carry out the free and forced vibration of FGP shallow shells on elastic foundation, which mainly includes the following aspects:
- (1) convergence analysis;
- (2) verification analysis, to compare the data obtained by self-compiled program with published results;
- (3) free vibration analysis of FGP shallow shells;
- (4) forced vibration, to analyze the effects of boundary conditions, load types, loading locations, material parameters $\rho_1=2702$ kg/m$^3$, $E_1=70$ GPa, $\nu=0.3$, the dimensionless frequency parameter $\omega = \sqrt{\rho_1/E_1}$.

### 5.3.1 Convergence

According to the theoretical derivation, it can be found that many aspects affect the convergence, such as boundary and elastic foundation parameters. Choosing an appropriate truncation number can help improve the calculation efficiency and accuracy of solutions. As a matter of convenience, truncation numbers $M=N=4\times4$, $8\times8$, $10\times10$, and $12\times12$ are selected in the analysis. For relatively high order cases, $M=N=8$ is sufficient to meet the convergence requirements.

### 5.3.2 Validity of the method

The preceding subsections have analyzed the convergence of the method proposed in this chapter. To ensure the correctness of the analysis, it is firstly necessary to compare the results with those of literature. Table 5.1 Convergence of dimensionless frequencies $\Omega$ of the functionally graded porous shell with different polynomial truncation

| Shell type | M $\times$ N | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $R_{\infty} = \infty$ | $4\times4$ | 0.1497 | 0.2263 | 0.2833 | 0.3257 | 0.3728 | 0.3757 | 0.4147 |
| | $6\times6$ | 0.0970 | 0.1734 | 0.2267 | 0.3197 | 0.3597 | 0.3797 | 0.3724 | 0.3767 |
| | $8\times8$ | 0.0971 | 0.1839 | 0.2159 | 0.3469 | 0.3401 | 0.3081 | 0.3604 | 0.3604 |
| | $12\times12$ | 0.0971 | 0.1841 | 0.2571 | 0.3050 | 0.3604 | 0.3051 | 0.3604 | 0.4148 |
| $R_{\infty} = 2$ | $4\times4$ | 0.1058 | 0.1841 | 0.2210 | 0.3276 | 0.3597 | 0.3724 | 0.3781 | 0.4148 |
| | $6\times6$ | 0.1058 | 0.1836 | 0.1834 | 0.2840 | 0.3752 | 0.3758 | 0.3789 | 0.3592 |
| | $10\times10$ | 0.1058 | 0.1889 | 0.2580 | 0.3092 | 0.3739 | 0.3595 | 0.3072 | 0.3613 |
| | $4\times4$ | 0.1144 | 0.1836 | 0.2135 | 0.3073 | 0.3002 | 0.3073 | 0.3072 | 0.4147 |
| | $6\times6$ | 0.1144 | 0.1889 | 0.2589 | 0.3126 | 0.3024 | 0.3385 | 0.3385 | 0.3799 |
| | $8\times8$ | 0.1144 | 0.1870 | 0.2151 | 0.3016 | 0.3525 | 0.3379 | 0.3358 | 0.3799 |
| | $10\times10$ | 0.1144 | 0.1872 | 0.2295 | 0.3078 | 0.3501 | 0.3108 | 0.3576 | 0.3558 |
| | $12\times12$ | 0.1144 | 0.1831 | 0.2329 | 0.3076 | 0.3076 | 0.3038 | 0.3588 | 0.3556 |
| $R_{\infty} = -2$ | $10\times10$ | 0.1133 | 0.1829 | 0.2595 | 0.3255 | 0.3060 | 0.3063 | 0.3071 | 0.3451 |
| | $4\times4$ | 0.1133 | 0.1796 | 0.2198 | 0.3177 | 0.3721 | 0.3721 | 0.3753 | 0.3785 |
| | $6\times6$ | 0.1133 | 0.1896 | 0.2573 | 0.3072 | 0.2384 | 0.3595 | 0.3595 | 0.3785 |
| | $8\times8$ | 0.1133 | 0.1896 | 0.2579 | 0.3067 | 0.3113 | 0.3113 | 0.3657 | 0.3696 |
| | $12\times12$ | 0.1133 | 0.1896 | 0.1896 | 0.3084 | 0.3083 | 0.3065 | 0.3096 | 0.3606 |
