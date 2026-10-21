
## 10.3.3 Long-term trackers

Long-term trackers must not only address the common tracking challenges faced by short-term trackers, but additionally handle long-term decay as well as target disappearance and target reappearance. In theory, model decay is inevitable when online learning is added to short-term trackers. Addressing long-term decay receives the most attention due to the fundamental and catastrophic nature of the challenge. We identify three families of approaches for long-term tracking, organized by way of learning and updating the tracker model given long-term decay: offline learning, online learning and hybrid learning.

### 10.3.3.1 Offline learning with Siamese trackers

At the core of all tracking algorithms is the model function f_φ : Y_1 × X_1 × X_t → Y_t from Eq. (10.1), by which the image of the target is matched to the incoming frames. The tracker model returns predictions y_{1:t}, which hopefully should be as close as possible to the true locations y*_{1:t}. The matching function for tracking ideally provides good matching even if the target in the video is occluded, changes its scale, rotates in and out-of-plane or, undergoes uneven illumination, camera motion and other disturbing factors (Smeulders et al., 2014; Wu et al., 2015).

As we discussed earlier, to address these tracking challenges models often rely on online updates using the model predictions as ground truth. This, in turn, leads to model decay that is especially prevalent in the case of long and challenging videos, effectively because we assume that the model predictions are equivalent to the ground-truth predictions during the updates, y_{1:(t−1)} ≡ y*_{1:(t−1)}. By this assumption we acknowledge the following peculiar paradox, which we coin the tracking paradox. On one hand, if the model is so accurate so that to assume ŷ_{1:(t−1)} ≡ y_{1:(t−1)}, then the model requires no further retraining. In other words, by retraining there is no additional benefit as the model predictions are already perfect. On the other hand, if the model is not as accurate as per the assumption, by setting ŷ_{1:(t−1)} ≡ y_{1:(t−1)} we only gain temporary improvements in accuracy but gradually make the model worse and worse, and set it to fail eventually.

To break the paradox, we could define a tracker model that relies on no model updating. In this case, the tracker model must be able to locate the target simply by the information it has available prior to tracking, that is only the bounding box in the first frame. This is clearly challenging, as in complex videos there exist severe challenges that the tracker model must be impervious to, as discussed in Section 10.1.1. In combination with online updates, the traditional way to address these challenges is by modeling each of these distortions explicitly by introducing affine transformations (Lucas and Kanade, 1981), probabilistic matching (Comaniciu et al., 2000), eigenimages (Ross et al., 2008), illumination invariants (Nguyen and Smeulders, 2006), occlusion detection (Pan and Hu, 2007), and so on. Unfortunately, modeling explicitly single challenges – while ignoring all others – yields trackers that may be optimal for that one type of distortion but suboptimal for many others, thus resulting in worse performance.

Rather than explicitly modeling all possible distortions with the tracker model f, another possibility is to cast tracking as an image matching problem, where the query image is always the target at the first frame. Because the query remains fixed and does not alter due to online updates using imperfect predictions for supervision, the model is guaranteed to work consistently and robustly for any length of time. The model definition of the tracker becomes

y_{t+1} = arg min_y f(h_φ(z), h_φ(x_t[y])). (10.18)

In this definition z is the patch of the target object in the first frame, x_t[y] corresponds to the patch in the t-th frame that corresponds to the y bounding box coordinates, h_φ are the convolutional neural networks that compute the representations from z and x_t[y], and f is the similarity matching function of the tracker. There are no constraints in the types of convolutional neural networks h_φ, although in practice some work better than others (Tao et al., 2016; Li et al., 2019a). While for simplicity we use the same parameters φ for both neural networks, the parameters do not have to be shared (Li et al., 2019a).

In the case of tracking by target matching the critical component is the matching function, which must be robust against all undesirable tracking challenges. Traditionally, this matching function is learned online given the specific target z. An alternative is to learn the matching function externally in an offline manner, specifically by comparing object appearances recorded at different time stamps, that is (x_i, x_j, y_ij*), where y_ij* = +1 if x_i and x_j depict the same object and −1 otherwise. The matching function f can be implemented by a multilayer perceptron (fully connected layer), and trained to minimize the contrastive loss (Tao et al., 2016)

arg min_φ ½ y_ij* d_ij² + ½ (1 − y_ij*) max(0, ε − d_ij²) (10.19)
d_ij = ||h_φ(x_i) − h_φ(x_j)||² (10.20)

or by the cosine similarity to minimize the logistic loss (Bertinetto et al., 2016b)

arg min_φ log(1 + exp(−y_ij* h_φ(x_i)^T h_φ(x_j))). (10.21)

At the heart of it, for both losses the distances, either the euclidean norm or the cosine similarity, are inner products. Considering that in the minimization of the search in Eq. (10.18) we iterate over bounding box locations that are densely packed on top of the feature maps, the iterative inner products can be more compactly written as convolutions, that is

y_{t+1} = arg min_y h_φ(z) * h_φ(x_t[y]). (10.22)

Eq. (10.22) allows for using fully convolutional Siamese networks (Bertinetto et al., 2016b) with great efficiency.

Visual object trackers that track by a target matching paradigm using Siamese deep neural networks are called Siamese trackers – see Fig. 10.3 for a graphical pipeline. Siamese trackers have two branches of convolutional neural networks. The first branch is the template branch, which convolves the target patch as determined in the first frame. The output is a template with which every future frame can be further convolved to localize the target. The second branch is the candidate branch, processing the new frames in the video sequences and trying to match the appearance of the target.

![](img/fe161b7f6e96e35e7e853eece52c6dce_372_0.png)

FIGURE 10.3 The Siamese tracker comprises two branches, each modeled by a convolutional neural network. The first branch always contains the target object patch at t = 0. The second branch analyzes any other frame in the video. The representations by the two branches are then compared with a similarity function. The similarity function is learned externally and offline, using tracked objects from different datasets. Although the similarity function has not seen the future targets, it can still match their appearance accurately for performing tracking by matching. Figure inspired by Bertinetto et al. (2016b); Tao et al. (2016).

### Search region.

As with short-term trackers, instead of searching for the target in the whole frame one can restrict the model to search for the next locations of the target within a predefined radius ρ. Setting a search region helps with improving the computational efficiency of the tracker algorithm, as the tracker must only analyze a much smaller image area. Limiting search into a certain region can also reduce the chances of false positives that could accidentally fire when examining the whole image.

The radius r0 is a hyperparameter that depends on the maximum velocity of the target. As in most cases we cannot know the maximum velocity of the target. Therefore, if we choose to set a search region, we must do so cautiously. If the target moves faster than r0/Δt, where Δt is the interval between any two frames (inverse of the recording speed in frames per second), the target will be outside the search region and the tracker will definitely miss the target. If the radius r0 is set such that r0 = max(H, W), where H and W are the height and the width of the frame, then the tracker will process the whole frame.

In determining the size of the search region, one must balance between improving precision and worsening recall. By setting a small search region the precision may be improved by avoiding excess false positives in the background. However, a small search region may also hurt recall as all locations outside the search region are automatically labeled as negatives; these will be false negatives when the target lies outside the search region. A similar argument can be made for large search regions.

1 Precision is computed as the ratio of true positives over true positives and false positives. Recall is computed as the ratio of true positives over the sum of true positives and false negatives.
