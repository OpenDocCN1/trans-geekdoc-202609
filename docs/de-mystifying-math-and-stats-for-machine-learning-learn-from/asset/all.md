   

**Copyright © 2021 Govindakumar M All rights reserved**

The information provided in this book is for informational and educational purposes only. The author does not make any guarantee or other promise as to any results that may be obtained from using the content of this book.

No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, electronic, mechanical, photocopying, recording, or otherwise, without express written permission of the author.

# Table of Contents

[Chapter 1: Introduction](#ch003.xhtml#chapter-1-introduction)

[Chapter 2: Central Tendency vs. Dispersion](#ch004.xhtml#chapter-2-central-tendency-vs.-dispersion)

[Chapter 3: Types of Distribution](#ch005.xhtml#chapter-3-types-of-distribution)

[Chapter 4: Precision vs. Accuracy](#ch006.xhtml#chapter-4-precision-vs.-accuracy)

[Chapter 5: Percentiles](#ch007.xhtml#chapter-5-percentiles)

[Chapter 6: Dependent Vs. Independent Variables](#ch008.xhtml#chapter-6-dependent-vs.-independent-variables)

[Chapter 7: Types of Data](#ch009.xhtml#chapter-7-types-of-data)

[Chapter 8: Population Vs. Sample](#ch010.xhtml#chapter-8-population-vs.-sample)

[Chapter 9: Hypothesis Testing](#ch011.xhtml#chapter-9-hypothesis-testing)

[Chapter 10: Outliers](#ch012.xhtml#chapter-10-outliers)

[Chapter 11: Machine Learning Concepts](#ch013.xhtml#chapter-11-machine-learning-concepts)

[Chapter 12: Measuring Accuracy in Algorithms](#ch014.xhtml#chapter-12-measuring-accuracy-in-algorithms)

[Chapter 13: Maths behind Regression](#ch015.xhtml#chapter-13-maths-behind-regression)

[Chapter 14: Linear Algebra in Machine Learning](#ch016.xhtml#chapter-14-linear-algebra-in-machine-learning)

[Chapter 15: Decision Tree](#ch017.xhtml#chapter-15-decision-tree)

[Chapter 16: k Nearest Neighbours (kNN)](#ch018.xhtml#chapter-16-k-nearest-neighbours-knn)

[Chapter 17: Gradient Descent](#ch019.xhtml#chapter-17-gradient-descent)

**About The Author**

![author's photograph](Images/file0.jpg)

Govind Kumar is an accomplished technology executive with more than 2 decades of experience in large multinational companies and startups.

He has held leadership roles in the areas of Customer Experience, Technology (AI ML) and Quality (Lean Six Sigma) and Strategy. He has also been a founder of an AI ML startup.

He has incubated and set up centers of excellence for analytics and fraud detection, and he brings his vast experience into this book.

**Books By This Author**

*   **From Fury to Faith : Decoding The Evolving Indian Customers**
    
*   **Customer Escalation Is A Gift**
    
*   **Comprehensive Machine Learning**
    
*   **Python Programming : With Google Colab Development Environment**
    

# Chapter 1: Introduction

Machine Learning (ML) is a field at the intersection of computer programming, mathematics and domain knowledge.

The author has observed that many budding machine learning students and enthusiasts make the mistake of jumping to build and work on algorithms without adequately understanding the math behind algorithms. That is not the right way to go about learning machine learning.

One must first understand the mathematics and statistics concepts relevant to machine learning. The algorithms and the associated programming should be learnt subsequently.

![understanding machine learning](Images/file1.jpg)

Without an understanding of math concepts relevant to machine learning, deploying and utilizing machine learning will always remain challenging. So, practitioners and budding enthusiasts need to assimilate the core concepts.

By mathematics, we are not referring to theoretical mathematics but rather applied mathematics. Applied mathematics and statistics is about applying the theoretical concepts to real world challenges and problems.

**The following core concepts are covered in this book.**

*   Measures of Central Tendency Vs. Dispersion
    
*   Mean Vs. Standard Deviation
    
*   Percentiles
    
*   Dependent Vs. Independent Variables
    
*   Types of data
    
*   Sample Vs. Population
    
*   Hypothesis testing
    
*   Outliers
    
*   ML concepts
    

**Concepts related to algorithms are also covered in this book.**

*   Measuring accuracy in algorithms
    
*   Math behind regression
    
*   Math behind decision tree
    
*   Math behind kNN
    
*   Gradient descent and optimization
    

These concepts are explained from an application perspective, that is how these concepts are applied in real life. The author is confident that understanding these concepts will help you to lay a solid foundation and build a thriving career in artificial intelligence.

# Chapter 2: Central Tendency vs. Dispersion

In this chapter, let's understand the concept of central tendency and dispersion. Whenever you are presented with any data set, it is crucial to understand what is going on in the data before developing any statistical models. And the best way to understand the data is to use the concept of central tendency and dispersion.

Central tendency provides the basic information about the data. Central tendency is described by metrics like mean, median and mode. Central tendency offers information from the perspective of the midpoint of the data.

Dispersion is the degree to which data is distributed around this central tendency and is represented by metrics like range, deviation, variance, standard deviation and standard error.

![two key measures for any data](Images/file2.png)

It is necessary to analyze the data from both central tendency and dispersion, though some people make the mistake of analyzing the data from the perspective of central tendency only. This may be convenient, but it leads to erroneous conclusions. An analysis using central tendency and dispersion will give beneficial and comprehensive insights.

**How to calculate measures of central tendency?**

Let us consider a simple dataset of 6 numbers or 6 observations.

*   Dataset = {9, 3, 1, 8, 3, 6}
    
*   Mean = Sum of observations / total no. of observations = 30/6 = 5
    
*   \[ 9 + 3 + 1 + 8 + 3 +6 = 30 \]
    

**Median** is the middle number in the dataset when the dataset is arranged in ascending order.

*   Dataset = {9, 3, 1, 8, 3, 6}
    
*   Dataset in ascending order = {1, 3, 3, 6, 8, 9}
    
*   Median **\=** midpoint of {1, 3, **3, 6**, 8, 9} = (3+6)/2 = 4.5
    

If the dataset has an odd number of observations like {1, 3, **3,** 8, 9}, then the median will be the midpoint (3). When there is an even number of values like in the previous example, the median is arrived at by finding the arithmetic average of the middle points.

**Mode** is simply the frequently occurring number.

Mode = 3

**Arithmetic Range / Range is** the difference between the highest and lowest values in the dataset. To find it, subtract the lowest number in the distribution from the highest.

Range = Maximum – Minimum = 9-1 = 8

**Mean Vs Standard Deviation:**

**Standard deviation** measures the extent of variation or dispersion in a dataset. A low standard deviation indicates that the values are closer to the mean of the set, while a high standard deviation indicates that the values are spread out over a broader range.

The standard deviation is calculated as the square root of variance by determining each data point's deviation relative to the mean.

![standard deviation equation](Images/file3.png)

Let us consider a dataset **{1, 2, 3, 4, 5}** and compute standard deviation

*   Here n (count) =5,
    
*   Average = (1+2+3+4+5) ÷ 5 = 15÷5 = 3
    
*   Calculating the difference of each element from average = { (1-3), (2-3), (3-3), (4-3), (5-3) } ={ -2,-1,0,1,2}
    
*   Squaring each of the difference value = {4, 1, 0, 1, 4} and we get a sum = 10
    
*   Applying formula, n - 1 = 5-1 = 4
    
*   Standard Deviation (SD) =$\\sqrt{10}/4$ = $\\sqrt{2}.5$ = 1.58
    

This calculation can be easily understood from the below representation.

![standard deviation table](Images/file4.png)

# Chapter 3: Types of Distribution

There are two types of distribution:

1\. Symmetrical Distribution

2\. Asymmetrical or Skewed Distribution

**Symmetrical Distribution:**

A symmetric distribution is a distribution in which the left and right sides mirror each other. The most well-known symmetric distribution is the normal distribution with a bell-shaped curve. In a symmetrical distribution, mean = median = mode. The values of mean, median, and mode are the same.

**Asymmetrical or Skew Distribution:**

Asymmetrical distribution occurs when the values occur at varying frequencies and the mean, median, and mode are not the same. If a distribution is non-symmetrical, it is said to be skewed. Skewness can be negative or positive.

Skewness is a distortion or asymmetry that deviates from the symmetrical bell curve (normal distribution) in a data set. If the curve shifts to the left or the right, it is said to be skewed. Here the mean, median, and mode will not be the same.

![Understanding Descriptive Statistics - Towards Data Science](Images/file5.jpg)

**Frequency Distribution:**

A simple way to understand the shape of the distribution is by using a frequency distribution. A frequency distribution shows the frequency of occurrence of each data point in a dataset.

Let us consider the dataset \[6,6,5,5,5,1,1,1,1,4,4,4,4,4,4,4,3,3,3,3,3,3,2,2,2,2,2,2,2,2,2,5,5,5\]

We first create a tally of the number of occurrences of each data point and plot the tally (or count) in the form of a graph. It is a standard practice in statistics to indicate the occurrence of a number using a vertical line. Once the tally reaches 4, the next (5^(th)) occurrence is indicated or characterized by a slanting line across the four vertical lines. This helps us to easily understand which number occurs more.

![frequency distribution](Images/file6.png)

The bar graph that you see above is a representation of the shape of the distribution. The below graph is a three-dimensional view of the bar graph to clearly see the distribution. In this dataset, mean, median and mode are not the same.

![frequency distribution graph](Images/file7.png)

Let us now understand how to apply the concept of central tendency vs. dispersion using the below example.

![central tendency vs dispersion](Images/file8.png)

In the above example, the average of both the groups is the same but the standard deviation (SD) is different. Can you find out which of the two groups is better and why?

Group A (plotted on the left) is better than Group B because the standard deviation is lower. When the Standard deviation is lower, the variation is lower. When variation is lower, the predictability of the future from the current data set is higher. When variation is higher, the predictability is lower.

If we had just relied on the average to evaluate the two groups, we would have said that both the groups have the same level of performance, which is not correct.

**Another Example: Standard Deviation**

In this example, Group A (test score shown on the left) has mean = 85 & standard deviation (SD) = 7 and Group B (test score shown on the right) has mean = 80 & SD = 15. Which is better and why?

![bar graph example of standard deviation](Images/file9.png)

Group A is better than Group B because the average is higher and variation (measured by standard deviation) is lower.

# Chapter 4: Precision vs. Accuracy

Accuracy refers to the closeness of the value (being measured) to the object’s actual measurement. At the same time, precision is the consistency of multiple measurements of the same object, irrelevant to the object’s actual measurement.

Accuracy is how close a shooter gets to the bull’s eye. Precision is how repeatable the shooter’s performance is, that is, how close is the second arrow to the first one (regardless of whether either of the arrows is near the mark).

![image of four targets](Images/file10.png)

**Of the four shooters, which shooter is the best and why?**

The Shooter 4 is the best because the variation is lower, and he is hitting the target often. Both precision and accuracy (Mean and Standard deviation) are higher.

Among the rest of the shooters, who do you think can come to the level of shooter 4 quickly?

In the case of shooters 2 and 3, their variation is high, possibly caused by multiple factors which are difficult to identify. Shooters 2 and 3 could also be amateurs, and they probably need to practice a lot more to become like shooter 4.

However, shooter 1 has high precision with low accuracy. The low accuracy could be due to issues like angle, focus, direction, or not understanding the wind pattern. These can be addressed relatively quickly and once the issue is addressed, shooter 1’s performance will be like that of shooter 4.

# Chapter 5: Percentiles

Percentile indicates the value below which a certain percentage of the data in a data set is found. The *n*th percentile of a data set is the value at which *n* percent of the data is below it, after the data is arranged in ascending order. In everyday life, percentiles are used to understand matters (or measures) such as test scores, health indicators and other biometric measurements.

The percentile is a measure of dispersion and is used to rank the data. We use the concept of percentile to understand dispersion and identify outliers.

## Percentile Formula

Percentiles for the values in a given data set can be calculated using the formula:

**n = (P/100) x N**

Where P = percentile, N = number of values in a data set (sorted from smallest to largest), and n = ordinal rank of a given value

**Percentiles should not be confused with percentages**. The latter is used to express fractions of a whole, while percentiles are the values below which a certain percentage of the data in a data set is found. In practical terms, there is a significant difference between the two.

Let us understand this with an example. The heights of 20 students in a class are being analyzed as shown below. As part of the analysis, the 80^(th) percentile is being computed.

![percentile formula example image](Images/file11.png)

If your height is 5’11” (five feet and eleven inches), 80% of students in the class are below 5’11”. That is, the value of the 80^(th) percentile is 5’11”

Please note that the data should be arranged in ascending order before finding out the percentile.

# Chapter 6: Dependent Vs. Independent Variables

An **independent variable** is a variable that represents a quantity that is being manipulated in an analysis or experiment. X is often the variable used to represent the independent variable in an equation.

A **dependent variable** represents a quantity whose value depends on how the independent variable is manipulated. Y is often the variable used to represent the dependent variable in an equation.

If x and y are two variables in an algebraic equation and every value of x is linked with any other value of y, then 'the y' value is said to be a function of x value known as an independent variable and 'y' value is known as a dependent variable.

In Machine Learning, the concept of dependent and independent variables is very important to understanding the data. Let us understand this with examples.

The growth of the plant (increase in plant’s height) is dependent on the quantity of water and fertilizer used. Therefore, the height of the plant is a dependent variable, and the quantity of water and fertilizer used are independent variables.

We have to establish the dependent and independent variables at the start of the machine learning and deep learning project.

![dependent and independent variable image](Images/file12.png)

**Insurance Example:**

The charges levied by the insurance company on individuals buying an insurance policy are dependent on multiple factors.

![insurance example](Images/file13.png)

In this scenario, insurance charges is the dependent variable and the rest are independent variables, that is, insurance charges is “dependent” on age, sex, body mass index or BMI, number of children, whether the individual is a smoker or not and which region the individual comes from.

**Banking Industry Example:**

In this example, the bank is evaluating whether a loan should be granted or not.

The bank can grant the loan to an individual based on factors like gender, marital status, number of dependents, education, type of employment, applicant’s income, co-applicant income, loan amount, credit history and property area.

![baking industry example](Images/file14.png)

*   Whether loan should be granted or not (Y) – Dependent variable
    
*   Factors (X1,X2,X3,X4,X5,X6,7,X8,X9,X10,X11) – Independent variables
    

Here, Y is a function of factors from X1 to X11.

# Chapter 7: Types of Data

In this chapter, let's understand the different types of data. We all know about the two broad categories of data viz., qualitative and quantitative data. But if you really see, a further subdivision is there within qualitative and quantitative data.

In Machine Learning, we should ascertain the different data types that exists in the data set. Algorithms are developed for quantitative data, so the qualitative data must be converted to quantitative data.

**Types of data:**

**1\. Quantitative data** - data that can be written in numbers, for example, the heights of children.

**Sub-types**:

*   **Discrete data** - numerical data that cannot be shown in decimals, for example, the number of students in a classroom.
    
*   **Continuous data** - numerical data that can be shown in decimals, for example, the heights of students.
    

The critical difference between the two is that continuous data can be measured on a continuum or a scale. You can subdivide it meaningfully. For example, if someone says 169 centimeters as their height, you can also represent it as 1.69 meters.

This kind of subdividing of data is not possible in discrete. If there are 30 students in a class, I can only say 30 students. I can’t tell 30.1 students or 29.8 students.

**2\. Qualitative data** - data that can only be written in words, not numbers. For example, the colors of cars in a car parking area.

**Sub-types:**

*   **Nominal –** data with no inherent order or ranking sequence, such as blood group, gender, race, etc. We can’t say that male is better than female or that O positive blood group is better than AB negative.
    
*   **Ordinal –** data that has ordered series, for example, performance grades.
    
*   **Binary –** data that has only two options: pass/fail, yes/no, true or false, etc.
    

Why is this understanding of different types of data necessary for machine learning?

Algorithms are developed for Quantitative data only, so the Qualitative data must be converted to Quantitative data. Even this conversion of qualitative data to quantitative data is only an approximation. Your aim should be to have more quantitative data and less qualitative data in your dataset. That will ensure a higher forecast accuracy of machine learning models.

Let us look at the banking and insurance examples for different data types. We will use the same examples we saw in the previous chapter on dependent and independent variables.

**Examples: 1) Insurance charges**

![insurance charges example](Images/file15.png)

Y – Independent Variable

X’s (factors) – Dependent Variable

In the above example, we can see Y, X1, X3, and X4 are numeric and X2, X5 & X6 are non-numeric. Float refers to continuous data in the above representation.

We must convert non-numeric data to numeric data.

**2) Banking Example**

![banking example](Images/file16.png)

Y – Independent Variable

X’s (factors) – Dependent Variable

In the above example, we can see only X3, X6, X7, X8 and X9 are numeric and all others are non-numeric. These must be converted to numeric.

# Chapter 8: Population Vs. Sample

This chapter is about population vs. sample and what we are learning here will form the basis for the next chapter – hypothesis testing.

When working on a machine learning project, you don't get to work on the complete data set. It could be due to various reasons like time challenges, cost constraints, some of the data may be corrupted, storage space may not be available etc.

So, you get to work on a part of the complete data set, known as a sample. We analyze the sample data and draw inferences from the analysis of sample data to the larger dataset or population. That is, we extrapolate the inferences of the sample to the population.

Let us say you are trying to understand buying behavior in your school or workplace. Do you think you can collect data from every person in your school or work? It is practically not possible. Instead, you select a sample and work on it. The sample is also the group of individuals who are likely to participate in your research.

To draw valid conclusions from your results, you have to carefully decide how to select a sample that is representative of the group.

First, you need to understand the difference between [a population and a sample](https://www.scribbr.com/methodology/population-vs-sample/) and identify the target population of your research.

*   The **population** is the entire group that you want to draw conclusions about.
    
*   The **sample** is the specific group of individuals that you will collect data from and analyze.
    

The population can be defined by geographical location, age, income, and many other characteristics.

It can be very broad or relatively narrow. It could be the whole adult population in a city, customers of a particular company or patients with a specific health condition.

It is essential to carefully define your target population according to the purpose and practicalities of your project. This single aspect can make or break your machine learning project.

Two key aspects that define the success of your sampling strategy are representativeness and randomness.

**Representative Sampling:**

A representative sample is **a subset of a population that seeks to accurately reflect the characteristics of the larger group**.

In the picture you see below, do you think the sample is representative of the population.

The percentage contribution of different types of students in the sample is significantly different from that of the population. Hence the sample is not representative.

![population sample 1](Images/file17.png)

![population sample 2](Images/file18.png)

Let us say you are developing a machine learning model that can be deployed across multiple countries to predict heart diseases. If most of your dataset comprises only Indians, what do you think will be the model's accuracy?

The accuracy will be low because your sample is not representative. The distribution of different nationalities in the sample should mirror the distribution in the world, which is the population.

Also, note that Indians (and South Asians in general) have a higher propensity for heart disease than Chinese or Caucasians and the model will not yield good accuracy.

The concept of representative sampling is equally vital in opinion polls. Let us say you're trying to assess the likelihood of a particular party winning the elections in the US or India; you must ensure that your sample is representative of the population of the electorate.

![India and USA regional maps](Images/file19.png)

If you're going to collect more feedback from northern or central India, your conclusion or inference won't be comprehensive or accurate. The same holds for the US also. If your feedback is primarily from coastal areas, and you ignore the southern and Midwest regions, your inference wouldn't be accurate because your sample is not representative of the population of electorates.

**Random Sampling:**

The other aspect when it comes to sampling is random sampling. Random sampling ensures that there are no biases when picking the sample for taking feedback or doing any type of study.

In the example that you see below, there is one yellow-colored ball, one red-colored ball, one blue-colored ball, and two green-colored balls in the sample (balls in the right group). For picking a blue-colored ball from the population (the balls in the left group), I could have taken balls numbered 6 or 8 or 9 or 11 or 14 or 17. Instead, I chose a ball numbered 6. I could have picked up an 8 or 11, 9, 14, 16 or 17.

![random sample example image](Images/file20.png)

Each of the blue balls in the population has an equal chance of being picked up in the sample. If I ensure that each of the blue balls has an equal chance of being picked up, then I have ensured randomness in the sampling.

If you are trying to take an opinion or feedback for joining a particular school from 20 students of a college (the total strength of the college is 100), you can ask the 20 students known well to you or any of the 100 students. The former is easier to do but it introduces bias. The latter is relatively more time-consuming and challenging but gives a better outcome.

Bias decreases the accuracy of the machine learning and practitioners should take care to ensure the randomness of the sample.

# Chapter 9: Hypothesis Testing

Hypothesis Testing is a type of statistical analysis in which you put your assumptions about a population parameter to the test. Hypothesis testing validates the inference we have drawn for the population, based on our study of the sample.

Two concepts related to hypothesis testing are null hypotheses and alternate hypotheses.

The **Null Hypothesis** is the assumption that the event will not occur. A null hypothesis has no bearing on the study's outcome unless rejected. H[0] is the symbol for it, and it is pronounced H-naught.

The **Alternate Hypothesis** is the logical opposite of the null hypothesis. The acceptance of the alternative hypothesis follows the rejection of the null hypothesis.

H[a] is the symbol for it.

Put simply, an alternate hypothesis is what we are trying to prove and the null hypothesis is the opposite of what we are trying to prove. We don't prove a hypothesis directly. Instead, we either accept or reject the alternate hypothesis. That's how we go about hypothesis testing.

We use fertilizers to improve plant growth and the growth depends on the proper usage of fertilizer. If we want to check if a particular type of fertilizer, called fertilizer A, increases plant growth, we will state the null and alternate hypotheses as follows.

![image of hand, seeds, and plant](Images/file21.png)

H[0]: Application of fertilizer A does not increase plant growth.

**H[a]**: Application of fertilizer A increases plant growth.

The alternate hypothesis is what we are trying to prove, and what we are trying to prove is mentioned as an alternate hypothesis. And the opposite of this is known as the null hypothesis. Why do we take this route? If you support a hypothesis a million times, and then on the 1,000,001st time you reject it, the hypothesis is not true.

**Type 1 and Type 2 Error:**

Even though hypothesis tests are meant to be reliable, they are not 100 percent certain. A hypothesis test can result in two types of errors.

**Type 1 Error**: A Type-I error occurs when a null hypothesis is rejected despite being true. This is known as a case of false positive.

**Type 2 Error**: A Type-II error occurs when the null hypothesis is not rejected even though it is false. This is known as a case of false negative.

An older man being diagnosed as pregnant or a full-term pregnant lady not being diagnosed as pregnant are classic examples of type 1 and type 2 errors. You will have these kinds of errors in real life.

So, we go for confidence level, which means how confident am I about the inference that I have made for the population based on the sample. A 95% confidence level means a 5% chance for errors.

Disease prediction algorithms warrant a higher accuracy say 99.9% because we are talking of life and death in a healthcare scenario. A sales process in the same healthcare industry may settle for a 90% confidence level.

These decisions have to be made keeping multiple factors in mind like time, cost, the criticality of the prediction, etc.

# Chapter 10: Outliers

Outliers are extreme points in our data set and they impact the accuracy of our models quite adversely.

You would remember this graph from the central tendency and dispersion chapter. I am going to use this graph to explain outliers. In the picture below, 96, 69, and 71 are outliers.

![test scores bar diagram](Images/file22.png)

How is this concept relevant to machine learning?

Can you afford to have outliers in your dataset? Yes, you can have them provided the number of such outliers is negligible. And a better way to handle outliers is to remove them. Outliers can skew the results of machine learning models. Unwanted inferences can result if outliers are present in our dataset.

**Box plot**

The box plot is a handy way of depicting the distribution and behavior of the data at the ends of the distribution. The box plot uses the median, and the lower and upper quartiles (the lower and upper quartiles correspond to the 25^(th) and 75^(th) percentile respectively). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3-Q1) is called the interquartile range or IQR.

The box plot is constructed by drawing a box between the upper and the lower quartiles with a solid line drawn across the box to locate the median.

The boundaries for the box plot are computed as below.

1.  Lower boundary: Q1-1.5\*(Q3-Q1)
    
2.  Upper boundary: Q3+1.5\*(Q3-Q1)
    

A point beyond the lower or upper boundary point is considered an outlier.

![understanding a box plot](Images/file23.png)

How to use box plots in excel has been explained below.

A dataset of 156 items of the invoice amount is used to create a box plot and identify outliers.

Select the datapoints

![select datapoints](Images/file24.png)

Click insert

![click insert](Images/file25.png)

Select Recommended charts

![select recommended charts](Images/file26.png)

Select the All charts tab

![select the all charts tab](Images/file27.png)

Choose Box & Whisker

![choose box and whisker](Images/file28.png)

Now you get the Box plot

![Box Plot](Images/file29.png)

Here the outliers are clearly shown as dots. We can manually remove the outliers from the box plot. We can also use Python or R or any other programming language to create box plots and remove the outliers programmatically.

# Chapter 11: Machine Learning Concepts

In this chapter, we are going to learn about machine learning concepts. But before seeing the machine learning concepts, let's understand what is A.I.

AI is computer software that thinks and acts like human beings. The software may even reside inside a hardware entity, but it's essentially software. We are already aware that AI is a fast-growing field with applications across healthcare, telecom, banking, retail, social media, etc.

There are two types of artificial intelligence (AI):

**Strong AI:**

Strong AI is software systems thinking at the level of human beings and displaying human behaviors like reasoning and thinking. We are not there yet. This type of AI is still being researched. This is also called Artificial General Intelligence (AGI) and Artificial Super Intelligence (ASI).

**Weak AI:**

Weak AI involves solving problems by detecting valuable patterns in data. This is the dominant mode of AI today.

We call the current level of artificial intelligence weak AI, only to distinguish it from strong AI or the artificial super intelligence. Even with the so-called weak AI, we are solving many problems.

**Pattern Detection**

A pattern is a consistent, recurring characteristic. A **pattern** repeats recognizably in numbers, images, designs, etc.

In the graph below, what are the patterns you can observe?

![Chart, line chart Description automatically generated](Images/file30.png)

1.  We can see that peaks in a calendar year occur in July
    
2.  The troughs or the lowest points in a calendar year occur in January.
    
3.  We can also note that the highest point in a calendar year is progressively increasing at nearly the same rate.
    

We can uncover these three patterns using our eyes. If the number of data points is more, will you be able to uncover patterns easily and quickly? We won’t and we need software to reveal the pattern. That is what an AI system will do.

Now, let's see how AI is applied to heart disease prediction.

The database used to build the prediction system will consist of patient records with details of heart disease, cholesterol, sugar, blood pressure, genetic predisposition, and BMI (Body Mass Index). These details would be available for people with and without heart disease.

The system will analyze the data and uncover the patterns contributing to heart disease.

People who have heart disease will probably have a certain level of BP, a certain level of sugar value, a certain level of cholesterol, etc. Those values in combination are called **patterns**. The system will uncover the pattern that is contributing to heart disease.

Whenever a patient record with values for the above parameters is fed into the system, the system will use the previously uncovered pattern to predict.

We can never be 100% sure of the prediction, so we use the terms “**likely** to develop the heart disease” and “**not likely** to develop the heart disease.”

The same concept is used in the loan default prediction also. Someone consistent in paying the loan will have a regular income possibly supported by their spouse’s income, a stable job, and possibly a thriving career. On the other hand, someone who is likely to default will exhibit the opposite of the above characteristics. So, the algorithm or the computer program will try to uncover the pattern for regular payers of loan and defaulters. This pattern will be used to predict defaulters.

**AI Vs. Machine Learning Vs. Data Science**

In this chapter and the earlier chapters, you would have noticed the use of words AI and machine learning, sometimes interchangeably. While AI is the headliner, machine learning is the technology that drives AI. Pattern recognition that we saw earlier is also part of machine learning. You may also hear another term when AI and machine learning are discussed. It is known as deep learning. Deep learning is a more advanced form of machine learning.

Another term that has gained traction in recent times is data science. Data science essentially refers to machine learning and the associated technology. The term ‘data science’ has been used more in the academic world.

Having understood AI and machine learning, let us understand the two types of machine learning - **Supervised Learning and Unsupervised Learning** using an example.

![examle image](Images/file31.png)

In supervised learning, the data fed into the system for the machine or software to learn the patterns will contain a reference to the variable or the kind of output that will be predicted in the future. In this example, it is insurance charges or Y. The reference is also called a label. Without this label or reference, the software will not know how to link the X’s to Y. Please note that one can use the X’s to predict something else also, viz., whether the company should give insurance or not to a customer.

Supervised machine learning relies on labeled data. The model learns the relationship between the labeled output and the input data. The majority of the models will be of supervised learning.

In unsupervised learning, the reference or label data won’t be there. Unsupervised learning processes unlabeled or raw data. Unsupervised learning is gaining importance since many companies don’t have labeled data readily available. Unsupervised learning can be a good starting place for companies to start their machine learning journey.

As you would have noted, machine learning works very differently from conventional programming. The below picture captures the difference clearly.

![traditional programming vs ML programming](Images/file32.png)

In traditional programming, we feed data into the system, and the program processes the input to create output.

In machine learning, the actual output is the statistical model or program that can make the prediction, and the reference or label or output is actually an input.

**Classification and Regression**

Earlier in this chapter, we saw the two types of machine learning – supervised and unsupervised learning. Supervised learning can be further sub divided into two types called classification and regression.

![classification and regression](Images/file33.png)

In a regression algorithm, the output variable will be numeric. In a classification algorithm, the output variable will be non-numeric – yes or no, good or bad, will it happen or not etc. If you are trying to predict tomorrow’s temperature, we are talking about a regression algorithm. On the other hand, if you are trying to predict whether it will be sunny or not, you are talking about a classification algorithm.

In the above picture, we are trying to predict the quantum of carbon dioxide emission based on vehicle volume and vehicle weight in a regression algorithm; in a classification algorithm, we use the same factors (vehicle volume and vehicle weight) to determine the likelihood of high carbon dioxide emission.

**Train data Vs. test data**

Machine learning works by uncovering the pattern in the dataset. To ensure that the developed model has a high level of accuracy, we split the given dataset or the historical data into train data and test data, and the statistical model (or equation) is developed on the train data. The developed model is then checked on test data for accuracy. If the accuracy is low, the model re-trains and tries to improve the accuracy over 2 or 3 cycles or even more. The finalized model is then used for current or future data for prediction purposes.

![Diagram Description automatically generated](Images/file34.png)

The ratio in which the train vs. test data is split is typically 80:20. It can even be 60:40 or 75:25. This is subjective, and practitioners sometimes play with this ratio to see if the accuracy improves or not.

# Chapter 12: Measuring Accuracy in Algorithms

In the previous chapter, we learned about machine learning concepts. We also saw the different types of machine learning, classification and regression. This chapter will see how to measure the accuracy of a classification algorithm and regression algorithm.

What is accuracy? Let us say I am predicting whether someone will get a disease.

Whether that person actually gets that disease or not is a measure of accuracy. So, accuracy provides a comparison between predicted and actual. The level of accuracy will be measured both during the stage of developing the statistical model and during deployment.

Accuracy is measured differently in a classification and a regression algorithm.

**Accuracy in a regression algorithm**

In a regression algorithm, we measure accuracy using R² and MAE. R² is a ratio involving the difference between actual versus predicted with respect to the mean. MAE (mean absolute error) tells the quantum of difference between actual versus predicted. In regression, we use both the R² and absolute error to assess how good the machine learning model is.

**R²** **\= 1 – RSS / TSS**

The residual sum of squares (RSS) is the difference between actual versus predicted. The explained sum of squares (ESS) is the difference between the predicted versus the average. The total sum of squares (TSS) is RSS + ESS.

If R ² is closer to 100%, the fitment is great, at 80%, the fitment is good. If it’s 40%, the fitment is ok, and at 0%, the fitment is low and there is no correlation. R² can also be negative. It merely means that the relationship is negative instead of positive. If you are wondering how that is possible, consider this example. A student put in a lot of effort to score good marks but failed. The more he studied, the fewer marks he got. In this case, R² will be negative.

![comparison image](Images/file35.png)

**Accuracy in a classification algorithm**

In a classification problem, we look at accuracy in terms of true positive and true negative, and compare that with all possibilities of true negative (TN), false positive (FP), false negative (FN) and true positive (TP).

Accuracy = TP + TN / TP + FP + FN + TN

![accuracy in a classication algorithm](Images/file36.png)

We also use another metric called area under the curve (AUC). This provides a range of values between 0 and 1. It uses all possibilities of TN, TP, FP and FN to give values between 0 and 1. If AUC is closer to 1, the accuracy is higher; if it’s closer to 0, accuracy is lower.

**Confusion Matrix:**

A confusion matrix is **an excellent way to summarize prediction results in a classification problem**. The number of correct and incorrect predictions are summarized with count values and broken down by each class. This is the key to the confusion matrix. The confusion matrix shows the ways in which your classification model succeeds or fails.

False positive and false negative are also called type 1 error and type 2 error, respectively.

![false positive and false negative](Images/file37.png)

# Chapter 13: Maths behind Regression

Let's understand the mathematics behind regression in this chapter. We will use an example to get started. Many of us have been told by our teachers and parents to study more to get more marks. Some have used this strategy successfully, while others have not got desired results. So, there is clearly a relationship between the number of hours studied and marks obtained for the former, while this relationship doesn’t hold for the latter. This relationship can be explained mathematically using the concept of regression.

Let us look at the table below. Do you think there is a relationship between the number of hours studied and marks obtained?

| **Marks obtained** || **No. of hours studied.** |
| --- | --- |
| 30 || 0 |
| --- | --- |
| 40 || 0.5 |
| 50 || 1 |
| 60 || 1.5 |
| 70 || 2 |
| 80 || 2.5 |
| 90 || 3 |
| 91 || 4 |
| 92 || 5 |
| 93 || 6 |

You can use the concept of linear regression to answer this question correctly. Let us see how to go about it in excel. First, select the two columns and choose the scatter plot. A Scatter plot helps to show the relationship between factors or variables.

![image](Images/file38.png)

![image](Images/file39.png)

![image](Images/file40.png)

Choose any of the data points in the graph and right-click, then choose the option to add a trendline. The trend line is also called the line of best fit. The line of best fit is expected to cover all the data points and adequately explain the relationship.

![image](Images/file41.png)

We will get the result as below.

![image](Images/file42.png)

The equation and R-Squared value have been displayed on the chart using the option to format the trendline.

![image](Images/file43.png)

Key results are:

*   The equation of the trendline is Y = 10.862x + 41.901
    
*   41.901 is the data point where the trend line cuts the Y-axis
    
*   10.862 is the slope, about which we will see shortly.
    

Now, let us convert the equation into practical terms:

Marks = 10.862\* No. of hours studied + 41.901.

Here, marks is the dependent variable and the number of hours studied is the independent variable.

If a student comes to you and says that she studied for 3.25 hours, can you predict the marks obtained? You can predict the marks obtained using the above equation.

Marks = 10.862\* 3.25 + 41.901 = 77.2

A linear regression line has an equation **Y = mX + c**, where X is the independent variable and Y is the dependent variable. The slope of the line is m and c is the intercept (intercept is the value of y when x = 0 or the value at which the line meets the Y-axis).

![image](Images/file44.png)

m = gradient or slope = height divided by base of the triangle = 4 divided by 2 = 2. The value of the slope will be the same whether I draw a smaller triangle or a bigger triangle on the line.

> Y=2x-1, Y=mx+c
> 
> c is the intercept (where the line meets the Y-axis).

This concept was used in the example of marks obtained vs. the number of hours studied.

**Multiple Regression:**

Multiple regression is also linear regression, but with more than one independent variable, that is, we try to predict a value based on **two or more** variables.

Let us take an example to understand this better. Let us say I am trying to predict the quantum of carbon dioxide emission of a car based on the volume of the car and the weight of the car. If I use either one of the two variables or factors - vehicle volume or vehicle weight- I will use simple linear regression. If I use two factors – vehicle volume and vehicle weight – to determine the outcome, I will use multiple linear regression.

![image](Images/file45.png)

**Logistic Regression**

In the earlier example, we tried to predict the quantum of carbon dioxide emission using vehicle volume and vehicle weight. If we use the same variables (vehicle volume and vehicle weight) and try to predict whether the vehicle will have a higher carbon dioxide emission or not, I will use logistic regression. Please note that the output or the predicted value will be a yes or no, that is, the vehicle will have higher carbon dioxide emissions or not.

![image](Images/file46.png)

Logistic regression is a supervised learning classification algorithm used to predict the probability of a target variable or dependent variable. In simple words, the dependent variable is binary having data coded as either 1 (stands for success/yes) or 0 (stands for failure/no)

Though we have covered logistic regression under regression, please note that logistic regression is not really a regression algorithm but one of the generalized linear models (GLM).

**Need for logistic regression**

Let us say we are trying to predict the malignancy of a tumor based on the size of the tumor.

![image](Images/file47.png)

If a regression is used in this case, the line of best fit, which would be a straight line, will not cover all the data points. On the other hand, if a curved line is used to cover the points, the curved line would cover most of the data points as below.

![image](Images/file48.png)

**Linear Vs. logistic regression equation:**

In the linear model, the equation of the line of best fit is y= mx+c. In the logistic model, it is a sigmoid function to find probability p.

A **sigmoid function** is a mathematical function having a characteristic "S"-shaped curve or **sigmoid curve**.

![image](Images/file49.png)

# Chapter 14: Linear Algebra in Machine Learning

Concepts of linear algebra are used extensively in machine learning. Let us start with the below example of simple linear regression to understand this.

| Y (Dependent Variable) || X (Independent Variable) |
| --- | --- |
| 2 || 6 |
| 4 || 10 |

The goodness of fit (y=mx+c, where m is the slope and c is the intercept) for the above dataset can be found using the below equations,

Solving the two equations will help us to identify the values of m and c. The two equations have been created from the above table, that is the values of x and y from the above table have been used in the equation y = mx + c.

Alternatively, we can use linear algebra to solve for m and c.

Let us first re-write the equations as below so that their representation in a matrix form is clearer.

We can now represent the above equation in the form of a matrix as below.

Linear algebra provides a cleaner and more efficient way to solve the problem. This is particularly helpful when one goes for higher order polynomial, logistic regression deep learning algorithms or a large dataset. Please note that we are not solving the problem programmatically and not through manual calculations.

Since many machine learning enthusiasts rely on libraries to do a fitment of machine learning models, what goes on inside the libraries (example linear algebra calculations) is not seen and hence not well understood.

# Chapter 15: Decision Tree

In this chapter, we will understand how to create a decision tree. The decision tree forms the basis for random forest and XGBoost – the two most widely used algorithms today.

So let's start this with an example. In this example, we are trying to predict the likelihood of an individual getting heart disease, and three factors (blood pressure, sugar and cholesterol) are considered.

![image](Images/file50.png)

The crucial aspect in creating the decision tree is to find the root node that is where to start the tree from. Should I start with blood pressure or sugar or cholesterol? The root node is the base node of the tree from which the entire tree starts.

A decision tree is constructed like the below.

![image](Images/file51.png)

The root node of the decision tree can be found using the GINI index or entropy. We will see in detail how to use GINI in finding the root node. Each factor will be considered in isolation to compute the GINI index.

The formula for GINI index is **GINI index = 1 – (prob of yes)² – (prob of no)²**

Acronym prob stands for probability.

The Gini Index is calculated by subtracting the sum of the squared probabilities of each class from one. The GINI index varies between 0 and 1

Let us compute the GINI index for high BP (blood pressure).

![image](Images/file52.png)

The tree can be interpreted as follows. Out of all people with high blood pressure (true node), 105 people developed heart disease (HD), and 39 people did not develop heart disease. Out of all the people who did not have high blood pressure (false node), 34 people developed heart disease and 125 people did not develop heart disease.

The Gini index for a true node is 0.395, and the Gini index for a false node is 0.336. They are computed as below.

![image](Images/file53.png)

![image](Images/file54.png)

These two values are used to determine the total gini.

![image](Images/file55.png)

The same process is repeated for other scenarios (high sugar and high cholesterol), and the node with the lowest gini value goes to the root node. In the example below, the root node will be a scenario of high sugar.

![image](Images/file56.png)

# Chapter 16: k Nearest Neighbours (kNN)

In this chapter, we will understand the math behind kNN. kNN is k nearest neighbor. k nearest neighbor is used both in a classification supervised learning algorithm and in unsupervised learning.

Let us understand this algorithm using an example. In the picture below, we are trying to find whether the green ball will go to the blue group or the red group. That decision will be based on the distance between the green ball and the nearest blue & red balls. The concept of Euclidean distance will be used to find the distance.

![image](Images/file57.png)

The formula for Euclidian distance is

![image](Images/file58.png)![image](Images/file59.png)

Euclidean distance is the shortest between the 2 points irrespective of the dimensions. The most common way to find the distance between two points is the Euclidean distance.

For a given value of k, the algorithm will find the k-nearest neighbors of the green ball and then it will assign the green ball to either a blue or red group based on the distance. In the picture below, k is 4. The algorithm can expand the value of k to cover more red and blue balls to make the right decision.

![image](Images/file60.png)

Let us look at one more example to understand this better. The table below provides the weight of seven employees and their corresponding height and age. How will you compute the weight of the eighth employee (last row) using the concept of kNN?

| Employee || Height || Age || Weight |
| --- | --- | --- | --- |
| 1 || 6 || 40 || 60 |
| 2 || 6.11 || 26 || 55 |
| 3 || 5.9 || 30 || 56 |
| 4 || 5.8 || 32 || 58 |
| 5 || 5.3 || 33 || 75 |
| 6 || 5.6 || 34 || 78 |
| 7 || 5.5 || 35 || 80 |
| 8 || 5.8 || 37 || ? |

We compute the Euclidian distance for each of the seven employees’ data points to the eighth employee’s data points. The calculation below is for employee 1 with respect to employee 8.

x[2] – x[1]\= 6 – 5.8 = 0.2

y[2] - y[1]\= 40 – 37 = 3

(x[2] – x[1])² = 0.04

(y[2] - y[1])² = 9

(x[2] – x[1])² + (y[2] - y[1])² = 0.04 + 9 = 9.04

Euclidian distance = $\\sqrt{9.04}$ = 3.01

Similarly, we calculate the distance for the rest of the employees’ data points. The Euclidian distance of nearest (or lowest value) data points is considered, and, in this case, three nearest points are considered.

![image](Images/file61.png)

The weights corresponding to these three highlighted employees are 60, 78 and 80. Hence, the average of these data points (average of 60, 78 and 80) will be taken or predicted as the weight of the last employee. Therefore, the weight of the individual with a height of 5.8 and an age of 37 is expected to be 72.67 (the average of 60,78 and 80 is 72.67).

# Chapter 17: Gradient Descent

In this chapter, we will understand the concept of gradient descent. Every machine learning or deep learning algorithm is an optimization exercise, that is, the algorithm tries to reduce the difference between predicted and actual, which can also be called a loss. Loss corresponds to the difference between predicted minus actual in one iteration. A cost function is the average of the loss over multiple iterations.

The algorithm attempts to minimize this cost or losses because the objective of any algorithm is to have a result that is as close to the actual as possible. We want the forecast accuracy to be higher, which means the cost function should be minimal, and the loss should be very low. This translates to the predicted value as close to the actual as possible. This is the optimization exercise.

**Understanding the math in gradient descent**

Let us understand this with an example. The insurance company is trying to predict whether an insurance policy should be issued to an individual or not based on six factors like age, sex etc., The algorithm works by identifying the relative importance or weights of these six factors. Once the relative importance or weights are known, it is easier to predict because we would know which factors are more important compared to the rest. The relative importance is denoted by W1, W2, W3 etc., corresponding to X1, X2, X3 etc.,

If the two (W’s and X’s) are multiplied, we will have an output corresponding to the predicted value. Comparing the predicted value with the actual will give us the error value or loss. This feedback is fed back into the algorithm. If the feedback suggests a high error, the algorithm will try for a new set of relative weights. Multiple iterations of this exercise will help to finalize the relative weights. This is nothing but an optimization exercise and this is how the world of algorithms works. The process of giving feedback about the extent of error or loss so that a new set of relative weights are assessed is known as back propagation. This entire process is intuitive to the algorithm and is not visible even to the algorithm’s developer; hence this part of the algorithm is called a hidden layer.

![image](Images/file62.png)

**Concept of Gradient Descent:**

You know how to come down to the base if you are currently at point x, highlighted in the picture below. You know that you have to take route 1. However, if you are a computer robot, how will you know how to come down. You can either take route 1 or 2, although route 2 will take more time than route 1.

![image](Images/file63.png)

So the gradient descent algorithm helps us to make those decisions. As part of this process, the algorithm determines whether you are closer to your goal or not. If you are closer to your destination, you need to take only smaller steps. If you are away from your goal, you would need bigger steps. This concept of bigger vs. smaller steps corresponds to the relative weights assigned to the factors.

How will the computer know whether it has to take smaller or bigger steps? That is, how will the computer know whether you are closer to the goal or not? The computer uses the concept of dy/dx, which is nothing but slope or gradient.

![image](Images/file64.png)

> The slope at point B is less steep than that at point A and this means the computer robot will need to take fewer steps to reach the base from B than A. Machine learning uses derivatives in optimization exercises. Optimization algorithms like gradient descent use derivatives to decide whether to increase or decrease the relative weights. If we can compute the derivative of a function, we will know which direction to proceed. In our algorithms, we compute the negative of the gradient (or gradient descent). This is nothing but the opposite of the gradient or negative value of dy/dx**.**