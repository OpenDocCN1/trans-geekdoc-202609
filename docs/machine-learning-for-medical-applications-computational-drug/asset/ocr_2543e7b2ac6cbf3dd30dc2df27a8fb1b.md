# 4.3.1 Causes of missing data and inconsistencies

There are many possible causes for missing data in biomedical material science data such as experimental errors, data entry errors, and the limitations of measurement instruments. This happens due to differences in procedures involved in data collection, and differences in measurements, among other factors, in datasets from different authors. Knowledge of the causes of missing data and other inconsistencies is important in choosing proper approaches to address them.

# 4.3.2 Strategies for handling missing data

Several methods are available for addressing missing data, each with its advantages and limitations:

Imputation techniques: Imputation is a process in which missing values in a dataset are estimated using statistical means. Mean imputation and median imputation are common techniques that involve replacing the missing values with average values, respectively. Some of the more sophisticated techniques include the use of methods such as multiple imputation and k-nearest neighbors (kNN) imputation, where the algorithm makes educated guesses using pattern recognition techniques to try and make a better-educated guess at the missing data.

Model-based approaches: Model-based imputation techniques, like regression imputation, create missing value expectations based on relationships established in data analysis. These techniques make use of available data to develop models for predicting gaps, and as such, imputations made using these methods are often more semantically suitable than average ones.

Data augmentation: Sometimes, bootstrapping activities can be applied in an attempt to mitigate missing data problems. This approach mainly involves the formulation of additional input feature data points whenever distribution patterns are noticed and can be utilized to improve the resiliency of the ML model.

# 4.3.3 Managing inconsistencies:

Addressing inconsistencies in biomedical material data requires a combination of techniques to standardize and harmonize the dataset:

Data cleaning: Data cleaning is the process of screening the data and removing or correcting any errors. These steps involve formatting and finalizing data in such a way as to make units of measurement consistent, making decisions that clarify differences between datasets, and fixing data entry mistakes. It is possible to use algorithms to solve some problems and organize the work of an analyst in such a way that focuses on critical cases.