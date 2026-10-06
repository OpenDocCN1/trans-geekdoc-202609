# Defining a task and learner to implement k-nearest neighbors (k-NNs) in mlr3

In step 2, we specify the learner: the type of ML we will be doing. mlr3 has two types of learners—classifiers and regressions. The learn () function helps us create this object, but there are only a couple of built-in learners. We must first load the accessory package mlr3learners to access a wider range, select .knn to the k-NN implementation in the kknn package (which must also be installed manually). If we inspect the learner object as created by default, we see the following:

```
## <LearnerClassifyKNN:class.knn>
* Model: list
* Parameters: k=7
* Packages: mlr3, mlr3learners, kknn
* Predict Types: [response], prob
* Feature Types: logical, numeric, factor, ordered
* Properties: multiclass, twoclass
```

There is useful information, as the feature types and the predictions we can make, that we can train a model like this. Inspecting the object is a quick way to see the parameters, but we can set them. Here, we see that the parameter for k-NN is k, and at the moment it is set to 7. So, just alter the value of k using the $ syntax. Its usage may be a little unfamiliar to you, so just think of this as meaning that the function we need is stored in the object itself and the $ lets us drill down to it. After using the learner$param_set$set_values() function to set k to 4, we see that the contents of the learner are:

```
## <LearnerClassifyKNN:class.knn>
* Model: list
* Parameters: k=4
* Packages: mlr3, mlr3learners, kknn
* Predict Types: [response], prob
* Feature Types: logical, numeric, factor, ordered
* Properties: multiclass, twoclass
```

In step 3, we use the partition () to set up the test/training split of the data. The ratio argument sets the proportion of the data to use in training. A random split is made and the row numbers of the set that each assigned to serve are.

In step 4, we're ready to go. We just have to ask the learner object to train itself, using the $train() function, performing the preprocessed task and split task. We can inspect the model produced here using the learner$model() function.