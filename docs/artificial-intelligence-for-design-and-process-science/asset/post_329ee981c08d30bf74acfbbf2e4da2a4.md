
# Introducing Feature Selection Before Propositionalization

In exchange for computation complexity, wrapper techniques provide better predictive accuracy estimates than filter models.

The third category is embedded models, in which the feature selection process is embedded as part of the training algorithm, as opposed to being a step in the preprocessing stage of machine learning.

Structured feature selection assumes that the feature space contains features that may be dependent on one another. FS strategy depends on the assumed structure, either group structure, tree structure, or graph structure.

J. Tang et al. (2014) [1] provides examples for structured feature selection for cases where the group structure has already been inferred. These examples are modifications of the embedded method, lasso regularization. Lasso regularization generates weights as part of the model optimization process, and feature selection is performed naturally when coefficients of features are set at 0 or close to 0.

Modifications are based on the structure of the features, which are group structures, tree structures, or graph structures.

When a group structure is assumed, features are put into groups, and feature selection is based on the group's performance instead of an individual feature's performance.

Tree structure assumes that features are hierarchical in nature with several levels of parent and child nodes, with features at the bottom layer. Nodes are examined for feature selection, in which case underperforming nodes and their underlying features are discarded.

Graph structures imply directionless relationships between features, in which case the weights of the lasso features are adjusted during selection based on related features in the graph.

T. Gao et al. (2015) [7] treated graph feature selection as a search problem to find a target Markov blanket by determining inter-feature relationships, the features and creates a Bayesian network determining which may be simplified to "Parent," "Child," "Spouse," and "Descendants." Compared to graph structures, a Bayesian network is simply a graph structure with directional relationship.

Gao et al. noted that the Markov blanket of a target feature, which contains its spouses, parents, and child, will contain the minimum number of features within the feature space, which also gives the maximum mutual information required for a classifier model.

## 3.2 Evaluation of Feature Selection Strategies

Evaluation of feature selection models is chiefly by evaluating the trained model's effectiveness [8]. As evaluating training models, performance metrics can include accuracy, precision, recall, F1-score, and area under the receiver operating characteristic (ROC) curve. These metrics measure the model's ability to

First, we perform Database Attribute Health Reduction (DAHFR), which is a filter method [9] that visualizes and selects relevant features from databases based on their relational missingness. This process requires the selection of a baseline feature for relational missingness comparison. Relational missingness for features are measured based on the percentage of baseline feature's data represented by the measured feature. Relational missingness is represented in two forms, table and attribute health, which discriminates some Missing Not at Random features from what would otherwise be treated as Missing Completely at Random features. Selection at this stage is performed by using a missingness threshold, which is different when used for single databases and multi-sourced databases.

# Introducing Feature Selection Before Propositionalization

## Multisource FSBp Methodology

![](img/accb0e713daa15f4a51070565405380d_194_0.png)

Fig. 1 FSBp process in relation to KDD and machine learning of oil data. FSBp refers to the timing of feature selection during KDD, while one implementation of FSBp

## 4.3 RFCM

Second, we perform Report Feature Correlation Matrix (RFCM), which converts reports generated from the database's data to create a feature graph (graph structure) that contains correlation data between features to represent business knowledge. With permission to access the reporting module of the system that uses the database, we explore the reporting module and record on a per-report basis and record properties and keywords related to the report. The keywords are grouped according to where they are found in the report generation process, e.g., scope of report, group by parameters, and report attributes. These keywords are refined by searching online resources, and then a graph is made based on how often the keywords are found together. The graph structure is used to estimate the Markov blanket [7] of a target label based on its keyword.

## 4.4 Relating DAFHR to RFCM

Third, we relate DAFHR to RFCM by linking the “database domain” and “business domain,” respectively, using the knowledge gained from the keyword search. The keywords are linked to tables on the tables’ names or their column names.

## 4.5 Feature Selection

Finally, we perform the selection process by selecting the target label concept in the RFCM/business domain and selecting the related relevant data in DAFHR/database domain.

## 4.6 Data Mining and Evaluation

After FSbP is performed, the data undergoes further selection and combined propositionalization and harmonization. For propositionalization and harmonization, a standard set of definitions is made for selected features from the five databases including the label, which is the oil-drilling phase duration.

As part of the data mining step, several preprocessing methods are used to determine the most effective methods.

The dataset is split 70/30 for training operations (randomly selected with identical seed values) and testing operations, and training is done with a tenfold cross validation, also splitting by operations instead of phases. This is because one oil drilling operation involves several phases that are pre-determined.

The performance of the models is evaluated on traditional ML metrics [10] of RMSE, MSE, and MAE, in addition to a custom metric; "larger than 0," as the result (being a prediction) must always be larger than 0. In addition, suitability of the resulting is determined by comparing the predicted DvD (drilling rate across phases) against the actual DvD of an operation.

# Results

## 5.1 FSbP Features Reduced

The FSbP process began with about 700 tables and 20,000 features per database.
As seen in Table 2, DAHFR was able to identify the sparsest (completely unused features) and reduce the feature scope to 131 tables with 2967 features. Further DAHFR leaves 37 tables with 707 features.

RFCM processed 125 distinct business reports and was used to identify and graph 48 keywords (Table 3). These 48 RFCM keywords were linked to 50 database tables.

Twenty-four keywords from RFCM were keywords related to "duration" or were neighbors to duration keywords (at this time, the Markov blanket was not used due to error). From these, 35 target tables were identified (Table 4). Further selection (based on DAHFR health table, keyword definition) reduces the number of tables for further examination to 22 tables of the initial 700 tables, a removal of 96.8% of tables from scope.

Unfortunately, only one database was used instead of all five by the end of the project to simplify the project, although harmonization was mostly completed.

## 5.2 Predictive Modeling Results

The dataset had an average of 82.5 h, median of 29.7 h, mode of 2694 h, and std dev of 124 h. SKLearn models of Random Forest Regressor, Linear Regressor, and Multilayer Perceptron are trained from the model with various preprocessing steps, resulting in the top-ranking models as shown in Table 5. The best model's accuracy distribution is shown in Fig. 2 while Fig. 3 shows a result where multiple predicted phase durations are compared against actual phase durations over the duration of a project.

# Table 2 Number of tables and features selected by DAHFR

| | Not including identifier features | | |
|---|---|---|
| | DAHFR Remove Unused Features | Harmonize DAHFR |
| # Tables | ~700 | 121 | 37 |
| # Features | ~20,000 | 2967 | 707 |
