
Data acquisition involves collection and organization of information. One must request and obtain pertinent data from the necessary organizations or individuals through the appropriate means.

The respondent can provide the data directly or through an interview. Date may also be extracted from administrative sources if proper permissions can be obtained granting access to administrative records.

The choice of data collection method is influenced by a number of factors. Such factors include the degree of accuracy required, the variable type, the strategy for data collection, and the skills of the enumerator.

Below are listed the common data collection methods:

Observation - data collected through observation can be viewed as “first-hand” information, meaning that the collected data will be direct and unbiased. The category includes systematic field observation, experimental, and participant observation. It is expensive, but more accurate than other methods of data collection

Interviewing - data obtained through the use of structured telephone interviews or self-administered questionnaires. Interviewing is a good data collection method when the questions being investigated are complex.

Questionnaires - question forms which must be completed and returned by respondents. Questionnaires can be an effective method for data collection if respondents are willing to cooperate, and where there are high literacy rates.

After data acquisition, one should move to the next step: data preprocessing.

## Data Preprocessing

Data Preprocessing involves transforming your raw data into a form which is understandable. Real-world data is usually incomplete, inconsistent, lacks some trends, and contains errors. The purpose of data preprocessing is to help in resolving these issues. Below are listed the steps followed in data preprocessing:

Data cleaning - the process of filling in the missing values, resolving inconsistencies and smoothing noisy data.

Data integration - the collected data is usually in different formats. This step includes the merging of all data into a standard format, with resolution of any formatting issues. Data transformation - this involves normalizing, aggregating and generalizing the data.

Data reduction - in this step, the aim is to get a reduced representation of the data in a warehouse.

Data discretization - the number of values for any continuous attribute is reduced by dividing the range of the attribute intervals.

## Techniques to handle Outliers

An outlier is simply an observation which lies at an abnormal distance from the other values in a random sample obtained from a given population. When dealing with data, most people ignore the outliers.

Even in controlled experiments, outliers are a common occurrence. They are normally caused by errors in measurements or by faulty measuring or recording instruments.

The best way to detect outliers in your data is through the use of graphical means. Other options include the use of statistical methods and tools such as R, Python, Excel, etc.

![Image](Images/image00076.jpeg)

Diagram Credits: Opabinia regalis

Scatterplots and boxplots are the two most common graphical representations used to reveal outliers. A histogram is another option. There are many strategies which can be used to deal with outliers.

Most tools used for outlier detection also provide means for dealing with them, but they typically differ in their approaches.

Let us discuss some of the strategies which can be used to handle outliers:

1.  

1. Create a filter in the testing tool.

Suppose you have an A/B testing tool which you are using to track revenue. You can create code which will identify and omit abnormally large orders from the test results. Past analytics data can help you determine the average web order, and the filter should be created with this in consideration. If you find the average to be $100, then any order above $150 might be considered an outlier.

1. Change or remove outliers during the post-test analysis

Another alternative is to trim the dataset so as to exclude as many outliers as possible. Trimming is easy in Excel through the use of the TRIMMEAN function. Simply specify the array to be manipulated and the amount by which you need to trim the upper and lower extremities.

R also provides a convenient trimming function, the mean function. A significant disparity between mean and median indicates the presence of data values sufficiently large or small to skew the body of data. To solve this problem, you can trim a certain percentage of data at both the low and high ends. You can use mean (*x, trim = .05*): in this case, *x* is the data set, and *.05* (or whatever you value you choose) is the percentage of extreme data to be omitted.

1. Changing the outlier value

Instead of removing the outlier, you can choose to give it another, more sensible (probable) value. But how will you decide which value is most sensible? There are various methods for doing this. Instead of using a more technical and complex processes to determine this, you may just want to identify the value in your data which makes sense to you, and use it for replacement. This way, you will have a standard data for training your model. 

1. Box-Cox Transformation

This involves the transformation of the data until it is normally distributed. There are a number of transformations for data normalization.

Possible options for data normalization include squaring or taking the reciprocal or square root of the data. In some other cases, the logarithms for the data values may be distributed normally. It depends upon the data.

Each of these transformations which may produce a normal distribution can be grouped together into a box-cox transformation. The box-cox transformation takes the following formula:![Trans2](Images/image00077.gif)

In this case, *x* is the raw data, *y* represents the transformed data, and lambda represents the transformation constant. If lambda is given a value of 1, the transformation has no effect. But if the value of lambda is 2, for example, the transformation becomes a square transformation function.

There are a number of ways through which you can find the value of the lambda in the Box-Cox transformation. One is Most Likely Estimate (MLE), but this approach can be time consuming. The easiest way to determine the correct value of lambda is by varying its value between -5 and 5, observing the results in order to determine which value for lambda will give you the most normal distribution.

The best value for lambda is the one which provides you with smallest standard deviation of the variation between transformed and normally distributed data. This will help you resolve the skewness of your data.

1. **Winsorize (Threshold Control)**

In this method, outliers are replaced with the nearest value in the data which is not considered to be an outlier.

The process of replacing the extreme values is known as *winsorization*. In most cases, winsorization involves setting all the extreme outliers to some specified percentile of your data. If you are using a winsorization of 90% for example, all the data below the 5^(th) percentile will be set to 5^(th) percentile, while all data above 95^(th) percentile will be set to 95^(th) percentile.

The winsorized estimators are known to be more robust to the outliers compared to the more standard forms. The purpose of winsorizing the outliers is to reduce their extremity to some specified value, so that they can more nearly fit a normal distribution curve.

All outliers can be conformed to specific chosen values, but there is another similar approach that is preferred by some. You can alternatively conform the first (least extreme high or low) outlier to your chosen near value, but bring the second outlier to an incrementally more extreme value than the first and the third to an incrementally more extreme value than the second, and so on.
