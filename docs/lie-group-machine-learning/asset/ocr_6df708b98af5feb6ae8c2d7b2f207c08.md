![](bbox=[0.18, 0.07, 0.65, 0.18])

The classifier category algorithm is obtained by the above algorithm, as shown in Figure 15.10.

For the learning algorithm $\mathcal{L}$ of Algorithm 15.1, we can use linear and nonlinear methods. When using a linear method, we can get the mapping $l$ of sample object $S$ to weighted object $W$ by using the Lagrange morphism.

$l: S \rightarrow W$. This morphism can be obtained by maximising

$$L(\alpha)=\sum_{i=1}^{l}\alpha_{i}-\frac{1}{2}\sum_{i=1}^{l}\sum_{j=1}^{l}y_{i}y_{j}\alpha_{i}\alpha_{j}\left(x_{i}\cdot x_{j}\right)\ .$$

For hyperplane morphism $k: X \cdot W \rightarrow D$, the morphism process can be represented as $w^{T}x+b=0$, where $D$ is a hyperplane object. At the same time, the maximum edge distance object $M$ is obtained. Thus, morphism $d$ can be mapped to objects $Y$, and the process can be accomplished by the inequality $y_{i}D(x_{k})/\|w\| \geq \delta$. Figure 15.11 shows the intuitive emission process.

![](bbox=[0.17, 0.63, 0.82, 0.74])

In general, three methods are used to find the relation morphism $g$. The detailed process can be found in the literature [20]. The first one uses majority voting to mark each morphism $f_{i}$ and count it. If the number of votes of object $f_{i}$ is assumed to be $N$, then $N_{j}=(i\mid f_{i}(x)$ belongs_to_class $j)$. Thus,

$$f(x)=g(f_{1}(x), f_{2}(x), \dots, f_{g}(x))=\underset{j}{\operatorname{arg}\operatorname{max}}(N_{j})\ .$$

Each $N_{j}$ corresponds to a morphism $f_{i}$.

The second method is a weighted voting method, which calculates a weighting factor $\beta_{i}$ for each morphism $f_{i}$. This weight is determined by the accuracy of the classifier’s morphism, and the associated morphism $g$ can be obtained:

$$f(x)=g(f_{1}(x), f_{2}(x), \dots, f_{q}(x))=\sum_{i=1}^{q}\beta_{i}f_{i}(x)\ .$$