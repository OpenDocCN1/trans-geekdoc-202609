
# Technical requirements

We will use renv to manage packages in a project-specific way. To use renv to install packages, you will first need to install the renv package. You can do this by running the following commands in your R console:

- 1. Install renv:

```
install.packages("renv")
```

- 2. Create a new renv environment:

```
renv::init()
```

This will create a new directory called .renv in your current project directory.
You can then install packages with the following:

```
renv::install_packages()
```

- 3. You can also use the renv package manager to install Bioconductor packages by running the following command:

```
renv::install("bioc::package name")
```

- 4. For example, to install the Biobase package, you would run the following:

```
renv::install("bioc::Biobase")
```

- 5. You can use renv to install development packages from GitHub by writing this:

```
renv::install("user name/repo name")
```

- 6. For example, to install the user danmaclean package rbioinfocookbook, you would run:

```
renv::install("danmaclean/rbioinfocookbook")
```

You can also install multiple packages at once by separating the package names using commas. renv will automatically handle any required dependencies for the packages you install.

Under renv, all packages will be installed into the local project directory and not the main central library, meaning you can have multiple versions of the same package, one specific to each project.

All the sample data you need for this package is in the specially created data package on GitHub: danmaclean/rbioinfocookbook. The data will become available in your project after installing that.

For this chapter, we'll need the following packages:

- Regular packages:
    - DALExtra
    - dplyr
    - factoextra
    - ggplot2
    - iml
    - magrittr
    - mlbench
    - mlr3
    - mlr3learners
    - mlr3pipelines
    - mlr3tuning
    - mlr3viz
    - palmerpenguins
    - purrr
    - RColorBrewer
    - Rtsne
    - tibble
    - tidyr
    - umap
- Bioconductor:
    - Biobase
- GitHub:
    - danmacan/rbioinfcookbook

In addition to these packages, we will also need some R tools, such as Conda. All of these will be described when needed.

# Further information

Not all the recipes in this section are in R; some are command line-based setups. I generally use a bash terminal for these bits. Most macOS and Linux machines will have these available in a terminal application. Windows users will likely not need to follow these specific steps, though various packages for running a Linux subsystem on Windows exist if you wish to search them out.

In R, it is standard practice to load a library and use functions directly by name. Although this is great in short interactive sessions, it can cause confusion when many packages are loaded at once and share function names. To clarify which package and function I am using at a given moment, I will occasionally use the `packageName:functionName()` by convention.

Sometimes in the middle of a recipe, I will interrupt the code to dive into some intermediate output or look at the structure of an object. When that happens, you will see a code block where each line begins with ## (double hash symbols). Consider the following command:

This will give us the following output:

```
## a b c e
```

Note that the output lines are prefixed with ##.

# Defining a task and learner to implement k-nearest neighbors (k-NNs) in mlr

The k-nearest neighbors (k-NN) classification is a non-parametric ML algorithm for classifying data points based on their proximity to other labeled data points. The algorithm determines the class membership of an unlabeled data point by examining the classes of its k-NNs in the feature space. The dataset consists of labeled data points, where each data point has a set of features (attributes) and belongs to a specific class or category. The value of k represents the number of nearest neighbors to consider for classification. It is typically chosen by cross-validation or other model selection techniques. The algorithm measures the distance between the unlabeled data point and all the points in the space. The most commonly used metric is Euclidean distance. The data points with the shortest distances are identified as its nearest neighbors. The algorithm assigns the class label that is most prevalent among the k-NNs.

The mlr provides a framework for efficiently carrying out many tasks, including k-NN. The package allows us to define a task object that describes the data we wish to train and create a learner object that defines parameters such as training/test sets. The package allows us to use the trained learner with test splits and provides performance measures to evaluate the model.

# Defining a task and learner to implement k-nearest neighbors (k-NNs) in mlr

In this recipe, we'll use mlr3 to build a classifier for breast cancer data. A set of measurements have been taken from tumors identified as either benign or malignant.

 Getting ready

For this recipe, we will need to install mlr3, knn, and mlr3viz packages. We will use the BreastCancer object from mlbench.

# How to do it

Here's how we begin classifying using mlr3:

- 1. Load the data and set up the task:
```r
library(mlr3)
library(mlr3viz)
library(mlbench)
data("BreastCancer")

selected <- BreastCancer[c("thickness", "cell_size", "cell_shape", "marginal_adhesion", "epithel_size", "chromatin", "mitoses")]
task <- as_task_class(selected, target="Class")
autoplot(task)
```

- 3. Specify the train/test data:
```r
split <- partition(task, ratio=0.8)
```

- 4. Train the model:
```r
learner$train(task, split)
learner$model
```

- 5. Predict on the test data:
```r
predictions <- learner$predict(task, split)
predictions
autoplot(predictions)
```

- 6. Specify some measures and assess the model:
```r
measures <- msrs(c("precision", "specificity", "sensitivity"))
predictions$score(measures)
```

From this code, we have trained a machine learning model and assessed it.

# How it works...

The first part of any data analysis is to clean the dataset. Even though this is a recipe, we still have to do that. Step 1 loads the packages we will need and the BreastCancer dataset. Some of the columns in BreastCancer contain NA values and character data, so we select the numeric and factor columns we need. Then, we use mlr3::as_task_class() to set up the task object—this is essentially the dataset wrapped so that it can be used by other mlr3 functions. The object knows the sort of task (classification) that is to be carried out with it, so it can warn you if you try to do something inapplicable. The autoplot() function generates a plot of the target data for us, as seen in Figure 11.1:

![](img/dd0dd9aaacf496c4d1d0e31d8378b3_314_0.png)

Figure 11.1 – A visualization of the classes in the target of our BreastCancer data

# Defining a task and learner to implement k-nearest neighbors (k-NNs) in mlr

In step 2, we specify the learner: the type of ML we will be doing. mlr3 has two types of learners—classifiers and regressions. The learn() function helps us create this object, but there are only a couple of built-in learners. We must first load the accessory package mlr3learners to access a wider range, select .knn to the k-NN implementation in the knn package (which must also be installed manually). If we inspect the learner object as created by default, we see the following:

```
## <LearnerClassifyKNN:class.knn>
* Model: list
* Parameters: k=7
* Packages: mlr3, mlr3learners, knn
* Predict Types: [response], prob
* Feature Types: logical, numeric, factor, ordered
* Properties: multiclass, twoclass
```

There is useful information, as the feature types and the predictions we can make, that we can train a model like this. Inspecting the object is a quick way to see the parameters, but we can set them. Here, we see that the parameter for k-NN is k, and at the moment it is set to 7. So, just alter the value of k using the $ syntax. Its usage may be a little unfamiliar to you, so just think of this as meaning that the function we need is stored in the object itself and the $ lets us drill down to it. After using the learner$param_set$set_values() function to set k to 4, we see that the contents of the learner are:

```
## <LearnerClassifyKNN:class.knn>
* Model: list
* Parameters: k=4
* Packages: mlr3, mlr3learners, knn
* Predict Types: [response], prob
* Feature Types: logical, numeric, factor, ordered
* Properties: multiclass, twoclass
```
