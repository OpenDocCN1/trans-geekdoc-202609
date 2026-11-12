
segmentation applications where the feature map is integrated by multiple characteristics, such as those described by histograms of two dimensions. For this reason, the MS segmentation algorithms consider only the use of grayscale values (one-dimensional data) with other computational techniques [43].

Under techniques based on one-dimensional and two-dimensional schemes, important details in images cannot be correctly segmented. In such conditions, the use of more pixel characteristics allows the classification of fine image details, since the possibilities of associating pixel characteristics increase. However, the employment of more characteristics (dimensions) in the density map expands the computational overload of the MS approach significantly. For this reason, the diminution of computational time in the MS technique permits it to expand its segmentation capabilities through the handling of multi-dimensional feature maps.

One widely used technique to diminish the investment cost of a computational approach is the consideration of only a random subgroup of elements from all available data. The idea behind it is to examine the operation of the process by using a very small, representative number of data instead of the whole information. After that, the partially produced results are extrapolated to involve information not used with the approach. Under such conditions, the reduction of the CC is determined by the portion of elements used in the operation of the approach in comparison with the total available data. Therefore, to obtain lower CCs, the number of used elements needs to be reduced until the approach presents a bad performance in terms as it has been operated with the complete dataset. This methodology has been considered in several schemes, such as the random sample consensus (RANSAC) [51] or the random Hough transform (RHT) [52], among others.

In this chapter, a segmentation method for intensity images based on the MS (MS) method [44] is explained. In this chapter, it is considered a three-dimensional density map that involves the information of the intensity value, the non-local mean [53], and the local variance of each pixel from the image. In the process of MS, it first generates a density map. This map is produced through the use of an Epanechnikov kernel function [43], which allows us to model a density map accurately, even with a few data. Then, considering as an initial point the location of each feature position, a gradient ascent technique is employed to detect the local maxima, which corresponds to its cluster center. To reduce the CC provoked by the use of a three-dimensional map, by using schemes that have been successfully employed to avoid expensive computations [51,52], the MS scheme is operated considering only a representative group of elements randomly sampled from the complete image data [50]. For this purpose, two sets of data are produced: operative elements (the reduced data employed in the MS operation) and inactive elements (the remainder of the available data). Therefore, the results obtained with the operative set of elements are generalized to include the not-used data [54]. With this mechanism, the MS method is able to segment complex regions, such as texturized elements and objects, under different illumination conditions.

## 5.2 Kernel Density Estimation (KDE) and the Mean-Shift Method

There is a complete association between KDE and clustering. The objective of KDE is to build the probability function of data distribution by analyzing its point concentration, which could also be employed for classification purposes. KDE represents a set of nonparametric schemes that do not consider any particular probability approach to modeling the probability density function. Instead, KDE computes the probability density directly for every element in the dataset.

MS [44] is a computational method that has generally been considered for clustering. In its operation, each element x contained in the feature space, it is assigned as a cluster Ci, whose central point xi* represents the local maximum of the density map. Accordingly, beginning at location x, a new position is determined following the orientation of the highest increment of the feature map until the nearest local maximal concentration xi* has been reached. The computation process of the MS consists of two stages. As a first step, the construction of a density map is achieved. This process is carried out through the use of a KDE scheme. Then, a search process that considers the gradient ascent as a basis is applied to detect the high local concentration points (local maxima) over the density map [55].

### 5.2.1 Concentration Map Generation

The nonparametric KDE is the most useful approach to generating an unknown density feature map. In the operation of a KDE scheme, the concentration in every location is estimated by using kernel functions that consider the collection of weighted near elements. A kernel model K is characterized as an asymmetric, non-negative kernel element K, such as it is defined in Equation 5.1.

$$ K(\mathbf{x}) \ge 0; K(-\mathbf{x}) = K(\mathbf{x}); \int K(\mathbf{x})d\mathbf{x} = 1 $$

Considering a group of n characteristics {x1, x2,..., xn}, the density function \hat{f}(\mathbf{x}), can be determined in terms of K, as shown in Equation 5.2.

$$ \hat{f}(\mathbf{x}) = \frac{1}{nh} \sum_{i=1}^n K\left(\frac{\mathbf{x}-\mathbf{x}_i}{h}\right) $$

where h corresponds to the support region of K.

The simplest kernel model is the discrete kernel function $K_D$, which calculates the respective concentration in a specific location by counting the number of data elements within a window of size $h$. $K_D$ is defined in Equation 5.3.

$$ K_D \left( \frac{\mathbf{x}-\mathbf{x}_i}{h} \right) = \begin{cases} 1 & \text{if } \left( \frac{\mathbf{x}-\mathbf{x}_i}{h} \right) \le h \\ 0 & \text{Otherwise} \end{cases} $$ (5.3)

Figure 5.1 presents the KDE considering the discrete kernel $K_D$ for several magnitudes of the value $h$ over a one-dimensional dataset. In the figure, the stack height represents the frequency at which the data are concentrated. As it is indicated in Figure 5.1a, if $h$ presents a small value, the resulting probability density shows several local maximal points. Nevertheless, as the value of $h$ increases from 0.25 to 2, the number of modes is reduced until $h$ gets high enough to produce a distribution with only one mode (unimodal).

Even though different kernel models have been used in KDE methods, the Gaussian function $K_G(x)$ represents the most popular kernel scheme in KDE approaches. The Gaussian or normal function is characterized by Equation 5.4, whereas its representation is illustrated in Figure 5.2.

$$ K_G ( x ) = \left( \frac{1}{\sqrt{2\pi}} \right) e^{\left( \frac{-x^2}{2h} \right)} $$ (5.4)

![](img/fa2d7e8bd88af7122f764c748b0a3723_191_0.png)

**FIGURE 5.1** Probability density estimation by using the discrete kernel $K_D$ by using different values of $h$. (a) $h = 0.5$, (b) $h = 1.0$, and (c) $h = 2.0$.

![](img/fa2d7e8bd88af7122f764c748b0a3723_192_0.png)

**FIGURE 5.2**
Distinct kernel functions: Normal kernel \( K_G(x) \) and Epanechnikov kernel \( K_E(x) \).

On the other hand, the Epanechnikov kernel \( K_E(x) \) (see Figure 5.2) [43] is an alternative for KDE due to its interesting properties. \( K_E(x) \) is defined in Equation 5.5.

$$ K_E(x) = \begin{cases} \left( \frac{3}{4} \right)(1 - x^2) & \text{if } |x| \le 1 \\ 0 & \text{otherwise} \end{cases} \quad (5.5) $$

A generic form to assess the modeling accuracy of a kernel scheme is the evaluation of the mean-squared error (MSE) generated between the density feature map \( f(\mathbf{x}) \) to be modeled and the estimated density \( \hat{f}(\mathbf{x}) \) obtained for a determined kernel formulation. This modeling precision can be computed using Equation 5.6.

$$ MSE\left( \hat{f}(\mathbf{x}) \right) = \frac{1}{n} \sum_{i=1}^n \left( \hat{f}(\mathbf{x}_i) - f(\mathbf{x}_i) \right)^2 \quad (5.6) $$

Under such conditions, the Epanechnikov kernel \( K_E(x) \) exhibits the best representation accuracy with regard to the \( MSE \) index since its model \( K_E(x) \), according to a different analysis reported in the literature [40,42], it delivers the functional solution that produces the minimal \( MSE \) value corresponding to Equation 5.6. This behavior persists even when there is a very limited amount of data available for computing the density of the feature map [40].
