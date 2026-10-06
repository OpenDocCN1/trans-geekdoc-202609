
# Examples of Feature Engineering in the Real World

It's generally accepted that feature engineering is part of the data preparation necessary before machine learning, but there have been some researchers who have demonstrated this in a couple of different domains by comparing machine learning done with and without good feature engineering. In both cases, it's clear that doing good feature engineering improved the models.

# Example 1: Expert Feature Engineering

A research group studied the effect of including data scientists during feature engineering in addition to domain experts in two medical outcome forecasting applications.¹ The first predicted falls and fractures in patients. The second predicted bone side effects from antiepileptic drugs. They had forecasting models for and compared performance with feature sets that were selected simply by domain experts (the standard) and ones that involved a data scientist working with domain experts to bring in more sophisticated features. They did all the standard machine learning tasks that are appropriate, including data prep, feature engineering, feature selection, and balancing the dataset. The study ran the feature engineering and selection two different ways, with and without the data scientists. And what they clearly found was that the performance was okay with only domain experts, bringing in a data science expert improved the performance dramatically. 

> ¹Case study—Feature engineering inspired by domain experts on real world medical data” by Olof Björnlund, Martin Carlsson, and Welf Löwe in Intelligence-Based Medicine, Volume 8, 2023 available at https://www.sciencedirect.com/science/article/pii/S2666521223000248

CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

We'll talk about performance measurement in a later chapter, but in the first project, adding a data scientist took the accuracy from 61% to 82% and, the second, from 80% to 91%.

# Example 2: Detecting Radiation More Effectively

Some other researchers did a similar study that showed that among many techniques that can be used to achieve more accurate machine learning results, quality feature engineering can bring the most improvement.² They also found that feature engineering could also lead to better explainability in the model itself. They were working with radiation detection in three conditions: with obstructions, with background, and with neither obstruction nor background. Their model predicted the angle for the direction the source radiation was located. They used a random forest model and also did the normal data prep and machine learning training like the researchers in the previous example. They ultimately found that feature engineering improved the results in all three conditions by a large factor.

# Feature Engineering Techniques

After you've worked through your data preprocessing as discussed in the last chapter, you're now ready to do the even more important work of fine-tuning and improving your features. There are many techniques that you may do at this point, but the first focus area is working with individual features, transforming existing ones and making interaction or other features.

> ²Feature Engineering: A Case Study For Radiation Source Localization In Complicated Environments” by Matthew Durbin, Ryan Matthew Sheatsley, Patrick McDaniel, and Azaree Linteer, 2021, available at https://resources.immm.org/annual-meeting-proceedings/feature-engineering-case-study-radiation-source-localization-complicated

You will often find that many of your features are perfectly solid on their own, without much modification (beyond cleanup and preprocessing). There's nothing wrong with using features as is, and you don't need to get carried away doing fancy feature engineering just because you think you're supposed to. But sometimes it can make a huge difference.

During your preprocessing work, you will have gotten to know your data. If you have a smallish number of features, maybe 50 or fewer, you've probably learned a bit about many, or all, of the features. You may already have a sense for ones that are strong, ones that need to be investigated a bit, ones that seem unnecessary or redundant, and ones that likely shouldn't be included. In this case it can be easy to know where to get started with your feature engineering. But if you have a lot of features or if they are not very intuitive to work with, you may not have a great sense for the quality of your individual features.

In either case, you can do some more work to know what steps to take next. Some of the techniques that are discussed in the “Feature Selection” section further down can be useful to help get started with features. But in addition to knowing your particular dataset, feature engineering is always hugely informed by domain knowledge. Knowing what types of transformations to make or how to combine features is much easier when you know the domain.

Just keep in mind that the whole reason for doing feature engineering is to find the most meaningful ways to represent whatever you're modeling or investigating, whether it's pizza restaurant sales or patient diagnoses, because that's the information that will be most valuable in a machine learning model.

Note that usually when you create a feature based on another feature (or features) (in some way), the original features are usually excluded.

CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

# Transformed Features

There are a lot of different ways you can transform your existing features to create new features. These are usually done considering an individual value, but some involve using info from the entire column. Many involve mathematical operations or statistical techniques.

A common one is the polynomial feature that's created by raising one feature to a power of two. A statistical one could involve a quantile, which would involve looking at the entire column. But there are many other possibilities. It's common in retail to track things. Imagine a pizza restaurant that wants to understand overall sales. Because pizzas come in different sizes, there's no clear way to combine units without losing information. But they could create a variable square inches sold instead, and then those values could be summed. See Table 14-1 for what this might like.

# Table 14-1. A new feature for a pizza restaurant, Sq. Inches Sold

| Order # | Size | Quantity Sold | Sales | Sq. Inches Sold |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Personal | 1 | 12.50 | 45 |
| 2 | Large | 1 | 21.00 | 154 |
| 3 | Medium | 2 | 34.00 | 226 |
| 4 | Large | 1 | 25.00 | 154 |
| 5 | Personal | 3 | 37.50 | 135 |
| 6 | Large | 2 | 47.50 | 308 |

CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

Often when you create a transformed feature, you wouldn’t use the other features, specifically in the same model. This is because sometimes it leads to including the same information more than once, which can skew results. (This is basically the collinearity that I’ll address later.) Because the new pizza feature (Sq. Inches Sold) combines Quantity Sold and Size (via a specific multiplier), we wouldn’t want all three in the same model. We could look at including either Quantity Sold and Size or Sq. Inches Sold.

# Interaction Features

Interaction features are new features you create from at least two other features based on some kind of mathematical operation, frequently multiplication or addition, but others are possible. These are usually done across a row alone. You don’t multiply a couple features for the heck of it—interaction features are intended to capture the relationship between different features and how that relationship specifically might affect the target variable. If you have several related features, it might make sense to take the min, max, or average among them as a starting point for an interaction calculation, rather than including them all.

An example of an interaction feature that a pizza restaurant might use based on the new feature we added above, the square inches sold, is the total sales per square inch. See Table 14-2 for that calculation.
