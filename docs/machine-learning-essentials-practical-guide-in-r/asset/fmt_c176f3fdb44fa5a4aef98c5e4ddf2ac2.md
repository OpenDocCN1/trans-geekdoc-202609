
![](Image00052.jpg)

Alboukadel KASSAMBARA

# Machine Learning Essentials

## Preface

### 0.1 What you will learn

Large amount of data are recorded every day in different fields, including marketing, bio-medical and security. To discover knowledge from these data, you need machine learning techniques, which are classified into two categories:

1. **Unsupervised machine learning methods**:

These include mainly *clustering* and *principal component analysis* methods. The goal of clustering is to identify pattern or groups of similar objects within a data set of interest. Principal component methods consist of summarizing and visualizing the most important information contained in a multivariate data set.

These methods are "unsupervised" because we are not guided by a priori ideas of which variables or samples belong in which clusters or groups. The machine algorithm "learns" how to cluster or summarize the data.

2. **Supervised machine learning methods**:

Supervised learning consists of building mathematical models for predicting the outcome of future observations. Predictive models can be classified into two main groups:

* *regression analysis* for predicting a continuous variable. For example, you might want to predict life expectancy based on socio-economic indicators.

* *Classification* for predicting the class (or group) of individuals. For example, you might want to predict the probability of being diabetes-positive based on the glucose concentration in the plasma of patients.

These methods are supervised because we build the model based on known outcome values. That is, the machine learns from known observation outcomes in order to predict the outcome of future cases.

In this book, we present a practical guide to machine learning methods for exploring data sets, as well as, for building predictive models.

You'll learn the basic ideas of each method and reproducible R codes for easily computing a large number of machine learning techniques.

### 0.2 Key features of this book

Our goal was to write a practical guide to machine learning for every one.

The main parts of the book include:

* **Unsupervised learning methods**, to explore and discover knowledge from a large multivariate data set using clustering and principal component methods. You will learn hierarchical clustering, k-means, principal component analysis and correspondence analysis methods.

* **Regression analysis**, to predict a quantitative outcome value using linear regression and non-linear regression strategies.

* **Classification techniques**, to predict a qualitative outcome value using logistic regression, discriminant analysis, naive bayes classifier and support vector machines.

* **Advanced machine learning methods**, to build robust regression and classification models using k-nearest neighbors methods, decision tree models, ensemble methods (bagging, random forest and boosting)

* **Model selection methods**, to select automatically the best combination of predictor variables for building an optimal predictive model. These include, best subsets selection methods, stepwise regression and penalized regression (ridge, lasso and elastic net regression models). We also present principal component-based regression methods, which are useful when the data contain multiple correlated predictor variables.

* **Model validation and evaluation techniques** for measuring the performance of a predictive model.

* **Model diagnostics** for detecting and fixing a potential problems in a predictive model.

The book presents the basic principles of these tasks and provide many examples in R. This book offers solid guidance in data mining for students and researchers.

Key features:

* Covers machine learning algorithm and implementation

* Key mathematical concepts are presented

* Short, self-contained chapters with practical examples. This means that, you don't need to read the different chapters in sequence.

At the end of each chapter, we present R lab sections in which we systematically work through applications of the various methods discussed in that chapter.

### 0.3 Book website

[`http://www.sthda.com/english`](http://www.sthda.com/english)

## 1 About the author

Alboukadel Kassambara is a PhD in Bioinformatics and Cancer Biology. He works since many years on genomic data analysis and visualization (read more: [`http://www.alboukadel.com/`](http://www.alboukadel.com/) ).

He has work experiences in statistical and computational methods to identify prognostic and predictive biomarker signatures through integrative analysis of large-scale genomic and clinical data sets.

He created a bioinformatics web-tool named GenomicScape (`www.genomicscape.com`) which is an easy-to-use web tool for gene expression data analysis and visualization.

He developed also a training website on data science, named STHDA (Statistical Tools for High-throughput Data Analysis, `www.sthda.com/english`), which contains many tutorials on data analysis and visualization using R software and packages.

He is the author of many popular R packages for:

* multivariate data analysis (**factoextra**, [`http://www.sthda.com/english/rpkgs/factoextra`](http://www.sthda.com/english/rpkgs/factoextra) ),

* survival analysis (**survminer**, [`http://www.sthda.com/english/rpkgs/survminer/`](http://www.sthda.com/english/rpkgs/survminer/) ),

* correlation analysis (**ggcorrplot**, [`http://www.sthda.com/english/wiki/ggcorrplot-visualization-of-a-correlation-matrix-using-ggplot2`](http://www.sthda.com/english/wiki/ggcorrplot-visualization-of-a-correlation-matrix-using-ggplot2) ),

* creating publication ready plots in R (**ggpubr**, [`http://www.sthda.com/english/rpkgs/ggpubr`](http://www.sthda.com/english/rpkgs/ggpubr) ).

Recently, he published several books on data analysis and visualization:

1. Practical Guide to Cluster Analysis in R ([`https://goo.gl/yhhpXh`](https://goo.gl/yhhpXh) )

2. Practical Guide To Principal Component Methods in R ([`https://goo.gl/d4Doz9`](https://goo.gl/d4Doz9) )

3. R Graphics Essentials for Great Data Visualization ([`https://goo.gl/oT8Ra6`](https://goo.gl/oT8Ra6) )

4. Network Analysis and Visulization in R ([`https://goo.gl/WBdn4n`](https://goo.gl/WBdn4n) )

## 2 Introduction to R

R is a free and powerful statistical software for analyzing and visualizing data.

In this chapter, you'll learn how to install R and required packages, as well as, how to import your data into R.

### 2.1 Install R and RStudio

RStudio is an integrated development environment for R that makes using R easier. R and RStudio can be installed on Windows, MAC OSX and Linux platforms.

1. R can be downloaded and installed from the Comprehensive R Archive Network (CRAN) webpage ([`http://cran.r-project.org/`](http://cran.r-project.org/) )

2. After installing R software, install also the RStudio software available at: [`http://www.rstudio.com/products/RStudio/`](http://www.rstudio.com/products/RStudio/) .

3. Launch RStudio and start use R inside R studio.

### 2.2 Install and load required R packages

An R package is a collection of functionalities that extends the capabilities of base R. To use the R code provide in this book, you should install the following R packages:

* `tidyverse` for easy data manipulation and visualization.

* `caret` package for easy machine learning workflow.

1. **Installing packages**:

```
```

3. **Load required packages**. After installation, you must first load the package for using the functions in the package. The function `library()` is used for this task. For example, type this:

```
```

Now, we can use R functions available in these package.

If you want to learn more about a given function, say `mean()`, type this in R console: `?mean`.

### 2.3 Data format

Your data should be in rectangular format, where columns are variables and rows are observations (individuals or samples).
