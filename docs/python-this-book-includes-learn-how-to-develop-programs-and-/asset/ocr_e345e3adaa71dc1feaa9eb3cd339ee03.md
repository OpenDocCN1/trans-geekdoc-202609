As you can see, 80 percent of the 150 rows, that is, 120 records, have been allocated to the training set. You have seen how you can easily divide input data into the train and the test sets.
Remember, this is a classification challenge. The algorithm has to be trained to predict the right class label for a specific unknown instance. For this, you need to present the algorithm and equal distribution of all the classes at the time of training. The Iris dataset represents a three-class problem. You need to have equal representation from all three classes. Let's find out whether the method has taken care of this.

It is important to define a function called get_class_distribution, which selects a single y parameter's array of class labels. This function outputs a dictionary, where the key represents the class label, and the value represents the percentage of records for this particular distribution. Therefore, the following dictionary represents the distribution of the class labels. You need to call this function in the following function to understand what the class distribution is on the train and the test datasets.

The print_class_label_split function is straightforward. You need to pass the train and the test datasets as the argument. Since you concatenated x and y, the last column is our classical label. Next, you extract the train and test class labels in y_train and y_test. You pass them to attain get_class_distribution to find a dictionary of the class labels and lastly, you print it.

You then invoke print_class_label_split, and the output should appear as follows:

Train data set class label distribution
---------------------------------------
Class label =0, percentage records =0.36
Class label =-1, percentage records =0.32
Class label =-2, percentage records =0.33

Test data set class label distribution
---------------------------------------
Class label =0, percentage records =0.23
Class label =-1, percentage records =0.40
Class label =-2, percentage records =0.37

Let's determine the output. As you can see, the training features different distribution of the class labels compared with the test set datasets.
In the last section of code, you make use of stratifiedshufflesplit from scikit-