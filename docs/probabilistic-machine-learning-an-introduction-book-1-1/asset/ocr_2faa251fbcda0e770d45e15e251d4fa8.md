# 8.1.4 Precision-recall curves

In some problems, the notion of a “negative” is not well-defined. For example, consider detecting objects in images: if the detector works by classifying patches, then the number of patches examined — and hence the number of true negatives — is a parameter of the algorithm, not part of the problem definition. Similarly, information retrieval systems usually get to choose the initial set of candidate items, which are then ranked for relevance; by specifying a cutoff, we can partition this into a positive and negative set, but note that the size of the negative set depends on the total number of items retrieved, which is an algorithm parameter, not part of the problem specification.

In these kinds of situations. we may choose to use a precision-recall curve to summarize the performance of our system, as we explain below, (See e.g., [DG06] for a more detailed discussion of the connection between ROC curves and PR curves.)

# 8.1.4.1 Computing precision and recall

The key idea is to replace the FPR with a quantity that is computed just from positives, namely the precision:

$\mathcal{P}(\tau) \triangleq p(y=1|\hat{y}=1,\tau)=\frac{TP_{\tau}}{TP_{\tau}+FP_{\tau}}$ (8.18)

The precision measures what fraction of our detections are actually positive. We can compare this to the recall (which is the same as the TPR), which measures what fraction of the positives we actually detected:

$\mathcal{R}(\tau) \triangleq p(\hat{y}=1|y=1,\tau)=\frac{TP_{\tau}}{TP_{\tau}+FN_{\tau}}$ (8.19)

If $\hat{y}_n \in \{0,1\}$ is the predicted label, and $y_n \in \{0,1\}$ is the true label, we can estimate precision and recall using

$\mathcal{P}(\tau)=\frac{\sum_n y_n \hat{y}_n}{\sum_n \hat{y}_n}$ (8.20)

$\mathcal{R}(\tau)=\frac{\sum_n y_n \hat{y}_n}{\sum_n y_n}$ (8.21)

We can now plot the precision vs recall as we vary the threshold $\tau$. See Fig. 8.2(b). Hugging the top right is the best one can do.

# 8.1.4.2 Summarizing PR curves as a scalar

The PR curve can be summarized as a single number in several ways. First, we can quote the precision for a fixed recall level, such as the precision of the first $K = 10$ entities recalled. This is called the precision at K score. Alternatively, we can compute the area under the PR curve. However, it is possible that the precision does not drop monotonically with recall. For example, suppose a classifier has 90% precision at 10% recall, and 96% precision at 20% recall. In this case, rather than measuring the precision at a recall of 10%, we should measure the maximum precision we can achieve with at least a recall of 10% (which would be 96%). This is called the interpolated