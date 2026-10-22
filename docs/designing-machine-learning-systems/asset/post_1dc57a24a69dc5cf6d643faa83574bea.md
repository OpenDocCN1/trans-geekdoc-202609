
P(Y|X) denotes the conditional probability of an output given an input—for example, the probability of an email being spam given the content of the email. P(X) denotes the probability density of the input. P(Y) denotes the probability density of the output. Label shift, covariate shift, and concept drift are defined as follows:

## Covariate shift

When P(X) changes but P(Y|X) remains the same. This refers to the first decomposition of the joint distribution.

## Label shift

When P(Y) changes but P(X|Y) remains the same. This refers to the second decomposition of the joint distribution.

## Concept drift

When P(Y|X) changes but P(X) remains the same. This refers to the first decomposition of the joint distribution.21

If you find this confusing, don’t panic. We’ll go over examples in the following section to illustrate their differences.

## Covariate shift

Covariate shift is one of the most widely studied forms of data distribution shift.22 In statistics, a covariate is an independent variable that can influence the outcome of a given statistical trial but which is not of direct interest. Consider that you are running an experiment to determine how locations affect the housing prices. The housing price variable is your direct interest, but you know the square footage affects the price, so the square footage is a covariate. In supervised ML, the label is the variable of direct interest, and the input features are covariate variables.

Mathematically, covariate shift is when P(X) changes, but P(Y|X) remains the same, which means that the distribution of the input changes, but the conditional probability of an output given an input remains the same.

To make this concrete, consider the task of detecting breast cancer. You know that the risk of breast cancer is higher for women over the age of 40,23 so you have a variable “age” as your input. You might have more women over the age of 40 in your training data than in your inference data, so the input distributions differ for your training and inference data. However, for an example with a given age, such as above 40, the

21 You might wonder what about the case when P(X|Y) changes but P(Y) remains the same, as in the second decomposition. I’ve never encountered any research in this setting. I asked a couple of researchers who specialize in data shifts about it, and they also told me that setting would be too difficult to study.

22 Wouter M. Kouw and Marco Loog, “An Introduction to Domain Adaptation and Transfer Learning,” arXiv, December 31, 2018, https://oreil.ly/VKSVP.

23 “Breast Cancer Risk in American Women,” National Cancer Institute, https://oreil.ly/BFP3U.

## Concept drift

Concept drift, also known as posterior shift, is when the input distribution remains the same but the conditional distribution of the output given an input changes. You can think of this as “same input, different output.” Consider you’re in charge of a model that predicts the price of a house based on its features. Before COVID-19, a three-bedroom apartment in San Francisco could cost $2,000,000. However, at the beginning of COVID-19, many people left San Francisco, so the same apartment would cost only $1,500,000. So even though the distribution of house features remains the same, the conditional distribution of the price of a house given its features has changed.

In many cases, concept drifts are cyclic or seasonal. For example, rideshare prices will fluctuate on weekdays versus weekends, and flight ticket prices rise during holiday seasons. Companies might have different models to deal with cyclic and seasonal drifts. For example, they might have one model to predict rideshare prices on weekdays and another model for weekends.

## General Data Distribution Shifts

There are other types of changes in the real world that, even though not well studied in research, can still degrade your models’ performance.

One is feature change, such as when new features are added, older features are removed, or the set of all possible values of a feature changes.28 For example, your model was using years for the “age” feature, but now it uses months, so the range of this feature’s values has drifted. One time, our team realized that our model’s performance plummeted because a bug in our pipeline caused a feature to become NaNs (short for “not a number”).

Label schema change is when the set of possible values for Y change. With label shift, P(Y) changes but P(X|Y) remains the same. With label schema change, both P(Y) and P(X|Y) change. A schema describes the structure of the data, so the label schema of a task describes the structure of the labels of that task. For example, a dictionary that maps from a class to an integer value, such as {“POSITIVE”: 0, “NEGATIVE”: 1}, is a schema.

28 You can think of this as the case where both P(X) and P(Y|X) change.

With regression tasks, label schema change could happen because of changes in the possible range of label values. Imagine you’re building a model to predict someone’s credit score. Originally, you used a credit score system that ranged from 300 to 850, but you switched to a new system that ranges from 250 to 900.

With classification tasks, label schema change could happen because you have new classes. For example, suppose you are building a model to diagnose diseases and there’s a new disease to diagnose. Classes can also become outdated or more fine-grained. Imagine that you’re in charge of a sentiment analysis model for tweets that mention your brand. Originally, your model predicted only three classes: POSITIVE, NEGATIVE, and NEUTRAL. However, your marketing department realized the most damaging tweets are the angry ones, so they wanted to break the NEGATIVE class into two classes: SAD and ANGRY. Instead of having three classes, your task now has four classes. When the number of classes changes, your model’s structure might change,29 and you might need to both relabel your data and retrain your model from scratch. Label schema change is especially common with high-cardinality tasks—tasks with a high number of classes—such as product or documentation categorization.

There’s no rule that says that only one type of shift should happen at one time. A model might suffer from multiple types of drift, which makes handling them a lot more difficult.

## Detecting Data Distribution Shifts

Data distribution shifts are only a problem if they cause your model’s performance to degrade. So the first idea might be to monitor your model’s accuracy-related metrics—accuracy, F1 score, recall, AUC-ROC, etc.—in production to see whether they have changed. “Change” here usually means “decrease,” but if my model’s accuracy suddenly goes up or fluctuates significantly for no reason that I’m aware of, I’d want to investigate.

Accuracy-related metrics work by comparing the model’s predictions to ground truth labels.30 During model development, you have access to labels, but in production, you don’t always have access to labels, and even if you do, labels will be delayed, as discussed in the section “Natural Labels” on page 91. Having access to labels within a reasonable time window will vastly help with giving you visibility into your model’s performance.

29 If you use a neural network using softmax as your last layer for your classification task, the dimension of this softmax layer is [number_of_hidden_units × number_of_classes]. When the number of classes changes, the number of parameters in your softmax layer changes.

30 You don’t need ground truth labels if you use an unsupervised learning method, but the vast majority of applications today are supervised.

| Detector | Tabular | Image | Time Series | Text | Categorical Features | Online | Feature Level |
|---|---|---|---|---|---|---|---|
| Kolmogorov-Smirnov | ✓ | ✓ |  | ✓ | ✓ |  | ✓ |
| Cramér-von Mises | ✓ | ✓ |  |  |  | ✓ | ✓ |
| Fisher's Exact Test | ✓ |  |  |  | ✓ | ✓ | ✓ |
| Maximum Mean Discrepancy (MMD) | ✓ | ✓ |  | ✓ | ✓ | ✓ |  |
| Learned Kernel MMD | ✓ | ✓ |  | ✓ | ✓ |  |  |
| Context-aware MMD | ✓ | ✓ | ✓ | ✓ | ✓ |  |  |
| Least-Squares Density Difference | ✓ | ✓ |  | ✓ | ✓ | ✓ |  |
| Chi-Squared | ✓ |  |  |  | ✓ |  | ✓ |
| Mixed-type tabular data | ✓ |  |  |  | ✓ |  | ✓ |
| Classifier | ✓ | ✓ | ✓ | ✓ | ✓ |  |  |
| Spot-the-diff | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| Classifier Uncertainty | ✓ | ✓ | ✓ | ✓ | ✓ |  |  |
| Regressor Uncertainty | ✓ | ✓ | ✓ | ✓ | ✓ |  |  |

Figure 8-2. Some drift detection algorithms implemented by Alibi Detect. Source: Screenshot of the project's GitHub repository

## Time scale windows for detecting shifts

Not all types of shifts are equal—some are harder to detect than others. For example, shifts happen at different rates, and abrupt changes are easier to detect than slow, gradual changes.37 Shifts can also happen across two dimensions: spatial or temporal. Spatial shifts are shifts that happen across access points, such as your application gets a new group of users or your application is now served on a different type of device. Temporal shifts are shifts that happen over time. To detect temporal shifts, a common approach is to treat input data to ML applications as time-series data.38

37 Manuel Baena-García, José del Campo-Ávila, Raúl Fidalgo, Albert Bifet, Ricard Gavaldà, and Rafael Morales-Bueno, “Early Drift Detection Method,” 2006, https://oreil.ly/Dnv0s.

38 Nandini Ramanan, Rasool Tahmasbi, Marjorie Sayer, Deokwoo Jung, Shalini Hemachandran, and Claudionor Nunes Coelho Jr., “Real-time Drift Detection on Time-series Data,” arXiv, October 12, 2021, https://oreil.ly/xmdqW.
