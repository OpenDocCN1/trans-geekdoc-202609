

其中 **n** 是 $S_{i}$ 边界处指向外部的单位法向量。重新整理上述方程可得

$$
\rho_{i}C_{i}\frac{\partial T_{i}(t)}{\partial t} = \frac{1}{S_{i}} \int_{\partial S_{i}} k_{i}\left(\frac{\partial T(t)}{\partial \mathbf{n}}\right)_{i} dl - w_{b,i}C_{b,i}(T_{i}(t) - T_{a,i}) + Q_{i} + H_{i} \tag{4.15}
$$

该方程可近似为

$$
\begin{aligned} 
\rho_{i}C_{i}\frac{\partial T_{i}(t)}{\partial t} = \frac{1}{S_{i}} \sum_{j \in N_{r}(i)} \frac{(k_{j}T_{j}(t) - k_{i}T_{i}(t))}{l_{ij}}(l_{uv} + l_{vw}) \\
- w_{b,i}C_{b,i}(T_{i}(t) - T_{a,i}) + Q_{i} + H_{i} 
\end{aligned} \tag{4.16}
$$

其中 $l_{ij} = \lVert \overline{\mathbf{P}_i \mathbf{P}_j} \rVert$，$l_{uv} = \lVert \overline{\mathbf{uv}} \rVert$ 且 $l_{vw} = \lVert \overline{\mathbf{vw}} \rVert$。重新整理上述方程得到

$$
\begin{aligned} 
\rho_{i}C_{i}\frac{\partial T_{i}(t)}{\partial t} = -\left( \frac{1}{S_{i}} \sum_{j \in N_{r}(i)} \frac{k_{i}(l_{uv} + l_{vw})}{l_{ij}} + w_{b,i}C_{b,i} \right) T_{i}(t) \\
+ \frac{1}{S_{i}} \sum_{j \in N_{r}(i)} \frac{k_{j}(l_{uv} + l_{vw})}{l_{ij}} T_{j}(t) + w_{b,i}C_{b,i}T_{a,i} + Q_{i} + H_{i} 
\end{aligned} \tag{4.17}
$$

可以看出，公式 (4.12) 和 (4.17) 非常相似；因此，通过将以下参数相关联，彭恩斯生物热传导方程（公式 4.17）的离散形式被嵌入到自主 CNN（公式 4.12）中：

$$
C_{x} = \rho_{i}C_{i}; \ v_{xi}(t) = T_{i}(t); \ v_{yj}(t) = T_{j}(t); \ I_{i} = w_{b,i}C_{b,i}T_{a,i} + Q_{i} + H_{i}
$$

$$
\begin{aligned} 
A(i;i) = -\left( \frac{1}{S_{i}} \sum_{j \in N_{r}(i)} \frac{k_{i}(l_{uv} + l_{vw})}{l_{ij}} + w_{b,i}C_{b,i} \right) + \frac{1}{R_{x}} \\
A(i;j) = \frac{1}{S_{i}} \frac{k_{j}(l_{uv} + l_{vw})}{l_{ij}} 
\end{aligned} \tag{4.18}
$$

## 4.3.3 三维网格上的生物热传递 CNN 表述

### 4.3.3.1 三维规则网格

三维规则网格上的 CNN 表述可以通过将二维 CNN 推广到更高维度的情况来表达，即使用三维矩形单元数组。定义与单元 $C(i,j,k)$ 相关的网格点 $i,j,k$，以及 $\Delta w_{k-1}=||\mathbf{P}_{i,j,k-1}\mathbf{P}_{i,j,k}||$ 和 $\Delta w_{k}=||\mathbf{P}_{i,j,k}\mathbf{P}_{i,j,k+1}||$，其中 $\mathbf{P}_{i,j,k}$ 是网格点 $i,j,k$ 的位置。类比于使用有限差分法（FDM）的二维规则网格情况，三维规则网格上彭恩斯生物热传导方程的离散形式可以表示为

$$
\begin{aligned}
\rho_{i,j,k}C_{i,j,k}\frac{\partial T_{i,j,k}(t)}{\partial t} &= -\left(\frac{2k_{i,j,k}}{\Delta u_{i-1}\Delta u_{i}}+\frac{2k_{i,j,k}}{\Delta v_{j-1}\Delta v_{j}}+\frac{2k_{i,j,k}}{\Delta w_{k-1}\Delta w_{k}}+w_{b,i,j,k}C_{b,i,j,k}\right)T_{i,j,k}(t) \\
&+\frac{2k_{i+1,j,k}T_{i+1,j,k}(t)}{\Delta u_{i}(\Delta u_{i-1}+\Delta u_{i})}+\frac{2k_{i-1,j,k}T_{i-1,j,k}(t)}{\Delta u_{i-1}(\Delta u_{i-1}+\Delta u_{i})} \\
&+\frac{2k_{i,j+1,k}T_{i,j+1,k}(t)}{\Delta v_{j}(\Delta v_{j-1}+\Delta v_{j})}+\frac{2k_{i,j-1,k}T_{i,j-1,k}(t)}{\Delta v_{j-1}(\Delta v_{j-1}+\Delta v_{j})} \\
&+\frac{2k_{i,j,k+1}T_{i,j,k+1}(t)}{\Delta w_{k}(\Delta w_{k-1}+\Delta w_{k})}+\frac{2k_{i,j,k-1}T_{i,j,k-1}(t)}{\Delta w_{k-1}(\Delta w_{k-1}+\Delta w_{k})} \\
&+w_{b,i,j,k}C_{b,i,j,k}T_{a,i,j,k}+Q_{i,j,k}+H_{i,j,k}
\end{aligned} \tag{4.19}
$$

自主 CNN 的参数与离散彭恩斯生物热传导方程的参数相关联，从而得到：

$$
C_{x}=\rho_{i,j,k}C_{i,j,k}; \nu_{x}i_{jk}=T_{i,j,k}(t); \quad I_{jk}=w_{b,i,j,k}C_{b,i,j,k}T_{a,i,j,k}+Q_{i,j,k}+H_{i,j,k}
$$

$$
A(i,j,k;i,j,k)=-\left(\frac{2k_{i,j,k}}{\Delta u_{i-1}\Delta u_{i}}+\frac{2k_{i,j,k}}{\Delta v_{j-1}\Delta v_{j}}+\frac{2k_{i,j,k}}{\Delta w_{k-1}\Delta w_{k}}+w_{b,i,j,k}C_{b,i,j,k}\right)+\frac{1}{R_{x}}
$$

$$
\begin{aligned}
A(i,j,k;i+1,j,k)&=\frac{2k_{i+1,j,k}}{\Delta u_{i}(\Delta u_{i-1}+\Delta u_{i})} &; \quad A(i,j,k;i-1,j,k)&=\frac{2k_{i-1,j,k}}{\Delta u_{i-1}(\Delta u_{i-1}+\Delta u_{i})} \\
A(i,j,k;i,j+1,k)&=\frac{2k_{i,j+1,k}}{\Delta v_{j}(\Delta v_{j-1}+\Delta v_{j})} &; \quad A(i,j,k;i,j-1,k)&=\frac{2k_{i,j-1,k}}{\Delta v_{j-1}(\Delta v_{j-1}+\Delta v_{j})} \\
A(i,j,k;i,j,k+1)&=\frac{2k_{i,j,k+1}}{\Delta w_{k}(\Delta w_{k-1}+\Delta w_{k})} &; \quad A(i,j,k;i,j,k-1)&=\frac{2k_{i,j,k-1}}{\Delta w_{k-1}(\Delta w_{k-1}+\Delta w_{k})}
\end{aligned} \tag{4.20}
$$

### 4.3.3.2 二维非规则网格

在三维非规则网格上，生物热传递的 CNN 表述通过将从二维的控制区域扩展为三维的控制体积来实现 [56]。类比于二维三角网格中的控制区域，三维四面体网格中的控制体积是通过一个对偶网格建立的，该网格连接了与计算点相邻的四面体的边中点、面质心和质心。类似于二维非规则情况，对于由控制体积 $\Omega_i$ 包围的点 $i$，彭恩斯生物热传导方程的离散形式可以表示为

$$
\begin{aligned}
\rho_iC_i\frac{\partial T_i(t)}{\partial t} &= -\left(\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_i\sum^n S_{j,n}}{l_{ij}} + w_{b,i}C_{b,i}\right)T_i(t) \\
&+\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_j\sum^n S_{j,n}}{l_{ij}}T_j(t) + w_{b,i}C_{b,i}T_{a,i} + Q_i + H_i
\end{aligned} \tag{4.21}
$$

其中 $\sum^n S_{j,n}$ 表示连接到 $\mathbf{p}_i$ 和 $\mathbf{p}_j$ 之间的边的边界表面的总和 [57]。

自主 CNN 的参数与离散彭恩斯生物热传导方程的参数相关联，结果如下：

$$
\begin{aligned}
C_x &= \rho_iC_i; \nu_{xi} = T_i(t); \nu_{yj}(t) = T_j(t); I_i = w_{b,i}C_{b,i}T_{a,i} + Q_i + H_i \\
A(i;i) &= -\left(\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_i\sum^n S_{j,n}}{l_{ij}} + w_{b,i}C_{b,i}\right) + \frac{1}{R_x} \\
A(i;j) &= \frac{1}{\Omega_i}\frac{k_j\sum^n S_{j,n}}{l_{ij}}
\end{aligned} \tag{4.22}
$$

## 4.3.4 初始和边界条件

为了完整描述 CNN 模型，必须指定初始条件和边界条件。初始条件是通过将单元的初始状态赋予组织的初始温度来实现的，即

$$
v_{x}(0)=T(0)
$$

狄利克雷类型的边界条件是通过将固定状态单元赋予预设的恒定温度来强制执行的，即

$$
v_{x, b}(t)=T
$$

其中 $v_{x, b}(t)$ 表示指定区域边界上在时间 t 时刻的单元状态。

CNN 的时间演化直接提供了由彭恩斯生物热传导方程控制的软组织温度场，随后用于热剂量计算。

## 4.4 数值示例

### 4.4.1 特定患者的热剂量计算

采用一组具有异质组织的特定患者虚拟数字模型来分析个性化热消融治疗中肝肿瘤的热剂量。如图 4.4 所示，特定患者的解剖模型是根据一名匿名患者的计算机断层扫描（CT）医学图像数据集构建的（该数据集可在 https://www.irCAD.fr/research/3dicadb/ 获取），并将其分割和重建为肝脏和骨骼。热剂量 $CEM_{d_3}$ 是根据组织热暴露历史（公式 4.1）计算得出的，其中组织温度由嵌入生物热传递的 CNN 计算得出，其性能在参考文献 [41] 中此前已得到评估。组织的异质性是通过根据不同区域组织/肿瘤的材料特性将单元参数设置为不同值来建模的。

如图 4.5 所示，使用高斯分布类型的体积热源作为外部施加的热源。模拟的热源被用于证明 CNN 方法论在估计组织温度和热剂量方面的适用性，并且它们可以被替换为不同尺寸和形状的热源，例如由不同的热消融方式引起的热源。

