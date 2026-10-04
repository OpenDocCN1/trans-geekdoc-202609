# Server and Servlet Architectures for a Cloud-Based Real-Time .

+   * Training the classifier using the buildClassifier() method from the MultilayerPerceptron class.
* Creating an Evaluation object that acts upon the MultilayerPerceptron object as well as the training dataset that specific training parameters can be retrieved and printed.
* Using the classifyInstance() method to classify each dataRaw object through a loop iterating through all the records in the object.
* Comparing the predicted value to the actual value using a double object denoted as allError.
* Calculating the number of incorrect predictions and thus determining the percentage accuracy.
* Fetching the user-input values to be classified from the GUI and passing them as a double [] into a DenseInstance object. It should be noted that despite using four variables, a dummy category is provided as well as the last value in the double [] object.
* The obtained classification is rounded to the nearest Integer which belongs to either 1, 2 or 3.
* The number is converted to its appropriate String object before being printed on the GUI.

It should be noted that the algorithm classifies an instance on a decimal scale from 0 to 3. This means the classification is more accurate if the returned value is closer to an integer. The rounding process, performed using the Math.round() operation from the JAMA library introduces back the numerical label.
The tuning of the hyper-parameters for the three cases namely the Desktop PC, the Android phone with Wi-Fi, and LTE values, are performed differently, as per Table 5.12.

# Table 5.12. Tuning parameters for MLP classification

| Parameter | PC (Wi-Fi) | Android (Wi-Fi) | Android (LTE) |
|---|---|---|--—|
| Learning rate | 0.1 | 0.0001 | 0.1 |
| Momentum | 0.2 | 0.1 | 0.1 |
| Epochs | 3000 | 7000 | 7000 |
| Hidden layers | 8 | 15 | 15 |

As observed in Table 5.12, the main differences in hyper-parameters lie between the PC and the Android databases. These differences are explained as follows:

+   * Learning rate: With the learning rate controlling how quickly the model adapts to the problem [ 15,16], a relatively higher one is chosen for the PC because rounded integers are used for the download and upload parameters while the Android phone values to three decimal places. This