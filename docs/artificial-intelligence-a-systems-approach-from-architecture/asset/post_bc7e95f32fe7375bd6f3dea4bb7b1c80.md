
## Chapter 3: Data Conditioning

(e.g., Snowflake and Databricks). At present, both Snowflake and Databricks are dominant in their specialties, with a market capitalization of tens of billions of dollars, which gives an indication of how significant data management and storage are to modern data processing and AI.

Databricks uses something that it calls the "datahouse," a platform meant to combine the best of data warehouses and data lakes [23]. Data warehouses primarily store data in structured format, where data lakes predominantly store data in unstructured format [24–26].

There is an ongoing trend to use AI in business intelligence, as well as integrating structured, sem, and unstructured data into the decision support workflow for a modern AI organization. This trend is very healthy for the AI community to looking at databases and data types as uniquely distinct environments. The digital transformation platform, discussed earlier, should incorporate these databases and data types into an integrated data environment.

An organization that has implemented a digital transformation, owning a modern platform infrastructure, can create value by either performing the process of Extract-Transform-Load (ETL) or Extract-Load-Transform (ELT), across data environments (e.g., data warehouses, data lakes, or data houses). In the data-conditioning stage, ETL is employed in the data manipulation flow using the data and database-management tools described earlier. ELT, in addition to reversing the operation of load and transform, is becoming the accepted data manipulation flow for a large volume of unstructured data, with data processing occurring close to where the data is stored (minimizing latency). An excellent resource to stay abreast of changes in the data and AI ecosystem is by Matt Turk (a venture capitalist at FirstMark), who regularly writes a comprehensive post with relevant updates [28].

So far, we have articulated the need for an AI organization to undergo a digital transformation in order to achieve a modern platform infrastructure. This platform utilizes the best of database management tools and techniques necessary to implement the data-conditioning stage. The next steps, after these foundational pieces are in place, are to perform data quality assessment, cleaning, and preparation prior to the ML stage. The next section elaborates on these data-processing functions in more detail.

## 3.4 Data Quality, Cleaning, and Preparation

The third-tier component of our earlier discussion of the transitioning and scaling of AI products and services is to focus on data-centric AI instead of putting the majority of the emphasis on model-centric AI. "Data-centric AI" simply refers to between the data-conditioning stage and the ML stage shown in figure 2.2, where the emphasis is on enhancing data (through data engineering) to achieve better performance from the ML algorithms [29]. Model-centric AI, in contrast to data-centric AI, focuses on improving the ML algorithms while doing minor tweaks to the initial data used in training/cross-validation and testing.

Effective implementation of data-centric AI relies on careful attention to the data-conditioning stage. There are many references in the literature that present an in-depth discussion on data conditioning [16, 30–33]. For our purposes, in this chapter we highlight some of the important data-conditioning exploration details and issues that the data scientists and data engineers must address.

Table 3.4 breaks the data conditioning exploration into the following categories:

- Data quality: Initial analysis of the available data.
- Data cleaning: Addressing corrections to the existing data, and determining if additional data collection is needed.
- Data preparation: Organizing the data prior to the ML stage.

These categories must be undertaken to convert raw data into useful information, leading to effective extraction of knowledge from the ML stage. It is also important to emphasize that this exploration is done iteratively with the ML step. The iterative process requires that the performance of the ML algorithm be evaluated through a set of performance metrics such as accuracy, confusion matrix, area under the curve (AUC), as discussed in more detail in chapter 4.

AI leaders and practitioners must have capable data scientists and data engineers on their AI teams. It is one of the most critical roles for the successful development and deployment of AI capabilities [34]. Data scientists are typically responsible for analyzing the data, performing the data functions enumerated in table 3.4. Data engineers complement the data scientists, and they are pivotal members of the team, with the responsibility for acquiring and maintaining robust and scalable data management tools. They must also play the stewardship roles for evolving the platform infrastructure discussed in sections 3.2 and 3.3.

The role of data scientists and data engineers is to do an initial data quality exploration. After understanding the stakeholders' business needs, the questions posed in table 3.1 must be answered. From these answers, one can perform a data quality assessment to determine if there is missing or incomplete data. For example, the output of ML could be either classification, predictions, or clustering estimates. Input data must be sufficiently heterogeneous to span the ML output. For example, to overcome this limitation, more data might need to be collected.

### Table 3.4 Data exploration and issues

| Data Exploration | Issues |
| :--- | :--- |
| Data quality | Missing or incomplete data<br> Outlier detection<br> Duplication<br> Bias versus trade-off |
| Data cleaning | Imputation<br> Rescaling<br> Pruning<br> Feature selection |
| Data preparation | Curse of dimensionality<br> Dimensionality reduction<br> Data augmentation<br> Data labeling<br> Data drift |

Data might also contain outliers, which can result in the poor performance of an ML model (e.g., underfitting). Data duplication must also be eliminated from the available data, as it can lead to data bias, discussed next.

There is a trade-off between the ML output and the expected output. High bias results in a model that underfits the training data. A solution is to try a different model or a more complex model (i.e., additional hyperparameters). Data variance is an error resulting from a high degree of sensitivity to small changes or fluctuations in the training data. High variance creates overfitting to the training data (e.g., when there are too many features but not training samples or the model is too complex). Employing a regularization term in the model's objective function can lead to higher bias but potentially lower variance, as well as a simpler model. We should also point out that model bias in this context is different than data bias, discussed in chapter 8 in the context of responsible AI (RAI), such as gender, age, and ethnic/race biases.

Once an initial exploration is performed, under a data quality assessment, the data cleaning involves multiple efforts such as the following:

- Imputation: Include representative values in the data set relative to the desired features of interest. This could be done through simulation or emulation using high-fidelity representations of the real-world environment.
- Rescaling: Avoid large dynamic range in the absolute data values. This can be addressed by normalizing the value range.
- Pruning: Excise training samples that are outliers or noisy from the data set. Data pruning helps in improving generalization and the resulting accuracy [35, 36]. There are also data-pruning techniques that focus on achieving acceptable performance with smaller data sets, while also reducing computation cost [37].
- Feature Selection: Remove irrelevant or redundant features that would cause overfitting, increase computational complexity, or both [38]. This step also helps with reducing the curse of dimensionality (as noted above).

Data quality assessment and data cleaning permit data scientists and engineers to move to the next step of data preparation. During preparation, it is conditioned to be well matched to the ML stage. For example, one must avoid the effect known as the "curse of dimensionality," which occurs when additional features are incorporated into the model but there is not enough data to support the desired output from the model. Let us look at a case as an example. In the application of real estate value prediction, if we add more representative features (e.g., bedrooms or square footage), we must also increase the number of available training samples to span the additional features. If we do not do so, the high-dimensional increase causes no samples to occupy that high-dimensional space. One approach to avoid this effect is employing dimensionality reduction, as principal component analysis (PCA).

Data augmentation is most used when there is underfitting in the model to perform a function such as computer vision. The training can be augmented by rotating the input image. These image rotations can be random transformations without actually changing the class object of interest (i.e., the target image).

Another important step in data conditioning is to label the data prior to employing a supervised learning algorithm. There are data sets that are already labeled, often used by algorithm developers and researchers, as discussed in the next section.

Finally, data conditioning is not an end state. Not only does it need to be done in an iterative phase with the ML stage, but it is imperative that during deployment, the AI system must be checked for data drift. Data drift means that the original ML model no longer matches well to the new real-world scenario and incoming data. This effect is uncommon as AI is applied to rapidly changing applications. The monitoring stage, shown in figure 2,2 in chapter 2, might cause us to return to the data-conditioning stage to collect or perform additional data quality assessment, data cleaning, or data preparation.
