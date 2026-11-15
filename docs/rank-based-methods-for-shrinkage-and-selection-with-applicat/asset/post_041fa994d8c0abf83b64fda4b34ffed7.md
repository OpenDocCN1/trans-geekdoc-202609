
![](img/f3b106d7e76ae3afcec8895afa28732c_449_0.png)

Figure 12.18 LNN and RNN convergence traces – loss vs. iterations (×100).

Table 12.12 MNIST training set size is n = 1000. In this case, 0 outliers were artificially added; however, 50 outliers were detected after training by RNN. 0 detected by LNN. The resulting models were used to predict on a test set with n = 40000. We see that the training set accuracy of RNN is closer to the test set accuracy than is the case for LNN.

| Train | Accuracy | Matched | Outliers |
|---|---|---|---|
| LNN | 100% | 1000/1000 | 0 |
| RNN | 95% | 950/1000 | 50 |
| Test | Accuracy | Matched | Outliers |
| LNN | 88.6% | 35441/40000 | — |
| RNN | 87.3% | 34820/40000 | — |

![](img/f3b106d7e76ae3afcec8895afa28732c_449_1.png)

Figure 12.19 Residue histograms for LNN (0 outliers) and RNN (50 outliers).

![](img/f3b106d7e76ae3afcec8895afa28732c_450_0.png)

Figure 12.20 These are 49 potential outlier images reported by RNN. Of these, the circled digits are not easily recognized by humans as a number. The data scientist would decide if they are to be kept or removed.

The reason turns out to be outliers detected in the original unaltered data by RNN. Even though no outliers were added artificially, RNN still detected 50 outliers. The histogram of residuals in Figure 12.19 indicates that all of the data were fitted in the case of LNN, while in the case of RNN, only 95% of the digits were recognized and fitted. The remaining 50 images were designated as potential outliers by RNN. We show 49 such images in Figure 12.20 and note that it is difficult to decide which digit is being represented in each circled case. Clearly, RNN is able to identify many images in the MNIST data set that are not easily recognizable as a known digit. At this point, the digits identified as outliers can be kept or removed from the data set. In our case, we will continue to keep them to see their effect as we introduce more and more artificial outliers.

Returning to Table 12.12, the models from LNN and RNN are used to predict 40,000 images of digits in the test set. We find that LNN is able to correctly predict 88.6% of test images correctly (i.e. 35,441 out of 40,000) while RNN predicted 87.3% correctly (34,820 out of 40,000). They are roughly the same (1.3% difference), although it could easily be argued that LNN is more accurate. However, given the small size of the training set, a different combination of 1000 images would produce different results. The issue with running a training set with 40000 images is simply runtime to convergence. It could take many long hours to reach convergence. Since our goal here is to introduce rank-based neural networks on realistic data sets and compare to log-likelihood neural networks, the use of 1000 images is sufficient for this purpose. Advanced methods such as mini-batch gradient descent would be required to perform full-scale analysis, along with the Adam optimizer and a convolutional neural network architecture. All of this is beyond the scope of this book, but worth pursuing as future research.

![](img/f3b106d7e76ae3afcec8895afa28732c_451_0.png)

Figure 12.21 LNN (0 outliers) and RNN (144 outliers) residue histograms.

Now consider the results for the cases when artificial outliers are inserted, as shown in Tables 12.13–12.15. The training set accuracy remains 100% for LNN in all cases since there are 784 variables and over-fitting the data of 1000 images is likely to occur. However, as the number of outliers increases, RNN identifies most of the outliers and fits only those images that are not considered to be outliers. This is exactly what we expect from RNN. When predicting on the test set, the results indicate that LNN accuracy drops to 81.4% (90 outliers), 76.0% (180 outliers) and 70.7% (270 outliers). For RNN, the corresponding accuracy values on the test set are 83.7% (90 outliers), 82.0% (180 outliers) and 79.1% (270 outliers). This is substantially better than LNN for obvious reasons.

We show the histograms of residuals for the case with 90 outliers manually inserted in Figure 12.21 and observe the significant increase in the number of outliers in the RNN case (total of 144 out of 1000), whereas none are detected in the LNN case. Again, we find that LNN has 100% accuracy on the training set, indicating that it over-fits across outliers. Recall that there are approximately 20000 free parameters in the neural network and only 1000 images. So over-fitting is a realistic possibility regardless of whether there are outliers or not. This is true in all instances where outliers were added.

The accuracy of multi-class classifiers can not be directly assessed using the methods used in binary classification. However, further insight when comparing LNN and RNN can be obtained by examining the confusion matrices shown in Figure 12.22. This is now a 10 × 10 matrix of correct and incorrect predictions for the case with 180 artificial outliers that were manually inserted. The number of correctly identified digits are along the diagonal and the specific incorrect predictions are on the off-diagonals for each case, starting with 0 and ending with 9. We note that the LNN is making substantial mistakes due

**Table 12.13** MNIST training set size is $n = 1000$. In this case, 90 outliers have been manually added; After training, the model was used to predict on a test set with $n = 40000$. We see that the training set accuracy of RNN is close to the test set accuracy. This is not the case for LNN.

| Train | Accuracy | Matched/total | Outliers |
|---|---|---|---|
| LNN | 100% | 1100/1100 | 0 |
| RNN | 87.6% | 967/1100 | 133 |
| Test | Accuracy | Matched/total | Outliers |
| LNN | 81.4% | 32591/40000 | — |
| RNN | 83.7% | 33464/40000 | — |

**Table 12.14** MNIST training set size is $n = 1200$. Here, 180 outliers have been manually added; After training, the model was used to predict on a test set with $n = 40000$. We see that the training set accuracy of RNN is close to the test set accuracy. This is not the case for LNN.

| Train | Accuracy | Matched/total | Outliers |
|---|---|---|---|
| LNN | 100% | 1200/1200 | 0 |
| RNN | 82.0% | 992/1200 | 208 |
| Test | Accuracy | Matched/total | Outliers |
| LNN | 76.0% | 30485/40000 | — |
| RNN | 82.0% | 32795/40000 | — |

![](img/f3b106d7e76ae3afcec8895afa28732c_452_0.png)

Figure 12.22 LNN and RNN confusion matrices and MCC scores.

Table 12.15 MNIST training set size is $n = 1300$. Here, 270 outliers have been manually added; After training, the model was used to predict on a test set with $n = 40000$. We see that the training set accuracy of RNN is close to the test set accuracy. This is not the case for LNN.

| Train | Accuracy | Matched/total | Outliers |
|---|---|---|---|
| LNN | 100% | 1300/1300 | 0 |
| RNN | 78.6% | 1021/1300 | 279 |
| Test | Accuracy | Matched/total | Outliers |
| LNN | 70.7% | 28268/40000 | — |
| RNN | 79.1% | 31625/40000 | — |

to over-fitting. Since it is difficult to assess 100 numbers in each table at a glance, the Matthews correlation coefficient (MCC) (Matthews, 1975), which is similar to the $F_1$ score, is also provided in the figure. For RNN, we find that MCC = 0.829 whereas for LNN we have MCC = 0.751. Clearly, RNN outperforms LNN when outliers are present.

## 12.10 Summary

In this chapter, we have opened the door to rank-based neural networks and illustrated some of the novel capabilities available with this approach. We have demonstrated that it is superior in many respects to log-likelihood based methods and support vector machines. It was used in conjunction with well-known data sets, such as cats vs. dogs and MNIST, to demonstrate its viability and multi-class capability. However, we have only skimmed the surface of the possible research topics in this area. We see a large potential in this direction and expect there to be fruitful outcomes for those who pursue this topic. Our hope is that this book and all of the new concepts and ideas will resonate with the readers and provide motivation to pursue some of these ideas in more detail in the near future.

## 12.11 Problems

- 12.1. How many partial derivative terms are computed for the neural network in Figure 12.3? Hint: consider the sizes of the matrices between layers and add up the total number of entries in all matrices. Make sure you include the bias terms.
