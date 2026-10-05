

The other neurons do not change their synaptic weights. This is the standard rule of competitive learning. Note that it is a linear combination between the input vector and the vector of synaptic weights, and the smaller the value of the learning rate, the smaller the modification of the synaptic weights. The learning rate of each neuron must be a decreasing function with respect to the stage number, so that after a suitable number of stages the network stabilises and stops learning. During the learning process, an input pattern is introduced at each iteration and the synaptic weights are updated, so that the learning process ends after the data set has been introduced several times.

With this network, neurons learn individually to specialise on sets of patterns and are thus feature detectors. Each vector of synaptic weights represents the prototype of the class or group that defines the corresponding neuron.

This algorithm is similar to MacQueen's K-means algorithm, which consists of assigning each pattern to the nearest centroid and redetermining the centroids of the new groups formed. Ahalt et al. (1990) have shown the convenience of using competitive learning to solve our problem as it leads to optimal or near-optimal solutions.

Ueda and Nakano (1994) have proposed a new competitive learning with a selection mechanism based on the equidistortion principle that allows the network to escape local minima and Uchiyama and Arbib (1994) have shown the relationship between our clustering problem and vector quantization, and present a competitive learning algorithm that generates units where the input data density is high, applying it to colour image segmentation.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.10 SPSS AND neural networks

![image](d2d_images/chapter_title_below.png)

Neural networks are the tool of choice for many predictive data mining applications because of their power, flexibility and ease of use. Predictive neural networks are especially useful in applications where the underlying process is complex; for example:

* Anticipate consumer demand to rationalise production and delivery costs.
* Predict the probability of response to direct mail marketing to determine to which households on a mailing list an offer should be sent.
* To score an applicant in order to determine the risk involved in granting credit.
* Detect fraudulent transactions in an insurance claims database.

Neural networks used in predictive applications, such as multilayer perceptron (`MLP`) and radial basis function (`RBF`) networks, are monitored in the sense that the results predicted by the model can be compared with the known values of the target variables. The neural networks option allows you to fit the `MLP` and `RBF` networks and save the resulting models for scoring.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 6.10.1 Multilayer Perceptron (MLP)

![image](d2d_images/chapter_title_below.png)

The IBM SPSS Multi-Layer Perceptron (`MLP`) procedure generates a predictive model for one or more dependent (target) variables based on the values of the predictor variables. Two situations in which the `MLP` procedure is used are described below:

A bank loan officer wants to be able to identify characteristics that are indicative of individuals who may cause credit delinquency and use these characteristics to identify positive and negative credit risks. Using a sample of past customers, he can train a multilayer perceptron, validate the analysis using a reserved sample of past customers, and then use the network to classify potential customers according to the credit risks they present. A hospital system is interested in tracking the costs and lengths of inpatient stays for myocardial infarction treatment. Obtaining accurate estimates of these measures allows the administration to properly manage the available beds as patients are treated. Using the treatment records of a sample of patients treated for myocardial infarction, the administrator can train a network that predicts both cost and length of stay.

In our case we consider an example similar to the first one presented here. A bank decision-maker has to identify to which customers he can grant a loan with sufficient guarantee of repayment. He has a database with a history of customers in which he knows whether or not the customers have repaid the loan (`CREDIT_V`), the professional category of the customers (`CAT_PROF`), their monthly salary (`PAY_MONTH`), their age (`AGE`) and whether or not they have credit cards (`AMEX`). With this information, it must build a predictive model that predicts the category of the dependent variable (does or does not repay the credit in the variable `CREDIT_V`) in which it must classify any new customer who applies for credit, knowing the values of its independent variables (`CAT_PROF`, `PAYMENT_MONTH` and `AMEX`).

We will use a multilayer Perceptron neural network. To do this, after loading the `credits.sav` file containing the information on the variables mentioned above into memory, we choose from the SPSS menus `Analyse → Neural Networks → Multilayer Perceptron` (Figure 6-4).

![image](d2d_images/image060.png)

Figure 6-4

The Multilayer Perceptron screen is obtained, in whose Variables tab (Figure 6-5) we define the dependent variable(s) of the model, the categorical independent variables (Factors) and the metric independent variables (Covariates). In the Partitions tab (Figure 6-6) we define the percentage of cases in the file that we will dedicate to network training, testing and reservation. In the Architecture tab (Figure 6-7) we define the architecture of the neural network by allowing automatic selection of the architecture (recommended option) or by customising the number of hidden layers of the network, the number of units, the activation function, the activation function of the output layer and the scaling of the scale dependent variables. In the Training tab (Figure 6-8) the training type, the optimisation algorithm and the training options are defined. The Results tab (Figure 6-9) defines the results to be obtained in the neural network model adjustment, both for the structure of the network, as well as for its performance and summary of case processing and importance of the independent variables. In the Save tab (Figure 6-10) we define the variables to be saved in the data file (predicted category of the dependent variables and their probabilities). In the Export tab (Figure 6-11) we can decide to export the synaptic weights to an XML file. In the Options tab (Figure 6-12) we can define the treatment of missing values, the stopping rules, the training time of the network, the data used to calculate the prediction error, the number of cases to store in memory and other values to adjust the network.

![image](d2d_images/image602.png)

Figure 6-5

![image](d2d_images/image601.png)

Figure 6-6

![image](d2d_images/image516.png)

Figure 6-7

![image](d2d_images/image504.png)

Figure 6-8

![image](d2d_images/image432.png)

Figure 6-9

![image](d2d_images/image313.png)

Figure 6-10

![image](d2d_images/image274.png)

Figure 6-11

![image](d2d_images/image518.png)

Figure 6-12

Clicking OK produces the output. A summary of cases and network information is shown in Figure 6-13.

![image](d2d_images/image042.png)

Figure 6-13

