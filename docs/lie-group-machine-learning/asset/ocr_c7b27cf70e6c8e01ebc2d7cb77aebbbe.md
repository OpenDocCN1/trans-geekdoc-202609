![](bbox=[0.18, 0.08, 0.58, 0.15])

![](bbox=[0.6, 0.06, 0.9, 0.2])

Fig. 10.14: The tensor model of a human face.

I_{4} are the numbers of dimensions of different orders. Then, we build the tensor data model of the human face image.

When the tensor model of the image data is obtained, we will analyse how to build a tensor space of a data cluster. Here, we followed high-order singular value decompo-sition to obtain the tensor space.

First, for each human tensor data, we perform singular value decomposition, and we have

$$T_{p}=S_{p \times 1} U^{(1)} \times_{2} U^{(2)} \times_{3} U^{(3)} \times_{4} U^{(4)} \cdot \quad \quad \quad \quad \quad \quad \quad \quad(10.39)$$

Then, we convert it to:

$$T_{p}=\sum_{f=1}^{i_{u}} B_{f} \times_{N} w_{f} \cdot \quad \quad \quad \quad \quad \quad \quad \quad \quad(10.40)$$

Here, $B_{f}=S_{f} \times U^{(1)} \times U^{(2)} \times U^{(3)}$, where $S_{f}$ is the $f$ sub-tensor of $S_{p}$ [21, 22] and $T_{i_{u}=f}$ is the $f$ sub-tensor of $T$. Thus, we have

$$T_{i_{u}=f}=\sum_{\nu=1}^{i_{u}} \sigma_{\nu} B_{\nu} \cdot \quad \quad \quad \quad \quad \quad \quad \quad(10.41)$$

The relationship between $\sigma_{\nu}$ and $w_{f}$ is $w_{f}=\left(\sigma_{1}, \sigma_{2}, \ldots, \sigma_{i_{u}}\right) .$

From the above, obviously, each colour human face $T_{i_{u}=f}$ is a linear combination of $B_{f}$ with the coefficient $w_{f}$. These $B_{f}$ values can represent the tensor basements of the $p$-th human face. Furthermore it can confirm a tensor space of a colour human face image.

Finally, in the test phase, we need to confirm the tensor space, which includes the sample. To be specific, we need to confirm the coefficients $w_{f}=\left(\sigma_{1}, \sigma_{2}, \ldots, \sigma_{F}\right)$ and make $\sigma_{1} B_{1}+\sigma_{2} B_{2}+\cdots+\sigma_{F} B_{F}$ equal to it. We have the following objective function.

$$\begin{array}{c} \underset{\sigma_{i}}{\operatorname{min}\|E-\sum_{i=1}^{F}\sigma_{i} B_{i}\|} \end{array} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad(10.42)$$

To solve this function is a least-squares problem [12]. We have:

$$\begin{aligned} \epsilon=\left\|E-\sum_{i=1}^{F} \sigma_{i} B_{i}\right\|^{2}=\left\langle E-\sum_{i=1}^{F} \sigma_{i} B_{i}, E-\sum_{i=1}^{F} \sigma_{i} B_{i}\right\rangle=\langle E, E\rangle-\sum_{i=1}^{F}\langle E, B_{i}\rangle^{2}=1-\sum_{i=1}^{F}\langle E, B_{i}\rangle^{2}. \end{aligned}$$