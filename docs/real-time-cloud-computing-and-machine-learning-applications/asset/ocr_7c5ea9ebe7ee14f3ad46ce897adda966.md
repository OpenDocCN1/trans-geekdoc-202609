![](bbox=[0.248, 0.101, 0.751, 0.415])

Figure 3.22. Multi-layered Perceptrons- Predicted output compared to the expected output.

The plot in Figure 3.22 shows that the trained MLP is capable of providing outputs that closely match the expected outputs. In the scenario where MLP is used for classification, the patternnet function from MATLAB's Deep Learning Toolbox is used [43]. The syntax of the function is as follows:

```
net= patternnet(hiddenSizes)
```

hiddenSizes: Size of the hidden layers given in a row vector in which each column corresponds to a hidden layer and each column gives the number of neurons in that layer.

The function outputs net which the feed-forward network in a network object form.

An example demonstrating the use of MLP for classification is given below.

In this example, arises from Fisher's dataset are classified into three classes based on their measurements. Firstly, training the data is loaded to MATLAB's workspace using the codes given in Listing 3.30. Matrix x is loaded with the measurements and matrix t is loaded with class details. Matrix t has three rows and 150 columns. Each column is assigned to one iris and a '1' in one of the 3 rows identifies the iris's class index (ranging from 1 to 3) [43]:

# Listing 3.30. Multi-Layered perceptrons classification- Load training data

```
[x,t] = iris_dataset; % Load predictors and responses into x and t respectively
```