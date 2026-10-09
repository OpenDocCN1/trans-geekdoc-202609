
![](img/456a7a56403cbb2b5f1a261793529a51_353_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_353_1.png)

Fig. 10.14: The tensor model of a human face.

Let $I_i, i=1,2,3,4$ be the numbers of dimensions of different orders. Then, we build the tensor data model of the human face image.

When the tensor model of the image data is obtained, we will analyse how to build a tensor space of a data cluster. Here, we followed high-order singular value decomposition to obtain the tensor space.

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

Here, $\varepsilon$ is the smallest error. For each tensor base, we need to obtain a new coefficient. According to the above, we have the following tensor bundle learning algorithm, which includes two steps, namely training and testing.

**Algorithm 10.3:** Training step of tensor bundle learning algorithm  
**Input:** sample set $X$, reduction dimension vector $R = \{R_1, R_2, \dots, R_K\}$.  
**Output:** tensor base set $\{A_1, A_2, \dots, A_c\}$, number of clusters $c$.  
**Process:**

- 1. Transform $X$ into tensor set $T$, and the number of orders is $K$.
- 2. Manipulate every element of $T$ by high-order singular value decomposition.
- 3. Construct tensor bases against the last order $K$ of tensor $T(c)$
    - a) Initialise $S$ to be the sub tensor;
    - b) Get the first column vectors to construct $U$;
    - c) Obtain the new $A_j$ by the mode-$j$ product of old $A_j$ and $U$;
    - d) Normalise $A_j$;
    - e) Return to step a;

**Algorithm 10.4:** Testing step of tensor bundle learning algorithm  
**Input:** Test sample $D$.  
**Output:** Cluster that $D$ belongs to.  
**Process:**

- (1) Transform $D$ into tensor representation $Z$.
- (2) Normalise $Z$.
- (3) Obtain the error $\varepsilon(c)$ of the approximate representation of $Z$.

    For each tensor space $A_c$ of the tensor bundle
    For each base tensor $A_j$ of $A_c$
        $\varepsilon(c) \leftarrow (A_j, Z)^2$
        $\varepsilon(c) \leftarrow 1 - \varepsilon(c)$
    End for
    End for

- (4) $D$ is assigned to object cluster $p$.

## 10.3.3 Classification model based on the tensor field

The first step of the data classification problem is to preprocess the data. The quality of the original data influences the classifying quality. Therefore, it is important to understand the intrinsic properties of the data [38, 39]. The intrinsic properties include the following:

- Diversity. In general, data sets come from multiple sources. On the other hand, the same property of different data sets has different names. Therefore, it is important to understand the diversity of the data.
- Redundancy. Data sets have a mass of redundant data, e.g., a data set may have repeatability.
- High dimension. In general, the classification of data sets exists in high-dimensional space.

| No. | User | Item | Tag | Weight |
|---|---|---|---|---|
| 1 | U1 | I1 | T1 | 1 |
| 2 | U2 | I2 | T2 | 1 |
| 3 | U3 | I3 | T3 | 1 |
| 4 | U4 | I4 | T4 | 1 |

| No. | User | Item | Tag | Weight |
|---|---|---|---|---|
| 1 | U1 | I1 | T1 | 0.72 |
| 2 | U2 | I1 | T1 | 1.17 |
| 3 | U3 | I2 | T2 | 0.72 |
| 4 | U4 | I3 | T3 | 1 |
| 5 | U5 | I2 | T2 | 0.44 |

The classification process has two main steps. First, we build a classification model based on the same features of a group of objects in the data set. We then map the data term into a class by using the model. For building a classification model, we divide the data set X into two parts; one part is called the training sample set $X_{tr}$, and the other part is called the testing sample set $X_{te}$. All the samples have the same cluster identification. The classification algorithm constructs the classification model by analysing $X_{tr}$. We test the classification precision of the model by using $X_{te}$. If the precision is sufficient, we use the corresponding algorithm to classify the data set (Tables 10.1 and 10.2).

On the basis of the above process, we have the classification model of a tensor field. Its basic principles include the following:

- The invariance principle of the tensor. A tensor can provide a uniform representation in different coordinate systems based on its tensor characteristics [23, 24].
- Rich expression ability. A high-order tensor can represent richer information. Most importantly, we can find the hidden information of the data by tensor reconstruction.

The data discussed in this chapter belongs to the same type. The data type usually includes some characters. There are some close relationships between these characters, which are simply operated. We use the tensor method to analyse these relationships and reflect the internal connection between the data objects.

$X$ is a data sample and represented by its neighbourhoods $\xi_X$ in the high-dimensional space. Based on the above analysis, we can obtain the category of $X$ by using $\xi_X$. Here, $\xi_X$ describes the environmental information of $X$. Every point has a corresponding tensor in the high-dimensional linear space, which constructs a tensor field model (Figure 10.15).

![](img/456a7a56403cbb2b5f1a261793529a51_356_0.png)

Fig. 10.15: The tensor model.

![](img/456a7a56403cbb2b5f1a261793529a51_356_1.png)

Fig. 10.16: The tensor model which is used to describe the interaction between different points.

Tensor reconstruction is useful for showing the inner rules of the data [14, 21]. If we decompose and reconstruct all the tensors in the tensor space, we can obtain the distribution rule of the high-dimensional space. There is an interaction between point $X$ and $\xi_{X}$ (Figure 10.16). However, this type of interaction is a local element, which is determined by the data distribution.

The block processing of data includes two important factors: dimensionality and locality.

- Dimensionality. In the tensor field methods, the dimension of the data corresponds to the order of the tensor. Therefore, the dimension of the order of each tensor is determined by each dimension of the original data. In general, the dimension is larger. Then, the tensor has the high-dimensional characteristic. The block processing of data would reduce the dimension of the tensor and increase the calculation efficiency.
- Locality. The relationship between close points is intimate. We can find this characteristic from the geometric structure characteristics. If we only processed all the
