add-more-if-bigger offers a nice tradeoff, from the adversary’s point of view, in terms
of poisoning effectiveness, and the attacker’s capabilities and risks.

We also evaluate the PCA detection algorithm on both anomalous and normal data, as
described in Section 6.4.1.2, to produce the ROC curves in Figure 6.5(b). We produce
a series of ROC curves (as shown) by first training a PCA model on the unpoisoned
data from the 20th week and then training on data poisoned by progressively larger add-
more-if-bigger attacks.

To validate PCA-based detection on poisoned training data, each flow is poisoned
separately in different trials of the experiment as dictated by the threat model. Thus,
for relative chaff volumes ranging from 5% to 50%, add-more-if-bigger chaff is added
to each flow separately to construct 144 separate training sets and 144 corresponding
ROC curves for the given level of poisoning. The poisoned curves in Figure 6.5(b)
display the averages of these ROC curves; i.e., the average TPR over the 144 flows for
each FPR.

The sequence of ROC curves show that the add-more-if-bigger poisoning scheme
creates an unacceptable tradeoff between false positives and false negatives of the
PCA detector: the detection and false alarm rates drop together rapidly as the level
of chaff is increased. At 10% relative chaff volume performance degrades significantly
from the ideal ROC curve (lines from (0, 0) to (0, 1) to (1, 1)) and at 20% the PCA’s
mean ROC curve is already close to that of a random detector (the y = x line with an
AUC of 1/2).

# 6.4.4 Evaluation of Antidote

We assess the effect of poisoning attacks on Antidote performance during a single
training period. As with the PCA-based detector, we evaluate the success of this detector
with each of the different poisoning schemes and compute ROC curves using the add-
more-if-bigger poisoning scheme to compare to the original PCA-subspace method.

Figure 6.6(a) depicts Antidote’s FNR for various levels of average poisoning that
occur in a single training period attack compared to the results depicted in Figure 6.5(a)
using the same metric for the original PCA detector. Comparing these results, the eva-
luation success of the attack is dramatically reduced for Antidote. For any particular level
of chaff, the evasion success rate of Antidote is approximately half that of the original
PCA approach. Interestingly, the most effective poisoning scheme on PCA (globally
informed poisoning) is the least effective poisoning scheme against Antidote. The
globally informed scheme was designed in an approximately optimal fashion to circum-
vent PCA, but for the alternative detector, globally informed chaff is not optimized and
empirically has little effect on PCA-GRID. For this detector, Random remains equally
effective because constant shifts in a large subset of the data create a bimodality that is
difficult for any subspace method to reconcile—since roughly half the data shifts by a
constant amount, it is difficult to distinguish between the original and shifted subspaces.
However, this effect is still small compared to the dramatic success of locally informed
and globally informed chaff strategies against the original detector.