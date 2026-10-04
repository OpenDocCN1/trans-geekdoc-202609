# 482 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoondonon

```
// Using the window size to create an array for the last (window-size) values
double[] pred = new double[window];
// Indexes for the last possible window in the dataset
int arrayIndex = 0;
int lastWindow = ((int) numItems) - window;

// For the last possible sliding window
for (int i = lastWindow; i < numItems; i++) {
    pred[arrayIndex] = (pacRec[i]) / factor;
    arrayIndex = arrayIndex + 1;
}
// Adding the testing set without outputs, i.e., only bearing inputs
testSet.addElement(new TrainingElement(pred));
// For every element in the set (only 1)
for (TrainingElement test : set.trainingElements()) {
    // Setting the neuralNet input values as the inputs
    neuralNet.setInput(test.getInput());
    // Using the trained neural network to calculate the value for the desired timestep
    neuralNet.calculate();
    // Obtaining the output in an array of size 1
double[] output = neuralNet.getAsArray();
    // Multiplying the output by the normalising factor
    mlpPrediction = output[0] * 10000;
    // Printing the inputs used to make the required condition
    System.out.print("Inputs: " + test.getInput());
    System.out.print("Output: " + Math.round(mlpPrediction) + " packets received at time t = " + t + " seconds");
    // Updating the GUI with the result
    predictedValue.setText("Prediction: " + 
        String.valueOf(Math.round(mlpPrediction)) + " packets received");
    accuracy.setText("Accuracy: " + 
        String.valueOf(numberFormat.format(percentageAccuracy)) + "%%");
}
```

#  5.1.13. Downloading to .csv Files

The same download functionalities implemented on both the edge devices, i.e., the Android phone and the Desktop PC, are included for the local server. The coding process, therefore, resembles that of the Desktop Application whereby the combination of the browse and download buttons is used to either download and display specific values by a batch of samples or by date. The download process can in turn be summarised through the same use of the three buttons and principles