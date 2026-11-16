

### 9.4.12 H2O Sparkling Water

For the purpose of enabling distributed machine learning on huge datasets, H2O Sparkling Water combines the capabilities of H2O.ai's AutoML with Apache Spark. It provides the ability to increase efficiency and improve performance. Its significant traits are the following:

- Integration with Apache Spark
- Scalable AutoML
- Distributed machine learning

### 9.4.13 Turi Create

A user-friendly AutoML platform for constructing machine learning models, Turi Create is presently a component of Apple's Core ML. It is especially well-suited for the building of applications on macOS and iOS platforms. Key Features:

- macOS and iOS compatibility
- Simplified model creation
- Core ML integration

### 9.4.14 Big ML

BigML delivers an AutoML platform that prioritizes user friendliness and the ability to interpret models. The method incorporates automated identification of models and optimization of hyperparameters. Major Features:

- User-friendly interface
- Model interpretability tools
- Automation of machine learning tasks

### 9.4.15 Hail

Hail is a freely available AutoML package specifically developed for the purpose of analyzing genetic data. The platform offers a range of technologies that facilitate distributed and scalable machine learning on genomic datasets. Its particularly striking characteristics are as follows:

- Genomic data analysis
- Scalable and distributed processing
- Integration with Apache Spark

## 9.5 Open-Source AutoML Libraries

### 9.5.1 Auto-Sklearn

Auto-sklearn improves on the idea of establishing an all-encompassing machine learning framework with appropriate global optimization, which was initially introduced with Auto-WEKA. Auto-sklearn enhances generalization by constructing an ensemble of all models that had been assessed all throughout the global optimization approach. It is an Automated Machine Learning toolkit built on scikit-learn.

![](img/5510bd7390ed7002b5774fe8c2be9eff_211_0.png)

Figure 9.4 Representation of AutoML pipeline.

![](img/5510bd7390ed7002b5774fe8c2be9eff_211_1.png)

Figure 9.5 Representation of automated TPOT.

### 9.5.2 TPOT (Tree-Based Pipeline Optimization Tool)

This tool known as TPOT is designed to optimize machine learning pipelines through the utilization of genetic programming concepts. By proactively exploring millions of potential pipelines, it will automate the most tedious aspect of machine learning and determine the most appropriate one for your data. It is adapted from IPython and is an Automated Machine Learning library using genetic programming.

### 9.5.3 AutoKeras

For Automated Machine Learning, AutoKeras is a software library that is available under an open-source license. AutoKeras offers a range of functions that facilitate the automated exploration of architectural and hyperparameter requirements for deep learning models. It can be installed via pip and deployed as an AutoML library for automated neural architecture search using Keras.

### 9.5.4 MLBox

MLBox is a robust Python module that supports Automated Machine Learning. The software offers the subsequent functionalities: rapid reading and preprocessing, cleansing, and formatting of distributed data; efficient and resilient selection of features and leak detection techniques; efficient optimization of hyperparameters in a high-dimensional space; and automated machine learning library for feature engineering, model selection, and hyperparameter tuning.

### 9.5.5 AutoGluon

An easy-to-use and extensible AutoML is made possible by AutoGluon, which focuses on deep learning, automated stack ensembling, and practical requests for text, image, and tabular data. It is an AutoML library developed by Amazon AWS for model selection, hyperparameter tuning, and ensemble learning.

### 9.5.6 H2O AutoML

H2O is a distributed in-memory ML platform that can scale linearly and is completely open source. H2O supports a variety of statistical and machine learning algorithms that are widely utilized in various fields. These algorithms include gradient boosted machines, deep learning, and others.

### 9.5.7 Auto-WEKA

Unlike other methods that address problems one at a time, Auto-WEKA tackles the problem of choosing a learning algorithm and fixing its hyper-parameters at the same time. When it comes to data mining tasks, Weka is a set of ML algorithms. The system encompasses a range of tools that facilitate various tasks such as data preparation, classification, regression, association rules mining, and visualization.

### 9.5.8 AutoGluon Tabular

It is possible for AutoGluon to generate models that can forecast values in one column built on values in other columns for normal datasets that are stored as tables (for example, stored as a CSV file or as a parquet from a database). AutoGluon makes it possible to use AutoML in a way that is both simple and straightforward, with a particular emphasis on DL and real-world applications that involve picture, text, or tabular data. AutoGluon is intended for those with varying levels of expertise in machine learning. It allows you to efficiently create prototypes of deep learning solutions for your data using a minimal number of lines of code.

### 9.5.9 FLAML

FLAML is a Python library that assists in the automatic discovery of accurate machine learning models while minimizing the amount of computational resources required. By doing so, data scientists are relieved of the burden of worrying about hyperparameter tuning and method selection. Developers are able to construct self-tuning software that adapts to new training data. According to FLAML, the most optimal model is lightgbm. The tuned hyperparameters of this model can be determined by utilizing the following code. This is a significant benefit of FLAML. The system efficiently identifies the appropriate machine learning method and hyperparameters within a matter of seconds.

### 9.5.10 Ludwig

The kinds of input and output features are inferred by AutoML, the model architecture is selected, and a Ray Tune Async HyperBand search task is initiated across a set of hyperparameters and ranges, with the time budget being limited by the parameters that have been defined. Ludwig is a machine learning framework that is open source and declarative in nature. It facilitates the definition of deep learning pipelines through a straightforward and adaptable data-driven configuration mechanism. Ludwig demonstrates compatibility with a diverse range of artificial intelligence workloads and is hosted by the Linux Foundation AI & Data. The Uber AI Labs has developed an AutoML package for deep learning.

## 9.6 Types of AutoML Approaches

### 9.6.1 Fully Automated

In AutoML solutions that are fully automated, the complete machine learning pipeline, encompassing data pretreatment and model deployment, is executed without the need for user involvement.

### 9.6.2 Human-in-the-Loop

The concept of “Human-in-the-Loop” Automatic Machine Learning (AutoML) solutions incorporate a certain level of user engagement enabling domain experts to offer input or tailor certain elements of the machine learning procedure.

### 9.6.3 Model Assisted

The idea of model-assisted AutoML involves the incorporation of human experience with automated methodologies to advance the performance of models or tackle specific problems encountered in the machine learning pipeline.

## 9.7 Benefits of AutoML

### Accessibility

AutoML simplifies the procedure of utilizing the power of ML to solve real-world problems by automating complex machine learning activities. This makes it easier for individuals and organizations with little experience to take advantage of the machine learning.

### Innovation

AutoML enables innovation in the field of ML by automating repetitive events allowing data scientists and ML engineers to focus their efforts on more creative and advanced jobs.

## 9.8 Challenges and Limitations

Despite the many compensations it offers, AutoML is also subject to a number of problems and limitations, including the following:

### Complexity

AutoML algorithms may meet difficulties when dealing with intricate datasets or actions that require domain-specific expertise, hence, constraining their effectiveness in specific situations.

### Scalability

In context with limited resources, it can be hard to scale AutoML solutions to handle large-scale datasets or computationally composite models. Scalability is a key factor in this challenge.

### Customization

The flexibility needed to suit domain-specific requirements or extensive customization options may be lacking in certain AutoML frameworks.

### Data Quality

The performance of AutoML models is meaningfully influenced by the excellence of the input data, with errors such as missing values or outliers having a detrimental effect.

## 9.9 Conclusion

Though AutoML paves the way in democratizing the fast pace in the world of technology, it comes with equivalent tasks and limitations. The lack of transparency and customization options makes the transition from ML to AutoML tedious. The transition from ML to AutoML needs an intrinsic version to overcome the hurdles for diverse users. In addition, computational resource requirements, data quality problems, and scalability are noted areas that need focus. The various challenges associated by adopting AutoML are discussed in the paper. Further, efforts in enhancing

