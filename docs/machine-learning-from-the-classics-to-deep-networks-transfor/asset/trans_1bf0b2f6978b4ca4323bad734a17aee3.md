
# 5.7 复值情况

在第 [4.4](#Chp004_119-175_B978044329238500010X.xhtml) 节中，当

$$y[n] \in \mathbb{C} \text{ and } \mathbf{x}[n] \in \mathbb{C}^{(l)},$$

时，引入了估计任务的*广义线性*公式来处理不满足循环性条件的复值数据。广义线性估计器的输出由下式给出

$$\widehat{y}_n = \mathbf{\varphi}^{H}\widetilde{\mathbf{x}}_n,$$

其中

$$\mathbf{\varphi} := \begin{bmatrix} \mathbf{\theta} \\ \mathbf{v} \end{bmatrix} \quad \text{and} \quad \widetilde{\mathbf{x}}_n = \begin{bmatrix} \mathbf{x}_n \\ \mathbf{x}_n^{\ast} \end{bmatrix},$$

$\mathbf{\theta}, \mathbf{v} \in \mathbb{C}^{(l)}$。MSE 代价函数为
