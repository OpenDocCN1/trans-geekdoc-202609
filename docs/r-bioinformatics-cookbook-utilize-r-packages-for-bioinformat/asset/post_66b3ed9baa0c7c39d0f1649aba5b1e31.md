
- 5. Run the ROC analysis:

```r
library (DALEXtra)
model <- explain_mlr3(
  data = cancer_x
)
```

This code builds the model and gives us a feature analysis.

# How it works...

*In step 1*, we carry out the familiar data cleaning and task definition processes before building the trained model in the *learner* object. You can read about this more in detail in the first recipe in this chapter *Defining a task and learner to implement k-nearest neighbors (k-NNs)* in mlr3. *Step 2* is a quick demonstration of how to use the `predict()` function to use the model to classify unseen data. Here, we simply pass the model in `learner` and a new set of data formatted like that which the model was trained on. The result is a simple vector of class names:

```
## [1] benign malignant malignant benign
Levels: benign malignant
```

*In step 4*, we can run and plot the feature importance analysis using the `FeatureImp$new()` function, then run the `plot()` method on the resulting imp object. That gives us *Figure 11.4*:

# Classifying using random forest and interpreting it with iml

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_327_0.png)

Figure 11.4 – A feature importance plot on the RandomForest model of the BreastCancer data

step 5, we can move on to the ROC curve, which is done with methods from the DALEX package. Again, we need to reform the data, as we do in explain_mlr3() function. We can inspect the model object to get a summary of performance that this looks like:

```
Preparation of a new explainer is initiated
-> model label : R6 ( default )
-> data : 209 rows 8 cols
-> target variable : 209 values
-> predict function : yhat.LearnerClassif  will be used ( default )
-> predicted values : No value for predict function target column ( default )
-> model info : package mlr3 , ver. 0.16.0 , task classification ( default )
-> predicted values : numerical, min = 9.42886e-05 , mean 0.3414915 , max = 1
-> residual function : difference between y and dhat ( default )
-> residuals : numerical, min = -0.7269598 , mean 0.003006121 , max = 0.8061695
A new explainer has been created!
Measures for: classification
recall : 0.9861111
precision : 0.9594955
f1 : 0.9726027
accuracy : 0.9808612
auc : 0.9984286
```

306 Machine Learning with mlr3

The resulting model object can now be passed to the model_performance() function and the result of that can be passed to the generic plot() function, specifying the roc geom. The resulting plot looks similar to Figure 11.5:

# Receiver Operator Characteristic

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_328_0.png)

Figure 11.5 – A ROC curve on the RandomForest model of the BreastCancer data

The plot is the ROC curve we were hoping to see.

# Dimension reduction with PCA in mlr3 pipelines

Principal Component Analysis (PCA) is a dimensionality reduction technique commonly used in bioinformatics to analyze and interpret high-dimensional biological data, such as gene expression data, protein profiles, or genomic data.

The main goal of PCA is to find a lower-dimensional representation of the data while preserving the important patterns and variability in the original data. It achieves this by transforming the data into a new set of uncorrelated variables called principal components. These principal components are ordered in such a way that the first component captures the maximum amount of variance in the data, the second component captures the maximum variance, and so on.

PCA is useful in bioinformatics for various applications, including visualization, it reduces data to two or three dimensions for use. PCA has an important role in feature selection, as it can be used to select the most informative features (genes, proteins, etc.) in a training set by assessing their contributions to the principal components. This helps in reducing the dimensionality of the data while retaining the most relevant variables and making the task more tractable. In this recipe, we'll look how to build a preprocessing-step such as PCA into an mlr3 pipeline rather than an external step.

# Getting ready

For this recipe, we'll use the mlr3 package, accessory packages mlr3learners, mlr3pipelines, and mlr3tuning, and the data mlbench. We'll also need the magrittr package.

# How to do it...

To build a pipeline with PCA preprocessing step, we proceed as follows:

1. Build the pipeline for scaling and PCA:
```r
library(mlr3pipelines)
scale <- po("scale")
pca <- po("pca")
```

2. Build the start of the pipeline:
```r
library(magrittr)
pipeline <- scale %>% pca %>% plot()
```

3. Add a learner as a pipeline object:
```r
library(mlr3learners)
learner = lrn("classif.knn")
learner$param_set$values(k = 4)
pipeline <- pipeline %>% po("learner", learner = learner) %>% plot()
```

4. Convert the pipeline to a learner:
```r
p_learner <- as_learner(pipeline)
```

5. Use the pipeline learner as usual:
```r
library(mlbench)
data("BreastCancer")
selected <- BreastCancer[c("Cl.thickness", "Cell.size", "Cell.shape", "Marg.adhesion", "Epith.size", "Bl.chromatin", "Normal", "nucleoli", "Mitoses"), "Class"]
task <- as_classify(selected, target="Class")
resamp_kcv <- rsmp("cv")
resamp_kcv$param_set$values(folds = 3)
result_kcv <- resample(task, p_learner, resamp_kcv)
measures <- msrs(c("class.precision", "class.specificity", "class.sensitivity"))
result_kcv$score(measures)
```

This code gives us the results of a PCA.

# How it works...

Step 1 is to start creating pipeline objects—the parts of the pipeline we will string together. We can do this with the po function and the name of the object. For the preprocessing step, we have chosen a "scale" and a "pca". These have no further options, though many of the pipeline objects we could create. In step 2, we string the parts into a pipeline using the magrittr %>% operator. The resulting pipeline object has a $plot method we can use to view the pipeline, as seen in Figure 11.6:

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_330_0.png)

Figure 11.6 – A basic pre-processing pipeline

In step 3, we build the k-NN learner using the learner() function, set its parameters as usual, and then add it to the end of the existing pipeline to give the pipeline seen in Figure 11.7:

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_331_0.png)

Figure 11.7 – The pipeline with the learner

In step 4, we take the pipeline and convert it into an object equivalent to a learner. The as_learner() function does this, and we can now proceed to use the pipeline as we have done before.

With step 5, the longest step, we process the datasets, task, and resampling strategy (as we did in the earlier recipe in this chapter) and run it. Then, we assess the result with selected measures. Printing the results gives us something like the following:

```
task_id learner_id resampling_id iteration classif.precision
1: selected scale.pca.classif. 0.9341317 kknn cv 1
2: selected scale.pca.classif. 0.9354839 kknn cv 2
3: selected scale.pca.classif. 0.9729273 kknn cv 3
```

The learner_id column confirms that this learner was preprocessed by scaling and PCA and that three-fold cross-validation was performed.

# There’s more...

Lots of the components of the mlr3 ecosystem can be used as pipeline components. To get a list from R, try inputting the following:

```r
library("mlr3pipelines")
as.data.table("mlr3_pipeops")
```

That should give you a list of components you can use in the pipeline.

# Creating a tSNE UMAP embedding

**t-Distributed Stochastic Neighbor Embedding (t-SNE) and Uniform Manifold Approximation and Projection (UMAP)** are both dimensionality reduction techniques commonly used in.

t-SNE is a non-linear technique used to visualize high-dimensional data in a lower-dimensional space while preserving the local structure. UMAP is another non-linear dimensionality reduction technique that has gained popularity due to its scalability and efficiency.

Both algorithms suffer from being computationally expensive, especially when dealing with large datasets. UMAP was developed to address this issue and is generally faster than t-SNE, but it can be slower than linear techniques such as PCA. Both algorithms are sensitive to the random initialization of the embedding, which means running the same algorithm with different seeds can produce different results. It's important to be aware of this when interpreting the visualizations.

Crucially, the lower-dimensional representations may not have a direct correspondence to the original features. The focus is on capturing the relationships between data points rather than preserving the global structure. Both techniques have several parameters that need to be set, such as the perplexity in t-SNE and the number of neighbors in UMAP. Choosing appropriate parameter values can significantly affect the quality and interpretability of the embeddings, making it important to experiment and tune these parameters.

Nonetheless, t-SNE and UMAP are useful for exploratory data analysis, pattern recognition, and visualization tasks, helping researchers and data scientists gain insights from complex and high-dimensional data.
