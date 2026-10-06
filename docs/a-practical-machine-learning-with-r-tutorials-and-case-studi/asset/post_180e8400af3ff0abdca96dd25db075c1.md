
## 10.7 Digital Resources

Below you will find a few digital resources related to this chapter such as:

- Videos
- Short articles
- Tutorials
- R scripts

These resources are recommended if you would like to review the chapter from a different angle or to go beyond what was covered in the chapter.

Here we show only a few of the digital resources. At the end of the list you will find a link to additional digital resources for this chapter that are maintained on the Internet.

You can find a complete list of digital resources for all book chapter on the companion website: https://ai.lang-analytics.com/digitalresources.html

## 10.7.1 Decision Trees

> Decision and Classification Trees, Clearly Explained!!! from StatQuest by Josh Starmer

The video introduces the basics of Decision Trees for classification. It is a good video to start learning about Decision Trees.

![](img/f240d449191f5add983daf6c380e4fe3_311_0.png)

Link: https://ai.lang-analytics.com/dr?a=407

> Regression Trees, Clearly Explained!!! from StatQuest by Josh Starmer

The video introduces the basics of Decision Trees used for regression. We recommend watching the StatQuest video about Decision Trees for classification first.

![](img/f240d449191f5add983daf6c380e4fe3_311_1.png)

Link: https://ai.lang-analytics.com/dr?a=403

# Decision Trees in Machine Learning Using R from DataCamp by James Le and Arunn Thevapalan

This is a free tutorial from DataCamp about Decision Trees. The provided R code shows how to build a Decision Tree model using tidymodels.

![](img/f240d449191f5add983daf6c380e4fe3_312_0.png)

Link: https://ai.lage-analytics.com/dr?a=408

## More Digital Resources

Only a subset of digital resources is listed in this section. The link below points to additional, concurrently updated resources for this chapter.

![](img/f240d449191f5add983daf6c380e4fe3_312_1.png)

Link: https://ai.lage-analytics.com/dr/dectrees.html

## 10.7.2 Random Forest

# Random Forests Part 1 - Building, Using and Evaluating from StatQuest by Josh Starmer

This video is Part 1 of a video series about Random Forest. The video explains the basics of Random Forest, including an introduction to Bootstrapping.

![](img/f240d449191f5add983daf6c380e4fe3_312_2.png)

Link: https://ai.lage-analytics.com/dr?a=409

## Tuning Hyper Parameters in a Random Forest Model

This blog post by Carsten Lange shows how the hyper-parameters of a Random Forest model that estimates COVID-19 vaccination rates in 2021 can be tuned using the 10-Step Tuning template.

![](img/f240d449191f5add983daf6c380e4fe3_313_0.png)

Link: https://ai.lange-analytics.com/dr?a=353

## More Digital Resources

Only a subset of digital resources is listed in this section. The link below points to additional, concurrently updated resources for this chapter.

![](img/f240d449191f5add983daf6c380e4fe3_313_1.png)

Link: https://ai.lange-analytics.com/dr/randforest.html

## 10.7.3 Boosting Trees Algorithms

# Gradient Boosting Video from StatQuest

A video from StatQuest by Josh Starmer. The video is the first part of four videos about Gradient Boosting. This video focuses on the main ideas behind using Gradient Boosting to predict a continuous variable.

![](img/f240d449191f5add983daf6c380e4fe3_313_2.png)

Link: https://ai.lange-analytics.com/dr?a=404

# Tuning XGBoost with tidymodels

This blog post from tidyTuesday by Julia Silge describes how to use tidymodels to build and tune an XGBoost model. The goal is to predict the outcome of volleyball games. The blog post also provides a video and an R tutorial.

![](img/f240d449191f5add983daf6c380e4fe3_314_0.png)

Link: https://ai.lange-analytics.com/dr?a=406

## More Digital Resources

Only a subset of digital resources is listed in this section. The link below points to additional, concurrently updated resources for this chapter.

![](img/f240d449191f5add983daf6c380e4fe3_314_1.png)

Link: https://ai.lange-analytics.com/dr/boostrees.html

## 11 Interpreting Machine Learning Results

In the previous chapters, you learned about different machine learning algorithms and applied them to predict continuous and categorical outcomes. In this chapter, we will introduce interpretation techniques for machine learning models that we can only cover a few selected algorithms.

This chapter examines how to interpret machine learning results. Being able to interpret machine learning results is crucial for many applications. For example, if a loan is not approved, the bank must be able to explain why.

Not long ago, many machine learning models, especially Deep Learning, would be considered black box models, meaning that although they generate excellent predictions, they fail to provide insights into how they are derived. The good news is that researchers have made significant progress in recent years in machine interpretability.

There are many techniques to interpret OLS models: the coefficients show how a change of a variable will impact the prediction, p-values indicate the significance of the prediction, and the overall contribution of predictor variables is additive. You can find more about the interpretation of OLS and its limits in Wooldridge (2020).

## 11.1 Impacts of Predictor Variable Change

Question 1: If the value of a predictor variable changes, how will this impact the predicted outcome?

In Section 11.5, we analyze how the prediction for a specific observation changes when one of the predictor variables changes. We will visualize the so-called Ceteris Paribus.

As an example, think about the loan application. How would the predicted risk score change if the applicant's salary were higher or lower?

We also use Partial Dependence Plots in Section 11.5 to quantify and visualize the impact on predictions overall. Partial Dependence Plots are a summary of Ceteris Paribus Plots for all observations and thus explain the overall impact of a predictor variable.

## 11.2 Predictor Variable Importance

Question 2: Which variables are more or less important for the prediction, and which variables can potentially be dropped?

Section 11.6 focuses on tree-based models, and we quantify how important each predictor variable is for the model's outcome prediction. We produce a Variable Importance Plot (VIP) that shows a list of all predictor variables and their importance for the model.

We quantify variable importance in two ways:

- In Section 11.6.1, we use an impurity reduction measure to analyze how much each predictor variable reduces impurity when splitting observations from parent nodes to the two child nodes.
- In Section 11.6.2, we estimate Variable Importance by the damage to the model's predictive quality (increase of MSE) when the influence of a specific predictor variable is removed. The greater the damage, the higher the importance of that particular variable.
