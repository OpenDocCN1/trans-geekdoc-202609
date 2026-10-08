
# Introducing Feature Selection Before Propositionalization

Clement Ting, Patrick Then, and Man Lu

**Abstract** The selection stage of knowledge discovery in databases (KDD) reduces the project scope to features relevant to the data objective while maintaining the final model's effectiveness. The scope reduction is important because the next stage of KDD, compilation (propositionalization), is a resource-intensive task that converts the data from a relational dataset into a propositional dataset for data mining. However, KDD selection is done manually because conventional feature selection techniques are not compatible with the pre-compiled, relational data.

In this chapter, we introduce an automated feature selection before propositionalization (FSbp) and compare its characteristics with traditional feature selection techniques. We provide a use case for FSbp in KDD for oil drilling data, where FSbp is vital for timely project completion. We also discuss the implementation of FSbp algorithms for the above use case, areas for improvement, and limitations of FSbp.

**Keywords** Feature selection before propositionalization · Big data · Harmonization · Knowledge discovery in databases · Oil drilling

## ## Introduction

Feature selection is a staple preprocessing task in machine learning that aims to remove redundant or irrelevant features from training sets. It has been shown to improve model accuracy, training time, generalization ability, and model running time. This process, however, assumes that the dataset to be used is already in proportional format [1]. In propositional format, data is stored in the form of an attribute-value representation in a single table [2].

The process of propositionalization is used to transform relational data into propositionalized data and may include steps as the joining of tables via their relationship and aggregation or other preprocessing techniques.

When performing KDD on previously collected oil drilling data [3], this transformation process is not feasible if performed on the entire sets of data, which is multi-sourced (requiring harmonization), and sparse [4] (each source containing about 700 tables and 20,000 columns/features), and sparse [5]. Because that the transformation of each feature requires prior knowledge of its business rules.

The above process becomes difficult when the database model is not available to determine relationships between tables and sparse data interferes with the table joining process and priors are either not available to the data scientist or sources of priors either conflict with one another or with the data.

A method is required to determine which data are most relevant to the learning objective before propositionalization that is not reliant on the availability of priors.

This chapter is broken down into seven sections. In the Introduction, we have introduced the motivation for FSbP. In the Introducing FSbP, we describe FSbP and Comparing it to KDD and regular feature selection environments. In the Literature Review section we discuss relation regarding feature selection techniques that may be relevant to the implementation and measuring the efficacy of FSbP. In the Methodology section, we discuss implementations of FSbP as used in the context of KDD for oil drilling. In the Results section, we show our results in the form of percentage of features selected and model performance. In the Discussion section, we discuss initial findings from the execution of FSbP, and we conclude with the Conclusion section.

## Introducing FSbP

A method is required to determine which data are most relevant to the learning objective before propositionalization that is not reliant on the availability of priors. To address this, we introduce a novel concept called feature selection before propositionalization (FSbP). FSbP is performed on propositionalized data, which is relational data that has not yet joined and compiled. This technique is different from any forms of feature selection (Table 1) because it allows for the selection of relevant features early in the KDD process, before the data has been fully processed and compiled.

FSbP is performed during the “selection” process of KDD, which is different from the “filtering” stage of machine learning. The objective of FSbP is to select the most relevant features to create a training set with minimal observation and exploration of the data. This technique is particularly useful for the KDD of high-dimensional datasets.

# Table 1 Comparing FSbP KDD FSS and ML FS

| FSbP | KDD FS | ML FS |
| --- | --- | --- |
| Purpose | Select features most relevant to project objective reduces scope with minimal reduction to model accuracy | KDD: Data Mining |
| Timing | KDD: Selection | Variance Threshold, Univariate Selection |
| Methodology | In this project, combining DAHER and RFCM | Gather expert knowledge to determine relevant features | Recursive Feature Elimination, Select from Model, Sequential Feature Selection |
| Metrics | Feature relevance gathered from measures before propositionalization In this project, data missingness, feature relation to label | Feature relevance as defined by expert knowledge | Variance of feature, Feature correlation to label or model accuracy |
| Advantage | Doesn't require propositionalization metrics results | Quick if expert knowledge is available | Reasonable and repeatable metrics and results |
| Limitation | Data have not been propositionalized Difficulty to measure (long project duration between KDD: Selection and completion of KDD:Data Mining). | Requires access to expert knowledge of database and business rules on existing business rules and may miss new knowledge. Less scalable when multiple experts (one or more for source) must be consulted Reliance on expert knowledge which may change from expert to expert | Requires standardized, propositionalized dataset |

The importance of FSbP is highlighted in situations where there is little knowledge available to determine the relevant features for the training set. In these cases, selecting relevant features in the KDD process reduces the dependence on expert knowledge and biases, which can improve the generalizability of the dataset. This also speeds up the data compilation process and reduces the amount of manpower required to process the features.

While there are some similarities between FSBP and existing forms of feature selection, our technique is unique in it is performed early in the KDD process and on un-propositional data, while feature selection is performed during the data mining stage. One example of FSbP exists in literature [6], where a wrapper method was used to select features, but the process was dependent on the availability of the entity relationship model (ERM) for the database that contained the features so automated data compilation could be performed for training purposes. Our form of FSbP performs without the full ERM knowledge, which is required because many of the features are in groups of irregular time series.

## 3 Literature Review

Machine learning algorithms rely on data to train models that can predict outcomes. However, not all data is equally relevant to the target objective. The inclusion of irrelevant or redundant features can negatively impact a model’s accuracy, training time, ability to generalize, and model running time. A feature selection process is used to remove such features from the dataset before the training begins or as part of the training process [1].

### 3.1 Categories of Feature Selection Strategies

Feature selection strategies are chosen based on assumed relationship or nature of the features. Well-established feature selection techniques assume a “flat feature” where features are assumed to be unrelated to one another. Other techniques account for inter-feature relationships, assuming either streaming or structured features [4]. 

In this chapter, we will briefly explain flat and structured features as they are relevant to guiding our strategies and their limitations.

Flat features are features that are assumed to be independent. Feature selection processes for features are grouped into three categories, which are filter methods, wrapper methods, and embedded methods.

Filter methods ranks and evaluates features based on a certain criterion. Examples of scores used for filter methods include the Filter Score, which evaluates a feature based on its variance with respect to class values, based on information gain and mutual information and information gain, and Relief and ReliefF, which uses calculated distances of nearest features (feature-wise) of instances between identical and different classes.

Filter-methods are simple to execute but does not guarantee an optimal feature set-FS.

The second category, wrapper methods, iterates through possible subsets of features from the initial training set and measures their suitability by measuring the performance of training models created from the feature sets, selecting the best feature set to be used for the final training.
