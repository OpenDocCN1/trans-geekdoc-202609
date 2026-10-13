
# 9.3.2 Unsupervised Classification and Ensemble-Based Updating

[Algorithm 9.1](#ch09.xhtml#alg9_1) summarizes the unsupervised classification and ensemble-based updating algorithm. Lines 3–4 build a new model from the most recent chunk and temporarily add it to the ensemble. Next, lines 5–13 apply each model in the ensemble to test graph *t* for possible anomalies. We use three varieties of GBAD for each model (P, MDL, and MPS), each discussed in this section. Finally, lines 14–30 update the ensemble by discarding the model with the most disagreements from the weighted majority opinion. If multiple models have the most disagreements, an arbitrary poorest-performing one is discarded. Note that no ground truth is used. However, majority voting of models serve so called “ground truth.” Weighted majority opinions are computed in line 15 using the formula

```
WA(E,a) = \frac{\sum_{\{ i|M_{i} \in E,a \in A_{M_{i}}\}}\lambda^{\ell - i}}{\sum_{\{ i|M_{i} \in E\}}\lambda^{\ell - i}}
```
(9.1)

where *M[i]* ∈ *E* is a model in ensemble *E* that was trained from chunk *i*, *AM[i]* is the set of anomalies reported by model *M[i]*, *λ* ∈ \[0, 1\] is a constant *fading factor* \[[CHEN2009](#ch09.xhtml#ref9_14)\] and *ℓ* is the index of the most recent chunk. Model *M[i]*'s vote therefore receives weight *λ*[−*i*], with the most recently constructed model receiving weight *λ*[0] = 1, the model trained from the previous chunk receiving weight *λ*[1] (if it still exists in the ensemble), etc. This has the effect of weighting the votes of more recent models above those of potentially outdated ones when *λ* < 1. Weighted average *WA*(*E, a*) is then rounded to the nearest integer (0 or 1) in line 15 to obtain the weighted majority vote. For example, in Figure 9.2, models *M*[1], *M*[3], and *M*[7] vote positive, positive, and negative, respectively, for input sample *x*. If *ℓ* = 7 is the most recent chunk, these votes are weighted *λ*[6], *λ*[4], and 1, respectively. The weighted average is therefore *WA*(*E, x*) = (*λ*[6] + *λ*[4])*/*(*λ*[6] + *λ*[4] + 1). If *λ* ≤ 0.86, the negative majority opinion wins in this case; however, if *λ* ≥ 0.87, the newer model's vote outweighs the two older dissenting opinions, and the result is a positive classification. Parameter *λ* can thus be tuned to balance the importance of large amounts of older information against smaller amounts of newer information. Our approach uses the results from previous iterations of GBAD to identify anomalies in subsequent data chunks. That is, normative substructures found in previous GBAD iterations may persist in each model. This allows each model to consider all data since the model's introduction to the ensemble, not just that of the current chunk. When streams observe concept-drift, this can be a significant advantage because the ensemble can identify patterns that are normative over the entire data stream or a significant number of chunks but not in the current chunk. Thus, insiders whose malicious behavior is infrequent can still be detected.

### 9.3.3 Ensemble for Supervised Learning

[Algorithm 9.2](#ch09.xhtml#alg9_2) shows the basic building blocks of our supervised algorithm. Here, we first present how we update the model. Input for [Algorithm 9.2](#ch09.xhtml#alg9_2) will be as follows: *D*[*u*] is the most recently labeled data chunk (most recent training chunk) and *A* is the ensemble. Lines 3–4 calculate the prediction error of each model on *D*[*u*]. Line 6 builds a new model using OCSVM on *D*[*u*]. Line 7 produces *K* + 1 models. Line 8 discards the model with the maximum prediction error, keeping the *K* best models. [Algorithm 9.3](#ch09.xhtml#alg9_3) focuses on ensemble testing. Ensemble *A* and the latest unlabeled chunk of instance *D*[*u*] will be the input. Line 3 performs feature extraction and selection using the latest chunk of unlabeled data. Lines 4–9 will take each extracted feature from *D*[*u*] and do an anomaly prediction. Lines 6–7 use each model to predict the anomaly status for a particular feature. Finally, line 9 predicts anomalies based on majority voting of the results.

Our ensemble method uses the results from previous iterations of OCSVM executions to identify anomalies in subsequent data chunks. This allows the consideration of more than just the current data being analyzed. Models found in previous OCSVM iterations are also analyzed, not just the models of the current dataset chunk. The ensemble handles the execution in this manner because patterns identified in previous chunks may be normative over the entire data stream or a significant number of chunks but not in the current execution chunk. Thus insiders whose malicious behavior is infrequent will be detected. It is important to note that we always keep our ensemble size fixed. Hence, an outdated model which is performing the worst on the most recent chunks will be replaced by the new one.

It is important to note that the size of the ensemble remains fixed over time. Outdated models that are performing poorly are replaced by better-performing, newer models that are more suited to the current concept. This keeps each round of classification tractable even though the total amount of data in the stream is potentially unbounded.

In a chunk, a model is built using one class support vector machine (OCSVM) \[MANE2002\]. The OCSVM approach first maps training data into a high dimensional feature space (via a kernel). Next, the algorithm iteratively finds the maximal margin hyperplane which best separates the training data from the origin. The OCSVM may be considered as a regular two class SVM. Here the first class entails all the training data, and the second class is the origin. Thus, the hyperplane (or linear decision boundary) corresponds to the classification rule:

```
f(x) = w · x + b
```
(9.2)

where *w* is the normal vector and *b* is a bias term. The OCSVM solves an optimization problem to find the rule with maximal geometric margin. This classification rule will be used to assign a label to a test example *x*. If *f* (*x*) *<* 0, we label *x* as an anomaly, otherwise it is labeled normal. In reality there is a trade-off between maximizing the distance of the hyperplane from the origin and the number of training data points contained in the region separated from the origin by the hyperplane.

### 9.3.4 Unsupervised Learning

[Algorithm 9.3](#ch09.xhtml#alg9_3) uses three varieties of graph-based anomaly detection (GBAD) \[COOK2000, COOK2007, EBER2007, YAN2002\] to infer potential anomalies using each model. GBAD is a graph-based approach to finding anomalies in data by searching for three factors: modifications, insertions, and deletions of vertices and edges. Each unique factor runs its own algorithm that finds a normative substructure and attempts to find the substructures that are similar but not completely identical to the discovered normative substructure. A normative substructure is a recurring subgraph of vertices and edges that, when coalesced into a single vertex, most compresses the overall graph. The rectangle in [Figure 9.3](#ch09.xhtml#fig9_3a) identifies an example of normative substructure for the depicted graph.

![Figure 9.3 A graph with a normative substructure (boxed) and anomalies (shaded).](images/fig9_3.jpg)

[Figure 9.3 A graph with a normative substructure (boxed) and anomalies (shaded).](#ch09.xhtml#Ffig9_3)

Our implementation uses SUBDUE \[[KETK2005](#ch09.xhtml#ref9_41)\] to find normative substructures. The best normative substructure can be characterized as the one with minimal description length (MDL):

```
L(S,G) = DL(G|S) + DL(S)
```
(9.3)

where *G* is the entire graph, *S* is the substructure being analyzed, *DL*(*G* □ *S*) is the description length of *G* after being compressed by *S*, and *DL*(*S*) is the description length of the substructure being analyzed. Description length *DL*(*G*) is the minimum number of bits necessary to describe graph *G* \[[EBER2011](#ch09.xhtml#ref9_26)\].
