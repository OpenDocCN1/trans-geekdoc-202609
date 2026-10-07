
## Iterative convolutional neural network 215

Since the compute-intensive parts of the CNN architectures are the CONV layers, the pruning slightly reduces the computational complexity as it only affects the FC layers. However, it considerably reduces the number of weights needed to be moved to the memory. CAPP is yielding a dynamic trade-off between accuracy, the required memory footprint and computational complexity. Pruning a larger number of classes results in higher complexity and memory footprint reduction while negatively affecting accuracy. It should be noted that, unlike the thresholding scheme, the pruning yields the same computational complexity for all images.

## 9.9.3.2 Context-aware pruning policy for CONV layer

Visualization of the ICNN filters by using deconvolution networks as described in [7] makes it possible to identify and remove trained filters that are closely associated with the classification of low-probability classes, extending the pruning feature into CONV layers. The pruning feature based on filter visualization is explored in Algorithm 4.

### Algorithm 4: Context-aware pruning policy for CONV layer ($CAPP_{CONV}$)

```
1: Pre-Process:Obtain $Pre(i, cnv, c)$
2: for $i=1$ to $N-1$ do
3: $P_i \leftarrow uCNN(i, \hat{C}_i, img)$;
4: Sort_descending($P_i$);
5: for $cnv=1$ in $CONV_{lst}$ do
6: $Flt_{rem} = {}$
7: for $c=1$ to $P_{th}[i]$ do
8: $Flt_{rem} += Pre(i, cnv, c)[1:rm]$
9: end for
10: $Flt_{rem} \leftarrow Maj(Flt_{rem}, rm)$
11: Update(uCNN, i, cnv, Flt_{rem})$
12: end for
13: end for
14: $\hat{P}_N \leftarrow uCNN(N, \hat{C}_L, img);
```

Algorithm 4 requires a statistical analysis by preprocessing a large dataset (i.e., 1.2 images in the training set). Based on this analysis, for each iteration, target CONV layer and class, a vector is calculated, in which filters are arranged in an ascending order of loss due to their removal from the network. $Pre(i, cnv, c)$ shows the preprocessing vector for the $i$th iteration, where $cnv$ refers to the target CONV layer and $c$ refers to class label. Thus, the removal of the filter associated with the first argument in $Pre(i, cnv, c)$ has the least effect on overall accuracy of class $c$. $CONV_{lst}$ is the list of CONV layers targeted for filter pruning. The variable $rm$ is the number of filters to be removed from each CONV layer.

In the $i$th iteration, the filters least affecting the top-$P_{th}$ classes are gathered in $Flt_{rem}$ determining the candidate filters for removal. Subsequently, the majority function Maj(Fltrrem, rm) returns rm most repeated arguments in Fltrrem. This allows us to find the union of filters that least affect the top-$P_{th}[i]$ classes in the ith iteration. Subsequently, Update(uCNN, cnv, Fltrrem) updates the ith uCNN by removing the rm filters in Fltrrem from cnv conv.

## 9.9.4 Pruning and thresholding hybrid policy

The pruning and thresholding hybrid policy (PTPH) scheme takes advantage of both early termination in the thresholding scheme and the pruning of the FC layers in CAPP. Two variants of PTPH are studied.

### 9.9.4.1 Fixed percentage PTPH

Algorithm 5 shows the first hybrid policy. uCNN(i, Cl, img) invokes the top-5 uCNN as input, requesting classification result for all classes in the Cl vector, and produces a vector of probabilities Pr, for each label in Cl. In the first uCNN, Cl contains all 1,000 labels. After uCNN, the top-5 confidence of (Σk=1 Pr[k]) is compared with DC[i]. If confidence is greater, the image is classified. Otherwise, a number of classes are pruned based on pruning policy Pb[i] defined for each iteration. For example, Prune[i] = 100 in choosing only the top 100 labels and disables all other neurons in the FC layer of next uCNN related to eliminated labels.

### Algorithm 5: Fixed-percentage pruning and thresholding (PTPHFP) policy

```
1: for i = 1 to N - 1 do
2:   Pr ← uCNN(1, Cl, img);
3:   Sort_descending(Pr);
4:   if ((Σk=1 Pr[k]) > DC[i]) then
5:     exit;
6:   else
7:     Cl ← Cl[1 : Pth[i]];
8:     Pr ← uCNN(i, Cl, img);
9:   end if
10: end for
11:  Pr ← uCNN(N, Cl, img);
```

### 9.9.4.2 Confidence-tracking PTPH

Algorithm 6 illustrates the confidence-tracking pruning and thresholding hybrid policy (PTPHTC) policy. In the first uCNN, the probability for all classes (all labels) is computed. In the while loop, if top-5 confidence is the detection threshold DC[i], the classification is terminated. Otherwise, based on the value of a saturation threshold Sh[i], a number of labels are selected for further processing in the next layer. The selected classes are the minimum number of labels with an accumulated probability of no less than $S_{th}^*[i]$. In this algorithm, $CC_L$ is the shrunk version of $\tilde{C}_L$ that only contains the labels of interest.

### Algorithm 6: Confidence-tracking pruning and thresholding (PTHP$_{CT}$) policy

```
$\bar{P}_r \leftarrow uCNN(i, \tilde{C}_L, img);$
for $i = 1$ to $N-1$ do
  $Sort_{descending}(\bar{P}_r)$;
  if ((\sum_{k=1} P_r[k]) > D_{ci}[i])$ then
    exit;
  else
    $Sum = 0, CC_L = [], label=1;$
    while $Sum < S_{th}[i]$ do
      $Sum += P_r[label];
      $CC_L[label] = \tilde{C}_L[label];
      $label++;
    end while
  $\bar{P}_r \leftarrow uCNN(i+1, \tilde{C}_L, img);$
end for
```

## 9.9.5 Variable bit-length selection

There are two general approaches to convert a network to fixed point. One is to use bit-length across layers [22]. The other approach is to use bit-length selection, which is more feasible for early iterations.
