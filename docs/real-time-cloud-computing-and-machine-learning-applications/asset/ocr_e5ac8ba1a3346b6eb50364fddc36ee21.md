# Machine Learning Algorithms 205

where 80% of the set of 150 rises are used as training data, 120 observations are made during the training.

# Listing 3.56. Random Forest– Create decision tree template

| t = templateTree('MaxNumSplits',119); % Create the decision tree template Mdi = fitensemble(tblTnr,'Y','Method','Bag','Learners',t); % Train model random forest and defining columns Y in tblTnr as the class name |

Finally, the model is tested to predict the iris species of the test dataset based only on their measurements using the predict function from MATLAB’s Statistics and Machine Learning Toolbox as shown in Listing 3.57.

# Listing 3.57. Random Forest– Predict iris using

| labels = predict(Mdi,meas,idxTest,); % Predict iris names of training data |

In Listing 3.58, a confusion chart is built using the confusionchart from MATLAB’s Statistics and Machine Learning Toolbox to visualise the accuracy of predictions by comparing the predicted rises’ species names of the training data to their actual names.

# Listing 3.58. Random Forest– Build confusion chart

| confusionchart(species(idxTest),labels) % Build confusion chart |

The above code generate the confusion chart showing that 28 of 30 rises have been properly classified.

![](bbox=[0.288, 0.6563300000000001, 0.712, 0.916])

Figure 3.35. Random Forest– Confusion chart.