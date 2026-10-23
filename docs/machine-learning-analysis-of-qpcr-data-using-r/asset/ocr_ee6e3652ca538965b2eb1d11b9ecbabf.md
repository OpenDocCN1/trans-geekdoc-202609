```
```r
> aggregate(Accuracy ~ Cost, accuracy_result, mean)

    Cost  Accuracy
1   0.01  0.6136364
2   0.10  0.9681818
3   0.50  0.9909091
4   0.75  0.9863636
5   1.00  0.9909091
6   2.00  0.9818182
7   5.00  0.9909091
8  10.00  0.9818182
```
```

The lowest cost that provided the highest accuracy was 0.5; the cost of 1 might be another good choice. Thus, the SVM model will be applied with the *rbf* kernel and a cost of 0.5.

The final step is to run the SVM algorithm with the chosen parameters. To generate a figure showing the hyperplanes with sufficient detail, a series of 1000 points between FCN 0-50 and MR 0-0.4 will be generated, and each will be classified according to the SVM model and plotted using the *contourplot* function of the *lattice* package. The plots are saved to objects and then printed as overlay of the samples’ plot. The diagnostic characteristics of the assay will be calculated.

```
```r
# Listing 3.10
library(lattice)
library(RColorBrewer)
library(latticeExtra)
make.grid = function(x, n = 1000) {
    xrange = apply(x, 2, range)
    x1 = seq(from = xrange[1,1], to = xrange[2,1], length = n)
    x2 = seq(from = xrange[1,2], to = xrange[2,2], length = n)
    expand.grid(X1 = x1, X2 = x2)
}
plot_list = list()
accuracy_result = data.frame(Set = numeric(), Accuracy = numeric(), Sensitivity = numeric(),
                             Specificity = numeric())
```
```