selection. The weights representing the relative significance of the qualities $Y$, are represented by $W_v$ ($v=1,2,3,...,V$). Eq. (7.1) illustrates how attribute weights can be displayed as a vector.

$W = W_v \quad (7.1)$

The steps listed below can be used to describe the TOPSIS method:

+   **Determine the normalized performance ratings:
Normalized performance ratings are obtained from Eq. (7.2) by applying vector normalization.

$D = \begin{bmatrix} d_{11} & d_{12} & d_{13} & \dots & d_{IV} \ d_{21} & d_{22} & d_{23} & \dots & d_{2V} \ d_{31} & d_{32} & d_{33} & \dots & d_{3V} \ \vdots & \vdots & \vdots & \ddots & \vdots \ d_{U1} & d_{U2} & d_{U3} & \dots & d_{UV} \end{bmatrix} \quad (7.2)$

where $D$ is a decision matrix. Each performance rating $d_{uv}$ in $D$ is split by its norm in this attribute ($u=1,2..,U; v=1,2..,V$). Equation (7.2) can be used to obtain the normalized ratings $t_{uv}$

$t_{uv} = \frac{d_{uv}}{\sqrt{\sum_{v=1}^V d_{uv}^2}} \quad (7.3)$

This conversion procedure uses dimensionless units to facilitate comparisons across attributes. As Eq. (7.4) indicates, the normalized performance ratings $t_{uv}$ can be expressed as a matrix $T$.

$T = \begin{bmatrix} t_{11} & t_{12} & t_{13} & \dots & t_{IV} \ t_{21} & t_{22} & t_{23} & \dots & t_{2V} \ t_{31} & t_{32} & t_{33} & \dots & t_{3V} \ \vdots & \vdots & \vdots & \ddots & \vdots \ t_{U1} & t_{U2} & t_{U3} & \dots & t_{UV} \end{bmatrix} \quad (7.4)$

+   **Combine ratings and weight:
As Eq. (7.5) indicates, the weighted and normalized performance rating $p_{uv}$ ($u=1,2..,U; v=1,2..,V$) is computed using Eqs. (7.1) and (7.4).

$p_{uv} = W_v * t_{uv} (u=1,2..,U; v=1,2..,V) \quad (7.5)$

In Eq. (7.6), the weighted-decision matrix $P$ is created by combining these weighted ratings.

$P = \begin{bmatrix} p_{11} & p_{12} & p_{13} & \dots & p_{IV} \ p_{21} & p_{22} & p_{23} & \dots & p_{2V} \ p_{31} & p_{32} & p_{33} & \dots & p_{3V} \ \vdots & \vdots & \vdots & \ddots & \vdots \ p_{U1} & p_{U2} & p_{U3} & \dots & p_{UV} \end{bmatrix} \quad (7.6)$