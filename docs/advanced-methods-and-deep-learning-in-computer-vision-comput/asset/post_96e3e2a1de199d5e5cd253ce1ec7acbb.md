
to human-centered sensing. This happens in several ways: Systems should adapt to the environment that is shaped for humans – and since vision is humans’ dominating sense involved in about 80% of our perception, learning, cognition, and activities (Ripley and Politzer, 2010), they need visual sensors. There are many examples for such environments, for instance, in the traffic scenario the highway code defines many signs and symbols that guide the driver visually. Also systems that share their workspace with humans for interaction and collaboration need visual capabilities. The appearance is a strong cue for behavior as well as intentions and humans use this actively by communicating in terms of, e.g., gestures. Finally, in order to be capable to predict human actions, their perception needs to be predicted as well – which is mostly based on vision.

## 9.1.4 Historical development

Many of the older approaches to visual tracking go back to problems within augmented reality, where visualization and sensing are combined into the same coordinate system to generate a mixed reality environment. Tracking is important here for two purposes: the relative head pose in the scene (Neumann et al., 1999) and the pose of moving objects (Neumann and Park, 1998).

Some major steps in the history of visual tracking as well as key works of the author are

- 1981: Lucas-Kanade algorithm (Lucas and Kanade, 1981)
- 1984: Phase-only matched filter (Horner and Gianino, 1984)
- 1994: “Tracking is a solved problem” (from the presentation of Shi and Tomasi, 1994)
- 1998: Phase only matched filters and equivariances (Felsberg, 1998)
- 2004: “Lucas-Kanade 20 Years On: A Unifying Framework” (Baker and Matthews, 2004)
- 2007: MATRIS project: L1-tracker and covariance (Skoglund and Felsberg, 2007)
- 2013: New tracking challenges OTB (Wu et al., 2013), VOT (Kristan et al., 2013), and a generative holistic tracker (Felsberg, 2013)
- 2014: Discriminative tracker (DSST) winner in VOT2014 (Danelljan et al., 2014a; Kristan et al., 2015a)
- 2018: Discriminative holistic trackers dominate VOT2018 with 75% (Kristan et al., 2019)
- 2020: Siamese trackers and segmentation methods gain importance (Kristan et al., 2020).

In the subsequent sections, several major developments during this period of 40 years are described in some detail, with a particular focus on discriminative and learning-based methods.

## 9.2 Template-based methods

Before looking deeper into the learning-based methods, we will briefly discuss relevant methods that build entirely on the initial annotated bounding-box, often called the template.

![](img/fe161b7f6e96e35e7e853eece52c6dce_329_0.png)

FIGURE 9.2 Template-based methods. Block diagrams of template-based method; generative (left), see Section 9.2.3, and discriminative (right), see Sections 9.2.4 and 9.3.1.

### 9.2.1 The basics

In general, we can divide the template-based methods into generative and discriminative methods. These methods are conceptually sketched in the block diagrams in Fig. 9.2.

The generative approach is the most frequently used template-based approach. Here, the model is basically the prototypical image patch, usually the template itself. The localization of the object in subsequent frames is obtained by matching the model to candidate positions in the frames. The matching requires a distance measure between image patches, for instance the L2-norm (least-squares) or the L1-norm of the pixel-wise difference.

The search can be done exhaustively, which works for highly efficient L1-methods (Skoglund and Felsberg, 2006), using heuristics to reduce the search window (e.g. dynamic models), or by means of iterative methods. The most dominating approach during the initial years was based on the L2-norm and the iterative approach, the method by Lucas and Kanade (1981). Methods based on this approach have been extensively studied in the review article by Baker and Matthews (2004) and we will restrict the discussion to the basic case in the end of Section 9.9.

Instead, we will focus more on the discriminative approach, where the model is dual to the initial template. In its most basic case, duality is understood in terms of the scalar product in a vector space. Let us assume d vectors v_k that span a d-dimensional vector space. These vectors are not assumed to be normalized or orthogonal. The dual basis is spanned by the d vectors \tilde{v}_k, such that

<v_k|\tilde{v}_l> = { 1 if k = l
0 if k ≠ l } for k,l ∈ {1,…,d}, (9.1)

where ⟨|⟩ denotes the scalar product. Note that in the case of an orthonormal basis {e_k}_{k=1…d} the basis vectors are dual to themselves \tilde{e}_k = e_k.

If we now rewrite vector v_k = Σ_{l=1}^d a_{kl} e_l with coefficients a_{kl}, we immediately see that the d × d matrix A with coefficients a_{kl} has rank d and its inverse exists. Without loss of generality we can assume {e_k}_{k=1…d} to be the canonical basis of ℝ^d and thus v_k, k = 1,…,d are the rows
of A. If we now apply a cyclic shift to the rows of A and multiply with A⁻¹, we will no longer get the identity matrix, but a cyclic shift of the identity matrix: we have successfully “tracked” our basis vector vₖ.

This concept can be applied to any vector space, including the one of functions or signals. Thus, the idea of the phase-only matched filter (Horner and Gianino, 1984) is to use the dual of the template for determining a distinctive score. This score attains its maximum if the bounding-box is located at the template and will be close to zero in the vicinity.

### 9.2.2 Performance measures

In the process of tracking, we locate the bounding-box based on some score function; we will get back to segmentation masks further down in this section. To measure how successful the localization was, the predicted bounding-box needs to be compared to the ground truth bounding-box. In both, the VOT-challenge (Kristan et al., 2013) and the OTB (Wu et al., 2013), the intersection-overunion (Everingham et al., 2010), or historically more correct, Jaccard index 𝒥 (Jaccard, 1912) has been chosen:

𝒥 = |R_G ∩ R_P| / |R_G ∪ R_P| = |R_G ∩ R_P| / (|R_G| + |R_P| − |R_G ∩ R_P|) = (|R_G| + |R_P| / |R_G ∩ R_P| − 1)⁻¹ , (9.2)

where R_G is the ground truth region, R_P is the predicted region, and |R| is the area of the region R. If the two regions do not overlap we obtain 𝒥 = 0 and if the two regions perfectly coincide we obtain 𝒥 = 1. If half of the predicted region overlaps with half of the ground truth region (a typical performance of many trackers) we obtain 𝒥 = ⅓. Note that the Jaccard index is a biased measure that tends to prefer systematic overestimation of the bounding-box size (Häger et al., 2018).

The Jaccard index measures the tracking accuracy per frame and this per-frame accuracy can be accumulated in several ways. OTB suggests to calculate two curves, the precision curve and the success curve, see Fig. 9.3. Both are calculated similar to the ROC-curve by setting thresholds and computing the ratio of frames that pass that threshold. The precision curve is obtained by thresholding the box-center distance from 0 to a maximum distance and the success curve is obtained by thresholding the Jaccard index from 0 to 1. The integral under the curve is then an integral measure of performance. Alternatively, particular thresholds can be used, e.g. 20 pixels distance or 50% overlap (Everingham et al., 2010).

In either case, a complete tracking failure leads to a decrease of the performance measure and cannot be distinguished from systematically poor accuracy: accuracy and robustness are strongly correlated under these measures (Kristan et al., 2016b). Therefore, the VOT challenge uses two measures that attempt to decorrelate these two effects: the accuracy measure and the robustness measure. The former measures the average Jaccard index if tracking succeeds and the latter measures the frequency of tracking failures (Kristan et al., 2013). This conditional treatment requires restarts of tracking, either by detecting failures and restarting the tracking using the ground truth, or by starting multiple tracking attempts from several anchor points in the sequence, about every 50th frame (Kristan et al., 2020). The performance is accumulated per sequence length and then averaged, where the performance is weighted by the respective sequence length.
