random forest represents one class prediction, and the class with the most votes become our model’s result.

5. *Extremely randomized trees classifier* [26]: Extremely randomized trees classifier (extra trees classifier) is a type of ensemble learning algorithm that aggregates the results of multiple decorrelated decision trees collected in a forest to output its result. Extra trees classifier is very similar to a random forest classifier and only differs from it in constructing the decision trees in the forest. Unlike random forest, which uses a greedy algorithm to select an optimal split point, the different trees algorithm selects a split point at random.

6. *Logistic regression with LASSO* [27]: Logistic regression is a statistical approach that uses a logistic function to classify the input into a binary variable. However, this model always faces overfitting issue. For that, as a method of regularization, LASSO helps the model improve the issue to enhance the interpretability of the resulting statistical model.

# 16.4 PERFORMANCE EVALUATION

In the following section, we first introduce how to prepare the IFA dataset, set up the experiments, and evaluate the performance of IFA and the result of IFA performance. We then introduce how to prepossess the dataset collected. Lastly, we introduce how to evaluate the performance of machine learning and then show the result.

# 16.4.1 Methodology

Based on the attacking scenarios in section 16.3, we generate IFA network traffic. As mentioned in section 16.3, we have defined two attacking scenarios, small scale and large scale. We use ns3 [28] as our main simulation platform and NDNsim [29] as the running protocol in ns3.

For the configuration of both attacking scenarios, we set up the following: (1) The simulation is fixed to 900 seconds. (2) All the legitimate users only send the request at a maximized data rate but do not bypass network congestion. This variable is calculated on the network topology