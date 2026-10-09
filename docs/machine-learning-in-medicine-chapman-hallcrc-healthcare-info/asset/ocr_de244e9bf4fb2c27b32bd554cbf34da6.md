fast computation of non-linear partial differential equations [29]. Hence, in analogy to the heat transfer equation with a given input of heat source that governs the non-linear bio-heat transfer behaviour in biological soft tissues, the presented CNN is formulated as the global propagation of a given current source (analogy to the heat source) through the locally interconnected activity of non-linear cell dynamics.

Consider a 2D CNN made of a rectangular computing array of M × N cells in M rows and N columns, the dynamics of CNN are given by [30]:

+   i. Cell state $v_{xj}(t)$

```
$$ C_x\frac{dv_{xj}(t)}{dt}=-\frac{1}{R_x}v_{xj}(t)+\sum_{C(k,l)\in N_r(i,j)}A(i,j;k,l)v_{ykl}(t) $$
$$ +\sum_{C(k,l)\in N_r(i,j)}B(i,j;k,l)v_{ukl}(t)+I_{lj} \tag{4.4} $$
```

+   ii. Cell output $v_{yij}(t)$

```
$$ v_{yij}(t)=\frac{1}{2}\left(|v_{xij}(t)+K|-|v_{xij}(t)-K|\right), K \geqslant 1 \tag{4.5} $$
```

+   iii. Constraint conditions

```
$$ v_{xij}(0) \leqslant K; \ |v_{ulj}| \leqslant K \tag{4.6} $$
```

+   iv. $r$-neighbourhood

```
$$ N_r(i,j)=\left\{C(k,l)|\max\{|k-i|,|l-j|\} \leqslant r, 1 \leqslant k \leqslant M; 1 \leqslant l \leqslant N\right\} $$
$$ (1 \leqslant i \leqslant M; 1 \leqslant j \leqslant N) \tag{4.7} $$
```

where $(i,j)$ and $(k,l)$ refer to the cell $C(i,j)$ at the $i$th row and $j$th column and the cell $C(k,l)$ at the $k$th row and $l$th column, respectively; $r$ is a positive integer (in our case $r = 1$ by considering directly connected cells); $C_x$ is the capacitance of linear capacitors, $R_x$ is the resistance of linear resistors, $I_{lj}$ is the current of current sources, $A(i, j; k, l)$ is the output feedback operator