abnormal. (Figure 1.12) depicts the block diagram of the algorithm for classifying images in the SCC system.

The performance of the system is measured by sensitivity, specificity, and accuracy. Table 1.2 below gives the accuracy obtained from the set of 75 and 100 coefficients of shearlet transform and K-NN classifier.

It is observed from Table 1.2 that the second level of shearlet features made from 100-point coefficients yield better performance compared to other levels of shearlet decomposition. The maximum accuracy of 96% is obtained in the second level of decomposition using shearlet transform and K-NN classifier. (Figure 1.13) depicts the K-NN classifier performance for 75 coefficients vis-a-vis 100 coefficients for four levels of decomposition.

![](bbox=[0.3, 0.31, 0.69, 0.63])

**FIGURE 1.12** Block Diagram of Shearlet and KNN SCC System.

**TABLE 1.2**
**Performance of K-NN Classifier**

| Shearlet Transform Decomposition Level | 75 Coefficients | 100 Coefficients |
|:---|:---|:---|
| First level | 82.5 | 88.5 |
| Second level | 88 | 96 |
| Third level | 81.5 | 91 |
| Fourth level | 85.5 | 92.5 |