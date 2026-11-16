
kernel density estimation (KDE) can be used [127]. After estimating the distribution of the decision statistic (e.g., Q and $T^2$), the threshold can be computed nonparametrically as the $(1-\alpha)$th quantile of this estimated distribution.

As we explained in Sect. 2.5.1, in projection-based monitoring approaches, the PC and residual subspaces are frequently inspected via the Shewhart-type monitoring chart (i.e., Q and $T^2$) for detecting abnormal changes. However, these schemes are designed to detect large faults but they fail to detect small changes. Alternatively, other types of multivariate schemes, such as MEWMA and MCUSUM, can be used [118,128]. Furthermore, the capability to detect small faults can be enhanced by amalgamating univariate schemes (CUSUM or EWMA) with Q and $T^2$, but it needs a good selection of the parameters of CUSUM or EWMA schemes [129]. Instead of the conventional multivariate monitoring schemes with projection based methods, other approaches exploit the sensitivity of distribution-based schemes, such as KLD [130,92,131,89] and HD [102,132], to detect incipient faults.

## 2.5.2 Fault isolation

Today engineering and environmental processes have become far more complex due to advances in technology. Multiple relevant process variables require to be supervised all together at the same time. Once a fault is detected, fault isolation (attribution) is required to ensure safe operation of the process and to avoid the risk of process shutdowns by making the necessary correction before the fault propagates and contaminates the process [133]. Isolating the detected faults, which is necessary for a systematic diagnosis and maintenance, is not an easy task because of the large number of variables that need to be inspected. The aim of fault isolation is finding process variables that contributed to the abnormal change, thus allowing the operators to concentrate only on the subsystem where the fault happened. Accordingly, fault isolation is crucial to significantly reduce the losses in profitability and to facilitate maintenance tasks. In this section, two basic tools for fault isolation, namely latent variable contribution plots and RadViz visualizer, are presented. In Chap. 3, more details about fault attribution in multivariate statistical monitoring will be presented.

### 2.5.2.1 Fault isolation using modified contribution plots

The underlying intuitive idea behind the contribution plot is to find the process variables with large contributions that are potential indicators to locate the source of abnormalities. Hence, the contribution plot provides relevant information to operators for enabling efficient fault diagnosis by focusing their analysis on a small number of variables which may be the cause of the detected anomalies [134,21,135,136].

Several fault isolation techniques are developed within multivariate statistical monitoring approaches, including contributions to the $T^2$ statistic, contributions to SPE, and contribution to individual scores, which are the most popular approaches in fault diagnosis [21,137,138]. The essence of these contribution-based approaches is that the variables with faults are expected to give significant contributions to the fault detection statistics. Most of the contribution-based fault isolation techniques have been summarized and generalized in [136]. However, this approach investigates the process variables separately without considering the correlation between them, which make it inappropriate for isolating faults in multiple variables that simultaneously participate in the fault occurrence. Other researchers [139] use the GLR test for fault isolation, which can also provide an estimate of the size of the isolated sensor fault. In [140], a reconstruction-based method is introduced to identify single and multiple faults. Another approach combining the desirable benefits of the contribution analysis and the reconstruction-based approach has been designed to further enhance the fault isolation. However, the reconstruction-based contribution approach is suitable only for identifying unidimensional faults with relatively large magnitudes. Recently, in [141], an approach based on exponential smoothing reconstruction has been designed for isolation of incipient faults. Next, we will review two of the most commonly used techniques in fault isolation – the contribution methods.

### $T^2$ contribution approach

The $T^2$ contribution-based approaches have been broadly applied in the industry to identify the process variables that significantly contribute to the fault detected by the $T^2$ monitoring scheme. The essence of this approach is based on computing the gradient of $T^2$ with regards to every variable. From Eq. (2.67) the gradient of the $T^2$ statistic provides the sensitivity to the variable vector $\mathbf{x}$ as

$$\mathbf{S}_{T^2} = \frac{\partial (T^2)}{\partial \mathbf{x}} = 2\mathbf{P}(\mathbf{P}^T \sum_{\mathbf{x}} \mathbf{P})^{-1} \mathbf{P}^T \mathbf{x} = 2\mathbf{P}\Lambda_p^{-1} \mathbf{P}^T \mathbf{x}. \quad (2.71)$$

The constant “2” can be ignored and the contribution from each variable can be computed as

$$T^2 \text{cont}_{x_i} = \frac{\sum_{j=1}^k (p_j x_i)^2}{\lambda_j} = x_i^2 \sum_{j=1}^k \frac{p_j^2}{\lambda_j}. \quad (2.72)$$

If $T^2 \text{cont}_{y_i}$ is the largest among all values calculated for $i = 1, \dots, n$, then $y_i$ is indicated as a potential cause of the fault.

### SPE contribution approach

When a fault is flagged by the $Q$ scheme, the $Q$ contribution plot is usually applied to isolate the fault [135]. Let $\mathbf{E} = [\mathbf{e}_1 \mathbf{e}_2 \dots \mathbf{e}_m]$ the residual matrix and $\mathbf{e}_j$ be the $j$th columns of the residuals matrix. From (2.69), we have

$$Q_j = \mathbf{e}_j^T \mathbf{e}_j. \quad (2.73)$$

Indeed, each row of the residual matrix E, e_i is the Q contribution for this specific sample. The fractional contribution of the ith variables to the overall Q at sample instant j can be computed as

$Qcont_{x_j} = \frac{e_{ij}^2}{Q_j}.$ (2.74)

The Q contributions’ plot is helpful to identify the variable making an important contribution to SPE as the suspected source of the fault.

### 2.5.2.2 Fault diagnosis using RadViz visualizer

RadViz visualization was first proposed by Patrick Hoffman et al. in [142,143] as a multivariate data visualization tool to classify DNA sequences. Indeed, RadViz enables nonlinear projecting of high dimensional data into a 2-dimensional space and allows direct interpretation of the position of the observation in the space. It can visualize high dimensional data comprising three or more variables in a 2-dimensional space. RadViz has been widely used to visualize, interpret, and cluster high dimensional datasets like microarray data and stock exchange trends.

Generally speaking, RadViz reaps the benefits of the dimensionality-reduction methods with scatterplots, where the value of each observation could be indicated from the distance to the anchors [144]. The anchor points are the visualized variables uniformly spaced in the circumference of a unit circle. Fig. 2.9 gives an illustrative example showing the basic concept of a RadViz Visualizer. In this method, each point is linked to every anchor by a virtual spring. Here, the position of each observation in the circle is calculated based on its relative influence by the anchors (i.e., spring force for each spring). The coordinates of each observation are at the point where the system of spring forces attains equilibrium. The influence of each anchor on the projected observation is relative to the amplitude of the coordinate for that anchor. The coordinates of each observation in RadViz are computed as

$x_i = \frac{\sum_{i=1}^d x_i \cos \theta_j}{\sum_{i=1}^d x_i}, \quad (2.75)$

$y_i = \frac{\sum_{i=1}^d x_i \sin \theta_j}{\sum_{i=1}^d x_i}, \quad (2.76)$

where x_i and y_i are the coordinate of the projected observation, and θ_j denotes the angular position on the circle for the anchor j; a_i,j represents the value for dimension j for the observation i; d is the number of dimensions; and n the number of observations.

The main characteristics of RadViz method can be summarized as follows. In this 2D space, observations in the center have approximately equal dimensional
