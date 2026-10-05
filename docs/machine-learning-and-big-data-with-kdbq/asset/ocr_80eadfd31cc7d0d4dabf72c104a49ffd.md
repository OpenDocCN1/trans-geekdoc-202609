# Nearest Neighbours

![](bbox=[0.156, 0.098, 0.843, 0.401])

FIGURE 21.1 Scatter plot of true clusters as defined in tableKNN

It is convenient to work with the following data arrangement,

tableKNN: select x:flip (x1;x2),f from tableKNN

where we have only two variables: the first one is an array of factors, the second being the classifier (dependent variable) f in our case the binary variable f. The implementation assumes such a form of data where x is of any dimension. The q function reads:

# LISTING 21.1

```
.quantQ.knn.prototypeKNN::[[table;k;R;iterations]]
// table -- the training data with array of features x and the
// classifier (dependent variable) f
// k -- the size of the neighbourhood
// R -- the number of centres per each class
// iterations -- the number of iterations
// distinct values
values=: exec distinct from table;
// parallel loop -- over distinct values of dependent variable
tableGlobalOut:rate [[table;k;R;iterations;fRealization]
// create a sub-sample
tableSub: select centre:x from feRealization;
// output table, contains initial draws of centres
tableOut: update centreID:i+i from (neg R)?(select centre:x,f from
// table where fRealization).
// loop over each centre
centresNew::[tableSub;k;iterations;centre]
// for each centre, search using neighbours
{{tableSub;k;centreX
```