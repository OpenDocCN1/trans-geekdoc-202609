
# Machine Learning Algorithms

- 1. Maximum time step for each episode= 50
- 2. Maximum number of episodes= 300
- 3. Training termination criterion: Stop when the average reward is greater than 10 over 20 consecutive episodes

The MATLAB codes for setting up the above training parameters are given in List 35.0:

# Listing 35.0. SARSA– Define training parameters

```
trainOpts = rlTrainingOptions; % For defining training parameters
trainOpts.MaxStepsPerEpisode = 50; % Specify maximum time step for each episode
trainOpts.MaxEpisodes = 300; % Specify maximum number of training episodes
trainOpts.StopTrainingCriteria = "AverageReward"; % Specify the criterion for ending
training
trainOpts.StopTrainingValue = 11; % Specify training termination criterion
trainOpts.ScoreAveragingWindowLength = 20;
```

In List 35.1, the function is used to start the agent in the Basic Grid World environment.

# Listing 35.1. SARSA– Start training

```
trainStats = train(sarsaAgent,env,trainOpts); % Start training
```

The above line of code opens MATLAB’s Episode Manager window which displays the progress of the training, as shown in Figure 3.29.

![](img/2b52fde0e707e8c2f05a10309c3f8982_210_0.png)

Figure 3.29. SARSA– MATLAB’s Episode Manager.

200 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondumon

The training is stopped after the training termination criterion has been met. A visualisation of the environment is set up using the codes given in Listing 3.52 so that the actions taken by the agent can observe:

# Listing 3.52. SARSA– Visualise environment

```
plot(env) % Plot the Basic Grid World
env.Model.Viewer.ShowTrace = true; % Show path taken
env.Model.Viewer.clearTrace; % Clear any existing trace
```

In Listing 3.53, the sim function is then used to simulate the agent in the environment:

# Listing 3.53. SARSA– Simulate agent in the environment

```
sim(sarsaAgent.env) % Simulate agent in the environment
```

At the end of the simulation, the trace of the path taken by the agent is generated as shown in Figure 3.30. The trace shows that the agent has taken the optimal path which includes the jump from the cell [2,4] to [4,4], hence achieving the highest reward in the environment.

![](img/2b52fde0e707e8c2f05a10309c3f8982_211_0.png)

Figure 3.30. SARSA- Agent's path trace.

## 3.6. ENSEMBLE LEARNING ALGORITHMS

## 3.6.1. Random Forest

A random forest consists of a large number of decision trees that work together as an ensemble. The layout of a random forest is given in Figure 3.31. Decision trees consist of decision nodes that branch to leaf nodes which represent the outcome. Each branch represents a decision rule. The predictions of all the decision trees are used to derive a final prediction [57].

Random forest may be used for classification and regression [58]. Basically, having a group of decision trees to perform classification or regression will outperform any individual constituent decision tree.

![](img/2b52fde0e707e8c2f05a10309c3f8982_212_0.png)

Figure 3.31. Random Forest- Typical Layout.

## Short-hand Example 12

In this example, random forest is used to help a user select the most appropriate internet offer for an internet connection with a 100 Mbps download speed among two internet service providers. The requirements of the user are:

- Upload speed > 30 Mbps
- Volume allowance > 1 TB
- Monthly subscription price < $100
- Wireless access point shall be included
- Installation cost < $10

Using the above requirements, a random forest is built:

202 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Son and M. Indoondonon

![](img/2b52fde0e707e8c2f05a10309c3f8982_213_0.png)

Figure 3.32. Random Forest- Random forest for selection given internet service offer.

The first internet service provider has the offer given in Table 3.17:

# Table 3.17. Random forest – Offer from first internet service provider

| Upload Speed | 50 Mbps |
| --- | --- |
| Volume Allowance | 500 GB |
| Price | $80 |
| Wireless Access Points | Included |
| Installation cost | $15 |

The details in the above table are used with the random forest to determine if the user should subscribe to the internet service provider:

![](img/2b52fde0e707e8c2f05a10309c3f8982_213_1.png)

Figure 3.33. Random Forest- Results for first internet service provider's offer.

Based on the majority of votes from the decision trees, the first internet service provider's offer is rejected.

The offer from the second internet service provider is given in Table 3.18:

### ### Table 3.18. Random forest – Offer from second internet service provider

| Upload Speed | 40 Mbps |
| Volume Allowance | 1 TB |
| Price | $90 |
| Wireless Access Points | Included |
| Installation cost | $15 |

The second offer is processed by the random forest to determine if the user should subscribe to the second internet service provider:

![](img/2b52fde0e707e8c2f05a10309c3f8982_214_0.png)

Figure 3.34. Random Forest- Results for second internet service provider's.

The majority of the votes from the decision trees indicate that the offer from the second internet service providers is appropriate for the user.

The fitensemble function from MATLAB's Statistics and Machine Learning Toolbox can be used to create a trained random ensemble classification model with 100 decision trees [59]. The syntax of the function is as follows:

```
**Mdl=fitensemble(Tbl,ResponseVarName,Name,Value)**
```

The inputs to the function are described below:

**Tbl:** Training data set in the form of a table.

**ResponseVarName:** Name of the response variable in Tbl. For data classification, this refers to the class name.

204 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonon

Name-Value pair: In the case where the random forest technique is used, the two Name-Value pair given in Table 3.19 must be defined:

# Table 3.19. Random Forest – Name-Value pair

| Name | Value | Description |
| --- | --- | --- |
| Method' | 'Bag' | The ensemble aggregation method for random forest must be defined as Bag so that the function bagging with random predictor selectors at each branch node. |
| 'Learners' | templateTree | A template object with parameters of the decision trees must be created and input to the fittest function. |

A MATLAB simulation demonstrating the use of the fitensemble function is described below. The simulation involves using the random forest technique for the classification of iris from Fisher's iris dataset based on their petals' measurements.
First of all, Fisher's iris dataset is loaded in the MATLAB workspace using the codes given in Listing 3.54:

# Listing 3.54. Random Forest– Load dataset

```
rng(1); % For reproducibility
load fisheriris
```

In Listing 3.55, the partition function is used to create a random partition in the data so that 80% of the data is used for training the model and 20% is used for testing it. The training dataset is then compiled in a table tblTr. Each row in the table consists of one iris and each column represents a measurement. The iris species names which can be considered as the class names are placed in the last column.

# Listing 3.55. Random Forest– Divide dataset

```
load fisheriris
N = size(meas,1);
cvp = partition(N,'Holdout',0.2); % Partition data in training and test sets
idxTrn = training(cvp); % Training set indices
idxTest = test(cvp); % Test set indices
% Create training dataset table
tblTr = array2table(meas(idxTrn));
tblTr.Y = species(idxTrn);
```

A decision tree template having a maximum of 119 branch nodes is created using the codes in Listing 3.56. The number of branch nodes must be $n-1$ where $n$ is the number of observations in the training set [60]. In this case,

# Machine Learning Algorithms 205

where 80% of the set of 150 rises are used as training data, 120 observations are made during the training.

# Listing 3.56. Random Forest– Create decision tree template

```
t = templateTree('MaxNumSplits',119); % Create the decision tree template
Mdi = fitensemble(tblTnr,'Y','Method','Bag','Learners',t); % Train model random forest and defining columns Y in tblTnr as the class name
```

Finally, the model is tested to predict the iris species of the test dataset based only on their measurements using the predict function from MATLAB’s Statistics and Machine Learning Toolbox as shown in Listing 3.57.

# Listing 3.57. Random Forest– Predict iris using

```
labels = predict(Mdi,meas,idxTest); % Predict iris names of training data
```

In Listing 3.58, a confusion chart is built using the confusionchart from MATLAB’s Statistics and Machine Learning Toolbox to visualise the accuracy of predictions by comparing the predicted rises’ species names of the training data to their actual names.

# Listing 3.58. Random Forest– Build confusion chart

```
confusionchart(species(idxTest),labels) % Build confusion chart
```

The above code generate the confusion chart showing that 28 of 30 rises have been properly classified.

![](img/2b52fde0e707e8c2f05a10309c3f8982_216_0.png)

Figure 3.35. Random Forest– Confusion chart.
