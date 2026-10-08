proportional format [1]. In propositional format, data is stored in the form of an attribute-value representation in a single table [2].

The process of propositionalization is used to transform relational data into propositionalized data and may include steps as the joining of tables via their relationship and aggregation or other preprocessing techniques.

When performing KDD on previously collected oil drilling data [3], this transformation process is not feasible if performed on the entire sets of data, which is multi-sourced (requiring harmonization), and sparse [4] (each source containing about 700 tables and 20,000 columns/features), and sparse [5]. Because that the transformation of each feature requires prior knowledge of its business rules.

The above process becomes difficult when the database model is not available to determine relationships between tables and sparse data interferes with the table joining process and priors are either not available to the data scientist or sources of priors either conflict with one another or with the data.

A method is required to determine which data are most relevant to the learning objective before propositionalization that is not reliant on the availability of priors.

This chapter is broken down into seven sections. In the Introduction, we have introduced the motivation for FSbP. In the Introducing FSbP, we describe FSbP and Comparing it to KDD and regular feature selection environments. In the Literature Review section we discuss relation regarding feature selection techniques that may be relevant to the implementation and measuring the efficacy of FSbP. In the Methodology section, we discuss implementations of FSbP as used in the context of KDD for oil drilling. In the Results section, we show our results in the form of percentage of features selected and model performance. In the Discussion section, we discuss initial findings from the execution of FSbP, and we conclude with the Conclusion section.

#  Introducing FSbP

A method is required to determine which data are most relevant to the learning objective before propositionalization that is not reliant on the availability of priors. To address this, we introduce a novel concept called feature selection before propositionalization (FSbP). FSbP is performed on propositionalized data, which is relational data that has not yet joined and compiled. This technique is different from any forms of feature selection (Table 1) because it allows for the selection of relevant features early in the KDD process, before the data has been fully processed and compiled.

FSbP is performed during the “selection” process of KDD, which is different from the “filtering” stage of machine learning. The objective of FSbP is to select the most relevant features to create a training set with minimal observation and exploration of the data. This technique is particularly useful for the KDD of high-dimensional datasets.