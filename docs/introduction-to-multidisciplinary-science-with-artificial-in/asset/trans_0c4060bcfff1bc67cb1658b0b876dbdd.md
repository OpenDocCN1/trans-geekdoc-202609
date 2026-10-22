
其中 $R_c = |R_c|$，(6.31) 中的带电粒子方程变为

$$m\frac{d\boldsymbol{v}(\boldsymbol{x},t)}{dt}=q\left(\frac{\boldsymbol{F}_{\text{cent}}}{q}+\boldsymbol{v}\times\boldsymbol{B}\right).\tag{6.47}$$

将该力直接代入 (6.32)，可得到离心漂移速度如下：

$$\boldsymbol{v}_{\text{drift}}=\frac{\boldsymbol{F}_{\text{cent}}\times\boldsymbol{B}}{qB^2}=\frac{mv_{\parallel}^2}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right)=\frac{2U_{\parallel}}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right),\tag{6.48}$$

其中 $U_{\parallel}=(mv_{\parallel}^2)/2$。因此，根据 $q$ 的符号，漂移方向为垂直纸面向内或向外。图 6.14 给出了带电粒子在环形几何非均匀磁场中引导中心轨迹的一个示例。粒子沿磁力线的弯曲方向漂移。

因为由 (6.48) 可知 $B$ 与 $1/R_c$ 成正比，我们可以验证 $\nabla B/B=\boldsymbol{R}_c/R_c^2$ [即 $\nabla(R_c^{-1})=-\boldsymbol{R}_c/R_c^3$]。因此，我们也可以将漂移速度写成如下形式：

$$\boldsymbol{v}_{\text{drift}}=\frac{2U_{\parallel}}{q}\left(\frac{\boldsymbol{B}\times\nabla\boldsymbol{B}}{B^3}\right).\tag{6.49}$$

在这种形式下，我们可以直接比较梯度 B 漂移和曲率漂移。总而言之，梯度漂移和曲率漂移方向相同，且与粒子能量成正比。最后，我们可以将总的引导中心漂移写成

$$\boldsymbol{v}_D=\underbrace{\frac{\boldsymbol{E}\times\boldsymbol{B}}{B^2}}_{E\times B\text{ 漂移}}+\underbrace{\frac{\boldsymbol{F}\times\boldsymbol{B}}{B^2}}_{\text{外力漂移}}+\underbrace{\frac{U_{\perp}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{grad-B 漂移}}+\underbrace{\frac{2U_{\parallel}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{曲率漂移}}.$$

这些只是粒子漂移的示例，粒子漂移即粒子引导中心的运动。由磁场与外力共同作用产生的漂移有许多已知和未知的类型。本章最后的练习以及表 6.4 和表 6.6 中的代码，为读者提供了实验此处所述漂移并探索可能的新漂移的机会。请注意，粒子漂移可用于解释和描述许多现象，例如行星磁场、日冕环和托卡马克。

## 6.2.3. 磁镜

我们继续考虑电场为零、磁场非均匀时带电粒子的运动。从图 6.15 可以看出，当粒子运动到强磁场区域时，由于这些区域像镜子一样，粒子可能被反射。带电粒子的弹跳运动是粒子在两镜之间沿（平行于）磁场的上下往复运动。我们这里的目标是解释弹跳运动背后的这种镜效应。我们将首先引入带电粒子运动的第二个常数，即磁矩。(6.6) 中引入的另一个常数是带电粒子动能的守恒。

## 表 6.5. 自然界中各种等离子体的一些性质。L 是所关注的宏观长度尺度或系统尺寸，B_eq 是磁场，t0 是观测时间。

|  | L (km) | B_eq (T) | t0 (s) |
|---|---|---|---|
| 托卡马克 | 0.020 | 3 | 3 × 10⁻⁶ |
| 地球磁层 | 4 × 10⁴ | 3 × 10⁻⁵ | 6 |
| 太阳日冕环 | 10⁵ | 3 × 10⁻² | 15 |
| 中子星磁层 | 10³ | 10¹¹ | 10⁻² |
| 年轻恒星体吸积盘（YSO） | 1.5 × 10⁶ | 10⁻⁴ | 7 × 10⁵ |
| 活动星系核吸积盘（AGN） | 4 × 10¹⁵ | 10⁻⁴ | 2 × 10¹² |
| 星系等离子体 | 10¹⁸ | 10⁻⁸ | 10¹⁵ |

## 表 6.6. 用于在磁偶极子（类地磁偶极子）存在的情况下模拟单粒子运动的 Matlab 代码。其输出为带电粒子（此处为质子）的轨迹和动力学。

```
close all; clear all;
e = 1.602176565e-19; mp = 1.672621777e-27; me = 9.10938291e-31;
c = 299792458; Re = 6378137 ; U = 15e6; % kinetic energy in eV
m = mp; vabs = c/sqrt(1-(m*c^2)/(U*e)); pitcha = 30.0; vx0 = 0.0;
vy0 = vabs*sin(pitcha*pi/180); vz0 = vabs*cos(pitcha*pi/180);
tf = 100; time = 0:0.01:tf;
[t,xx] = ode45(@Lorenz,time,[4*Re ;0; 0; vx0; vy0; vz0]); % solve eqn
plot3(xx(:,1)/Re,xx(:,2)/Re,xx(:,3)/Re,'r'); % trajectory in 3D
xlabel('x[Re]'); ylabel('y[Re]'); zlabel('z[Re]')
%plot(xx(:,1)/Re,xx(:,2)/Re,'r'); % trajectory in 2D
hold on; sphere(30); hold off;grid on
```

```
function xxf = Lorenz(t,xxin)
xxf = zeros(6,1); Beq = 3.07e-5; Re = 6378137; e = 1.602176565e-19;
mp = 1.672621777e-27; me = 9.10938291e-31; c = 299792458;
qem = e/mp; % qom=e/mp for proton & qom=-e/me for electron
usB00 = -Beq*Re^3/(xxin(1)^2 + xxin(2)^2 + xxin(3)^2)^2.5;
Bx = 3*xxin(1)*xxin(3)*usB00; By = 3*xxin(2)*xxin(3)*usB00;
Bz = (2*xxin(3)^2 -xxin(1)^2 -xxin(2)^2)*usB00;
xxf(1) = xxin(4); xxf(2) = xxin(5); xxf(3) = xxin(6); % (dx/dt,dy/dt,...)
xxf(4) = qem*(xxin(5)*Bz - xxin(6)*By); % dvx/dt = qem*(v x B)-x
xxf(5) = qem*(xxin(6)*Bx - xxin(4)*Bz); % dvy/dt = qem*(v x B)-y
xxf(6) = qem*(xxin(4)*By - xxin(5)*Bx); % dvz/dt = qem*(v x B)-z
end
```

其中

μ_mag = (m v_⊥²)/(2B) = |q| v_⊥²/(2Ω₀) = U_⊥/B = (垂直于磁场的动能)/(磁场强度). (6.51)

我们使用由 grad-B 漂移产生的粒子速度中沿磁场方向的分量。量 μ_mag 称为磁矩，由于它是常数，因此它在粒子运动中守恒。让我们证明 μ_mag 确实是

![](img/f5b5b8709fc3a81631262f22d3552c5e_631_0.png)

图 6.15. 磁镜示意图，其中包含 t = 8000 dt、t = 19000 dt、t = 29000 dt 和 t = 39000 dt 时刻带电粒子运动的快照。这里使用的非均匀磁场为 B = Br0 i_r + Bz i_z = [Br0 cos(Ωg t), Br sin(Ωg t), Bz]^T，其中 Bz = Bz0 + x dBx/dx + y dBy/dy，Ωg = mq/Bz0，Br0 = 1100 nT，Bz0 = 30 nT。更多细节可参见表 6.4。回旋半径在磁场较弱处较大，在磁场较强处较小。注意，粒子可以在磁镜上反射（弹跳）。

在粒子运动过程中是一个常数。注意，我们也可以通过沿包围面积 A 的闭合回路流动的电流来引入磁矩。面积为 A、电流为 I 的电流回路具有磁矩 μ_mag = I A / c0，其中 c0 是光速。带电粒子沿其拉莫尔半径运动就是这样一种回路，其中 A = π r_g^2，I = q(Ω/2π)，Ω = v⊥/r_g，由此我们得到 (6.51) 中的结果。还要注意，磁矩是一个绝热不变量，这意味着在外部变量缓慢变化时它保持不变。我们接下来的任务是证明这一结果。

如果用 v∥ 对 (6.50) 两边取点积，我们得到

d/dt (1/2 m v∥^2) = - μ_mag v∥ dB/dz = - μ_mag dz/dt dB/dz = - μ_mag dB/dt . (6.52)

利用动能守恒，我们可以构造一个包含 μ_mag 的第二个独立方程如下：

d/dt (1/2 m v∥^2 + 1/2 m v⊥^2) = d/dt (1/2 m v∥^2 + μ_mag B) = 0 . (6.53)

我们使用了磁矩的定义 ½mv⊥² = μmag B。令 (6.52) 与 (6.53) 相等，可得

```
d(μmag B)/dt − μmag dB/dt = 0 ⇔ dμmag/dt = 0 ,
```

对于 μmag 不随时间变化（即为常数）的情况，该式成立。在上述推导中，我们使用了磁场随时间缓慢变化这一事实。

磁矩守恒本质上就是关于引导中心的角动量守恒。正如我们在 Ikle (2023b) 中定义的，角动量为 L = m x0 × v，其大小为

```
|L| = m |x0| v sinθ = m r0 v⊥ = 2m / |q| μmag ,
```

其中 θ 是 x0 与 v 之间的夹角，如 Ikle (2020) 中所定义，且 v⊥ = v sinθ。由于 L 是常数，μmag 也是常数。

## 磁镜力。

现在考虑图 6.16 中的磁场。当场均匀时，磁力线相互平行，粒子沿椭圆运动，洛伦兹力垂直于 B 和 v⊥，并指向引导中心。当场不均匀时（图 6.16），在这种情况下磁力线向右汇聚，磁场与磁力线之间形成一个夹角，因此洛伦兹力在 z 方向上的分量不再为零。因而，粒子将沿着与场强增大方向相反的方向被加速。粒子将被反射回来，磁场增强的区域因此充当反射器，称为磁镜。为了定量描述这一结果，让我们在柱坐标系中计算 z 方向上的洛伦兹力：

```
Fz = q (v × B)z / c0 = q v⊥ Br / c0 ,
```

其中 B = Br r + Bz z，Br 是磁场在柱坐标 r 方向上的分量，z 方向如图 6.16 所示。我们假设磁场是轴对称的（即 ∂B/∂θ = 0）。利用麦克斯韦方程 ∇ · B = 0，并再次在柱极坐标中处理，我们得到

```
1/r ∂(r Br)/∂r + ∂Bz/∂z = 0 ⇒ ∂(r Br)/∂r = -r ∂Bz/∂z .
```

如果 ∂Bz/∂z 在 r = 0 处给定，并且随 r 变化不大，那么

```
r Br ≈ -1/2 r² [∂Bz/∂z ]_{r=0} ⇒ Br = -1/2 r [∂Bz/∂z ]_{r=0} .
```

我们得到洛伦兹力的垂直分量

```
∇ · B = 1/r ∂(r Br)/∂r + ∂Bz/∂z = 0
```
