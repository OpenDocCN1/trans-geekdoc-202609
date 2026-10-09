
Pennes bio-heat transfer equation [46], which accounts for the effects of heating and cooling of heat conduction, blood perfusion, metabolic heat generation, and external heat sources. It was validated against experiments [47,48] that the Pennes bio-heat model can offer reliable tissue temperature predictions, and it was widely used to model tumour management by hyperthermia and thermal ablative treatments [49–52]. For soft tissues of mass density \(\rho\), specific heat capacity \(C\), thermal conductivity \(k\), blood perfusion rate \(w_b\), blood specific heat capacity \(C_b\), arterial blood temperature \(T_a\), metabolic heat generation rate \(Q\), and subject to an external heat source \(H\), the Pennes bio-heat transfer equation is given by [46]

$$\rho C \frac{\partial T(t)}{\partial t} = \nabla \cdot (k \nabla T(t)) - w_b C_b (T(t) - T_a) + Q + H \tag{4.3}$$

where $\nabla \cdot$ represents the divergence operator, and $\nabla$ represents the gradient operator.

## 4.3 CELLULAR NEURAL NETWORKS

### 4.3.1 Architecture

A CNN is a dynamic information-processing system that processes signals in real-time in a large-scale non-linear analogue circuit; the fundamental unit of a circuit in CNN is called a cell, and every cell is a time-continuous non-linear dynamic signal processing unit made of capacitors, resistors, and voltage-controlled current sources of linear and non-linear types [30]. Cells are interconnected and communicate with their adjacent cell neighbours [53]; as a result, it leads to a global propagation that cells not directly connected influence each other implicitly [54]. An example of a 2D CNN is shown in Figure 4.1. Owing to the behaviours of non-linear cell dynamics, local cell interaction, global cell propagation and simultaneous cell activity, CNNs are well suited for high-speed parallel signal processing such as

![](img/6554116edbb19a8210b75a29243fd6ec_51_0.png)

FIGURE 4.1 A 2D CNN of grid size 3×3: the rectangles are the cells, and the connections between cells denote local cell interactions.

fast computation of non-linear partial differential equations [29]. Hence, in analogy to the heat transfer equation with a given input of heat source that governs the non-linear bio-heat transfer behaviour in biological soft tissues, the presented CNN is formulated as the global propagation of a given current source (analogy to the heat source) through the locally interconnected activity of non-linear cell dynamics.

Consider a 2D CNN made of a rectangular computing array of M × N cells in M rows and N columns, the dynamics of CNN are given by [30]:

-   i. Cell state $v_{xj}(t)$

$$ C_x\frac{dv_{xj}(t)}{dt}=-\frac{1}{R_x}v_{xj}(t)+\sum_{C(k,l)\in N_r(i,j)}A(i,j;k,l)v_{ykl}(t) $$
$$ +\sum_{C(k,l)\in N_r(i,j)}B(i,j;k,l)v_{ukl}(t)+I_{lj} \tag{4.4} $$

-   ii. Cell output $v_{yij}(t)$

$$ v_{yij}(t)=\frac{1}{2}\left(|v_{xij}(t)+K|-|v_{xij}(t)-K|\right), K \geqslant 1 \tag{4.5} $$

-   iii. Constraint conditions

$$ v_{xij}(0) \leqslant K; \ |v_{ulj}| \leqslant K \tag{4.6} $$

-   iv. $r$-neighbourhood

$$ N_r(i,j)=\left\{C(k,l)|\max\{|k-i|,|l-j|\} \leqslant r, 1 \leqslant k \leqslant M; 1 \leqslant l \leqslant N\right\} $$
$$ (1 \leqslant i \leqslant M; 1 \leqslant j \leqslant N) \tag{4.7} $$

where $(i,j)$ and $(k,l)$ refer to the cell $C(i,j)$ at the $i$th row and $j$th column and the cell $C(k,l)$ at the $k$th row and $l$th column, respectively; $r$ is a positive integer (in our case $r = 1$ by considering directly connected cells); $C_x$ is the capacitance of linear capacitors, $R_x$ is the resistance of linear resistors, $I_{lj}$ is the current of current sources, $A(i, j; k, l)$ is the output feedback operator

![](img/6554116edbb19a8210b75a29243fd6ec_53_0.png)

FIGURE 4.2 Bio-heat conduction on a 2D rectangular grid.

defining cell interactions with its adjacent neighbours and $B(i,j,k;l)$ is the input control operator defining the impact of input on the cell state; $v_{u ij}(t)$, $v_{xij}(t)$ and $v_{yij}(t)$ are the input, state, and output of cell $C(i, j)$ at time $t$.

When there is no cell input, Eq. (4.4) can be written as

$$ C_x \frac{d v_{xij}(t)}{dt} = -\frac{1}{R_x} v_{xij}(t) + \sum_{C(k,l) \in N_r(i,j)} A(i,j;k,l) v_{y kl}(t) + I_{ij} \quad (4.8) $$

which becomes an autonomous CNN [37].

### 4.3.2 CNN Formulation of Bio-Heat Transfer on 2D Grids

#### 4.3.2.1 2D Regular Grids

As illustrated in Figure 4.2, the CNN formulation of bio-heat transfer on a 2D rectangular grid is achieved by using FDM to discretise the Pennes bio-heat transfer equation in the spatial domain, yielding:

$$ \begin{aligned} \rho_{i,j} C_{i,j} \frac{\partial T_{i,j}(t)}{\partial t} &= - \bigg( \frac{2 k_{i,j}}{\Delta u_{i-1} \Delta u_i} + \frac{2 k_{i,j}}{\Delta v_{j-1} \Delta v_j} + w_{b,i,j} C_{b,i,j} \bigg) T_{i,j}(t) \\ &+ \frac{2 k_{i+1,j} T_{i+1,j}(t)}{\Delta u_i(\Delta u_{i-1} + \Delta u_i)} + \frac{2 k_{i-1,j} T_{i-1,j}(t)}{\Delta u_{i-1}(\Delta u_{i-1} + \Delta u_i)} + \frac{2 k_{i,j+1} T_{i,j+1}(t)}{\Delta v_j(\Delta v_{j-1} + \Delta v_j)} \\ &+ \frac{2 k_{i,j-1} T_{i,j-1}(t)}{\Delta v_{j-1}(\Delta v_{j-1} + \Delta v_j)} + w_{b,i,j} C_{b,i,j} T_{a,i,j} + Q_{i,j} + H_{i,j} \quad (4.9) \end{aligned} $$

where the subscript $i,j$ indicates the respective quantities at the grid point $i,j$ associated with the cell $C(i,j)$, and $\Delta\boldsymbol{u}_{i-1}=\|\overrightarrow{\textbf{P}_{i-1,j}\overrightarrow{\textbf{P}_{i,j}}}\|$, $\Delta\boldsymbol{u}_{i}=\|\overrightarrow{\textbf{P}_{i,j}\overrightarrow{\textbf{P}_{i+1,j}}}\|$, $\Delta\boldsymbol{v}_{j-1}=\|\overrightarrow{\textbf{P}_{i,j-1}\overrightarrow{\textbf{P}_{i,j}}}\|$, and $\Delta\boldsymbol{v}_{j}=\|\overrightarrow{\textbf{P}_{i,j}\overrightarrow{\textbf{P}_{i,j+1}}}\|$, where $\|\overrightarrow{\bullet}\|$ denotes the magnitude of a vector, and $\textbf{P}_{i,j}(x_{i,j}, y_{i,j}, z_{i,j})$ denotes the position of the grid point $i,j$. It can be seen that Eqs. (4.8) and (4.9) are remarkably similar; therefore, the discrete form of the Pennes bio-heat transfer equation (Eq. 4.9) is embedded into the autonomous CNN (Eq. 4.8) by associating the following parameters:

$$C_{x}=\rho_{i,j}C_{i,j};\ v_{xij}(t)=T_{i,j}(t);\ I_{ij}=w_{b,i,j}C_{b,i,j}T_{a,i,j}+Q_{i,j}+H_{i,j}$$

$$A = \left\{\begin{matrix}0 & \frac{2k_{i,j+1}}{\Delta v_{j}\left(\Delta v_{j-1}+\Delta v_{j}\right)} \\ \frac{2k_{i-1,j}}{\Delta u_{i-1}\left(\Delta u_{i-1}+\Delta u_{i}\right)} & -\left(\frac{2k_{i,j}}{\Delta u_{i-1}\Delta u_{i}}+\frac{2k_{i,j}}{\Delta v_{j-1}\Delta v_{j}}+w_{b,i,j}C_{b,i,j}\right) & \frac{1}{R_{x}} \\ 0 & \frac{2k_{i,j-1}}{\Delta v_{j-1}\left(\Delta v_{j-1}+\Delta v_{j}\right)}\end{matrix}\right. + \left\{\begin{matrix}0 \\ \frac{2k_{i+1,j}}{\Delta u_{i}\left(\Delta u_{i-1}+\Delta u_{i}\right)} \\ 0\end{matrix}\right\}\tag{4.10}$$

#### 4.3.2.2 2D Irregular Grids

To establish CNN on 2D irregular grids such as a triangular grid, the original definition of “$r$-neighbourhood” is generalised from the rectangular grid to handle arbitrary grids, in which the grid points are positioned arbitrarily and linked to their neighbouring points. The $r$-neighbourhood of the cell $C(i)$ associated with the grid point $i$ is defined by

$$N_{r}(i)=\left\{C(j)|\text{links}\left(C(i),C(j)\right)\le r\right\}\tag{4.11}$$

The state of a cell in the autonomous CNN is expressed by the following equation:

$$C_{x}\frac{dv_{xi}(t)}{dt}=-\frac{1}{R_{x}}v_{xi}(t)+\sum_{c(j)\in N_{r}(i)}A(i,j)v_{yj}(t)+I_{i}\tag{4.12}$$

![](img/6554116edbb19a8210b75a29243fd6ec_55_0.png)

FIGURE 4.3 Bio-heat conduction on a 2D triangular grid. The control area $S_i$ (surrounded by the dashed lines) of the point $i$ is formed by connecting each centroid (such as **u** and **w**) of the adjacent triangles and the mid-points (such as **v**) of the adjacent edges connecting $\mathbf{P}_i$ and $\mathbf{P}_j$.

where the subscripts $i$ and $j$ denote the respective quantities at the grid points $i$ and $j$ associated with the cells $C(i)$ and $C(j)$.

To discretise the Pennes bio-heat transfer equation on the 2D irregular grids, the CNN formulation is achieved with the assistance of the concept of control area [55]. The problem domain is divided into a finite number of non-overlapping control areas with computation (grid) points located at centres, over which the conservation of energy is enforced in a discrete manner. An example of a control area of the point $i$ is illustrated in Figure 4.3, and it is formed by connecting each centroid of the triangles and the mid-points of the edges adjacent to $\mathbf{P}_i$.

For the point $i$ enclosed by the control area $S_i$, the discrete form of the Pennes bio-heat transfer equation can be expressed as

$$\int_{S_i} \left( \rho_i C_i \frac{\partial T_i(t)}{\partial t} + w_{b,i} C_{b,i} \left( T_i(t) - T_{a,i} \right) - Q_i - H_i \right) dS = \int_{S_i} \nabla \cdot \left( k_i \nabla T_i(t) \right) dS \quad (4.13)$$

Applying Gauss's divergence theorem yields

$$\begin{aligned} & \int_{S_i} \left( \rho_i C_i \frac{\partial T_i(t)}{\partial t} + w_{b,i} C_{b,i} \left( T_i(t) - T_{a,i} \right) - Q_i - H_i \right) dS \\ & = \int_{\partial S_i} k_i \nabla T_i(t) \cdot \mathbf{n} \, dl = \int_{\partial S_i} \left. \left( k_i \frac{\partial T(t)}{\partial \mathbf{n}} \right) \right|_i dl \quad (4.14) \end{aligned}$$
