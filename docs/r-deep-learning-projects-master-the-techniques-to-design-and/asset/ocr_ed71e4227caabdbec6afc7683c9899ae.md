```
iter 60 value 11026.672273
iter 70 value 10654.855058
iter 80 value 10193.580947
iter 90 value 9854.836168
iter 100 value 9544.973159
iter 110 value 9307.192737
iter 120 value 9043.028253
iter 130 value 8845.069307
iter 140 value 8686.707561
iter 150 value 8525.104362
iter 160 value 8281.609223
iter 170 value 8140.051273
iter 180 value 7998.721024
iter 190 value 7854.388240
iter 200 value 7712.459027
iter 210 value 7636.945553
iter 220 value 7557.675909
iter 230 value 7449.854506
iter 240 value 7355.021651
iter 250 value 7259.186906
iter 260 value 7192.798089
iter 270 value 7055.027833
iter 280 value 6957.926522
iter 290 value 6866.641511
iter 300 value 6778.342997
final value 6778.342997
stopped after 300 iterations
```

We fit the model with parameters including:

+   * size=50: There are 50 hidden units in the hidden layer.
+   * MaxNWts=100000: It allows at most 100,000 weights. In our case, there are (784 input dimensions + 1 bias) * 50 hidden units = 39,250 elements in the weight matrix w<sup>(1)</sup> and (50 hidden units + 1 bias) * 10 output units = 510 elements in the weight matrix w<sup>(1)</sup>. So there are 39,760 weights in total.
+   * decay=1e-4: The regularization strength, the weight decay is 0 .0001.
+   * maxit=300: The maximum number of iterations is set to be 300.

We apply the trained network model on the testing set:

```
> prediction_nn <- predict(model_nn, data_test, type = "class")
> cm_nn = table(data_test$label, prediction_nn)
> cm_nn
prediction_nn
0 1 2 3 4 5 6 7 8 9
0 987 0 3 3 2 11 10 7 5 5
```