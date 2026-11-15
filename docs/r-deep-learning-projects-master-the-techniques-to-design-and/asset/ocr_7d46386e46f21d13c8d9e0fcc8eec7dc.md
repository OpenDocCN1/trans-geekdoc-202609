+   • initializer=mx.init.uniform(0.1): Initial weights are randomly generated from the uniform distribution ranging from 0 to 1, so as to lower the chances of the weight exploding and vanishing in the deep network

After the model is trained, let's see how it performs on the testing set. First, remember to conduct the same pre-processing on the test dataset:

```
> data_test.x <- data_test[,-1]
> data_test.x <- t(data_test.x/255)
```

Then, predict the testing cases and evaluate the performance:

```
> prob_dnn <- predict(model_dnn, data_test.x)
> prediction_dnn <- max.col(t(prob_dnn)) - 1
> cm_dnn = table(data_test$label, prediction_dnn)
> cm_dnn
prediction_dnn
0 1 2 3 4 5 6 7 8 9
0 1041 0 2 0 0 1 3 0 8 1
1 0 1157 3 1 1 0 1 3 1 0
2 2 1 993 3 3 1 2 13 5 2
3 1 3 14 1033 1 13 0 5 14 6
4 0 2 1 0 991 0 4 4 1 12
5 4 2 3 12 3 892 4 3 6 8
6 10 0 1 0 3 4 988 0 4 0
7 0 5 9 1 2 0 0 1116 2 1
8 4 8 3 5 0 0 8 3 2 1020 12
9 1 1 0 4 13 3 0 16 2 957
> accuracy_dnn = mean(prediction_dnn == data_test$label)
> accuracy_dnn
[1] 0.9704706
```

By adding one more hidden layer, accuracy is improved from 91.4% to 97.0%! Since each hidden layer in a deep neural network provides representations of the data at a certain level, can we simply conclude that the more hidden layers (such as 100, 1,000, 10,000...), the more underneath patterns are discovered, the better the classification accuracy? It might be true if we have plentiful resources and time to enable computation and to make sure overfitting does not occur with such complex networks. Is there any way where we can extract richer and more informative representations than by simply chaining more hidden layers, and at the same time, not excessively grow our networks? The answer is CNNs.