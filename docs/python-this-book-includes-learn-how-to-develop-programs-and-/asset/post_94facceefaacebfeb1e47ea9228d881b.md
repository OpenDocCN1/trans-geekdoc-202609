
# Step 3 – To assign the Opportunity Result column as “target”, use command `target = sales_data['Opportunity Result']` data.head(n=2).

The “Opportunity Number” column was removed since it just acts as a unique identifier for each record. The “Opportunity Result” contains the predictions we want to generate, so it becomes our “target” variable and can be removed from the data set for this phase. The first line of the above code will select all the columns except “Opportunity Number” & “Opportunity Result” in. These columns are then assigned to the “cols” variable, a new data framework was developed. Using the columns in the “cols” variable, a new data framework is going to be the “feature set.” Next, the column “Opportunity Result” from the `sales_data` data frame was used to develop a new data framework called “target.”

The second phase in this stage is to separate the data frames into training and testing subsets using the steps below. Depending on the data set and desired predictions, it needs to be split into training and testing subset accordingly. For this exercise, we will use 75% of the data as a training subset, and 25% will be used for the testing subset. We will leverage the `train_test_split()` technique in Scikit-Learn in order to separate the information using steps and code as follows:

- Step 1 – To import the required module, use the command `sklearn.model_selection import train_test_split`.
- Step 2 – To separate the data set, use command “split data set into train and test setsdata_train, data_test, target_train, target_test = train_test_split(data, test_size=0.30, random_state=10)”.

With the code above, the “train_test_split” module was first imported, followed by the use of “train_test_split() technique to generate “training subset (data_train, target_train)” and “testing subset (data_test, data_train).” The “train_test_split() technique’s first argument pertains to the features that were divided in the preceding stage, the next argument relates to the (“Opportunity Result”) target. We are using 30% for this example, although it can be any amount. The fourth ‘random state’ argument is used to make sure that the results can be reproduced every time.

# Building the Machine Learning Model

The “machine_learning_map” provided by Scikit-Learn is widely used to choose the most appropriate ML algorithm for the data set. For this exercise, we will be using “Linear Support Vector Classification” and “K-nearest neighbors’ classifier” algorithms.

# Linear Support Vector Classification

“Linear Support Vector Classification” or “Linear SVC” is a sub-classification of “Support Vector Machine (SVM)” algorithm, which we have reviewed in chapter 2 of this book titled “Machine Learning Algorithms.” Using Linear SVC, the data can be divided into different planes so the algorithm can identify the optimal group structure for all the data classes.

Here are the steps and code for this algorithm to build our first ML model:

- **Step 1** – To import the required modules, use commands `sklearn.svm import LinearSVC` and `from sklearn.metrics import accuracy_score`.
- **Step 2** – To develop a LinearSVC object type, use command `svc_model = LinearSVC(random_state=0)`.
- **Step 3** – In training the algorithm and generating predictions from the testing data, use command `pred = svc_model.fit(data_train, target_train).predict(data_test)`.
- **Step 4** – To display the model accuracy score, use command `print('LinearSVC accuracy:', accuracy_score(target_test, pred, normalize=True))`.

With the code above, the required modules were imported in the first step. We then developed a type of Linear SVC using the “svc_model” object with “random_state” as ‘0’. In step 3, the “Linear SVC” algorithm is trained on the training data and subsequently used to generate predictions for the testing data. The “accuracy_score() technique was used in the end to verify the “accuracy score” of the model, which could be displayed as “LinearSVC accuracy: 0.777811004785”, for instance.

# K-nearest Neighbors Classifier

The “k-nearest neighbors (k-NN)” algorithm is referred to as “a non-parametric method used for classification and regression in pattern recognition.” In cases of classification and regression, “the input consists of nearest k closest training examples in the feature space.” K-NN is a form of “instance-based learning,” or “lazy learning,” in which the function is only locally estimated, and all calculations are delayed until classification. The output is driven by the fact, whether the classification or regression method is used for “k-NN”

- “k-nearest neighbors classification” - The “output” is a member of the class. “object” is classified by its neighbors’ plurality vote, assigning the object to the most prevalent class among its nearest “k-neighbors,” where “k” denotes a small positive integer. If k=1, the “object” is simply allocated to the closest neighbor’s class.
- “k-nearest neighbors regression” - The output is the object’s property value, which is computed as an average of the k-nearest neighbors’ values.

A helpful method for both classification and regression can be assigning weights to the neighbors’ contributions to allow closer neighbors to make more contributions in the average compared to the neighbors far apart. For instance, a known “weighting scheme” is to assign each neighbor a weight of “1/d,” where “d” denotes the distance from the neighbor. The neighbors are selected from a set of objects for which the “class” (for “k-NN classification”) or the feature value of the “object” (for “k-NN regression”) is known.

Here are the steps and code for this algorithm to build our new ML model:

Step 1 – To import required modules, use the command “from sklearn.neighbors import KNNClassifier” and “from sklearn.metrics import accuracy_score”.

Step 2 – In creating the object of the classifier, use command “neigh = KNeighborsClassifier(n_neighbors=3)”.

Step 3 – In training the algorithm, use command “neigh.fit(data_train, target_train).”

Step 4 – To generate predictions, use command “pred = neigh.predict(data_test)”

Step 5 – To evaluate the accuracy, use command “print (‘KNeighbors accuracy score:’, accuracy_score(target_test, pred)).”

Now that our preferred algorithms have been introduced, the model with the highest accuracy score can be easily selected. In Scikit-Learn, the “Yellowbrick library” can be used, which offers techniques to depict visually.

# Data Visualization with Scatter Plots

A scatter plot can be defined as a “two-dimensional visualization that uses dots to represent the values obtained for two variables-one plotted along the x-axis, and the other plotted along the y-axis. It is also known as a “scatter graph” or “scatter chart.” For instance, the "scatter plot" seen in the picture below depicts a fictional set of height and weight measures for children. Each "dot" in the plot is used to represent an individual with measures of height along the "x-axis" and weight along the "y-axis."

![img/43582740ac1227a817786ef73e0f3772_143_0.png

“Scatter plots” are highly useful when you are interested in representing the relationship that exists between two variables. “Scatter plots” are often referred to as “plots of correlation,” given the fact that they demonstrate how two distinct variables are related to each other. In the "scatter plot" above, the chart depicts much more than a simple log of the height and weight of children. It also offers a visual of the relationship between the two, denoting that as the height increases, the child's weight is also increasing. Now, you can easily conclude that this height and weight relationship isn't ideal, as some taller kids can weigh less than shorter kids, but the overall trend is fairly satisfactory, and it can be observed that there is a direct relationship between the height and weight of children.

It is important to remember that not all relationships can be linear. For instance, the chart in the picture below indicates an "average of daily high temperature" measured over 7 years, demonstrating a familiar parabolic relationship between these variables as the daily high temperature tends to peak during summer.

![img/43582740ac1227a817786ef73e0f3772_144_0.png

Scatter plots” often contain a trend-line to clarify the relationship between the variable, as shown in the picture below.

![img/43582740ac1227a817786ef73e0f3772_144_1.png]
