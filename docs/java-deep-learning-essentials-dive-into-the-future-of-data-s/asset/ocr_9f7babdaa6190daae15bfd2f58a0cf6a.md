The graphical model of this example is as follows:

![](bbox=[0.17, 0.17, 0.82, 0.43])

After the building comes the training. Since we have multiple mini-batches, we need to iterate training through all the batches. This can be achieved easily using .hasNext() on DataSetIterator and mnistIter in this case. The whole training process can be written as follows:

```
model.setListeners(Arrays.asList((IterationListener) new ScoreIterationListener(listenerFreq)));
while(mnistIter.hasNext()) {
    mnist = mnistIter.next();
    trainTest = mnist.splitTestAndTrain(splitTrainNum, new Random(seed));
    trainInput = trainTest.getTrain();
    testInput.add(trainTest.getTest().getFeatureMatrix());
    testLabels.add(trainTest.getTest().getLabels());
    model.fit(trainInput);
}
```

Here, the test data and test labels are stocked for further use.