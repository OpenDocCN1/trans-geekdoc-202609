
To identify the LCDG model, a criterion, consisting of expected log-likelihoods, is employed \[[16](#C20_chapter13.xhtml#ref13_16)\]. Consider that a 3D MRA image is represented by `***X***` = (`***X***`[s]: *s* = 1,…, *S*), which contains *S* co-registered 2D slices `***X***`[s] = (*X*[s] (*i*, *j*): (*i*, *j*) ∈ *R*; *X*[s] (*i*, *j*) ∈ *Q*). On the other hand, a rectangular arithmetic lattice supporting the 3D image is represented by `***R***` and a finite set of gray levels and *Q*‑ary intensities are represented by `***Q***` = {0, 1,…, *Q*−1}. Consider `***F***`[s] = (*f*[s] (*q*): *q* ∈ `***Q***`; ∑[q]∈[`***Q***] *f*[s] (*q*) = 1; in this equation, *q* is one of the gray levels, considered to be an empirical marginal probability distribution for gray levels of the slice `***X***`[s] within the MRA.

According to Ref. \[[18](#C20_chapter13.xhtml#ref13_18)\], each slice of the MRA image is thought of as a *K*‑modal one, having a determined number *K* of the main modes of the regions of interest. For the segmentation of the slice by modes separating, it is important to estimate the probability distributions of the signals individually. Said signals associate each mode from `***F***`[s]. `***F***`[s] is closely approximated with LCDG opposing the conventional mixture of Gaussians, one per region, or slightly more flexible mixtures involving other simple distributions, one per region. Sub‑models, each representing a dominant mode, are the result of the division of the LCDG image \[[19](#C20_chapter13.xhtml#ref13_19), [20](#C20_chapter13.xhtml#ref13_20), [21](#C20_chapter13.xhtml#ref13_21)\].

A discrete Gaussian distribution is defined on the set of integers (gray levels) `Q` = {0,1,…,*Q*−1} by the probability mass function  

$$\psi{\\left( q \\middle| \\theta \\right) = \\begin{Bmatrix} {\\Phi\\left( 0.5 \\right),} & {q = 0} \\\\ {\\Phi\\left( q + 0.5 \\right) - \\Phi\\left( q - 0.5 \\right)} & {1 \\leq q < Q - 1} \\\\ {1 - \\Phi\\left( q - 0.5 \\right),} & {q = Q - 1,} \\\\ \\end{Bmatrix}}$  

where the parameter `θ` = (`μ`, *σ*), and Φ is the CDF of a normal distribution with mean μ and variance *σ*². Then the LCDG with *C*[p] positive components and *C*[n] negative components, such that *C*[p] ≥ *K*, has the probability mass function  

$${p\_{w,\\Theta}\\left( q \\right) = \\sum\\limits\_{r = 1}^{C\_{p}}w\_{p,r}\\psi\\left( {q\\text{|}\\theta\_{p,r}} \\right) - \\sum\\limits\_{l = 1}^{C\_{n}}w\_{n,l}\\psi\\left( q \\middle| \\theta\_{n,l} \\right)}\\mspace{54mu}\\operatorname{(13.1)}$$  

The weights `w` = (`w`[p,1],…, *w*[p, Cp], *w*[n,1],…, *w*[n, Cn]) are restricted to be all non‑negative and to satisfy  

$${\\sum\\limits\_{r = 1}^{C\_{p}}w\_{p,r} - \\sum\\limits\_{l = 1}^{C\_{n}}w\_{n,l} = 1}\\mspace{54mu}\\operatorname{(13.2)}$$  

In general, for a probability to be valid, it has to be non‑negative: *p*[w], Θ(*q*) ≥ 0 for all *q* ∈ `***Q***`. This implies that a valid subset of all the LCDGs in (13.1) only uses the probability distributions. This subset can however have negative components, *p*[w,] Θ (*q*) < 0 for some *q* ∈ `***Q***`.

It is the aim of this study to find a *K*‑modal probability model, which closely approximates the marginal distribution of gray level, which is not known. If `***F***` is the Bayesian estimate of `***F***`[s], the former can be described as follows \[[22](#C20_chapter13.xhtml#ref13_22)\]: *f*(*q*) = (|**R**|*f*[s] (*q*) + 1)/(|**R**| + *Q*). The model to be devised should work on increasing the expected log‑likelihood of the statistically independent empirical data to its maximum limits, along with its other parameters:

$${L\\left( {w,\\operatorname{}\\Theta} \\right) = \\sum\\limits\_{q \\in Q}f\\left( q \\right)\\log p\_{w},_{\\Theta}\\left( q \\right)}\\mspace{54mu}\\operatorname{(13.3)}$$  

The algorithm used in segmentation in its entirety is as follows \[[16](#C20_chapter13.xhtml#ref13_16)\].

1. For each slice `***X***`[s], *s* = 1,…*S*,

    *   The first is to gather the marginal empirical probability distribution *F*[s], which represents gray levels.

    *   Pinpoint a starting LCDG model, which is close to *F*[s]. This is done with the use of the initialization algorithm, which can approximate the values of *C*[p]−*K*, *C*[n], and the parameters `w`, `θ` (marking weights, means, and variances) of both negative and positive discrete Gaussians (DG).

    *   Fix *C*[p] and *C*[n], use the modified EM algorithm to refine the LCDG‑model by manipulating other parameters.

    *   Make *K* submodels by separating the final LCDG model. There would be a submodel for each dominant mode. This is done by minimizing the misclassification predicted errors and selecting the LCDG‑submodel that has the greatest average value (corresponding to the pixels with the highest brightness) to be the model of the wanted vasculature.

    *   Use intensity threshold *t* to extract the voxels of the blood vessels in the MRA slice, which separates their LCDG‑submodel from the background.

2. Remove the artifacts from the extracted voxels whole set with the help of a connection filter, which chooses a system to construct by a 3D growing algorithm, which comes in the form of the greatest connected tree \[[23](#C20_chapter13.xhtml#ref13_23)\]. Algorithm 13.1 summarizes the adopted segmentation approach:

This procedure aims to decipher each MRA slice’s threshold, which will enable the complete extraction of the bright blood vessels while removing the darker unwanted tissue while also separating surrounding non‑vasculature tissue that may be of similar brightness and along the same boundaries. When step 1b is initialized, the LCDG with the non‑negative beginning probabilities *p*[w], `θ` (*q*) is created. In step 1c, a refinement takes place, increasing the likelihood, but still, probabilities are non‑negative. In Ref. \[[16](#C20_chapter13.xhtml#ref13_16)\], experiments showed that the opposite situations never took place.

Automatic segmentation’s accuracy is evaluated by calculating total error compared to the ground truths. For evaluation purposes, segmentations are measured, including both true positive (TP) and true negative (TN), as well as false positive (FP) and false negative (FN).

In [Figure 13.3](#C20_chapter13.xhtml#f13_3), if C is the segmented region, G is the ground truth, and R represents the entire image frame, then the TP = |C∩G|, TN = |R−C∪G|, FP = |C−C∩G|, and FN = |G−C∩G|. The total error *ε* is given in Ref. \[[24](#C20_chapter13.xhtml#ref13_24)\] as *ε* = (FN + FP)/(TP + FN) = (FN + FP)/G.

![FIGURE 13.3 Illustration of segmentation accuracy and errors of the proposed automatic segmentation (C) by comparing to the ground truth (G) \[5\].](images/fig13_3.jpg)

FIGURE 13.3 Illustration of segmentation accuracy and errors of the proposed automatic segmentation (C) by comparing to the ground truth (G) \[[5](#C20_chapter13.xhtml#ref13_5)\].

**Matching of Voxels**: Voxels are defined as an array of volume elements, which constitute a notional 3D space. A 3D affine registration is used to handle the pose, orientation, and the data spacing changes and other scanning parameter changes between day 0 and day 700 \[[25](#C20_chapter13.xhtml#ref13_25)\]. In this step, the determined Euclidian radii are converted into diameter values. The output is then converted into a distance map.

**Generation of Probability Distribution Function and Validation**: The EM‑based technique is adapted to the LCDG‑model. In order to calculate the probability distribution of changes in the cerebrovascular structure, the distance map is used to extract the distribution of pixel distances. The distribution of white pixels is marked by the PDF, as a true value and black pixels being ignored for the data set. The diameters of the blood vessels are determined by estimating Euclidian center point distances from the edge of a vessel. The data points in the generated PDFs are then extracted and compared to the BP data using statistical analysis.
