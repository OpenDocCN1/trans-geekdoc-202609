![](EPUB/cover.jpg)

   

# 

# 

Machine Learning Algorithms for Data Scientists: An Overview

 

Preface

Machine Learning models are widely used in different fields such as Artificial Intelligence, Business, Clinical and Biological Sciences which includes self-driving cars, predictive models, disease prediction, genome sequencing, spam filtering, product recommendation, fraud detection and image recognition . It has gained importance due to its capabilities of handling large volume of data, prediction and classification accuracy and validation procedures.

Machine Learning models are built on the basis of statistical and mathematical algorithms. One important aspect of machine learning is it does not stick to standard algorithm throughout modeling process instead it learns from the data over a period of time and improves the accuracy of the model.   Classification and prediction tasks are carried out based on the characteristics, patterns and relationship of the features present in the data set. Machine learning model also forms the basis of Deep Learning models.

Machine Learning models involve supervised learning, unsupervised learning, semi supervised learning and reinforcement learning algorithms.

Data Scientists analyze, model and visualize data and provide actionable insights to the decision makers. Machine learning algorithms and tools help the data scientist to carry out these tasks with the help of software such R and Python.

This book provides an overview of Machine Learning models, algorithms and its application in different fields through the use of R Software. It also provides short introduction to R software for the benefit of users.

Author assumes the users have basic descriptive and inferential statistical knowledge which is essential for building Machine Learning models.

Data sets used in the books can be downloaded from the author’s website.

Vinaitheerthan Renganathan

Title: Machine Learning Algorithms for Data Scientists: An Overview

Author: Vinaitheerthan Renganathan

Publisher: Self Published

Edition: 1 st Edition

Copyright: © 2021 Vinaitheerthan Renganathan 

## 

Contents

 

Chapter 1:  Introduction

Chapter 2:  R Software

Chapter 3:  Data Preprocessing

Chapter 3:  Decision Tree Algorithm

Chapter 4:  Random Forest Algorithm

Chapter 5:  Support Vector Machine Algorithm

Chapter 6:  Naïve Bayes Algorithm

Chapter 7:  Artificial Neural Network Algorithm

Chapter 8:  Clustering Algorithm

Chapter 9:  Text mining algorithms

Chapter 10: Image processing and classification

![](media/file0.png)

### Chapter 1:  Introduction

![](media/file0.png)

Machine learning term became a buzz word in recent times due to its capabilities, easy to implement characteristics and high computing power. Machine learning models uses data to learn and take decision related to classification, pattern recognition and prediction. Machine Models improve the task under consideration through learning from the data and evaluating the results based on the performance measures. 

Machine learning models are being applied in different fields to carry out the following tasks (not limited to)

Speech Recognition

Pattern Recognition

Computer Vision

Robotic Control

Disease progression

Fraud detection

Spam filtering

Network intrusion detection

Self-driving cars

Recommender systems

There are different types of Machine Learning algorithms are available. Supervised, Unsupervised and Reinforcement Learning Algorithms

Supervised learning algorithms involve training and test data sets. The algorithm is trained on the training data set which contains outcome variable which needs to be classified or predicted i.e. Class label in case of classification problem or predicted value in case of regression problem. In some cases test data set used in the ML algorithms will not contain the outcome variable i.e. class label or predicted values which will be used to test the predictive accuracy of the machine learning algorithms. One of the issues with the supervised learning algorithm is to get the class label for the training data set and it might not be available for a large dataset.

Unsupervised learning algorithm will not be having any training or test data sets separately. It works on the whole data set to identify natural clusters or groups or patterns in the data set.

Reinforcement learning involves learning through experiences of its action on the external environment (obtaining feedbacks on the actions). The Reinforcement learning system involves policies which maps the state with actions of the agent and provide feedbacks in the form of rewards for the agent’s action. It helps the agent to take optimal decisions in the future by trial and error method.

Machine learning systems involve descriptive, predictive and prescriptive analytics. Descriptive systems involve the description about the data sets currently under consideration. Predictive systems involve predicting the future scenarios with the current data sets. Prescriptive systems suggest actions based on the analysis of data set.

Machine Learning algorithms not only analyze numeric data sets but also can analyze text, audio and videos. Text based data are analyzed using Statistical algorithms as well as Natural Language Processing (NLP) algorithms. NLP algorithms use language models and dictionaries to analyze the text.

The following chapters provide overview of R Software and machine learning algorithms.

References

Mohri, M., Rostamizadeh, A., & Talwalkar, A. (2018). Foundations of machine learning. MIT press.

Mueller, J. P., & Massaron, L. (2021). Machine learning for dummies. John Wiley & Sons.

Burkov, A. (2019). The hundred-page machine learning book (Vol. 1). Canada: Andriy Burkov.

Goodfellow, I., Bengio, Y., & Courville, A. (2016). Machine learning basics. Deep learning, 1, 98-164.

Zhang, X. D. (2020). Machine learning. In A Matrix Algebra Approach to Artificial Intelligence (pp. 223-440). Springer, Singapore.

Aghbashlo, M., Peng, W., Tabatabaei, M., Kalogirou, S. A., Soltanian, S., Hosseinzadeh-Bandbafha, H., … & Lam, S. S. (2021). Machine learning technology in biodiesel research: A review. Progress in Energy and Combustion Science, 85, 100904.

Kushwaha, S., Bahl, S., Bagha, A. K., Parmar, K. S., Javaid, M., Haleem, A., & Singh, R. P. (2020). Significant applications of machine learning for COVID-19 pandemic. Journal of Industrial Integration and Management, 5(4).

Sailusha, R., Gnaneswar, V., Ramesh, R., & Rao, G. R. (2020, May). Credit Card Fraud Detection Using Machine Learning. In 2020 4th International Conference on Intelligent Computing and Control Systems (ICICCS) (pp. 1264-1270). IEEE.

Janai, J., Güney, F., Behl, A., & Geiger, A. (2020). Computer vision for autonomous vehicles: Problems, datasets and state of the art. Foundations and Trends® in Computer Graphics and Vision, 12(1–3), 1-308.

Wei, X., Chen, W., & Li, X. (2021). Exploring the financial indicators to improve the pattern recognition of economic data based on machine learning. Neural Computing and Applications, 33(2), 723-737.

Ayanouz, S., Abdelhakim, B. A., & Benhmed, M. (2020, March). A smart chatbot architecture based NLP and machine learning for health care assistance. In Proceedings of the 3rd International Conference on Networking, Information Systems & Security (pp. 1-6).

Choi, H., Teague, T., & Luce, T. (2020). Positive cycle of integrating teaching and research: machine learning self-driving car. Journal of Computing Sciences in Colleges, 35(7), 74-87.

Gaurav, D., Tiwari, S. M., Goyal, A., Gandhi, N., & Abraham, A. (2020). Machine intelligence-based algorithms for spam filtering on document labeling. Soft Computing, 24(13), 9625-9638.

Jiang, T., Gradus, J. L., & Rosellini, A. J. (2020). Supervised machine learning: a brief primer. Behavior Therapy, 51(5), 675-687.

Verbeeck, N., Caprioli, R. M., & Van de Plas, R. (2020). Unsupervised machine learning for exploratory data analysis in imaging mass spectrometry. Mass spectrometry reviews, 39(3), 245-291.

### Chapter 2:  R Software

![](media/file0.png)

Ris open source software initially developed for Statistical computing and graphic applications. It is similar to S language developed by Bell Laboratories, USA. Now it includes machine learning, deep learning and natural language processing algorithms. It includes functions, arrays, conditional statements, graphical display features.

R is a flexible software and can be used with other software such Java, Python and SAS. It can run platforms like Windows, UNIX and MacOS.  High memory usage by R software is one of the disadvantages.

R software has its own Graphic User Interface but it does not offer much functionality. But there are many Integrated Development Environments (IDEs) are available such as R Studio, Rattle and Visual Studio.

R software can be downloaded from

https://cran.r-project.org/bin/windows/base/ .

R Studio software can be downloaded from https://rstudio.com/products/rstudio/download/ .

R studio contains the following four sections or windows

Code window – Top left window

Environment, History and Connections – Top right window  

Output Console and Terminal -  Bottom left window

File, Plots, Packages, Help and Viewer – Bottom right window.

![](media/file1.png)

R software has a built in core system. It contains tools which are used for basic operations and basic statistical calculations.

Apart from the core system it has number of packages developed by R community. Packages can be used by any user by installing them from the Cran r Repository using install.packages statement (or through R studio Tools menu option) and needs to be called into the R studio environment using library statement.

R Objects

R software contains the following elements such as vectors, factors, data frame and matrix.

Vectors are nothing but list of values which can be numeric or string or date values.

Factors are variables which are having different levels or categories.

Data frame is made up of rows and columns which can contain both numbers as well as strings.

Matrix is similar to data frame but can contain either numeric or string.

List is a high level object in R which can contain different objects in it. It can contain numbers, strings, vector, matrices and other list also.

We will start with the examples for each of the R objects above. We need to define working directory first using setwd statement. 

![](media/file2.png)

With getwd() statement we can get the current working directory name.

We can use # symbol to include a comment line in R.

![](media/file3.png)

We can print the output by using print statement or the variable itself.

![](media/file4.png)

The following output is obtained

![](media/file5.png)

READING FROM DIFFERENT data sources

Data can be brought into R environment through different sources such as raw input, text files, Comma Separated Value (CSV) files, Excel file, Statistical Analysis System (SAS), Statistical Package for Social Sciences (SPSS) files, Relational Databases, XML and JSON files. Except for raw data, text files and CSV files, corresponding packages needs to be installed and defined for all the other data sources using library statement in the R Studio environment.

Let us read data from a text file from the working directory using read. delim statement

![](media/file6.png)![](media/file5.png)

THE FIRST FEW ROWS of the custtext data set can be viewed with the help of head statement.

Similarly we can read data from CSV file using CSV statement

![](media/file7.png)![](media/file5.png)

THE FIRST FEW ROWS of the custcsv data set can be viewed with the help of head statement.

We need to use xlsx package to read the data from the xlsx file. First we need install and define using library statement 

![](media/file8.png)

The first few rows of the custexcel data set can be viewed with the help of head statement.

We need to use sas7bdat package to read data from a SAS file

![](media/file9.png)![](media/file10.png)

We can read data from the SPSS file using foreign package

![](media/file5.png)

WE CAN READ DATA FROM mysql database using RMySQL or RMariaDB package. We need to use dbConnect and dbSendQuery statements to connect to the MySQL database and perform SQL manipulation queries such as insert and select queries.

![](media/file11.png)![](media/file5.png)![](media/file12.png)

WE CAN READ DATA FROM xml file using XML package and its function xmlParse

We can read data from JSON file using rjson package and its function fromJSON.

![](media/file13.png)

We can write the R data sets back to excel using writexl package. The file will be stored in the working directory

![](media/file14.png)![](media/file5.png)

REFERENCES

R Core Team (2020). R: A language and environment for statistical computing. R Foundation for Statistical Computing, Vienna, Austria. URL  https://www.R-project.org/ .

RStudio Team (2020). RStudio: Integrated Development for R. RStudio, PBC, Boston, MA URL http://www.rstudio.com/ .

Claes, M., Mens, T., & Grosjean, P. (2014, February). On the maintainability of CRAN packages. In 2014 Software Evolution Week-IEEE Conference on Software Maintenance, Reengineering, and Reverse Engineering (CSMR-WCRE) (pp. 308-312). IEEE.

Hornik, K. (2012). The comprehensive R archive network. Wiley interdisciplinary reviews: Computational statistics, 4(4), 394-398.

German, D. M., Adams, B., & Hassan, A. E. (2013, March). The evolution of the R software ecosystem. In 2013 17th European Conference on Software Maintenance and Reengineering (pp. 243-252). IEEE. 

Fox, J. (2005). Getting started with the R commander: a basic-statistics graphical user interface to R. J Stat Softw, 14(9), 1-42.

Williams, G. (2009). Rattle: a data mining GUI for R.

Fellows, I. (2012). Deducer: a data analysis GUI for R. Journal of statistical Software, 49(8), 1-15.

Mora-Cantallops, M., Sánchez-Alonso, S., & García-Barriocanal, E. (2020). A complex network analysis of the Comprehensive R Archive Network (CRAN) package ecosystem. Journal of Systems and Software, 170, 110744.

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/web/packages/sas7bdat/index.html

https://cran.r-project.org/package=XML

https://cran.r-project.org/package=foreign

https://cran.r-project.org/package=rjson

### Chapter 3:  Data Preprocessing

![](media/file0.png)

With the introduction of Big Data, size of data stored and processed is huge and which introduces challenges related to data quality. Data quality is concerned with factors such as inaccuracy, inconsistency, missing data, outliers and data not in a suitable format. When the data with poor quality is used in the analysis it fails to provide quality results.

Data cleaning

Data cleaning process will help us to solve some of the quality issues such as missing values.

Handling missing values

Missing values in a data set can be handled in different ways. We need to find out whether values are missing randomly or there is a pattern in missing values. Based on this, the following ways can be adopted to solve the issue

Omit the record which contains the missing values. This can be done only when we have adequate number of records for further processing.

We can use a constant value to fill the missing values and the same will be taken care by omitting those values during the analysis stage. Here we will lose information only about the particular field not for the whole record. 

Replace the missing values with measures like mean or median value of the variable.

Replace the missing values with values from the similar records determined by measures like correlations.

We can estimate the missing values through models such regression and replace the same with the estimated value.

Handling noisy data

Outliers in the data set some times affect the quality of the results. Some of the algorithms are capable of handling the outliers even they are present in the dataset. There are different statistical tests and visualization tools such as box plot are available to find the outliers in the data set.

Box Plot – It will help us to visualize the outliers present in the data. It includes median and 75 th and 25 th quartile values in the box region.

Z score – When we compute the Z Score or Standard Normal Distribution variable, we will be able to find the values which lies within the acceptable range say 95% or 99%. The values which lie outside this range are considered as outliers. 

Grubb’s Test – It helps us to detect a single outlier in the data set which uses the standard normal distribution. It measures the absolute deviation from the sample mean divided by the sample standard deviation.

Generalized ESD Test – With the calculated upper bound it starts testing from  single outlier till the given number of outliers says k are tested in the dataset. This test uses maximum absolute deviation from the sample observation divided by the standard deviation.

![](media/file5.png)

DATA TRANSFORMATION

Data Transformation is an important aspect of data preprocessing process. Most of the Machine Learning algorithms can be improved by data transformation, normalization and data scaling techniques.

There are different types of data normalization and data scaling techniques are available.

Min-Max Normalization – Here the original data values will be replaced with the deviation from the minimum value divided by the deviation between the maximum and minimum value.

Z-score normalization – Here the original values will be replaced with z scores which is calculated from deviation from the mean value divided by the standard deviation. Here the mean and standard deviation of the normal distribution is used.

Logarithmic transformation – Here the natural logarithmic values of the original data set is used.

Data Reduction

When we have more number of features or variables and each one of them may be correlated with other features or variables of the data set which may introduce multi co-linearity problem in the analysis stage.

To avoid this, either we can drop the feature or variable from the data set or we can use factor or principle component analysis to reduce the features by creating latent features. Latent features are nothing but the linear combination of correlated features in the data set.

References

Famili, A., Shen, W. M., Weber, R., & Simoudis, E. (1997). Data preprocessing and intelligent data analysis. Intelligent data analysis, 1(1), 3-23.

Kotsiantis, S. B., Kanellopoulos, D., & Pintelas, P. E. (2006). Data preprocessing for supervised leaning. International Journal of Computer Science, 1(2), 111-117.

Friedman, J., Hastie, T., & Tibshirani, R. (2001). The elements of statistical learning (Vol. 1, No. 10). New York: Springer series in statistics.

Walfish, S. (2006). A review of statistical outlier methods. Pharmaceutical technology, 30(11), 82.

Grubbs, F. E. (1969). Procedures for detecting outlying observations in samples. Technometrics, 11(1), 1-21.

Patro, S., & Sahu, K. K. (2015). Normalization: A preprocessing stage. arXiv preprint arXiv:1503.06462.

Jo, J. M. (2019). Effectiveness of normalization pre-processing of big data to the machine learning performance. The Journal of the Korea institute of electronic communication sciences, 14(3), 547-552.

Ali, P. J. M., Faraj, R. H., Koya, E., Ali, P. J. M., & Faraj, R. H. (2014). Data normalization and standardization: a technical report. Mach Learn Tech Rep, 1(1), 1-6.

### Chapter 3:  Decision Tree Algorithm

![](media/file0.png)

Decision tree algorithm is one of the supervised machine learning algorithms. We can use Decision Tree algorithm for both classification and regression problems. We need to have training and test data sets to perform the algorithm.

Decision tree helps us to take decision on the target attribute or class based on the rules. It includes root node, decision node and leaf node. The root node is starting point of a decision tree. Decision node consists of test or rule based on an attribute. Branches represent the decision.  Nodes represent outcomes of the decision. Leaf node or final nodes consists of values of the class or target value.

Selecting the attribute at each decision node is an important process which is done through information gain (or misinformation). Information gain helps us to measure the reduction in uncertainty in the splitting process.  We need to find out which attributes splits the data into class more accurately or near accurate. Splitting algorithms consists of measures like ID3 and Gini index (measure of impurity).

If the attribute is categorical then the splitting is done on presence or absence of factors or categories will be considered. If the attribute is continuous then certain threshold value will be considered for splitting.

The splitting process will be continued till there is no attribute left for splitting or there is no information gain.

Let us start with the hypothetical customer data set which we can use for our decision tree algorithm example (purchasedata.xlsx). The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php

We can use r packages such as caret, rpart, rpart.plot and party packages to build decision trees. We need to define the required packages using

![](media/file15.png)![](media/file5.png)

WE WILL IMPORT THE data in the form of excel using xlsx package

![](media/file16.png)

The following are the first few rows of the dataset.

![](media/file17.png)

Decision Tree – Classification problem

We will be using decision tree algorithm to classify the data set based on the ‘satisfied’ field. It will help us to classify who are likely to be satisfied based on the features (Classification problem).

We need to split the data set into train and test data set

![](media/file18.png)

We will use train function of the caret package to build the decision tree. We will print the model and its summary

![](media/file19.png)![](media/file20.png)

Here we have rattle package to plot the decision tree.

![](media/file21.png)

Here the accuracy is 49% and it might be low due to nature of hypothetical data set.

![](media/file22.png)![](media/file23.png)

We can use predict function to predict the class of test data set.

![](media/file24.png)![](media/file25.png)![](media/file5.png)

DECISION TREE - REGRESSION Problem

We can also use regression trees to predict the values of the dependent variable using predictors or features. We can also use rpart package for the same to predict and plot the tree.

![](media/file26.png)![](media/file5.png)![](media/file27.png)![](media/file28.png)

THE SAME IS PLOTTED as decision tree below.

![](media/file29.png)

We can rerun model by creating new test data set by leaving the pamount variable  using the dplyr package and select statement.

![](media/file30.png)

Advantages of Decision tree algorithm

Easy to build

Decision tree can be build fast

Decision tree models are easy to interpret

Can be used for binary and multiple classification problems

Disadvantages of Decision Tree algorithm

Affected by over fitting problem

There is a chance of increasing bias with more levels of categorical variables.

To increase the accuracy and avoid over fitting Pruning, Bagging and Boosting methods are used and the details are given below.

Pruning

Pruning cuts the nodes of the decision tree which are not providing valuable information and allows us to reduce error due to the over fitting problem.

Bagging

Bagging process involves creating Bootstrap samples from the data set and then creating tree from each sample. Each tree classifies the sample data set with respect to labels (give vote for class label). The class with higher voters is considered as final outcome.

Boosting

Starts with the single tree and identifies the wrong classification. Then it improves the wrong classification by adjusting weights and this process is sequentially continued till wrong classification is minimized. This method helps to reduce high bias among weak models.

References

Brijain, M., Patel, R., Kushik, M. R., & Rana, K. (2014). A survey on decision tree algorithm for classification.

Yang, J., Zhang, N. N., LI, J., LIU, Y. M., & LIANG, M. H. (2010). Research and application of decision tree algorithm. Computer Technology and Development, 2.

Singh, S., & Gupta, P. (2014). Comparative study ID3, cart and C4. 5 decision tree algorithm: a survey. International Journal of Advanced Information Science and Technology (IJAIST), 27(27), 97-103.

Zhong, Y. (2016, August). The analysis of cases based on decision tree. In 2016 7th IEEE international conference on software engineering and service science (ICSESS) (pp. 142-147). IEEE.

Zhang, Y., & Cao, J. (2016). Decision tree algorithm for big data analysis. Computer Science, 43(S1), 374-379.

Zhou, H., Zhang, J., Zhou, Y., Guo, X., & Ma, Y. (2021). A feature selection algorithm of decision tree based on feature weight. Expert Systems with Applications, 164, 113842.

Hernández, V. A. S., Monroy, R., Medina-Pérez, M. A., Loyola-González, O., & Herrera, F. (2021). A Practical Tutorial for Decision Tree Induction: Evaluation Measures for Candidate Splits and Opportunities. ACM Computing Surveys (CSUR), 54(1), 1-38.

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rpart

https://cran.r-project.org/package=rpart.plot

https://cran.r-project.org/package=dpylr

### Chapter 4:  Random Forest Algorithm

![](media/file0.png)

Random Forest is the extension of decision tree algorithm which is based on bagging concept wherein numbers of trees are constructed using bootstrap sample which is a random sample with replacement methods.

Random forest is a bagging technique with random features is selected from the random sample which makes the trees independent of each other. Each tree classifies the data set with labels and it is termed as a vote for that particular class. The class which is having highest vote is considered as final outcome. It reduces higher variance among complex model.

Random Forest algorithm uses Out of Bag (OOB) error estimate to validate the built model. Random Forest uses only bootstrap samples from the training data set and not all the data or row in the training data set. The Out of Bag error is calculated from the bootstrap samples which were left out during the model building process. 

We can use the same hypothetical customer data set which was used for decision tree algorithm example. The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php

We will use RandomForest package to build the model. We need to define the required packages such as RandomForest, xlsx, party using library statement.

![](media/file5.png)![](media/file31.png)

WE WILL IMPORT THE data in the form of excel using xlsx package as done in the previous chapter

![](media/file32.png)![](media/file33.png)

The following are the first few rows of the dataset.

Random Forest – Classification problem

We will be using Random Forest tree algorithm to classify the data set based on the ‘satisfied’ field. It will help us to classify who are likely to be satisfied based on the features (Classification problem).

We need to split the data set into train and test data set

![](media/file34.png)

We will use RandomForest function of the RandomForest package to build the model and print the model summary.

![](media/file35.png)![](media/file5.png)![](media/file36.png)

HERE THE OOB ESTIMATE of error rate is 49.57% which was calculated from the left bootstrap samples from the training dataset.

VarimpPlot function provides importance of each feature in classifying the predicted variable

![](media/file37.png)

Here pamount, pid and dom features are at the top of important features list in both the methods MDA and MDG.

Here pamount is a derived variable from qty and price. We can rerun model by creating new test data set by leaving the pamount variable  using the dplyr package and select statement.

![](media/file38.png)

We can use predict function to predict the test data set and calculate the prediction accuracy.

![](media/file39.png)

The following output obtained

![](media/file40.png)![](media/file5.png)

HERE THE ACCURACY IS 48.4% and it might be low due to nature of hypothetical data set.

We can use party package to plot the random forest using cforest, cmdscale,op and pairs function as follows.

![](media/file41.png)

The following Multidimensional Scale Plot based on the proximity or closeness between sample points or rows in the random forest.

![](media/file42.png)

Random Forest – Regression Problem

We can use Random Forest model for regression problem. We will use RandomForest function of the RandomForest package to build the model and print the model summary.

![](media/file43.png)![](media/file5.png)![](media/file44.png)

THE ABOVE MODEL CONTAINS a pamount which is a derived variable from qty and price. Because of this variable the % explained variance may be high. We can rerun model by creating new test data set by leaving the pamount variable  using the dplyr package and select statement.

![](media/file45.png)![](media/file5.png)

VARIMPPLOT FUNCTION provides importance of each feature in classifying the predicted variable

![](media/file46.png)

Here pamount, pid, qty features are at the top of important features list in both the methods MDA and MDG. Here  pamount is a derived variable from qty and price which might be reason it tops the list. We can replot the same by leaving this variable from the dataset as discussed above.

We can use predict function to predict the test data set and calculate the prediction accuracy.

![](media/file47.png)

We can plot the actual vs predicted values using ggplot package.

![](media/file48.png)![](media/file49.png)![](media/file5.png)

ADVANTAGES OF RANDOM Forest Algorithm

Random Forest algorithm overcomes the problem of over fitting

We can build both classification and regression models

Not affected by outliers

Can handle non-linear and large datasets

Disadvantages of Random Forest Algorithm

Large number of trees makes the algorithm slow

Random forest models are complex to understand

References

Biau, G., & Scornet, E. (2016). A random forest guided tour. Test, 25(2), 197-227.

Svetnik, V., Liaw, A., Tong, C., Culberson, J. C., Sheridan, R. P., & Feuston, B. P. (2003). Random forest: a classification and regression tool for compound classification and QSAR modeling. Journal of chemical information and computer sciences, 43(6), 1947-1958.

Schonlau, M., & Zou, R. Y. (2020). The random forest algorithm for statistical learning. The Stata Journal, 20(1), 3-29.

Yao, D., Zhan, X., Zhan, X., Kwoh, C. K., Li, P., & Wang, J. (2020). A random forest based computational model for predicting novel lncRNA-disease associations. BMC bioinformatics, 21, 1-18.

Gholizadeh, M., Jamei, M., Ahmadianfar, I., & Pourrajab, R. (2020). Prediction of nanofluids viscosity using random forest (RF) approach. Chemometrics and Intelligent Laboratory Systems, 201, 104010.

Babar, B., Luppino, L. T., Boström, T., & Anfinsen, S. N. (2020). Random forest regression for improved mapping of solar irradiance at high latitudes. Solar Energy, 198, 81-92.

Speiser, J. L., Miller, M. E., Tooze, J., & Ip, E. (2019). A comparison of random forest variable selection methods for classification prediction modeling. Expert systems with applications, 134, 93-101.

Probst, P., & Boulesteix, A. L. (2017). To Tune or Not to Tune the Number of Trees in Random Forest. J. Mach. Learn. Res., 18(1), 6673-6690.

Mishra, S., Tadesse, Y., Dash, A., Jena, L., & Ranjan, P. (2021). Thyroid Disorder Analysis Using Random Forest Classifier. In Intelligent and Cloud Computing (pp. 385-390). Springer, Singapore.

Kandhoul, N., Dhurandher, S. K., & Woungang, I. (2021). Random forest classifier‐based safe and reliable routing for opportunistic IoT networks. International Journal of Communication Systems, 34(1), e4646.

Vakharia, V., Vaishnani, S., & Thakker, H. (2021). Appliances Energy Prediction Using Random Forest Classifier. In Recent Advances in Mechanical Engineering (pp. 405-410). Springer, Singapore.

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rpart

https://cran.r-project.org/package=rpart.plot

https://cran.r-project.org/package=party

### Chapter 5:  Support Vector Machine Algorithm

![](media/file0.png)

Support Vector Machine (SVM) Algorithm aims to find out the hyper plane which differentiates the classes in the data set while maximizing the margin between the classes.  Support vectors are those sample observation which lies closer to the hyper plane. The hyperplane can be linear or non-linear. 

Kernel functions of the SVM algorithm helps us to transform the non-linear data sets into higher dimensional space and then use linear equations to divide the space using different Kernel functions such as linear, non-linear, Radial Basis Function and Sigmoid.

We will use cardiology patient’s survival data set for building the SVM model (survival.xlsx). The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php .

We can use packages such as e1071 and caret to build SVM models.

We need to define the required packages such as e1071, and xlsx using library statement.

![](media/file50.png)![](media/file5.png)

WE WILL IMPORT THE data in the form of excel using xlsx package as done in the previous chapter

![](media/file51.png)![](media/file52.png)

The following are the first few rows of the dataset.

SVM - Classification problem

![](media/file53.png)

We will be using SVM to classify the data set based on the ‘Diseasestatus’ field. It will help us to classify who are likely to be survived based on the features (Classification problem).

![](media/file5.png)![](media/file54.png)

WE CAN USE TUNE FUNCTION to tune model with different values for the cost parameter

![](media/file55.png)![](media/file5.png)![](media/file56.png)

FROM ABOVE TUNE SUMMARY we can infer that the cost with value 0.1 gives the best model.

We can use predict function to predict the test data set and calculate the prediction accuracy. We will use the first model with cost 15 for the prediction purpose.

![](media/file57.png)![](media/file5.png)

THE FOLLOWING OUTPUT obtained

![](media/file58.png)![](media/file5.png)

HERE THE ACCURACY IS 50.8% and it might be low due to nature of hypothetical data set.

![](media/file59.png)

We can plot the receiver operating curve with the help of ROCR package and prediction function.

The following curve is obtained with False Positive Rate and True Positive Rate.

![](media/file60.png)

Advantages of SVM

SVM is suitable for high dimension data sets

It works well with different types of data such as text, numbers and images

Offers unique solution

Disadvantages of Random Forest Algorithm

Processing time will be more while handling large data sets

Final model might difficult to understand

References

Wang, L. (Ed.). (2005). Support vector machines: theory and applications (Vol. 177). Springer Science & Business Media.

Xie, W., She, Y., & Guo, Q. (2021). Research on Multiple Classification Based on Improved SVM Algorithm for Balanced Binary Decision Tree. Scientific Programming, 2021.

Suthaharan, S. (2016). Support vector machine. In Machine learning models and algorithms for big data classification (pp. 207-235). Springer, Boston, MA.

Pavlidis, P., Wapinski, I., & Noble, W. S. (2004). Support vector machine classification on the web. Bioinformatics, 20(4), 586-587.

Peng, S., Hu, Q., Chen, Y., & Dang, J. (2015). Improved support vector machine algorithm for heterogeneous data. Pattern Recognition, 48(6), 2072-2083.

Zhang, Y. (2012, September). Support vector machine classification algorithm and its application. In International Conference on Information Computing and Applications (pp. 179-186). Springer, Berlin, Heidelberg.

Noble, W. S. (2004). Support vector machine applications in computational biology. Kernel methods in computational biology, 71, 92.

Osowski, S., Siroic, R., Markiewicz, T., & Siwek, K. (2008). Application of support vector machine and genetic algorithm for improved blood cell recognition. IEEE Transactions on Instrumentation and Measurement, 58(7), 2159-2168.

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rpart

https://cran.r-project.org/package=rpart.plot

https://cran.r-project.org/package=e1071

https://cran.r-project.org/package=ROCR

### Chapter 6:  Naïve Bayes Algorithm

![](media/file0.png)

Naïve Bayes works on the Bayesian principle and assumes independence among the features given the class label in the data set. It includes the following probabilities in classifying the data set into class

Prior probability for the class

Posterior probability for the class given the features

Likelihood of predictor or  features given the class

Prior probability of features or predictors  

We will use the same cardiology patient’s survival data set which is used for building the SVM model. The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php .

We can use packages such as e1071, naivebayes and caret to build Naïve Bayes models as we built the SVM model.

We need to define the required packages such as e1071, and xlsx using library statement.

![](media/file61.png)![](media/file5.png)

WE WILL IMPORT THE data in the form of excel using xlsx package as done in the previous chapter

![](media/file5.png)![](media/file62.png)![](media/file5.png)

THE FOLLOWING TABLE provides first few rows of the dataset. We will remove the patientid variable from the original data set for analysis purpose

![](media/file63.png)

Naïve Bayes - Classification problem

We will be using Naïve Bayes algorithm to classify the data set based on the ‘Diseasestatus’ field. It will help us to classify who are likely to be survived based on the features (Classification problem).

![](media/file64.png)![](media/file5.png)![](media/file65.png)![](media/file66.png)![](media/file67.png)

THE ABOVE OUTPUT PROVIDES conditional probability for class variable with respect to each feature.

![](media/file68.png)

We can use predict function to predict the test data set and calculate the prediction accuracy.

![](media/file5.png)

THE FOLLOWING OUTPUT obtained

![](media/file69.png)![](media/file5.png)

HERE THE ACCURACY IS 49.16% and it might be low due to nature of hypothetical data set.

We can plot the receiver operating curve with the help of ROCR package and prediction function.

![](media/file70.png)

The following curve is obtained with False Positive Rate and True Positive Rate.

![](media/file71.png)

Advantages of Naïve Bayes 

Easy to build

Suitable for large dataset

It is scalable with increasing features and observations.

It can be used with text and numeric data sets.

Disadvantages of Naïve Bayes

Assumption of independence between predictors

References

Vembandasamy, K., Sasipriya, R., & Deepa, E. (2015). Heart diseases detection using Naive Bayes algorithm. International Journal of Innovative Science, Engineering & Technology, 2(9), 441-444.

Zhang, H., & Li, D. (2007, November). Naïve Bayes text classifier. In 2007 IEEE International Conference on Granular Computing (GRC 2007) (pp. 708-708). IEEE.

Chen, S., Webb, G. I., Liu, L., & Ma, X. (2020). A novel selective naïve Bayes algorithm. Knowledge-Based Systems, 192, 105361.

Krithiga, B., Sabari, P., Jayasri, I., & Anjali, I. (2021, January). Early detection of Coronary Heart Disease by using Naive Bayes Algorithm. In Journal of Physics: Conference Series (Vol. 1717, No. 1, p. 012040). IOP Publishing.

Zhang, H., Jiang, L., & Yu, L. (2021). Attribute and instance weighted naive Bayes. Pattern Recognition, 111, 107674.

Zhang, H., Cheng, N., Zhang, Y., & Li, Z. (2021). Label flipping attacks against Naive Bayes on spam filtering systems. Applied Intelligence, 1-12.

Nainwal, A., Gupta, D., & Pant, B. (2021). Probabilistic Model Using Bayes Theorem Research Paper Recommender System. In Research in Intelligent and Computing in Engineering (pp. 901-909). Springer, Singapore.

Sendari, S., Zaeni, I. A. E., Lestari, D. C., & Hariyadi, H. P. (2020). Opinion Analysis for Emotional Classification on Emoji Tweets using the Naïve Bayes Algorithm. Knowledge Engineering and Data Science, 3(1), 50-59.

Akbar, R., Nasution, S. M., & Prasasti, A. L. (2020, October). Implementation Of Naive Bayes Algorithm On IoT-based Smart Laundry Mobile Application System. In 2020 International Conference on Information Technology Systems and Innovation (ICITSI) (pp. 8-13). IEEE.

Winarti, T., & Vydia, V. (2020, February). Feature selection for optimizing the Naive Bayes algorithm. In Engineering, Information and Agricultural Technology in the Global Digital Revolution: Proceedings of the 1st International Conference on Civil Engineering, Electrical Engineering, Information Systems, Information Technology, and Agricultural Technology (SCIS 2019), July 10, 2019, Semarang, Indonesia (p. 47). CRC Press.

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rpart

https://cran.r-project.org/package=rpart.plot

https://cran.r-project.org/package=e1071

https://cran.r-project.org/package=ROCR

### Chapter 7:  Artificial Neural Network Algorithm

![](media/file0.png)

Artificial Neural Network (ANN) works on the principles of Human Nervous system. Human Nervous system includes components like Neurons, Synapse and dendrites to process and transfer information between neurons. Similar to It, ANN includes components such as artificial neurons and weights and transfer functions to process the information. Learning process takes place in ANN by adjusting weights in the system. 

ANN is made up of three layers input, hidden and output layers. The input features are fed into the system through input layer and weights are added to the input features and the same is transformed with the help of activation function and passed on to the output layer to produce final outcome.

ANN forms the basis for the other algorithms such as feed forward network, Reinforcement Learning, Convolution network, Long Short Term Memory (LSTM) network.

In feed forward network, the system adjusts the weights based on the error calculated between the actual and expected output. Adjustment of weights is done through back propagation method. Feed forward network works in the forward direction from input to output layer.

In reinforcement learning, feedback is provided to system and system needs to take action based on the situation through trial and error which maximizes the reward. The system will not be instructed what actions need to be taken and it needs to use trial and error method to check which action provide better reward.

We will use the same cardiology patient’s survival data set which is used for building the SVM model. The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php .

We can use package nnet, neuralnet to build ANN model.

We need to define the required packages such as nnet and xlsx using library statement.

![](media/file72.png)![](media/file5.png)

WE WILL IMPORT THE data in the form of excel using xlsx package as done in the previous chapter

![](media/file73.png)![](media/file5.png)![](media/file74.png)

THE FOLLOWING TABLE provides first few rows of the dataset. We will remove the patientid variable from the original data set for analysis purpose

![](media/file75.png)![](media/file5.png)

ARTIFICIAL NEURAL NETWORK - Classification problem

We will be using ANN algorithm to classify the data set based on the ‘DiseaseStatus’ field. It will help us to classify who are likely to be survived based on the features (Classification problem). Nnet function fits single hidden layer with 2 nodes ANN network. 

![](media/file76.png)![](media/file77.png)![](media/file78.png)

We can use predict function to predict the test data set and calculate the prediction accuracy.

![](media/file5.png)

THE FOLLOWING OUTPUT obtained

![](media/file79.png)

Here the accuracy is 49.8% and it might be low due to nature of hypothetical data set.

We can plot the receiver operating curve with the help of ROCR package and prediction function.

![](media/file80.png)![](media/file5.png)

THE FOLLOWING CURVE is obtained with False Positive Rate and True Positive Rate.

![](media/file81.png)

Advantages of ANN

Suitable for non-linear data

Not affected by outliers or noise in the data set 

Disadvantages of ANN

Difficult to interpret the model parameters

Problem of over fitting

Computationally heavy

References

Mehlig, B. (2019). Artificial neural networks. arXiv preprint arXiv:1901.05639.

Heriz, H. H., Salah, H. M., Abdu, S. B. A., El Sbihi, M. M., & Abu-Naser, S. S. (2018). English Alphabet Prediction Using Artificial Neural Networks.

Nasser, I. M., & Abu-Naser, S. S. (2019). Predicting Tumor Category Using Artificial Neural Networks.

Shenfield, A., Day, D., & Ayesh, A. (2018). Intelligent intrusion detection systems using artificial neural networks. ICT Express, 4(2), 95-99.

Yang, G. R., & Wang, X. J. (2020). Artificial neural networks for neuroscientists: A primer. Neuron, 107(6), 1048-1070.

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rpart

https://cran.r-project.org/package=rpart.plot

https://cran.r-project.org/package=e1071

https://cran.r-project.org/package=ROCR

https://cran.r-project.org/package=nnet

### Chapter 8:  Clustering Algorithm

![](media/file0.png)

Clustering algorithm is one of the unsupervised ML algorithms which do not contain separate train and test data set to build model. Clustering algorithm finds natural grouping and patterns in the data set.

There are different types of clustering algorithms are available such as

Partitioning clustering

Hierarchical clustering

Density based clustering

Model based clustering

Partitioning clustering – K means clustering

Partitioning clustering involves partitioning the data sets into predefined number of clusters. K means clustering algorithm is an example of partitioning clustering algorithm where the data set is partitioned into k clusters and observations are assigned to nearest clusters and cluster centroid are calculated for each k clusters.

The cluster membership is reassigned based on the closeness to new cluster centroids and the cluster centroids are again calculated after the new assignment. This process will continue till there is no change in cluster centroids.

Hierarchical Clustering

Hierarchical Clustering include clustering process which can use top down (Divisive) or bottom up (Agglomerative) approach. It provides us a tree like structure called dendogram to represent the clusters.

Divisive clustering algorithm starts to cluster the data set with single cluster and divide that top most cluster into different sub clusters till all the observations of the dataset are in one single cluster each.

Agglomerative clustering algorithm starts to cluster the data set by placing each observation into one single cluster and continue to aggregate each clusters and the process of aggregation continues till all the individual clusters are combined into one single cluster at the end. Here the clusters are combined based on the distance between them or clusters which are similar are aggregated first. There are different types of linkage methods are available such as

Single Linkage – Distance between two clusters are calculated using the distance between their closest points

Complete Linkage – Distance between two clusters are calculated using the distance between their furthest points

Average Linkage - Distance between two clusters are calculated using average distance between each and every points of two clusters.

There are different distance measures such as Euclidean (squared distance between two points), Manhattan (absolute difference between two points) are used to calculate the distance between two points or vectors.

Density based clustering

The data set is divided into clusters with high density and clusters with low density in data space. The points lie in the region which separates the low and high density space is generally considered as outliers in the data set.

Model based clustering

In Model based clustering method, clusters are generated from probability distributions and then the fitted model will be tested based on the data to finalize the clusters. This method provides the probability for each observation related to the belongingness to one particular cluster. It also helps us to identify the number of clusters present in the data set.

Partitioning clustering - K means clustering

We will start with building k means clustering model using purchase data set used in Decision tree algorithm to find the natural groups. The same file can be downloaded from author’s website www.vinaitheerthan.com/book.php

We need to define the required packages such as cluster ,factoextra and xlsx using library statement.

![](media/file82.png)![](media/file5.png)

WE WILL IMPORT THE data in the form of excel using xlsx package as done in the previous chapter

![](media/file83.png)![](media/file5.png)![](media/file84.png)

THE FOLLOWING TABLE provides first few rows of the dataset. We will remove the pamount variable from the original data set for analysis purpose

We will be using Kmeans algorithm to group the customers based on the Purchase data. It will help us to identify the groups or segments of customers who are close to each other in terms of products purchase, price, place, age and gender

![](media/file85.png)![](media/file5.png)

THE ABOVE CODE PROVIDES us the clustering summary for 5 clusters (k=5) along with the graphical representation.

![](media/file86.png)![](media/file87.png)![](media/file88.png)

The above table provides cluster means for each feature along with cluster membership for all the observations as cluster vectors.

The following plot provides data set divided into 5 clusters

![](media/file89.png)

WE CAN ALSO FIND OUT how many clusters are required to group the data set through Elbow plot which minimizes the within cluster sum of squares.

In our example we have started with the value k=5 and normally we can start with the Elbow plot and run the k-means algorithm based on the result.

![](media/file90.png)![](media/file5.png)![](media/file91.png)

FROM THE ABOVE PLOT we can infer that the within cluster sum of squares is not decreasing significantly after 4/5 th cluster.

Advantages of K-means Clustering Algorithm

Easy to implement

Faster

Disadvantages of K-means Clustering Algorithm

Difficult to predict number of clusters

Difficult to scale

Affected by initial seed values

Hierarchical clustering – Agglomerative  

![](media/file92.png)

We can build Hierarchical Agglomerative clustering using hclclust function. Algorithm will provide dendogram which is a visual representation of the clusters and we demarcate the clusters using cut tree function 

![](media/file93.png)

HERE WE HAVE USED THE default distance and linkage method. We can specify distance measures like Euclidean and Manhattan distance measures and complete linkage and ward method.

Advantages of Hierarchical Clustering Algorithm

Easy to implement

Produces hierarchy of clusters which helps us to decide the number of clusters

Disadvantages of Hierarchical Clustering Algorithm

Affected by outliers

Affected by initial seed values

Difficult to scale

Model based clustering

We can use mclust package to build the model based clustering. It uses maximum likelihood estimation method to find the best model and number of clusters using Bayesian Information Criteria (BIC).

![](media/file94.png)![](media/file5.png)![](media/file95.png)![](media/file96.png)

ADVANTAGES OF MODEL based Clustering Algorithm

Statistically based clustering algorithm which helps us to draw inferences from the clusters easily

Easy to find the number of clusters

Handles outliers well

Disadvantages of Model based Clustering Algorithm

BIC scores may not be available when there are less number of sample points

References

Likas, A., Vlassis, N., & Verbeek, J. J. (2003). The global k-means clustering algorithm. Pattern recognition, 36(2), 451-461.

Rani¹, Y., & Rohil, H. (2013). A study of hierarchical clustering algorithm. ter S & on Te SIT, 2, 113.

Zhong, S., & Ghosh, J. (2003). A unified framework for model-based clustering. The Journal of Machine Learning Research, 4, 1001-1037.

Yu, M., Jieyan, Y., Jiajia, Z., & Xinzhou, C. (2021). Intelligent Detection of Network Coverage Problems Based on the Clustering Algorithm. In Signal and Information Processing, Networking and Computers (pp. 1010-1018). Springer, Singapore.

Sinaga, K. P., & Yang, M. S. (2020). Unsupervised K-means clustering algorithm. IEEE Access, 8, 80716-80727.

https://cran.r-project.org/package=cluster

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=factoextra

### Chapter 9:  Text mining algorithms

![](media/file0.png)

Text mining algorithms helps us to analyze the data which is in unstructured or non-numerical or text format.  Text mining algorithms forms the basis for Natural Language Processing (NLP) Algorithms which helps us to understand the meaning of text and sentiment analysis algorithms helps us to understand the hidden sentiments in the text.

Text mining algorithm involves the following steps

Extraction of text data from the source

Creation of text corpus

Preprocessing of the text

Tokenize

Stemming

Lemmatizing

Stop removal

Part of Speech Tagging

Chunking

Analysis of text data

Computing document related measures

Statistical Modeling

Supervised Machine Learning

Unsupervised Machine Learning

Topic Modeling

Sentiment Analysis

Graphical representation of text data

Extraction of text data from the source

There are large amount text based data available in social media websites like Facebook and Twitter and also in the form of reviews in e-commerce websites like Amazon and e-bay. Text data can be extracted using Application Program Interface provided by sites like Twitter or we can extract the text using web scarping methods. Web scrapping methods involve extracting the contents inside the html tags such as 

and

.

Creation of Text Corpus

After extracting the text from the source it needs to be saved in text corpus which can include text or texts in the form of documents for further processing. Each sentence in the corpus is treated as single document. Each document is in turn represented by multi-dimensional vectors.

Preprocessing of the text

Once we create the text corpus we need to preprocess the text before proceeding to the analysis stage. The following are the components of preprocessing

Tokenization 

The sentences need to be broken into meaningful components such as words. White space or punctuation marks helps us to tokenize the sentences into words.

![](media/file5.png)

Stemming

STEMMING PROCESS HELPS us to retain the root of the given word.  It helps remove the duplicate words which have same root word in the sentence.

Lemmatizing

It is similar to stemming but with difference of linking words with similar meaning while removing the inflectional ending from the words.

Stop words removal

Stop words removal plays an important role in the preprocessing as it removes the stop words such as ‘a’, ‘the’ ‘and’ which occurs very frequently in a document.

Parts of Speech Tagging (POS)

Parts of speech tagging helps us to tag the parts of speech in a sentence like Noun, Verb and Adjectives.  POS plays an important role in NLP and Sentiment analysis tasks.

Chunking

Chunking is done at the token level in sentence by grouping the tokens into similar chunks or syntactically correlated tokens.

Analysis of text data

Analysis text data involves computing document related measures, Statistical, Supervised and Unsupervised Machine Learning Algorithms, Natural Language Processing techniques and sentiment analysis techniques.

Document related Measures

At the starting of point of analysis we need to calculate the following measures such as Term Frequency (TF), Inverse Document Frequency (IDF) and Term Document Matrix (TDM).

Term Document Matrix (TDM)

Term Document Matrix is the matrix representation of documents in the text corpus. Here it contains documents in the column level and terms in the row level and the particular cell in the matrix is the term weight. The term weight can be measured using binary weight or TF or IDF or TF-DIF combined. Here Binary weights are nothing but whether a term is present in that particular document or not and represented by 0 and 1.

Term Frequency (TF)

Term Frequency is the frequency of terms in a specific document (A document can be a single sentence or whole document such as research article).

Inverse Document Frequency (IDF)

Inverse Document Frequency assigns higher weight to uncommon words and lower weights to common words such ‘a’ and ‘the’.

Term Frequency - Inverse Document Frequency (IDF)

Higher weights are given to terms which are uncommon as well as having significant level of frequency.

Statistical Modeling

Statistical Modeling in text mining involves the use of statistical probability concepts and distribution in the analysis stage. The following aspects are considered in statistical modeling

Sentence is made up of sequence of words

Probability of next word is obtained through condition probability

Probability of whole sentence is calculated from joint probability.

We will use language models such as Unigram and N-gram models to generate probability distribution sequence of words. Here Unigram models generate words independently given the condition probability and wherein the N-gram model assumes dependence up to n-1 terms in the sequence. 

Markov model helps us to model the probabilities as it assumes the future state depends only on the current state and not the past states. Hidden Markov Models are extension of Markov Models and it contains states, observations and transition probabilities of going from state i to state j.

Smoothing techniques will help us to fine tune the probabilities of words in the sequence when the probabilities for a given conditional probability is unknown. The unknown probabilities will be estimated using techniques like Laplace and additive smoothing techniques.

Supervised Machine Learning Algorithms

Supervised Machine Learning Algorithms helps us to classify or categorize the text into a given topic or class. The well- known example of text classification is email spam filtering.

Text classification process can be done with rule based method also which use linguistic rules to classify the incoming text. The system uses predefined or stored knowledge about the particular domain and uses it for classification. Creating the domain and rules are challenging part of this method

Compared to Rule based classification system, Supervised Machine Learning system does not require the complete domain knowledge about the domain but it learns through data and improves its classification or categorization accuracies. The previously seen supervised Machine Learning Algorithms such as Support Vector Machine and Naïve Bayes can be used to classify the text based datasets also.

Unsupervised Machine Learning Algorithms

The unsupervised Machine Learning Algorithms helps us to group or find association between the documents. The previously seen clustering algorithms such K-means partitioning algorithms or Hierarchical Clustering algorithms can be used to group the documents.

For example we can group scientific articles which are having similar topic or discussing similar topic and patients records which are having same disease conditions.

Topic Modeling

Topic modeling uses techniques such as Latent Dirichilet Allocation (LDA) to assign topics to the given set documents. LDA first generates the probability model of words under given topic.  Then it examines the incoming document and assigns the topic based on the generated probability model.

![](media/file5.png)

Sentiment analysis

SENTIMENT ANALYSIS helps us to extract the hidden sentiment in the given text data set. Sentiment analysis is useful analyzing the reviews about the products or hotel or any service where the user or customer given their reviews. The reviews can be classified as positive, neutral or negative given the context of the text data set.

Graphical representation of text data

The extracted text can be visualized using graphical tool Word Cloud. It represents cluster of words from the data set in a graphical form wherein the most frequently occurring word will be represented with higher font denoting its importance in the data set.

Text mining examples

Let us start with the task of classifying and clustering the example data sets using supervised and unsupervised ML algorithms.  Also we will carry out the sentiment analysis based on the example dataset.

Let us consider a hypothetical product review dataset which contains reviews about the product and each review will be termed as a document for our analysis purpose. Here we have extracted the reviews and stored it in a single text document. In real time application it will be better to use APIs or web scrapping methods.

Twitter – Tweet extraction through API

The following code helps us how to use Twitter APIs to extract the Tweets. To get the tweets from the Twitter user need to have twitter account and register for API request and upon registration we will get the following keys

Consumer key

Consumer secret key

We need to install the rtweet package and define the same along with other required packages

We will have to input the same in the following code

![](media/file97.png)

We will get the confirmation from the Twitter. Now we can search the twitter and get the required tweets to our R environment using the following code.

![](media/file98.png)

The same can be used for further processing.

Web scraping

We can extract the text from online websites through web scrapping methods. We need to install rvest and xml2 package to carry out the web scrapping.

The following code helps us to extract data from a website. Here  we will use read\_html() and html\_nodes() to read and extract the html tags such as 

respectively. To extract the contents inside these tags we need to use html\_text() function.

![](media/file99.png)![](media/file5.png)

PRODUCT REVIEW EXAMPLE

Now we start with the hypothetical product review example data set which is stored in the text file in the work directory.

![](media/file100.png)![](media/file5.png)![](media/file101.png)

WE WILL USE TM PACKAGE to carry out the text mining process.

We will create corpus from the text file and represent it in a vector space. In the next step, preprocess the document by removing stop words, punctuations, numbers and white spaces using tm\_map function of the tm package.

![](media/file102.png)

Here we have converted each sentence into single document for the analysis purpose. We will now construct the Term Document Matrix (TDM)

![](media/file103.png)

Few rows from the final TDM is given below

![](media/file5.png)![](media/file104.png)![](media/file105.png)

WE WILL VISUALIZE THE text using wordcloud package.

![](media/file106.png)

TEXT CLASSIFICATION example – Supervised Machine Learning Algorithms

We will now use publically available data set from the below link which has product reviews and reviews classified into label1 and lable2 (label1-positive and label2-negative) to classify the reviews using Support Vector Machine (SVM) Algorithm

https://github.com/necronet/RML-101/blob/master/svm\_textclassification/corpus.csv

We will define the required package to build the SVM model and read the content of the excel file

![](media/file107.png)![](media/file5.png)

WE WILL DEFINE THE training and test data set for building the SVM model

![](media/file108.png)![](media/file5.png)

WE WILL MAKE THE LABEL variable as factor and use it the SVM Model below

![](media/file5.png)![](media/file109.png)![](media/file5.png)

THE SUMMARY OF THE model is given below

![](media/file110.png)![](media/file111.png)

We can check the prediction accuracy through confusion matrix

![](media/file5.png)![](media/file112.png)

HERE THE ACCURACY IS less 0.53 which may be due to the data set.

We can plot ROC curve using ROCR package.

![](media/file113.png)

The following ROC curve obtained

![](media/file114.png)

TEXT CLASSIFICATION example – Unsupervised Machine Learning Algorithms

We can use unsupervised Machine Learning Algorithms to group or cluster the product reviews using Agglomerative clustering technique. We will be using same product review data set but with labels column removed and only 50 reviews will be taken for analysis

![](media/file115.png)![](media/file5.png)![](media/file116.png)

WE WILL PREPROCESS the data as before with the help of tm\_map function of the tm package.

The following Document Term Matrix is obtained wherein the rows represents document or reviews and columns represents the words in the corpus.

![](media/file117.png)

We will define the distance measures and build hierarchical clustering models using hclust function and also plot the dendogram which provides the graphical representation of association between the reviews or documents under consideration. It shows which reviews are similar or in turn which customers given similar reviews.

![](media/file118.png)![](media/file5.png)![](media/file119.png)

SENTIMENT ANALYSIS example

We can extract the hidden sentiment through syuzhet package. We will be using the product review data set with 50 reviews.  We will use get\_nrc\_sentiment function to get the sentiments and calculate the sentiment scores on 10 sentiment heads like “Anger”, “Joy”, “Positive” and “negative”. The same will be depicted in the graphical format.

![](media/file120.png)![](media/file121.png)![](media/file122.png)![](media/file123.png)

REFERENCES

Aggarwal, C. C., & Zhai, C. (Eds.). (2012). Mining text data. Springer Science & Business Media.

Hotho, A., Nürnberger, A., & Paaß, G. (2005, May). A brief survey of text mining. In Ldv Forum (Vol. 20, No. 1, pp. 19-62).

Berry, M. W., & Kogan, J. (2010). Text mining. Applications and Theory. West Sussex, PO19 8SQ, UK: John Wiley & Sons.

Cheng, M. Y., Kusoemo, D., & Gosno, R. A. (2020). Text mining-based construction site accident classification using hybrid supervised machine learning. Automation in Construction, 118, 103265.

Ju, Z., Wang, J., & Zhu, F. (2011, May). Named entity recognition from biomedical text using SVM. In 2011 5th international conference on bioinformatics and biomedical engineering (pp. 1-4). IEEE.

Agnihotri, D., Verma, K., & Tripathi, P. (2014, April). Pattern and cluster mining on text data. In 2014 Fourth International Conference on Communication Systems and Network Technologies (pp. 428-432). IEEE.

Vijayarani, S., Ilamathi, M. J., & Nithya, M. (2015). Preprocessing techniques for text mining-an overview. International Journal of Computer Science & Communication Networks, 5(1), 7-16.

Kadhim, A. I., Cheah, Y. N., & Ahamed, N. H. (2014, December). Text document preprocessing and dimension reduction techniques for text document clustering. In 2014 4th International Conference on Artificial Intelligence with Applications in Engineering and Technology (pp. 69-73). IEEE.

Gräbner, D., Zanker, M., Fliedl, G., & Fuchs, M. (2012, January). Classification of customer reviews based on sentiment analysis. In ENTER (pp. 460-470).

https://cran.r-project.org/package=tm

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=rvest

https://cran.r-project.org/package=cluster

https://cran.r-project.org/package=xml2

https://cran.r-project.org/package=xlsx

https://cran.r-project.org/package=e1071

https://cran.r-project.org/package=caret

https://cran.r-project.org/package=ROCR

https://cran.r-project.org/package=syuzhet

### Chapter 10: Image processing and classification

![](media/file0.png)

Image processing and classification can be done through keras package in R. Deep learning models are widely being used in image classification.

The raw images need to be converted into array format which includes image id, height and width of images. After that we need to covert the array into matrices by reshaping the width and height. We also need to convert the color or gray scale values between 0 and 1.

We need to train and test data set to train and test the model.

Keras sequential model which has different layers such as dense and drop out layers and activation function helps us to process and classify the images.

We can use Keras inbuild image data sets such digit mnist and fashion MNIST datasets for our image classification models.

Here the image data set is a list with image and its labels values stored as arrays of numbers with respect to image characteristics such height, width and color

![](media/file124.png)

We will now create the train and test image data sets

![](media/file125.png)![](media/file126.png)

We need to reshape and rescale the train and test datasets for further processing

We now proceed to build the keras model with dense and drop out layers

![](media/file127.png)

The following model summary is obtained

![](media/file128.png)![](media/file129.png)![](media/file130.png)

We will now proceed to compile the model

![](media/file131.png)

After compilation we fit the model

The following is output out of first 2 Epoch out of 30 Epochs

![](media/file132.png)

The same is given in the graphical form

![](media/file133.png)![](media/file134.png)

We will now use test data set to evaluate and predict the model.

![](media/file5.png)![](media/file135.png)

THE MODEL PROVIDED 88.75% accuracy in classifying the fashion image data set and following predicted class labels are given below

![](media/file136.png)

References

https://tensorflow.rstudio.com/guide/keras/

https://cran.r-project.org/package=keras

Mishra, N. K., & Celebi, M. E. (2016). An overview of melanoma detection in dermoscopy images using image processing and machine learning. arXiv preprint arXiv:1601.07843.

Pandey, R., Naik, S., & Marfatia, R. (2013). Image processing and machine learning for automated fruit grading system: A technical review. International Journal of Computer Applications, 81(16), 29-39.

Kumar, V. B., Kumar, S. S., & Saboo, V. (2016, September). Dermatological disease detection using image processing and machine learning. In 2016 Third International Conference on Artificial Intelligence and Pattern Recognition (AIPR) (pp. 1-6). IEEE.

Lézoray, O., Charrier, C., Cardot, H., & Lefèvre, S. (2008). Machine learning in image processing.

Jagadev, P., & Virani, H. G. (2017, May). Detection of leukemia and its types using image processing and machine learning. In 2017 International Conference on Trends in Electronics and Informatics (ICEI) (pp. 522-526). IEEE.

Dey, A. (2016). Machine learning algorithms: a review. International Journal of Computer Science and Information Technologies, 7(3), 1174-1179.

Šajn, L., & Kukar, M. (2011). Image processing and machine learning for fully automated probabilistic evaluation of medical images. Computer methods and programs in biomedicine, 104(3), e75-e86.

Page 

Don’t miss out!

Click the button below and you can sign up to receive emails whenever Vinaitheerthan Renganathan publishes a new book. There’s no charge and no obligation.

![](media/file137.png)

https://books2read.com/r/B-A-YASK-KWGPB

![](media/file138.png)

Connecting independent readers to independent writers.

Also by Vinaitheerthan Renganathan

Business Intelligence : an Overview

Stock Price Analysis Through Statistical And Data Science Tools: an Overview

Machine Learning Algorithms for Data Scientists: An Overview

Biostatistics Explored Through R Software: An Overview

Watch for more at Vinaitheerthan Renganathan’s site .

About the Author

Statistician and Data Scientist with 26 years of experience in the field of Clincal,Manufacturing, Quality Assurance and Marketing Research. 

Read more at Vinaitheerthan Renganathan’s site .