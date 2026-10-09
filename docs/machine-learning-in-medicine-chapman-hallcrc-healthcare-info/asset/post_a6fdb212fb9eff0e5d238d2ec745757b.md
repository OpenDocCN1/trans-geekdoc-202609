
It is important to estimate the probability distributions of the signals individually. Said signals associate each mode from *F*. *Fs* is closely approximated with LCDG, opposing the conventional mixture of Gaussians, one per region, or slightly more flexible mixtures involving other simple distributions, one per region. Sub-models, each representing a dominant mode, are the result of the division of the LCDG image [19–21].

A discrete Gaussian distribution is defined on the set of integers (gray levels) *Q* = {0, 1, ..., *Q* − 1} by the probability mass function

$$\psi(q|\theta) = \begin{cases} \Phi(0.5), & q = 0 \\ \Phi(q + 0.5) - \Phi(q - 0.5) & 1 \leq q < Q - 1 \\ 1 - \Phi(q - 0.5), & q = Q - 1, \end{cases}$$

where the parameter $\theta = (\mu, \sigma)$, and $\Phi$ is the CDF of a normal distribution with mean $\mu$ and variance $\sigma^2$. Then the LCDG with $C_p$ positive components and $C_n$ negative components, such that $C_p \geq K$, has the probability mass function

$$p_{\mathbf{w},\Theta}(q) = \sum_{r=1}^{C_p} w_{p,r} \psi(q | \theta_{p,r}) - \sum_{l=1}^{C_n} w_{n,l} \psi(q | \theta_{n,l}) \tag{13.1}$$

The weights $\mathbf{w} = (w_{p,1}, \dots, w_{p,\ C_p},\ w_{n,1}, \dots, w_{n,\ C_n})$ are restricted to be all non-negative and to satisfy

$$\sum_{r=1}^{C_p} w_{p,r} - \sum_{l=1}^{C_n} w_{n,l} = 1 \tag{13.2}$$

In general, for a probability to be valid, it has to be non-negative: $p_{\mathbf{w}} \oplus(q) \geq 0$ for all $q \in \mathbf{Q}$. This implies that a valid subset of all the LCDGs in (13.1) only uses the probability distributions. This subset can however have negative components, $p_{\mathbf{w}} \oplus < 0$ for some $q \in \mathbf{Q}$.

It is the aim of this study to find a *K*-modal probability model, which closely approximates the marginal distribution of gray level, which is not known. If *F* is the Bayesian estimate of *F*$_s$, the former can be described as follows [22]: $f(q) = (\mathbb{R}[f_s(q) + 1])/(|\mathbb{R}| + Q)$. The model to be devised should work on increasing the expected log-likelihood of the statistically independent empirical data to its maximum limits, along with its other parameters:

$$L(\mathbf{w}, \Theta) = \sum_{q \in \mathbf{Q}} f(q) \log p_{\mathbf{w},\Theta}(q) \tag{13.3}$$

The algorithm used in segmentation in its entirety is as follows [16].

1. For each slice \( \mathbf{X_s} \), \( s = 1,\dots, S \):
    - a. The first is to gather the marginal empirical probability distribution \( F_s \), which represents gray levels.
    - b. Pinpoint a starting LCDG model, which is close to \( F_s \). This is done with the use of the initialization algorithm, which can approximate the values of \( C_p - K, C_n \), and the parameters \( \mathbf{w}, \boldsymbol{\Theta} \) (marking weights, means, and variances) of both negative and positive discrete Gaussians (DG).
    - c. Fix \( C_p \) and \( C_n \), use the modified EM algorithm to refine the LCDG-model by manipulating other parameters.
    - d. Make \( K \) submodels by separating the final LCDG model. There would be a submodel for each dominant mode. This is done by minimizing the misclassification predicted errors and selecting the LCDG-submodel that has the greatest average value (corresponding to the pixels with the highest brightness) to be the model of the wanted vasculature.
    - e. Use intensity threshold \( t \) to extract the voxels of the blood vessels in the MRA slice, which separates their LCDG-submodel from the background.

2. Remove the artifacts from the extracted voxels whole set with the help of a connection filter, which chooses a system to construct by a 3D growing algorithm, which comes in the form of the greatest connected tree [23]. Algorithm 13.1 summarizes the adopted segmentation approach:

### **Algorithm 13.1: Main Steps of the Segmentation Approach**

For each slice \( \mathbf{X_s} \), the following steps were completed:

1. **LCDG Initialization**:
    - Find the marginal empirical probability distribution of gray levels \( \boldsymbol{F_s} \).
    - Estimate \( C_p - K, C_n, \boldsymbol{W} \), and \( \boldsymbol{\Theta} \) of the positive and negative DGs.
    - Find the initial LCDG-model that approximates \( \boldsymbol{F_s} \).

2. **LCDG Refinement**:
    - Fixing $C_p$ and $C_n$, refine the LCDG-model with the modified EM algorithm by manipulating other parameters.

3. **Initial Segmentation**:
    - Divide the final LCDG-model into $K$ submodels by minimizing the expected errors of misclassification.
    - Select the LCDG-submodel that has the largest mean value to be the model of the wanted vasculature.
    - Use the intensity threshold $t$ to extract the voxels of the blood vessels in the MRA slice, separating their LCDG-submodel from the background.

4. **Final Segmentation**:
    - Remove the artifacts from the extracted voxels whole set with a connection filter, which chooses the greatest connected tree system built by a 3D growing algorithm.

This procedure aims to decipher each MRA slice's threshold, which will enable the complete extraction of the bright blood vessels while removing the darker unwanted tissue while also separating surrounding non-vasculature tissue that may be of similar brightness and along the same boundaries. When step 1b is initialized, the LCDG with the non-negative beginning probabilities $p_{w, \ o}(q)$ is created. In step 1c, a refinement takes place, increasing the likelihood, but still, probabilities are non-negative. In Ref. [16], experiments showed that the opposite situations never took place.

Automatic segmentation's accuracy is evaluated by calculating total error compared to the ground truths. For evaluation purposes, segmentations are measured, including both true positive (TP) and true negative (TN), as well as false positive (FP) and false negative (FN).

In Figure 13.3, if C is the segmented region, G is the ground truth, and R represents the entire image frame, then the TP= $|C \cap G|$, TN= $|R - C \cup G|$, FP= $|C - C \cap G|$, and FN= $|G - C \cap G|$. The total error $\epsilon$ is given in Ref. [24] as $\epsilon=(\mathrm{FN}+\mathrm{FP}) /(\mathrm{TP}+\mathrm{FN})=(\mathrm{FN}+\mathrm{FP}) / \mathrm{G}$.

**Matching of Voxels**: Voxels are defined as an array of volume elements, which constitute a notional 3D space. A 3D affine registration is used to handle the pose, orientation, and the data spacing changes or other scanning parameter changes between day 0 and day 700 [25]. In this step, the determined Euclidian radii are converted into diameter values. The output is then converted into a distance map.

![](img/6554116edbb19a8210b75a29243fd6ec_254_0.png)

FIGURE 13.3 Illustration of segmentation accuracy and errors of the proposed automatic segmentation (C) by comparing to the ground truth (G) [5].

**Generation of Probability Distribution Function and Validation:** The EM-based technique is adapted to the LCDG-model. In order to calculate the probability distribution of changes in the cerebrovascular structure, the distance map is used to extract the distribution of pixel distances. The distribution of white pixels is marked by the PDF, as a true value and black pixels being ignored for the data set. The diameters of the blood vessels are determined by estimating Euclidian center point distances from the edge of a vessel. The data points in the generated PDFs are then extracted and compared to the BP data using statistical analysis.

**Calculation of Cumulative Distribution Function:** The integral of the PDF is used to generate the CDF. (The CDF $F_X$ of a random variable $X$ is calculated from its PDF $f_X$ using $F_X(x) = \int_{-\infty}^{x} f_X(t)dt$.) The CDF shows the total summated probability that a blood vessel will take a value less than or equal to a diameter value that represents an average blood vessel diameter in each slice. It shows the cumulative distribution of the PDF with an upper limit of 1. The more quickly the CDF line approaches 1, the more certain that the diameter of the blood vessel is smaller compared to a CDF that takes longer to approach 1. This is illustrated in the Results section.

## 13.2.3 Statistical Analysis

Statistical analysis was performed using R software, version 3.3. A mixed effects linear model was used to test the relationship of MRA data with clinical BP measurements. Brain slices were separated into upper
