Testing or evaluating the model is also easy with DL4J. First, the variables for evaluation are set up as follows:

```
Evaluation eval = new Evaluation(outputNum);
INDArray output = model.output(test.getFeatureMatrix());
```

Then, we can get the values of the feature matrix using:

```
eval.eval(test.getLabels(), output);
log.info(eval.stats());
```

By running the code, we will have the result as follows:

```
=====================Scores======================
Accuracy:  0.7667
Precision: 1
Recall:    0.7667
F1 Score:  0.8679245283018869
===================================================
```

F1 Score, also called F-Score or F-measure, is the harmonic means of precision and recall, and is represented as follows:

$$F_1 = 2.\frac{Precision.Recall}{Precision + Recall}$$

This value is often calculated to measure the model's performance as well. Also, as written in the example, you can see the actual values and predicted values by writing the following:

```
for (int i = 0; i < output.rows(); i++) {
    String actual = test.getLabels().getRow(i).toString().trim();
    String predicted = output.getRow(i).toString().trim();
    log.info("actual " + actual + " vs predicted " + predicted);
}
```

That's it for the whole training and test process. The neural networks in the preceding code are not deep, but you can easily build deep neural networks just by changing the configuration as follows:

```
MultiLayerConfiguration conf = new NeuralNetConfiguration.Builder()
    .seed(seed)
    .iterations(iterations)
    .learningRate(1e-6f)
```