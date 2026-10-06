# CHAPTER 1. INTRODUCTION

+   **Data exploration.** This step aims to familiarize yourself and understand the data so you can make informed decisions during the following steps. Some of the tasks involved in this phase include summarizing your data, generating plots, validating assumptions, and so on. During this phase you can, for example, identify outliers, missing values, or noisy data points that can be cleaned in the next phase. Chapter 4 will introduce some data exploration techniques. Throughout the book, we will also use some other data exploratory methods but if you are interested in dipping deeper into this topic, I recommend you to check out the “Exploratory Data Analysis with R” book by Peng (2016).

+   **Data cleaning.** After the data exploration phase here, we can remove the outliers, remove noisy data points, remove variables that are not needed for further computation, and so on.

+   **Preprocessing.** Predictive models expect the data to be in some structured format and satisfying some constraints. For example, several models are sensitive to class imbalances, i.e., the presence of many instances with a given class but a small number of instances with other classes. In fraud detection, most of the instances will belong to the normal class but just a small proportion will be of type ‘illegal transaction’. In this case, we may to do some preprocessing to balance the dataset. Some models are also sensitive to feature differences. For example, a variable *weight* would be in kilograms but another variable *height* in centimeters. By training a predictive model, the data needs to be prepared in such a way that the models can get the most out of it. Chapter 5 will present some common preprocessing steps.

+   **Training and evaluation.** Once the data is preprocessed, we can then proceed to train the models. Furthermore, we also needs to evaluate their generalization performance on unseen instances. The purpose of this phase is to try, and fine-tune models to find the one that performs the best. Later in this chapter, some model evaluation techniques will be introduced.

+   **Interpretation and presentation of results.** The purpose of this phase is to analyze and interpret the models’ results. We can use performance metrics derived from the evaluation phase to make informed decisions. We also want to understand how the models work internally and how the predictions are derived.

# 1.5 Evaluating Predictive Models

Before showing how to train a machine learning model, in this section, I would like to introduce the process of **evaluating** a predictive model, which is part of the data analysis