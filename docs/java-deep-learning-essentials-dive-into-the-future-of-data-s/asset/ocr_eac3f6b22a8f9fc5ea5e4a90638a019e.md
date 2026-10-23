```
```java
.build())
.layer(2, new DenseLayer.Builder().nIn(4).nOut(4)
        .activation("relu").dropOut(0.5)
        .weightInit(WeightInit.XAVIER)
        .build())
.layer(3, new OutputLayer.Builder(LossFunctions.LossFunction
.NEGATIVELOGLIKELIHOOD)
        .weightInit(WeightInit.XAVIER)
        .activation("softmax")
        .nIn(4).nOut(outputNum).build())
.backprop(true).pretrain(false)
.build();
```
```

# # CNNMnistExample.java/LenetMnistExample.java

CNN is rather complicated compared to other models because of its structure, but we don't need to worry about these complications because we can easily implement CNN with DL4J. Let's take a look at `CNNMnistExample.java` in the package of convolution. In this example, we train the model with the MNIST dataset (http://yann.lecun.com/exdb/mnist/), one of the most famous benchmark indicators. As mentioned in *Chapter 1, Deep Learning Overview*, this dataset contains 70,000 handwritten numbers data from 0 to 9, with both a height and width of 28 pixels each.

First, we define the values necessary for the model:

```
```java
int numRows = 28;
int numColumns = 28;
int nChannels = 1;
int outputNum = 10;
int numSamples = 2000;
int batchSize = 500;
int iterations = 10;
int splitTrainNum = (int) (batchSize*.8);
int seed = 123;
int listenerFreq = iterations/5;
```
```