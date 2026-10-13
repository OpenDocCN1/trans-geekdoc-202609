

## 凸函数定义

函数 $f: \mathcal{X} \subseteq \mathbb{R}^l \mapsto \mathbb{R}$ 被称为**凸函数**，如果 $\mathcal{X}$ 是凸集，且对任意 $\mathbf{x}_1, \mathbf{x}_2 \in \mathcal{X}$，以下不等式成立：

```
f(\lambda \mathbf{x}_1 + (1-\lambda)\mathbf{x}_2) \le \lambda f(\mathbf{x}_1) + (1-\lambda)f(\mathbf{x}_2) \quad (8.2)
```

其中 $\lambda \in [0, 1]$。

如果当 $\lambda \in (0, 1)$ 且 $\mathbf{x}_1 \neq \mathbf{x}_2$ 时，上述不等式取严格不等号，则该函数称为**严格凸函数**。式 (8.2) 的几何解释是：连接点 $(\mathbf{x}_1, f(\mathbf{x}_1))$ 和 $(\mathbf{x}_2, f(\mathbf{x}_2))$ 的线段位于 $f(\mathbf{x})$ 的图像之上（如图 8.3 所示）。若函数 $-f$ 是凸（严格凸）的，则称该函数为**凹（严格凹）函数**。下面陈述三个重要定理。

## 定理 8.1：一阶凸性条件

**设** $\mathcal{X} \subseteq \mathbb{R}^l$ **为凸集，且** $f: \mathcal{X} \mapsto \mathbb{R}$ **为可微函数。则 $f$ 是凸函数的充要条件是** $\forall \mathbf{x}, \mathbf{y} \in \mathcal{X}$，

```
f(\mathbf{y}) \ge f(\mathbf{x}) + \nabla^T f(\mathbf{x})(\mathbf{y} - \mathbf{x}) \quad (8.3)
```

该定理的证明见习题 [8.3](#Chp008_343-416_B9780443292385000147.xhtml#o0045)。该定理可推广至不可微凸函数，将在第 [8.10](#Chp008_343-416_B9780443292385000147.xhtml#s0090) 节讨论。

![图 8.3 连接点 $(x_1,f(x_1))$ 和 $(x_2,f(x_2))$ 的线段位于 $f(x)$ 的图像之上。阴影区域对应函数的超图。](images/B9780443292385000147/gr003.jpg)

图 8.4 说明了该定理的几何解释。这意味着凸函数的图像位于仿射函数

$$g: \mathbf{y} \mapsto \nabla^T f(\mathbf{x})(\mathbf{y} - \mathbf{x}) + f(\mathbf{x})$$

的图像之上，该仿射函数定义了图像在点 $(\mathbf{x}, f(\mathbf{x}))$ 处的切超平面。

![图 8.4 凸函数的图像位于其图像上任意一点的切平面之上。](images/B9780443292385000147/gr004.jpg)

## 定理 8.2：二阶凸性条件

**设** $\mathcal{X} \subseteq \mathbb{R}^l$ **为凸集。则二阶可微函数** $f: \mathcal{X} \mapsto \mathbb{R}$ **是凸（严格凸）的充要条件是海森矩阵为半正定（正定）。**

