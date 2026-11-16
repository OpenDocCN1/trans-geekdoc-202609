

**TIP** Be sure to clean up data by handling missing values using imputation techniques like mean or median values, regression, or MICE, and take care of outliers using normalization techniques like min-max scaling or standardization.

## Data Partitioning

It is important to split data into training, validate, and test datasets so that the models do not overfit, and you can evaluate the models accurately. You need to ensure that there is no leakage of test datasets into training datasets. One way to achieve this is to remove duplicates before splitting.

## Data Scaling (Normalize, Standardize)

Consider the example of predicting the sales of various products in the store. Say you have collected a dataset with the following features:

- Average customer footfall per day, ranging from 100 to 400
- Average income level, ranging from $50,000 to $200,000
- Average price of the product, ranging from $1 to $100

### Normalization

To calculate the normalized value, you take each value, subtract the minimum value from it, and then divide it by the range. So, for a footfall value of 200, your normalized value is (200–100)/300 = 0.33.

You do the same for the income level and the price. By normalizing all the values, the vast difference in the absolute values is minimized, and therefore your algorithm will give equal weightage to all these features.

| FEATURE | ORIGINAL RANGE | NORMALIZATION METHOD | NORMALIZED EXAMPLE |
|---|---|---|---|
| Average customer footfall/day | 100–400 | (value-min)/range | For a customer footfall value of 200, normalized value is (200–100)/300 = 0.33. |
| Average income level ($K) | 50–200 | (value-min)/range | For an income of 100, normalized value is (100–50)/150 = 0.33. |
| Average price of product ($) | 1–100 | (value-min)/range | For a product price of 50, normalized value is (50–1)/99 = 0.49. |

### Standardization

If you didn't scale these values, income levels would have an unfair advantage in influencing the predictions, making your results inaccurate. Note that standardization is preferred for handling outliers, as it's less sensitive to them.

## Unbias and Balance (Detection and Mitigation)

This section discusses detecting and mitigating bias in data. Say you are trying to predict your customers' spending habits and using features such as age, income, purchasing habits, and location. When you train the model and discover that it has different accuracies for different age groups, that is an example of bias. For example, this might happen if most of your data belongs to middle-income, middle-aged customers, so your model may be very good at predicting those segments. However, it might not be suitable for lower-income, younger groups, or high-income, older groups.

Sometimes the bias can come from the algorithm itself. For example, if it has the predisposition to predict favorably for larger group segments, and if you're running a discount program using this model, it might give more discounts to the middle-aged, middle-income groups.

You can mitigate bias by adopting data level, algorithm level, post-deployment level including continuous monitoring techniques, as shown in the following table:

| BIAS MITIGATION TECHNIQUES | DESCRIPTION | EXAMPLE |
|---|---|---|
| Data level | You can build a balanced dataset by undersampling the overrepresented groups and oversampling the underrepresented groups. | You could attempt to balance your dataset by including more data from lower-income, younger groups, or high-income, older groups. |
| Algorithm level | 1. Try different algorithms.<br>2. Change the parameters of the chosen algorithm.<br>3. Use an ensemble method that combines the predictions of multiple models. | You can test different algorithms or adjust the parameters of your chosen algorithm to see if they perform better for underrepresented groups. You could also use ensemble methods to combine the predictions of several models. |
| Post-processing level | 1. Conduct a fairness audit of the model.<br>2. Do a fairness correction to adjust the model's output until the bias is reduced. | First you must check if the model is predicting accurately across multiple groups. Then, you can experiment by adjusting the model's output to reduce any identified bias. |
| Continuous monitoring | 1. Monitor the model's performance across all groups.<br>2. Make corrections to the model as needed. | To begin with, regularly monitor the model's performance across all customer groups and adjust as necessary. This can help ensure that the model continues to make accurate predictions for all customer groups. |

**NOTE** You can detect and mitigate bias in machine learning models by using tools like SageMaker Clarify, AWS Machine Learning Interpretability Toolkit, Azure Fairlearn, and GCP Explainable AI.

Using SageMaker Clarify, you can monitor for bias at the data preparation stage before the training starts and during each stage of the ML lifecycle. This can also detect bias after deployment and provides detailed reports that quantify different types of bias and provide feature importance scores to explain how the model made its predictions. It explains the data, model, and monitoring used to assess predictions.

Azure provides the Azure Machine Learning Interpretability Toolkit and Azure Fairlearn, and Google provides GCP Explainable AI to detect and mitigate bias and provide explanations for predictions.

## Data Augmentation

Another technique you can use is data augmentation. This involves creating new data from existing data. It is often used in deep learning. See the following table for more details:

| STEPS | TECHNIQUES AND METHODS | RETAIL CASE STUDY EXAMPLE |
|---|---|---|
| Creation of new data | This involves creating new data from the existing data. | In a retail setting, you could create synthetic new customer reviews to augment your existing dataset. |
| Adding noise to data | Adding noise to data can help improve the robustness of the model. | You could add noise to the sales data. This could allow your model to handle a broader range of data and possibly improve its performance. |

## Handling Inconsistent Formats

In the case of inconsistent formats, you can use either text processing or parsing techniques. For example, you can rectify the incorrect date formats using dateUtil libraries or regular expressions.

## FEATURE ENGINEERING

Each unique attribute of data is a feature. Feature engineering is about selecting the right attributes for the model to become more accurate and generalizable for new data. You choose different features based on the type of model.

Feature engineering consists of the components shown in Figure 15.7.

- Feature selection
- Feature transformation
- Feature creation (encoding, binning)
- Feature extraction (automated through deep learning)

**FIGURE 15.7:** Feature engineering components

### Feature Types

This section explains the various feature types that you can create for your models. The following table lists these feature types, their suitable models, and some examples:

| FEATURE DESCRIPTION TYPES | USEFUL MODELS | CASE STUDY EXAMPLE |
|---|---|---|
| Time-series features Time-series features capture temporal information such as day of the week, month, holiday season, or if it's a weekend. | ARIMA, Prophet | The fluctuating sales throughout the week or the sales promotions during the holiday season. |
| Ratio-based features Ratio-based features represent relationships between different numerical variables. For instance, the relationship between the current price and the average price. | Decision trees (XGBoost and random forests), regression models | Comparison of the price of an item among its competitors. |
| Categorical features | Categorical features represent categories or discrete values such as the type of promotion. | Classification models such as logistic regression, support vector machines | Promotion type can be a key feature, for instance, “Buy one get one” versus “20% off.” |
| Binary features | Binary features take on two possible values like yes/no or 1/0. | Various models | Whether or not a sales promotion was running. |
| Sentiment scores or topic features | These features are derived from text data like customer reviews. Sentiment scores or topics extracted using NLP techniques. | Deep learning models such as RNNs, transformers | Sentiment scores or topics obtained from the analysis of customer reviews. |
| Interaction features | Interaction features represent dependencies between other features, such as the interaction between price and promotions. | Useful for any model that might miss these relationships | For instance, a feature representing the effect of a promotion on a high-priced item. |

**TIP** Use domain knowledge to create features that are relevant to the problem you are trying to solve.

### Feature Selection

Feature selection is the process of selecting the attributes that are more relevant to predicting the results. Consider the use case of predicting a customer's spending habits. Assume the dataset contains features such as the customer's age, income, location, purchase habits, number of children, job title, education level, and frequency of store visits.

When selecting the features to predict the customer's spending habits, you have to decide which feature is going to be more relevant to predict this spending habit, and you have to decide which one is irrelevant, a duplicate, or even counterproductive.

### Feature Importance Scores

