
# Iterative convolutional neural network 211

![](img/e6e752b99eb1621488c89445a57e2a86_236_0.png)

**Figure 9.16** Prediction rank ($PR_{\mu}$ and $PR_{\mu} + 2 \times PR_{\sigma}$) for various classes at iteration 1): (a) maximum $PR_{\mu}$, among all classes in each iteration and (b) maximum $PR_{\mu} + 2 \times PR_{\sigma}$ among all classes in each iteration

## 9.8.2 Pruning neurons in FC layers

Let us sort the probabilities for each image in descending order. The rank of a class is the location of the class in the sorted array. When we set the pruning threshold ($P_{th}$) to value $L$ in a given iteration, all classes with ranks greater than $L$ are eliminated in the next iteration. Hence, computation of FC layer for these classes can be skipped. This results in significant reduction in required for FC computation, and elimination of memory transfer of parameters related to the classification of eliminated classes.

For example, let us consider the input image to be classified as a tabby cat. The first iteration of ICNN yields high probability values for tabby cat, Egyptian cat, Persian cat and possibly other animals, while the probability values associated with other categories (e.g., various types of vehicles) are close to zero. Hence, in the FC layer of next uCNN, the neurons for other low probability categories are disabled and those are eliminated.

## 9.8.3 Pruning filters in CONV layers

In addition to eliminating neurons in the FC layers, CONV filters in final layer(s) can also be eliminated. To this end, for each class, we carry out a statistical analysis on the 1.2 million images in the training set. In this study, we identify the classes that are least affected by elimination of each CONV filters at each iteration. When we set the pruning threshold ($P_{th}$) to value $L$ in a given iteration, all classes with ranks greater than $L$ are eliminated in the subsequent iteration. Hence, the required CONV filters

## 212 Hardware architectures for deep learning

are only those needed by remaining classes, and the computation of other filters could be skipped.

It should be noted that while filter pruning has been a well-known approach for reducing the computational complexity of CNN [38–40], ICNN allows the pruning to be carried out based on the feedback from previous iterations. An ignorant pruning approach removes a number of filters that least affect the overall accuracy; however, context-aware pruning allows us to remove the filters that least affect the top-$P_{th}$ classes of the previous iteration, promising an increased accuracy.

## 9.9 Policies for exploiting energy-accuracy trade-off in ICNN

The iterative transformation of learning algorithm can be exploited to yield the highest accuracy while meeting deadlines or create a trade-off between computational complexity and accuracy. To this end, we investigate the following policies to explore the benefits of ICNN and its trade-offs in terms of computational complexity (thus energy consumption) and accuracy.

### 9.9.1 Dynamic deadline (DD) policy for real-time applications

Many real-time applications require fast and deadline-driven computations to operate safely and correctly. To speed up the CNN-based classifier, one could adapt more powerful resources and benefit from higher parallelism. However, solutions are extremely expensive in terms of hardware cost and energy requirements. ICNN, on the other hand, provides a cost and energy-effective solution for real-time applications. Each uCNN in CNN is able to produce a classification early exit upon reaching a scheduled deadline. For the deadline-driven applications, the ICNN classifier processes the image up until the uCNN iteration, which the scheduled deadline is reached, and subsequently a classification are made. Consequently, the accuracy of the detection and computational complexity is dependent on the deadline-budget and the number of iterations that can be completed within the scheduled deadline. Note that in this mode of operation, only FC layer(s) in the processed uCNN iteration are required to make a classification decision, and the FC layers in the previous iterations for availability of computation-time-budget is skipped. This is due to the fact that for the deadline-driven applications, we rely solely on the classification results from the last processed iteration.

Algorithm 1 captures the implementation of DD policy. In this algorithm, $N$ marks the number of ICNN iterations. $uCNN_{CONV}(i, img)$ invokes the convolution layers in the $i$th uCNN with $img$ as input, returning Ofmaps from the last CNN layer ($O_{fu}$) and the elapsed time ($t_{CONV}$). The Ofmaps are concatenated with the Ofmaps of the previous iterations. Subsequently, $t_{CONV}$ is compared to the deadline, $t_D$, and if lower with a $t_{mrg}$ margin, the next uCNN is invoked. $t_{mrg}[i+1]$ accounts for the projected time of the next iteration of uCNN. Upon reaching the deadline, $uCNN_{FC}(i, Of)$ invokes the FC layers of the $i$th uCNN producing a vector of probabilities $P_r$, one for each of $lk$ layers.

# Iterative convolutional neural network 213

```
Algorithm 1: Dynamic deadline (DD)
Of $\leftarrow$ [];
$t_{mrg}[i]$ $\leftarrow$ iteration\_time\_budget;
for $i = 1$ to $N-1$ do
 $t_{CONV}$ $\leftarrow$ uCNN(i, img);
 $Of_{i}$ $\leftarrow$ $Of_i + t_{CONV}$;
 if $t_{CONV} < t_D - t_{mrg}$ then $t_{mrg}[i+1] \leftarrow$ projected time;
 else
  invoke uCNN(i+1, img);
 end if
end for
$uCNN_{FC}(i, Of)$ $\leftarrow$ $P_r$;
```

## 9.9.2 Thresholding policy (TP)

Using this policy, the ICNN terminates as soon as the sum of top-5 probabilities (e.g., $C=5$) exceeds a threshold $D_C$. Algorithm 2 implements the thresholding policy. $uCNN($i, C_L, img$) returns a vector of probabilities $P_r$ for label in $C_L$.

```
Algorithm 2: Thresholding policy (TP)
for $i = 1$ to $N-1$ do
 $P_i$ $\leftarrow$ uCNN($i, C_L, img$);
 Sort_descending($P_i$);
 if $\sum_{k=1}^5 P_i[k] > D_C$ then
  exit;
 end
end for
$P_r \leftarrow$ uCNN(N, $C_L, img$);
```

## 214 Hardware architectures for deep learning

classification above $D_{Ci}$. For these images, the results of last iteration are used. In this approach, the classification dynamically varies for iteration. Moreover, the number of parameters required for images significantly drops, which directly results in memory footprint and energy consumption. Note that the $D_{Ci}$ values are different for each iteration of ICNN to explore TPs.

### 9.9.2.1 Fixed thresholding policy

In the fixed TP, a fixed value for $D_{Ci}$ is used across all uCNNs.

### 9.9.2.2 Variable thresholding policy

In variable TP, the confidence threshold value for iterations is varied.

## 9.9.3 Context-aware pruning policy

Based on the contextual awareness obtained upon completion of initial uCNNs, CONV and FC pruning policies are beneficial.

### 9.9.3.1 Context-aware pruning policy for FC layer

Context-aware pruning policy (CAPP) for FC layer modifies the FC layer in the next uCNN to skip the computation and memory transfer of parameters related to the classification of classes with very low probabilities. Based on the discussion in Section 9.8.2, Algorithm 3 introduces the implementation of CAPP for FC neurons. In the first uCNN, $C_L$ contains all 1,000 labels. The uCNN($i, C_L$) invokes the ith uCNN for an input $img$ returning a vector of probabilities $P_h$ that store one probability for each label in $C_L$. Subsequently, the less-probable classes are pruned based on threshold stored in pruning policy vector $P_h$. For instance, $P_h[i] = 100$ results in only choosing the stored 100 labels and disables all other neurons in the FC layer of the uCNN$(i+1)$ associated with the eliminated labels.

```
Algorithm 3: Context-aware pruning policy for FC layer (CAPP$_{FC}$)
for i = 1 to N - 1
 $P_h \leftarrow$ uCNN($i, C_L, img$);
 Sort_descending($P_h$);
 $C_L \leftarrow C_L[1 : P_h[i]]$;
end for
$P_h \leftarrow$ uCNN(N, $C_L, img$);
```
