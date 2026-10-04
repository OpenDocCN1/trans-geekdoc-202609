# 458 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonondon

4. The same principles of KNN classification are used for this database, as shown in steps 1 and 2 but they are catered for, using the fetchClassificationValuesLTE() and KNNClassificationLTE() methods respectively. To calculate the accuracy, the KNNAccuracyLTE() method is used. These methods are similar in the logic used but differ in the sense that different queries are used for the fetching process, with different arrays filled for the analytics. They are provided on the book's website.

# 5.1.11.5. Classifying Networks Using Multilayer Perceptron (MLP)

This section elaborates on the pre-processing performed on the dataset which is fed into the algorithm. To illustrate the process of MLP classification, Figure 5.15 shows the different objects denoted as dataRow and testinstance, which represent the original dataset with pre-labelled values and the set of values to be classified respectively. To classify a particular tuple, classifyInstance() is used. These variables and methods are employed in Listing 5.15.

| Original dataset | Upload Speed | Packets Received | Packets Sent | Actual Class | Predicted Class |
|---|---|---|---|---||
| | 2 | 11 | 18 | | 1 |
| | 129 | 13 | 179 | 91 | | 2 |
| | 2368 | 51 | 1678 | 796 | | 3 |
| Set to classify | 500 | 10 | 500 | | 1 |

Figure 5.15. Illustration of MLP classification.

# 5.1.11.6. Performing Multilayer Perceptron (MLP) Classification

This section focuses on the classification of network parameters using the MLP algorithm by employing the Weka library to facilitate the training of the neural network. Since two different devices are being used, the tuning of the parameters to train the dataset is different for each. The classification is performed using the Classification() method defined in LocServer.java and is called just after the fetchClassificationValues() method in the “Predict” button as shown in Section 5.10. The steps involved in this section are as follows and based on the logic explained in Section 5.1.1.5.

+   - Creating an Instances object to hold the dataset from the fetchClassificationValues() method.
- Creating a MultilayerPerceptron object which will carry out the training process.
- Using the Instances to set the last column of the dataset as the one to be classified.
- Allocating different neural network parameters such as learning rate, time, number of hidden layers and momentum separately each device.