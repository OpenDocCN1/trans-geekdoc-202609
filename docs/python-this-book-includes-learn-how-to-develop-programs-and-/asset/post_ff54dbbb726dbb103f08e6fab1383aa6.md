
learn to attain equal class distribution in the training and the test sets. Let's look at the parameters of StratifiedShuffleSplit:

The first parameter describes the input dataset. You pass all the rows and the last column. The test size is described by the test_size variable, which was initially declared. You can make an assumption that you need only one split applying the n_iter variable. Next, we proceed to trigger the print_class_label_split to display the class label distribution. Let's look at the output:

| Train data set class label distribution |
|--- |
| Class label =0, percentage records =0.33 |
| Class label =1, percentage records =0.33 |
| Class label =2, percentage records =0.33 |

| Test data set class label distribution |
|--- |
| Class label =0, percentage records =0.33 |
| Class label =1, percentage records =0.33 |
| Class label =2, percentage records =0.33 |

Now, you have the class labels distributed uniformly between the test and train sets.
Still, there's more....
You need to prepare the data carefully before it's applied in the machine learning algorithm. Providing a uniform class distribution to both the train and test sets is necessary for creating a successful model. When it comes to machine learning cases, you build another dataset known as dev set you might not get your model right during the first iteration. However, you don't want to reveal the test dataset to the model because this may create some bias in model building. The 80/20 rule of thumb is a great scenario. But in most practical applications, you may not have sufficient data to leave out many instances. There are different techniques that come into play.

## Identifying Nearest Neighbors

Before we dive in, let's take time to understand whether the classification model is working to satisfaction. At one point in the chapter, we discussed the confusion matrix. A confusion matrix refers to the arrangement of actual versus predicted class labels. Say, for example, you have a two-class problem that can take value T or F. Assume you have trained a classifier to predict y. Then you can complete your confusion matrix using this:

| | Predicted |
|---|---|---|
| **Actual** | TP | FP |
| | FN | TN |

In the above table, it is important to list the results from the test set. Keep in mind that you know the class labels in the test set; thus you can compare the classification model output with the actual label.

- TP stands for True Positive, it has a count of all records within the test set whose labels feature T and where the model predicted T.
- FN stands for False Negative, which you have a count of all the records.
- FP stands for False Positive, where the actual label is F but the algorithm predicted as T.
- TN stands for True Negative, where the algorithm predicted both the original label as F.

With the above knowledge about the confusion matrix, you can extract performance metrics using the quality of our classification model.

Accuracy is defined as the ratio of correct prediction to the total number of predictions. From the confusion matrix, you know that the sum of TP and TN totals the number of correct predictions. Accuracy from the training set is normally very optimistic. It is important to consider the test set's accuracy value to define the performance of the model.

The first classification problem that you will consider is k-nearest neighbor, shortened as KNN. Before jumping to details of KNN, let's consider a simple classification algorithm known as the rote classifier that memorizes the whole training data; it loads all the data within the memory. You need to conduct classification on an unseen training instance. You will try to match the new training instance using any of the training instances within the memory. It will match each attribute within the training instance. In case it discovers a match, it predicts the class label of the test insurance as the class label of the matched training instance. So far, you need to know that this classifier will fail if the test instance isn't similar to any of the training instances loaded into the memory.

KNN resembles the rote classifier, except that instead of searching for an exact match, it applies a similarity measure. Resem the rote classifier, KNN loads all the training sets into the memory. When it requires to classify a test instance, it determines the distance between the test instance and all the training instances. Using the above distance, it selects K closest instances within the training set. Next, the prediction for the test set is defined based on the number of nearest neighbors. For example, if you have a two-class classification problem and select the K value as three, and if the test record's three nearest neighbors have classes 1, 1, and 0, it will categorize the test instance as 1, which is popular. KNN is part of the family of algorithms known as instance-based learning. Besides, the decision to categorize a test instance is considered last; it is also known as a lazy learner.

For this algorithm, you will generate some data by making use of the scikit_classification method. This will produce a matrix of four columns and 100 instances: The get_data function internally requests make_classification to produce data for any classification task.

It's always a great practice to visualize the data before beginning to feed it into any algorithm. The plot_data function generates a scatter plot between the variables.

![](img/43582740ac1227a817786ef73e0f3772_264_0.png)

In the above diagram, you have plotted all the variable combinations. The top two charts demonstrate combinations between the 0th and 1st column, followed by 0th and 2nd. The points are also colored using their class labels. This presents a hint of how much information is available for variable combinations to perform a classification task.

## How to Achieve It

You will need to divide your dataset preparation and model training into two different methods: get_train_test to find the train and test data, and build your model. Finally, you will apply the test_model to verify the usefulness of the model.

## How it Operates

You must start by calling get_data and plotting it using plot_data. It is also important to separate a section of the training data for the testing that is required to determine the model. Next, invoke the get_train_test to achieve the same. The 80/20 rule of thumb is a great scenario. But in most practical applications, you may not have sufficient data to leave out many instances. There are different techniques that come into play. combine both x and y to a single matrix using NumPy’s column_stack method. Next, leverage StratifiedShuffleSplit to attain an equal class distribution between the training and test sets.

Armed with the following train and test sets, you should be ready to create a classifier. You must trigger the build model using the training set, class labels y, and attributes x. This function also accepts K, the number of neighbors, as a parameter, with a default value of two. We apply scikit-learn's KNNClassifier. Then build an object of the classifier and call fit method to create the model. You should be ready to test how good the module is by leveraging on the training data. You can pass the training data (x and y) and model to the test_model function. You know the actual labels (y). Invoke the predict function using x to get the predicted labels. Next, some of the model evaluation metrics. You can then begin with printing the accuracy of the model, follow it using a confusion matrix, and then display the output of a function known as classification_report. Scikit-learn's metrics module offer a function called classification_report, which can display different evaluation metrics. Let's explore the model metrics:

| Model evaluation on training set |
|--------------------------------|
| Model accuracy - 91.25% |
| Confusion Matrix |
|=================
| array([[40, 0], [7, 53]]) |
| None |
| Classification Report |
| precision | recall | f1-score | support |
| 0.0 | 0.85 | 1.00 | 0.92 | 40 |
| 1.0 | 1.00 | 0.82 | 0.90 | 40 |
| avg / total | 0.93 | 0.91 | 0.91 | 80 |

As you can see, the accuracy is 91.25 percent. You will not repeat the definition accuracy; you can refer to the introduction part. Let's consider the confusion matrix. The top-left cell represents a positive cell. You should see that there are no false negatives, but there are seven false positives. Lastly, you have precision, remember an F1 score, and support within the
