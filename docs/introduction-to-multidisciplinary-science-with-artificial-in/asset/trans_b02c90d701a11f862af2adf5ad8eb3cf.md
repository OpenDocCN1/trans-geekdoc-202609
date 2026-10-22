
![](img/f5b5b8709fc3a81631262f22d3552c5e_752_0.png)

Figure A.1. 求解三维弹性动力学方程的自然非交错网格结构的示意图。所有波场分量均在其自然位置的网格点上定义，即在单元顶点处（即所有波场分量均在每个顶点处定义）。

在交错网格技术中，微分方程 (A.43)-(A.44) 中的并非所有量都栅格化在参考网格的点上。有些量定义在参考网格之外半个网格点处，例如 x = (i ± ½) Δx 而不是 x = iΔx。图 A.2 显示了在介质仅具有正交各向异性对称性时方程 (A.43)-(A.44) 的交错栅格配置示例。我们限制自己的原因将在本小节后面讨论。注意正应力、比容和刚度位于同一位置。由此产生两个问题：(i) 为什么有些量位于参考网格上而其他量位于参考网格之外？以及 (ii) 我们为什么选择使用交错网格有限差分技术而不是标准有限差分技术？让我们从第二个问题开始。我们将某些量置于参考网格上而其他量置于参考网格之外的目标是得到一个有限差分格式，其中微分算子仅作用于波场变量，而不作用于介质参数。记住波场按定义在空间和时间上是连续的，因此适合对空间和时间变量求微分，而介质参数通常是关于空间变量的不连续函数，因此不太适合对空间求微分。因此，只要可能就应避免对介质参数求微分。交错网格技术使我们能够做到这一点。

现在让我们转向交错栅格配置中物理量位置的问题。首先，在交错栅格配置中定位弹性波动方程的物理量并没有唯一的方法。

![](img/f5b5b8709fc3a81631262f22d3552c5e_753_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_753_1.png)

Figure A.2. (a) 在假设介质具有正交各向异性对称性的情况下，(A.43)-(A.44) 的一个交错栅格化示例。(b) 同一方程的另一个交错栅格化示例。

例如，图 A.2 是两个有效解。在交错栅格配置中选择物理量位置的目标是各种微分算子必须仅在交错网格点处需要波场分量，在这些点上这些分量被定义；微分算子必须不需要任何插值来实现这一目标。当满足这一目标时，质点速度分量可独立于应力进行更新。这一结果产生了一种有效的实现，尽管与标准有限差分技术相比，其计算机代码需要一些额外的思考（特别是在各种变量的索引方面）。

使用图 A.2a 中的定义，方程 (A.43)-(A.44) 中量的离散形式可写为如下：

$C_{IJ}(x,y,z)=C_{IJ}\left[(i+\tfrac12)\Delta x,(j+\tfrac12)\Delta y,(k+\tfrac12)\Delta z\right]=[C_{IJ}]_{i+1/2,j+1/2,k+1/2}$,
$\sigma(x,y,z)=\sigma\left[(i+\tfrac12)\Delta x,(j+\tfrac12)\Delta y,(k+\tfrac12)\Delta z\right]=\sigma_{i+1/2,j+1/2,k+1/2}$

对于介质参数，以及

$\tau_{pp}(x,y,z,t)=\tau_{pp}\left[(i+\tfrac12)\Delta x,(j+\tfrac12)\Delta y,(k+\tfrac12)\Delta z,n\Delta t\right]=[\tau_{pp}]_{i+1/2,j+1/2,k+1/2}^{n}$,
$\tau_{yz}(x,y,z,t)=\tau_{yz}\left[(i+\tfrac12)\Delta x,j\Delta y,k\Delta z,n\Delta t\right]=[\tau_{yz}]_{i+1/2,j,k}^{n}$,
$\tau_{xz}(x,y,z,t)=\tau_{xz}\left[i\Delta x,(j+\tfrac12)\Delta y,k\Delta z,n\Delta t\right]=[\tau_{xz}]_{i,j+1/2,k}^{n}$,
$\tau_{xy}(x,y,z,t)=\tau_{xy}\left[i\Delta x,j\Delta y,(k+\tfrac12)\Delta z,n\Delta t\right]=[\tau_{xy}]_{i,j,k+1/2}^{n}$,
$v_x(x,y,z,t)=v_x\left[i\Delta x,(j+\tfrac12)\Delta y,(k+\tfrac12)\Delta z,(n+\tfrac12)\Delta t\right]=[v_x]_{i,j+1/2,k+1/2}^{n+1/2}$,
$v_y(x,y,z,t)=v_y\left[(i+\tfrac12)\Delta x,j\Delta y,(k+\tfrac12)\Delta z,(n+\tfrac12)\Delta t\right]=[v_y]_{i+1/2,j,k+1/2}^{n+1/2}$,
$v_z(x,y,z,t)=v_z\left[(i+\tfrac12)\Delta x,(j+\tfrac12)\Delta y,k\Delta z,(n+\tfrac12)\Delta t\right]=[v_z]_{i+1/2,j+1/2,k}^{n+1/2}$
(A.50)

其中 $p = x, y, z$ 为正应力。

在给出交错网格技术中的最终方程之前，让我们回顾一下计算一阶导数的基本公式。有限差分技术中的一阶导数基于泰勒级数的近似。导数可以用二阶算子、四阶算子甚至更高阶算子来近似。阶数越高，差分算子越长，实际一阶导数的精度越高，计算时间也越昂贵。

对于任意 $\alpha$，函数 $g(x)$ 的一阶导数可由 Abramowitz 和 Stegun (1964) 给出的三点公式近似：

$\frac{\partial g(x+\alpha\Delta x)}{\partial x}= \frac{1}{\Delta x}\left[\left(\alpha-\frac12\right)g(x-\Delta x)-2\alpha g(x)+\left(\alpha+\frac12\right)g(x+\Delta x)\right]+...$ (A.51)

将方程 (A.51) 在 $\alpha = 0$ 处求值可得到参考网格上的导数：

$\frac{\partial g(x)}{\partial x}\approx\frac{1}{\Delta x}\left[-\frac12 g(x-\Delta x)+\frac12 g(x+\Delta x)\right]$ (A.52)

类似地，将方程 (A.51) 在 $\alpha = 1/2$ 处求值可得到

$\frac{\partial g\left(x+\frac12\Delta x\right)}{\partial x}\approx\frac{1}{\Delta x}\left[-g(x)+g(x+\Delta x)\right]$ (A.53)

我们也可以通过将方程 (A.53) 在负方向平移半个网格点来得到参考网格上的导数；即

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ -g \left( x - \frac{1}{2}\Delta x \right) + g \left( x + \frac{1}{2}\Delta x \right) \right] \ . \] (A.54)

方程 (A.54) 是近似一阶导数的二阶算子。我们的时间导数基于此公式。

对于空间导数，我们将使用四阶或更高阶近似。我们可以使用五点公式得到四阶近似。对于任意 α，函数 g(x) 的一阶导数可由五点公式近似，如下：

\[\frac{\partial g(x + \alpha\Delta x)}{\partial x} = \frac{1}{\Delta x} \left[ \frac{1}{12} (2\alpha^3 - 3\alpha^2 - \alpha + 1) g(x - 2\Delta x) 
 - \frac{1}{6} (4\alpha^3 - 3\alpha^2 - 8\alpha + 4) g(x - \Delta x) 
 + \frac{1}{2} (4\alpha^3 - 3\alpha) g(x) 
 + \frac{1}{6} (4\alpha^3 - 3\alpha^2 - 8\alpha + 4) g(x + \Delta x) 
 - \frac{1}{12} (2\alpha^3 - 3\alpha^2 - \alpha + 1) g(x + 2\Delta x) \right] + ... \ . \] (A.55)

将方程 (A.55) 在 α = 0 处求值可得到参考网格上的导数：

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{12}g(x - 2\Delta x) - \frac{2}{3}g(x - \Delta x) + \frac{2}{3}g(x + \Delta x) - \frac{1}{12}g(x + 2\Delta x) \right] \ . \] (A.56)

类似地，将方程 (A.55) 在 α = 1/2 处求值可得到

\[\frac{\partial g(x + \frac{1}{2}\Delta x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{24}g(x - \Delta x) - \frac{9}{8}g(x) + \frac{9}{8}g(x + \Delta x) - \frac{1}{24}g(x + 2\Delta x) \right] \ . \] (A.57)

我们也可以通过将方程 (A.57) 在负方向平移半个网格点来得到参考网格上的导数；即

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{24}g(x - \frac{3}{2}\Delta x) - \frac{9}{8}g(x - \frac{1}{2}\Delta x) + \frac{9}{8}g(x + \frac{1}{2}\Delta x) - \frac{1}{24}g(x + \frac{3}{2}\Delta x) \right] \ . \] (A.58)
