# CSVExample.java

In the previous example, we train the model with the dataset used as a benchmark indicator. When you would like to train and test the model with your own prepared data, you can easily import it from CSV. Let's look at CSVExample.java in the CSV package. The first step is to initialize the CSV reader as follows:

```
RecordReader recordReader = new CSVRecordReader(0,",");
```

In DL4J, a class called CSVRecordReader is prepared and you can easily import data from a CSV file. The value of the first argument in the CSVRecordReader class represents how many lines should be skipped in the file. This is convenient when the file contains header rows. The second argument is the delimiter. To actually read a file and import data, the code can be written as follows:

```
recordReader.initialize(new FileSplit(new
ClassPathResource("iris.txt").getFile()));
```

With this code, the file in resources/iris.txt will be imported to the model. The values in the file here are the same as ones as in the Iris dataset. To use this initialized data for model training, we define the iterator as follows:

```
DataSetIterator iterator = new RecordReaderDataSetIterator(recordReader,4,3);
DataSet next = iterator.next();
```

In the previous example, we used the IrisDataSetIterator class, but here the RecordReaderDataSetIterator class is used because we use our own prepared data. The values 4 and 3 are the number of features and labels, respectively.

Building and training a model can be done in almost the same way as the process explained in the previous example. In this example, we build deep neural networks of two hidden layers with the dropout and the rectifier, that is, we have an input layer - hidden layer - hidden layer - output layer, as follows:

```
MultiLayerConfiguration conf = new NeuralNetConfiguration.Builder()
    .seed(seed)
    .iterations(iterations)
    .constrainGradientToUnitNorm(true).useDropConnect(true)
    .learningRate(1e-1)
    .l1(0.3).regularization(true).l2(1e-3)
    .constrainGradientToUnitNorm(true)
    .list(3)
    .layer(0, new DenseLayer.Builder().nIn(numInputs).nOut(3)
        .activation("relu").dropOut(0.5)
        .weightInit(WeightInit.XAVIER)
        .build())
```