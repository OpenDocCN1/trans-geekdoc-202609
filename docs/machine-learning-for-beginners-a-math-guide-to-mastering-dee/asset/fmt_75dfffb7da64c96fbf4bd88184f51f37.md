
# Introduction to Statistics

![](rsrcWS.jpg)

Statistics is the mathematical science of data. It is a practice by which data is collected, observed, and analyzed in order to infer meaning and examine quantifiable relationships between different variables. Machine learning is a form of inferential statistics, meaning that by examining the relationship between variables, we should be able to come up with predictions for new variables. Statistics is used in a wide variety of disciplines. It's used in biology to study and examines animal and plant life. It has wide applications in the business world from making stock market forecasts to analyzing consumer behavior. Economists use statistics to explain quantifiable patterns in world markets. In medicine, statistics can be used to improve the way that doctors and disease specialists look at the spread and prevention of disease. Statistics make up the core of machine learning. If you aren’t willing to dive into statistics, then machine learning isn’t for you. Machine learning uses statistical algorithms to help computers learn. Machine learning is all about the tracking of data and how computers can use data to improve themselves.

## Types of Statistical Analysis

There are two types of statistics which are relevant to this book. The first one is descriptive analysis, which you might use during the beginning of your modeling process to look for indicators in your data. But most of what we do in machine learning falls into a different category called predictive analysis.

### Descriptive Analysis

Key term; Descriptive analysis. The descriptive analysis helps us examine we are right now. Looking at our current situation in context to the past and seeing why things are the way they are. Why do some things sell better than others? What trends are we seeing in products currently on the market?

### Predictive Analysis

Key term; Predictive analysis. Predictive analysis helps us to see and understand what will happen in the future based on indicators that are currently present. When we are using machine learning for predictive analysis, it’s important for us to stay current and continue to feed the model new data. What trends should we be on the lookout for? Machine learning is just another way to understand the data that is around us and to help us understand our present and predict the future. But it requires data from the past and present so that we can find trends and see where they might lead.

## Categories of Data

Within statistics, there are two over-arching categories of data that we will use, and all our data will fall into one category or the other somehow. The first category is quantitative data. Quantitative data is data that can be measured with a numerical value. Some examples of quantitative data include height, income, or the square footage of a house. All these variables can be measured by some number, which makes them quantitative.

The second category is qualitative data. Qualitative data is data where the variables are assigned to categories or classes. Examples of qualitative data would include someone’s gender, blood type, or whether a piece of real estate has a pool or not. This data can be sorted by its identity and is non-numerical. Therefore it is qualitative.

### Quantitative Data

Quantitative data can either be discrete or continuous. If we have a data set where there is a variable recording the number of patients that a hospital had last year, this would be considered discrete. Discrete variables have a finite amount of values that they can have, and they are always whole numbers. It would be impossible to have half a patient or a percentage of a patient. Therefore this variable is discrete.

Data can also be continuous. An example of continuous data would be a variable for income. Income can take on half values, and there is a virtually infinite amount of possibilities for the value of income in data.

## Measures of Central Tendency

Some other important terms to remember are the mean, median, and mode. You will often hear these three things referred to in this book when we are talking about regressions. These are all different measures of central tendency.

The mean is our average value for data. If we have a variable for a person’s age, we will find the mean of age by adding all the ages together and then dividing by the number of respondents in a data set.

The median is the value in the middle of the dataset. If you took all the responses for age and found the response that was in the exact middle of a sorted list of responses, then this would be your median.

The mode is the response that occurs the most frequently. If we took a sample of eleven people’s ages and found that the ages were 19, 19, 20, 21, 22, 22, 22, 23, 24, 24, 25 then the mode would be 22, because it occurs the most frequently in this sample. The median would also be 22 because it happens to be in the middle of this sorted list of responses.

## Bias and Variance

When you are making a statistical model, there are many important terms that have to do with the accuracy of our models. The most important, and the most frequently mentioned in this book are bias and variance. These are different kinds of prediction errors that can occur when we are creating statistic models. Ideally, we’d like to minimize the prevalence of bias and variance in our models. They will always be present, and as a data scientist, you will have to find the right balance of bias and variance in your models, whether that’s by choosing different data or using different types of models.

There are many ways to reduce variance and bias within a model, dependent on what you are trying to do with the data. By trying to reduce these with the wrong approach, you run the risk of overfitting or underfitting your model.

When your model is bias, it means that the average difference between your predictions and the actual values is very high. Variance is how to spread out our predicted data points are. Usually, the variance is a result of overfitting to the sample data we used to create the model. It doesn't do very well at predicting the outcome of new variables.

There will always be some level of error in your models. It’s a fact of life that no matter how good you are at predicting something, there is always some random or nonrandom variation in the universe that will make your prediction slightly off from the true outcome.

I’ve created a visual example of four bullseye targets to help illustrate the difference between models suffering from high bias and variance. In this instance, the center of the bullseye represents the true value that our model is trying to predict. The top left corner is the ideal model. Notice that all our predicted data points are falling right on the bullseye. This model is quite accurate and places our predicted data points all around the true value. This is because of low variance; a lack of ‘spread out’ data points, and low bias; underfitting that skews our results.

![](rsrcWT.jpg)

In the top right target, the model is suffering from high variance. You can see that our data points are clustered around the bullseye. Unfortunately, the average distance between the predicted values and the bullseye is high due to high variance.

In the bottom left target, the model didn’t suffer much from high variance. The average distance between the predicted data points is low, but they aren’t clustered around the bullseye but slightly off it as a result of high bias. This is probably the result of too little training data, which means that the model doesn’t perform well when it gets introduced to new data.

The bottom right model suffers from both high variance and high bias. In this worst-case scenario, the model is very inaccurate because the average distance between predicted data points and the true value is high, and the predicted data points are skewed.

Variance can be caused by a significant degree of correlation between variables. If you use too many independent variables, this can also be a cause of the high variance. Sometimes, if the variance is too high, we can combat that by allowing a small amount of bias in the model. This is known as regularization. We’ll cover that a little later.

## Population and Sample

In statistics, the population is the group of people or the set of data you are trying to analyze. The sample is the subgroup of that population, whose data you use to create your model. The parameters are the characteristic of the variables of the population that you are trying to identify and make predictions from in your model.

Descriptive statistics is the use of data to examine a population. Typically, descriptive statistics involve the mean or average, mode, media, size, correlation. Machine learning falls into the category of inferential statistics because we are using the data to find patterns and relations but also to make predictions based on this information.

Inferential statistics, or descriptive stats, is using the characteristics of your population to make predictions. This is where your regression models and classification models will come in. When we infer something, we make a logical deduction about a population-based and the knowledge we are given.

## Data Distribution

When you are looking at data, you should also take note of the distribution. This is how the data is spread out on our graph. It shows the frequency of values of our data and how they appear in conjunction with one another.

We use our variance to find the standard deviation. Standard deviation is the average of the distances between the predicted data points and the real data points on a regression or prediction model.

We must also be sure to be aware of models that suffer from overfitting and underfitting. An overfitted model is good at predicting outcomes using the training data, but when you introduce new data, then it struggles. It’s like a model that memorizes instead of learns. It can happen if you don’t use random data in your training sample.

Underfitting describes a model that is too simple, and it doesn't examine any significant data patterns. It may do a good job of predicting, but the variables and parameters aren't specific enough to give us any meaningful insights if you don't have enough training data, your model could be under fitted.

## Correlation vs Causation

One of the most commonly made mistakes when people are looking at data, is confusing correlation with causation. If I told you that every person who committed a murder last year bough eggs every week, I couldn’t claim that people who buy eggs are murderers. Maybe looking at my data, I see a rise in people buying milk, as well as a rise in teen pregnancy. Would I be able to claim that there is an association between people drinking a lot of milk and teen pregnancy? Or teenagers getting pregnant caused people to buy more milk. This is the difference between correlation and causation.

Sometimes the data shows trends that seem like they are related. When two events are correlated, it means that they seem to have a relationship because they move along the graph at a similar trajectory, and during a similar space in time. Whereas causation means that the relationship between the two events involves one event causing another.

In order to imply that two things have a causal relationship, a few criteria need to be met. The first is covariation. The causal variable, and the event, it is supposed to have caused the need to be covarying, meaning that a change in one lead to a change in the other.

The second criterion that needs to be met is that the causal event needs to occur before the event it is supposed to have caused. For an event to be considered causal, it must come first.

Third, the data scientist must control for outside factors. In order to make a strong case that one thing causes another; you need to be able to present evidence that the other variables of the event are not the true cause. If the causal variable still creates the effect, even when other variables are considered, then you can claim there is a causal relationship.
