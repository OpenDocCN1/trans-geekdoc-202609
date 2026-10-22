
![](img/f5b5b8709fc3a81631262f22d3552c5e_622_0.png)

(a) E × B 漂移。电子和离子一起运动。注意 E × B 漂移与电荷和质量无关。因此，该漂移运动不会产生电流。(b) 由磁场梯度引起的粒子漂移。Grad-B 漂移是与空间非均匀磁场相关的漂移。B 大致均匀，力线为直线，但其密度在特定方向上增加，例如 y 方向，该密度由 ∇B 描述。在这种情况下，漂移垂直于 ∇B 和 B，离子和电子向相反方向漂移。该漂移运动会产生电流。

关联的运动方程变为

```
m \frac{dv}{dt} = q (v \times B) + F = q \left( \frac{F}{q} + v \times B \right) , (6.31)
```

并且我们用以下替换 v_E

```
v_F = \frac{F \times B}{q B^2} . (6.32)
```

![](img/f5b5b8709fc3a81631262f22d3552c5e_623_0.png)

> 练习：考虑一个在均匀恒定电场且无磁场的带电粒子。式 (6.5) 中的粒子运动方程简化为 m(dv/dt) = qE。假设 E = E_x i_x 且 v(t = 0) = 0。因此，(x, y) 平面包含电场和初始速度。由于垂直于该平面的加速度为零，且如果垂直于该平面的初始速度为零，则运动保持在该平面内。验证随后运动为 x(t) = (qE_x/2m)t² 且 v_x(t) = (qE_x/m)t。还验证粒子的动能为 U_E = m v_x²/2 = [(qE_x)²/(2m)]t²。在这种情况下，粒子轨迹为抛物线。

在重力场的情况下，例如，我们有 v_F = (m g × B) / (q B²)，(6.33) 且 v_F 被称为重力漂移 (Goldston and Rutherford, 1995)。因此，对带电粒子施加外力也可以产生带电粒子的漂移。由于重力漂移取决于粒子的电荷，原子核和电子向相反方向漂移。

计算练习：
- 使用表 6.3 中的 Matlab 代码，重现图 6.8b 中的回旋运动。
- 使用表 6.3 中的 Matlab 代码，重现图 6.10 中带有 E × B 漂移的回旋运动。

## 测验
让我们考虑 B = [0,0,Bz]^T 且 E = [Ex,0,0]^T。验证带电荷 q 的粒子的漂移速度为 v_E = [0,-Ex/Bz,0]^T，这意味着该漂移垂直于 E 和 B。还验证

v_y = ± sin( (|q|Bz)/m t + φ0 ) - Ex/Bz.  (6.34)

粒子导心在 -i_y 方向漂移，即 -y 方向。因此加上一个电场（垂直于 B），等离子体开始垂直于 E 和 B 漂移（E × B 漂移）。

非均匀磁场对带电粒子动力学有不同的影响。例如，一个在具有非零梯度的磁场中的带电粒子会发生所谓的 grad-B 漂移（Baumjohann and Treumann, 1997）。沿弯曲磁力线运动的带电粒子会受到垂直于磁场的离心力。因此带电粒子在运动中会发生漂移。这种漂移被称为曲率漂移（Baumjohann and Treumann, 1997）。与非均匀磁场中带电粒子的运动相关联的漂移还有很多。我们将集中讨论 grad-B 漂移和曲率漂移。

## 表 6.3. (上) 用于模拟均匀磁场环境中运动带电粒子的代码；x(t) = [rg sin(Ωg t + θ), rg cos(Ωg t + θ), v∥ t]^T。 (下) 用于模拟 E = [Ex,0,0]^T 且 B = [0,0,Bz]^T 时回旋运动的 E × B 漂移的代码。

```
clear all; clear figure; Bz=-5; m=5; vpara=[0 0 0.5]; vper=[3 4 0]; q=-1;
rg=m*(norm(vper))/(q*Bz); theta=atan(vper(2)/vper(1))+pi/2;
xc=rg*cos(theta); yc=rg*sin(theta); wg=norm(vper)/rg; figure
plot3(-15:0.1:15,0,0); hold on; plot3(0,-15:0.1:15,0); plot3(0,0,-15:0.1:15)
xlim([-15 15]); ylim([-15 15]); t=0; tic
for n=1:500
    dt = toc; tic; x=xc+rg*cos(wg*t+theta); y=yc+rg*sin(wg*t+theta);
    z=vpara(3)*t; plot3(x,y,z,'-'); hold on ; t=t+dt; pause(0.00000000215)
end
q=+1; rg = m*(norm(vper))/(q*Bz);
xc=rg*cos(theta); yc=rg*sin(theta); wg= norm(vper)/rg; t=0; tic
for n=1:400
    dt = toc; tic; x=xc+rg*cos(wg*t+theta); y=yc+rg*sin(wg*t+theta);
    z=vpara(3)*t; plot3(x,y,z,'-r'); hold on; t=t+dt; pause(0.0000000025)
end
```

```
Bz=5; Ex = 2900; m=5; vpara=[0 0 0.5]; vper=[3 4 0];
q=-1; rg=m*(norm(vper))/(q*Bz); theta=atan(vper(2)/vper(1));
xc=rg*cos(theta); yc=rg*sin(theta); z0=-10; wg=norm(vper)/rg; figure
plot3(-15:0.1:15,0,0); hold on; plot3(0,-15:0.1:15,0);
plot3(0,0,-15:0.1:15); xlim([-15 15]); ylim([-15 15]); t=0; tic
for n=1:700
    dt = toc; tic; x=xc+rg*cos(wg*t+theta);
    y=yc+rg*sin(wg*t+theta)-(Ex/Bz)*t*0.0001;
    z=z0+(vpara(3)*t); plot3(x,y,z,'-.'); hold on; t=t+dt; pause(0.0000000025)
end
```

虽然我们不能对最一般的非均匀磁场解析求解 (6.5)，但仍可对某些类非均匀磁场求解。我们在此描述非均匀磁场中带电粒子的运动，其磁场可表示如下（Baumjohann and Treumann, 1997）：

$$\boldsymbol{B}(\boldsymbol{x},t) \approx \boldsymbol{B}_0 + \boldsymbol{B}_1(\boldsymbol{x},t) = \boldsymbol{B}_0 + (\boldsymbol{x}\cdot\nabla)\boldsymbol{B}(\boldsymbol{x},t)\,,\qquad(6.35)$$

with

$$\boldsymbol{B}_1(\boldsymbol{x},t) = (\boldsymbol{x}\cdot\nabla)\boldsymbol{B}(\boldsymbol{x},t)\,,\qquad(6.36)$$

其中 $\boldsymbol{B}_0$ 为均匀磁场，且 $|\boldsymbol{B}_1| = |(\boldsymbol{x}\cdot\nabla)\boldsymbol{B}|$ 与 $|\boldsymbol{B}_0|$ 相比非常小。这种近似意味着磁场强度可在距离 $|\boldsymbol{x}-\boldsymbol{x}_0| < |\boldsymbol{x}_0|$ 时进行泰勒展开，其中 $r_0 = |\boldsymbol{x}_0|$ 为回旋半径。我们仅保留了泰勒级数的前两项。我们还将粒子速度和位置分解如下：

$$\boldsymbol{v} = \boldsymbol{v}_0 + \delta\boldsymbol{v}\quad\text{and}\quad \boldsymbol{x} = \boldsymbol{x}_0 + \delta\boldsymbol{x}\,,\qquad(6.37)$$

with

$$\boldsymbol{v}_0 = \frac{d\boldsymbol{x}_0}{dt}\quad\text{and}\quad \delta\boldsymbol{v} = \frac{d(\delta\boldsymbol{x})}{dt}\,,\qquad(6.38)$$

且 $|\delta\boldsymbol{v}| \ll |\boldsymbol{v}_0|$ 且 $|\delta\boldsymbol{x}| \ll |\boldsymbol{x}_0|$。将这些分解代入 (6.5) 并假设 $\boldsymbol{E}=\boldsymbol{0}$，我们得到

$$\begin{aligned}
m\frac{d\boldsymbol{v}(\boldsymbol{x},t)}{dt} &= q\boldsymbol{v}(\boldsymbol{x},t)\times\boldsymbol{B}(\boldsymbol{x},t)\\
&= q\big[\boldsymbol{v}\times\boldsymbol{B}_0 + (\boldsymbol{v}_0+\delta\boldsymbol{v})\times(\boldsymbol{x}\cdot\nabla)\boldsymbol{B}\big]\\
&\approx q(\boldsymbol{v}\times\boldsymbol{B}_0)+\boldsymbol{F}_{\mathrm{grad}}(\boldsymbol{x}_0,\boldsymbol{v}_0)
\end{aligned}\qquad(6.39)$$

with

$$\boldsymbol{F}_{\mathrm{grad}}(\boldsymbol{x}_0,\boldsymbol{v}_0)=\boldsymbol{v}_0\times(\boldsymbol{x}_0\cdot\nabla)\boldsymbol{B}\,.$$
\qquad(6.40)

所有二阶修正项都被舍弃，因为我们处理的是微小变化。

现在我们必须处理 $\boldsymbol{v}_0$ 和 $\boldsymbol{x}_0$ 是周期函数这一事实，如前一小节所述，通过对时间和平面对 $\boldsymbol{F}_{\mathrm{grad}}(\boldsymbol{x}_0,\boldsymbol{v}_0)$ 取平均。记住，对于 $\boldsymbol{B}=B_z\boldsymbol{i}_z$，我们有

$$\boldsymbol{x}_0 = [x_0 + r_0\sin(\Omega_0 t + \phi),\, y_0 \pm r_0\cos(\Omega_0 t + \phi),\, z_0 + v_{z0}t]^T\qquad(6.41)$$

![](img/f5b5b8709fc3a81631262f22d3552c5e_627_0.png)

图 6.14. 曲率漂移的另一幅说明（即 B 场线弯曲）显示了非均匀磁场存在下带电粒子的导心轨迹。此处使用的非均匀磁场为 **B** = [B_r cos(Ω_g t), B_r sin(Ω_g t), 0]^T，其中 B_r ∝ √(x² + y²)，Ω_g = m q / B_z0，且 B_z0 = 30 nT。

在我们对 **v**_grad-B 的上述推导中，我们假设 **B** = B_z **i**_z。实际上，式 (6.44) 中的漂移速度对具有很小非零梯度的任意非均匀磁场均有效，与 **B** 的方向无关。我们只需将 B_z 替换为 B；即：

**v**_grad-B = U_⊥ / (q B³) [ **B** × ∇B ] = **F** × **B** / (q B²) , (6.45)

其中 **F** = -μ_mag ∇B 且 μ_mag = U_⊥ / B。

## 曲率漂移。

我们已看到 grad-B 漂移使带电粒子在 B 场横向漂移，当电荷相反时漂移方向相反。该非均匀磁场的力线近似为直线，但其密度在特定方向上增加。这些密度变化由 ∇B 描述。除了 grad-B 漂移之外，还有曲率漂移，这是弯曲磁力线的结果。换句话说，当 **B** 场线弯曲且粒子沿场线的 v_∥ 不为零时，会发生另一种漂移。

沿弯曲磁力线运动的带电粒子会受到离心力（图 6.12b）。假设曲率半径 R_c 与回旋半径 r0 相比很大（即 r0 ≪ R_c）。如 Ikelle (2023a) 所描述，向外的离心力为

**F**_cent = m v_∥² / R_c **R**_c / R_c , (6.46)
