# Machine Learning Algorithms 165

The inputs to the function are described below:

**X**: Predictors.

**Y**: Classes.

The classes names are defined using the following **Name-Value pair:**

**Name**: 'Classsnames'
**Value**: {'Name 1', 'Name 2', 'Name 3'}

The function outputs a trained model *Mdl* which is ready to classify data. A MATLAB simulation demonstrating the use of the *fitcnb* function is described below. The simulation involves using Naive Bayes classification to group petals from Fisher's iris dataset based on their lengths and widths. The iris species names are used as class names. Arrays containing the known set of data are first created using the codes in Listing 3.23:

# Listing 3.23. Naïve Bayes – Load dataset

```
load fisheris
X = meas(:,3:4); % The third and fourth columns of meas contain the length and
widths respectively
Y = species; % Array Y contains the species name for each iris
```

The **fitcnb** function is used to train a Naive Bayes Model based on the petal measurements and their corresponding species names by executing the line of code given in Listing 3.24:

# Listing 3.24. Naïve Bayes – Train model

```
Mdl = fitcnb(X,Y,'ClassNames','setosa','versicolor','virginica'); % Train Naïve
Bayes model
```

The Naive Bayes Model is then used to classify a new iris based on the measurements given in array U by the lines of code given in Listing 3.25. The function **predict** from the Statistics and Machine Learning Toolbox [33] is used to perform this classification.

# Listing 3.25. Naïve Bayes – Classify data

```
U=[5.81 1.7]; % Measurements of petals from unclassified irispredictedspecies =
predict(Mdl,U) %Predict species of the unclassified iris
```