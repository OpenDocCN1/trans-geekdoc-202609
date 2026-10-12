![cover](OEBPS/images/cover.jpg)

![image](OEBPS/images/cover.jpg)

# Data Science  
and  
Machine Learning

# Interview Questions using

# Python

![](OEBPS/images/line.jpg)

# *A Complete Question Bank to  
Crack Your Interview*

![](OEBPS/images/line.jpg)

# *by*

# Vishwanathan Narayanan

![](OEBPS/images/logo.jpg)

**SECOND REVISED AND UPDATED EDITION 2020**

**FIRST EDITION 2019**

**Copyright © BPB Publications, India**

**ISBN: 978-93-89845-785**

All Rights Reserved. No part of this publication may be reproduced or distributed in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s & publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners.

**Distributors:**

**BPB PUBLICATIONS**

20, Ansari Road, Darya Ganj

New Delhi-110002

Ph: 23254990/23254991

**MICRO MEDIA**

Shop No. 5, Mahendra Chambers,

150 DN Rd. Next to Capital Cinema,

V.T. (C.S.T.) Station, MUMBAI-400 001

Ph: 22078296/22078297

**DECCAN AGENCIES**

4-3-329, Bank Street,

Hyderabad-500195

Ph: 24756967/24756400

**BPB BOOK CENTRE**

376 Old Lajpat Rai Market,

Delhi-110006

Ph: 23861747

Published by Manish Jain for BPB Publications, 20 Ansari Road, Darya Ganj, New Delhi-110002 and Printed by him at Repro India Ltd, Mumbai

# Dedicated to

*Dedicated to Pratyangira, Bala, Durga, Mom, Dad, Chitti my aunt, my sister Ishwarya, Sridhar my brother in law and to all my mentors especially Shiv without whom this book would still be a dream. Also the support extended by Shyam Sir, Khadak and BPB Publications is very much appreciated.*

*Durga has been a great inspiration for this book.  
She has always been and will me my encouragement to write more books.*

*Also remember Sudarshan as a friend in need.*

*Also dedicated to my students from whom I equally learned as I taught them.*

*Along with all the blessing of almighty is also remembered here without which even a blade of grass does not move*

# About the Author

**Mr Vishwanathan** has twenty years of hard code experience in the software industry spanning across many multinational companies and domains. Playing with data to derive meaningful insights has been his domain and that is what took him towards data science and machine learning.

# Preface

Data science is one of the hottest topics mainly because of the application areas it is involved and things which were once upon of time, impossible with earlier software has been made easy. This book tries to comprehend the ocean of data science into small book which is mainly intended to be used as last minute revision. Before interview, all the important concepts have been given in simple and understand format.

This book tries to include various terminologies and logic used both as a part of Data Science and Machine learning for last minute revision. As such you can say that this book acts as a companion whenever you want to go for interview.

Simple to use words have been used in the given answers for the questions to help ease of remembering and representation of same. Examples where ever deemed necessary have been provided so that same can be used while giving answers in interview. Author tried to consolidate whatever he came across, on multiple interviews that he attended and put the same in words so that it becomes easy for the reader of the book to give direction on how the interview would be.

With the number of data science jobs increasing, Author is sure that everyone who wants to pursue this field would like to keep this book as a constant companion. Soon, Author will be coming shortly with a new book on R too, so that it makes a complete data science stack.

Happy reading to all the readers, your feedback is highly appreciated.

# Foreword

It is not wrong to say that today’s dynamic world is driven totally by statistics. With decision making becoming important in being successful the use of software this task has become common, Thanks to the advancement made with respect to technology. While software application always existed for doing the above task, the volume and ability of software programmes to represent complex equation related to statistics and probability was limited.

Thanks to pandas, numpy, scipy and sklearn modules of Python, the above problem faced has been removed to a great extent and the problem is no more a challenge. With complex mathematical concepts easily convertible to algorithms the life of data scientist and analyst has become quite easy.

This book is mainly intended to help people represent their answer in a sensible way to the interviewer. The answers have been carefully rendered in a way to make things quite simple and yet represent the seriousness and complexity of matter. Since data science is incomplete without mathematics we have also included a part of the book dedicated to statistics.

Python has already taught us that small code does not mean lesser powerful the same concept has been adopted to keep the book a powerful weapon for any one attending interview.

# [CHAPTER 1](#toc.xhtml#c01)

# [Data Science Basic Questions and Terms](#toc.xhtml#c01)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: Explain the steps involved in data science?](#toc.xhtml#c01q1a)

*Ans:* Following are the steps involved:

1.  Get data from various data sources available.
2.  Generate research question from data.
3.  Identify variables present in data. Also, identify important variables or variables to be analyzed as such.
4.  Generate hypothesis.
5.  Analyze data using graph data like histogram for example.
6.  Fit a model from analyzed data.
7.  Accept or reject the hypothesis.
8.  Research question answer found.

![](OEBPS/images/1.jpg)

**Example of above steps:**

1.  Get data related to temperature for India reference [https://data.gov.in/catalog/annual-and-seasonal-maximum-temperature-india](https://data.gov.in/catalog/annual-and-seasonal-maximum-temperature-india)
    
    A template of data set:
    
    `“YEAR”,”ANNUAL”,”JAN-FEB”,”MAR-MAY”,”JUN-SEP”,”OCT-DEC”`
    
    `“1901”,”28.96”,”23.27”,”31.46”,”31.27”,”27.25”`
    
    `“1902”,”29.22”,”25.75”,”31.76”,”31.09”,”26.49”`
    
    `“1903”,”28.47”,”24.24”,”30.71”,”30.92”,”26.26”`
    
    `“1904”,”28.49”,”23.62”,”30.95”,”30.67”,”26.40”`
    
    `“1905”,”28.30”,”22.25”,”30.00”,”31.33”,”26.57”`
    
    `“1906”,”28.73”,”23.03”,”31.11”,”30.86”,”27.29”`
    
    `“1907”,”28.65”,”24.23”,”29.92”,”30.80”,”27.36”`
    
    `“1908”,”28.83”,”24.42”,”31.43”,”30.72”,”26.64”`
    
    `“1909”,”28.39”,”23.52”,”31.02”,”30.33”,”26.88”`
    
    `“1910”,”28.53”,”24.20”,”31.14”,”30.48”,”26.20”`
    
    `“1911”,”28.62”,”23.90”,”30.70”,”31.14”,”26.31”`
    
    `“1912”,”28.95”,”24.88”,”31.10”,”31.15”,”26.57”`
    
    `“1913”,”28.67”,”24.25”,”30.89”,”30.92”,”26.42”`
    
    `“1914”,”28.66”,”24.59”,”30.73”,”30.84”,”26.40”`
    
    `“1915”,”28.94”,”23.22”,”31.06”,”31.51”,”27.18”`
    
    `“1916”,”28.82”,”24.57”,”31.88”,”30.52”,”26.32”`
    
    `“1917”,”28.11”,”24.52”,”30.06”,”30.24”,”25.74”`
    
    `“1918”,”28.66”,”23.57”,”30.68”,”31.11”,”26.77”`
    
2.  Research question, is the annual temperature in India rising?
3.  Variable of interest from the above data set ANNUAL.
4.  Hypothesis: Temperature is rising.
5.  Analyze data from the above data set.
    
    ![](OEBPS/images/2.jpg)
6.  Fit the model.
7.  Hypothesis accepted or rejected.

[Q2: Explain variable and different types of variables?](#toc.xhtml#c01q2a)

*Ans:* Anything which keeps on changing is called variable. Variables are of different type and below are the following:

**Dependant/Outcome:** A variable being affected, for example annual temperature in above example.

**Independent/Predictor:** A variable affecting the outcome for e.g. deforestation, pollution, and so on in above example.

[Q3: Explain Categorical measurement?](#toc.xhtml#c01q3a)

*Ans:* Categorical measurement contains categories i.e. distinct entities. Example of categories of life on earth is plants, animals, and so on.

[Q4: Explain Binary variables?](#toc.xhtml#c01q4a)

*Ans:* Binary variables are those in which only two classes exist, like live or dead male or female on or off.

[Q5: Explain Nominal measurement?](#toc.xhtml#c01q5a)

*Ans:* Nominal measurements are there more than two classes. Such categories can be numbers too.

[Q6: Explain Ordinal variable?](#toc.xhtml#c01q6a)

*Ans:* These are nominal variables which have logical order. Examples include team ranks in cricket or football, merit list of students appearing for grade students.

[Q7: Explain Continuous variables?](#toc.xhtml#c01q7a)

*Ans:* These are variables which can take can any value on the measurement scale example includes pitch of voice which can take any possible value within the range.

[Q8: Explain Discrete variables?](#toc.xhtml#c01q8a)

*Ans:* These are variables which can take fixed values in range. For example, number of customers in a bank.

[Q9: Is it possible to convert continuous values to discrete and vice versa?](#toc.xhtml#c01q9a)

*Ans:* Yes, based upon the motive of study, it is possible to convert discrete values to continuous and vice versa for example, Level of water in tank can take any value in the range and as such a continuous variable.

But we can approximate the same to three different levels like empty, full, or half empty and this now becomes discrete in nature.

[Q10: What are interval variables?](#toc.xhtml#c01q10a)

*Ans:* These are variables which are grouped on interval. Example is age can be divided in range like 10-20, 20-30 and so on and, person with particular age would be placed in one of the above groups. When intervals are equal, they represent difference in equal property being measured.

[Q11: What are ratio variables?](#toc.xhtml#c01q11a)

*Ans:* This is sub type of interval variables where ratio of scales is used for measurement.

For Example Water representation in chemistry is H[2]O which represent two molecules of hydrogen and one molecule of oxygen. Thus, the ratio of elements is 2: 1.

[Q12: What are Univariate and Bivariate variables?](#toc.xhtml#c01q12a)

*Ans:* **Univariate variable:** When the variable under consideration is only one then it is called univariate variable study.

**Bivariate variable:** Involves study of relationship between two variables.

[Q13: What is measurement error?](#toc.xhtml#c01q13a)

*Ans:* The discrepancy between the measured value and actual value in terms of number is called measurement error.

For Example While buying fruits from a vendor in kilograms, if we wanted 1 kilogram of fruits and the vendor’s weighing machine showed 1 kilogram when we brought the same. After checking the same in another machine, if the measured value shows 0.1 kilogram less than expected then this difference is what we call as measurement error.

[Q14: Explain Validity?](#toc.xhtml#c01q14a)

*Ans:* Validity implies whether an instrument measures what it is supposed to measure.

[Q15: Explain Reliability?](#toc.xhtml#c01q15a)

*Ans:* Reliability implies whether the instrument gives consistent result across different conditions.

For example, if we test the same value twice on the same entity then the results from the instrument should remain same if it has to be reliable. Such tests are known as test-retest.

[Q16: What are the different ways to test hypotheses?](#toc.xhtml#c01q16a)

*Ans:* There are two ways in which hypotheses can be tested:

1.  Correlational research 
    *   This is also known as cross-sectional research
    *   This involves observing the natural pattern or occurrence to test
    *   Original occurrences are not manipulated
2.  Experimental research 
    *   We select the variables of interest
    *   Then we manipulate some aspect of the environment
    *   Observe the effect on selected variable

[Q17: Explain the different types of variation?](#toc.xhtml#c01q17a)

*Ans:* There are two types in variation explained as follows:

**Systematic variation:**

*   Introduced by experimenter
*   The participants are tested under different conditions and the difference in condition is introduced by experimenter

For Example to test use of woolen clothes w.r.t. temperature, we can test a group of 20 people, in both hot and cold climate. Thus, the difference introduced here is in terms of temperature only.

**Unsystematic variation:**

*   Introduced by random factors that exist between the experimental conditions.
*   For Example To test use of woolen clothes w.r.t. temperature, we can test a group of 20 people. Of the selected set some might behave differently than expected due to factors like illness and so on.

[Q18: Explain repeated-measures design?](#toc.xhtml#c01q18a)

*Ans:* Same measure is measured under different conditions on same set participants.

The difference in two conditions can be caused by the following:

*   The manipulation/changes that was carried out on the participants
*   Factors that might affect the way in which a participant performs from one time to the next

[Q19: What is independent design?](#toc.xhtml#c01q19a)

*Ans:* Same measure is measured under different conditions on different set of participants.

The differences between the two conditions can be caused by the following:

*   The manipulation/changes that were carried out on the participants
*   Difference in nature or characteristics of participants in each case

[Q20: Explain the role of randomization w.r.t variation?](#toc.xhtml#c01q20a)

*Ans:* By using randomization we can ensure that any variation introduced, is due to changes in the conditions/variables introduced rather than any other unexpected changes during the process. Thus, it helps in removing other sources of systematic variation.

[Q21: Explain various summary measures.](#toc.xhtml#c01q21a)

*Ans:* **Mode:** Represents the value/score which occurs most frequently in data set.

For example: In the values of occurrences of goal in football by players having T-shirt numbers is as follows:

1, 2, 2, 3, 4, 1, 1, 1, 1, 1, 1

If we arrange it in form of table:

![](OEBPS/images/3.jpg)

Thus the mode in above example is 1 which happens to have maximum frequency of 7. This can be easily determined from histogram as shown in the following screenshot:

![](OEBPS/images/4.jpg)

**Median:** This is the middle value which is obtained by ordering the values/scores in ascending order. If the middle value happens to have two numbers then the average is taken as such:

**For example:**

Median of 2, 3, 4, 5, 6 happens to be 4.

Median of 2, 3, 4, 5 happens to be average of 3 and 4 which is 3.5.

Median is least affected by outliers.

**Mean:** Represents mathematical average which is sum of all the elements divided by number of elements.

For example, average strike rate of the batsmen in the game of cricket is the average of strike rates in individual matches.

**Range of scores:** Subtraction between the maximum value and minimum value in range is called range of scores. This indicates dispersion.

**Trimmed mean:** Represents the mean after removing extreme cases from both the end i.e. from minimum and maximum end. Both the minimum and maximum values may represent values which are not normal and hence represent outlier. So, while fining trimmed mean, we specify the percentage of values to be ignored from both the ends. Hence, trimmed mean gives better representation of data excluding outlier.

**Interquartile range (IQR)**

It is a measure of variability, based on dividing a data set into quartiles.

Quartiles are the three values that split the sorted data into four equal parts:

*   Q1 is the *middle* value in the first half of the rank-ordered data set
*   Q2 is the *median* value in the set
*   Q3 is the *middle* value in the second half of the rank-ordered data set

The interquartile range is equal to Q3 minus Q1.

The lower quartile is the median of the lower half of the data.

The upper quartile is the median of the upper half of the data.

**Mean absolute deviation:** Represents the mean of the absolute value of the deviations from the mean.

**Mean absolute deviations from median:** Represented by absolute value of the deviations from the median.

**Outliers:** Represents the value which are not normal or within the range and hence data which is corrupted at the time of capture or due to some other reasons. Since it affects all while finding the mean and other summary values they need to represent this data properly.

[Q22: Explain alternate hypotheses and null hypotheses.](#toc.xhtml#c01q22a)

*Ans:* **Alternative hypotheses:**

*   Also called experimental hypotheses
*   Denoted by H[1]
*   It assumes that effect as per prediction would exist in the conclusion

**Null hypotheses:**

*   Denoted by H[0]
*   It assumes that effect as per prediction would not exist in the conclusion
*   Thus, this represents opposite of alternative hypotheses

[Q23: What is p value?](#toc.xhtml#c01q23a)

*Ans:* It measures the strength of evidence in support of null hypotheses. If this value is less than significance level then null hypotheses is accepted, else rejected.

The range of values that leads the researcher to accept the null hypothesis is called the region of acceptance.

The region other than acceptance is called region of rejection.

[Q24: What happens when null hypotheses is rejected?](#toc.xhtml#c01q24a)

*Ans:* When a null hypothesis is rejected, it becomes Type 1 error. The probability of Type 1 error occurring is called significance level.

[Q25: Explain directional and non-directional hypotheses.](#toc.xhtml#c01q25a)

*Ans:* **Directional hypotheses:**

*   Gives an indication whether the effect which is being studied would grow positively or negatively
*   One tailed test is generally used for such cases

**Non directional hypotheses:**

*   Does not give indication of whether the effect which is being studied would grow positively or negatively
*   Two tailed test is generally used for such cases

[Q26: Explain fit of model?](#toc.xhtml#c01q26a)

*Ans:* It represents the degree till which the determined statistical model represents the data.

Fit of model can represent either under fit, over fit, or perfect fit as such.

A model which is good fit would have low variance between the calculated value and measured value.

[Q27: What is relation between sample and population?](#toc.xhtml#c01q27a)

*Ans:* Samples are subset or part of original data or population. If population is very big hence performing analysis on the whole population as such is not easy. Hence, a subset of population data is taken which is known as sample data.

Whether the sample data is true representation of original data set considered is determined with the help of estimation, confidence interval, and so on.

![](OEBPS/images/5.jpg)

[Q28: What is estimation?](#toc.xhtml#c01q28a)

*Ans:* By using information available from sample, we can make inferences w.r.t. population, which is what is known as estimation. Parameters used are mean, standard deviation, and so on.

[Q29: Explain deviation score?](#toc.xhtml#c01q29a)

*Ans:* This is defined as the difference between actual score/value and mean.

[Q30: Explain variance?](#toc.xhtml#c01q30a)

*Ans:* Variance is the average error between the mean and the measured values.

It indicates the difference between the average value calculated and the observed value as such.

It is an indication of how different individuals in group differ or vary from each other.

The population variance is given:

PV = Σ (Xi - X)2 / N

*   PV is the population variance
*   X is the population mean
*   Xi is the i^(th) element from the population
*   N is the number of elements in the population
    
    The sample variance is given by:
    
    SV = Σ (xi – x)2 / (n – 1)
    
*   SV is the sample variance
*   x is the sample mean
*   xi is the i^(th) element from the sample
*   n is the number of elements in the sample

[Q31: Explain Standard deviation.](#toc.xhtml#c01q31a)

*Ans:* Square root of the variance is also called standard deviation.

This is done to keep the measurement same as original one.

They indicate the nearness of the points measured w.r.t. mean.

Smaller the standard deviation will be more nearer to mean and vice versa.

[Q32: Explain standard error.](#toc.xhtml#c01q32a)

*Ans:* Standard error indicates how well a sample represents the original population. When we break the original population into various small samples, we would like to know the difference between the sample considered and original population. This is represented by standard error.

The smaller the standard error, the closer or true representation of original population.

SE = Σ (sample mean – overall population mean)2 / (number of samples)

[Q33: What is precision?](#toc.xhtml#c01q33a)

*Ans:* It refers to the closeness between estimates from different samples. Thus indicating the opposite of standard error and are inversely related to Standard error.

[Q34: Explain confidence intervals.](#toc.xhtml#c01q34a)

*Ans:* This indicates the boundaries in which the mean value will fall.

It is a range of scores constructed, such that the population mean will fall within.

They are limits constructed such that for a certain percentage of the time the true value of the population mean will fall within these range.

[Q35: Explain confidence level.](#toc.xhtml#c01q35a)

*Ans:* Refers to the percentage of all possible samples that can be expected to include the true population parameter.

[Q36: Explain alpha.](#toc.xhtml#c01q36a)

*Ans:* Alpha is defined as 1-confidence interval. This implies probability that the true value remains outside the confidence interval. If confidence interval is 99% then alpha is 1-99% which is 0.01.

[Q37: Explain Beta.](#toc.xhtml#c01q37a)

*Ans:* The probability of committing Type 2 error is called beta. Type 2 error is one in which a rejected null hypotheses is accepted. The probability of avoiding Type 2 error is called power of test.

[Q38: Explain Accuracy.](#toc.xhtml#c01q38a)

*Ans:* It indicates how much does sample value or parameters matches with the population statistic. If the value of mean of both sample and population are exactly equal then we can say that the sample is fully accurate. If not fully equal then we say that sample is accurate by n limit where n is the difference between sample and population.

[Q39: Explain Bias.](#toc.xhtml#c01q39a)

*Ans:* Bias indicates whether the estimation of sample is over fit or under fit w.r.t. population data. For e.g. if the population mean is 4 and sample mean calculated is 3 then this is under estimate bias. Such estimate in which both sample and population parameter is not equal are called bias estimate.

[Q40: What is central limit theorem?](#toc.xhtml#c01q40a)

*Ans:* It states that the distribution of the mean of any independent, random variable can be approximated to normal if the sample size is large enough.

Generally, the sample size of above 30 or sometimes 40 is taken as reference.

This all ows us to approximate bigger samples to normal distribution without having to take hundreds or thousands of distribution.

Standard Normal distribution is preferred as such because mean is equal to zero and variance is one.

![](OEBPS/images/6.jpg)

[Q41: Explain Absolute value?](#toc.xhtml#c01q41a)

*Ans:* Absolute value is positive value or magnitude irrespective of its initial sign.

[Q42: What is degree of freedom?](#toc.xhtml#c01q42a)

*Ans:* It is equal to the number of independent observations in a sample minus number of population parameters to be estimated.

[Q43: Explain cluster sampling.](#toc.xhtml#c01q43a)

*Ans:* In this method the number of clusters or groups to be formed as pre decided (generally denoted by N) from population data.

![](OEBPS/images/7.jpg)

The number of elements in each cluster is known and each element from population data is assigned to one cluster. For e.g. clustering can be done on attributes like customer state.

Sampling can be further classified as:

*   **One-stage sampling:** All of the elements within selected clusters are included in the sample.
*   **Two-stage sampling:** A subset of elements within selected clusters is randomly selected.

[Q44: Explain Correlation coefficients?](#toc.xhtml#c01q44a)

*Ans:* Correlation indicates the relationship between two variables.

*   As such variables can be positively correlated in which positive change in one variable effect the other variable positively.
*   If variables are negatively correlated the positive change in one variable affects the other variable negatively.
*   The formula for above is given by:
    
    *Correlation co-efficient* = Σ(*xy*)/ *sqrt*\[(Σ*x*²) \* (Σ*y*²)\], where *x* and *y* are variables under consideration.
    
*   The value of correlation co-efficient ranges from -1 to +1.

[Q45: Explain sample space.](#toc.xhtml#c01q45a)

*Ans:* The outcomes of any statistical experiment are denoted by sample space. Any outcome from such space is called sample point. One or more sample point is called event. When events do not have any sample point in common they are known as mutually exclusive event.

[Q46: What is non parametric algorithm?](#toc.xhtml#c01q46a)

*Ans:* Non parametric algorithm does not make any assumptions on data distribution.

[Q47: How can learning be classified?](#toc.xhtml#c01q47a)

*Ans:* Following are the classifications:

*   **Supervised:** 
    *   Data is clearly labeled and the algorithms learn to predict the output from the input data
    *   Offline analysis of data possible
    *   The number of classes are predefined
    *   Accuracy is high
    *   Examples include classification and regression
*   **Unsupervised:** 
    *   Much amount of data is unlabeled and the algorithms learn to inherent structure from the input data
    *   Analysis is on real time data
    *   Number of classes may be unknown
    *   Accuracy ranges from moderate to high
    *   Examples include Clustering and Association
*   **Semi-supervised:** 
    *   A mixture of data having label and no labels forms this one
    *   Can be considered as intermediate to above two

[Q48: What is classification?](#toc.xhtml#c01q48a)

*Ans:* Classification predictive modeling is the task of approximating a mapping function (f) from input variables (X) to discrete output variables (y).

The output variables are often called labels or categories.

The mapping function predicts the class or category for a given observation.

![](OEBPS/images/8.jpg)

[Q49: Explain the steps involved in classification.](#toc.xhtml#c01q49a)

*Ans:*

![](OEBPS/images/9.jpg)

[Q50: What is regression?](#toc.xhtml#c01q50a)

*Ans:* Regression predictive modeling is the task of approximating a mapping function (f) from input variables (X) to a continuous output variable (y).

A continuous output variable can be a real-value, such as an integer or floating point value and be any measures such as size amount, and so on.

Error indicates the difference between actual value and predicted value in case of regression mostly root mean square error is used w.r.t. regression.

![](OEBPS/images/10.jpg)

[Q51: Explain the similarities and differences between Classification and Regression.](#toc.xhtml#c01q51a)

*Ans:* Differences between classification and regression:

![](OEBPS/images/11.jpg)

The similarities are that both try to make prediction based on input values.

[Q52: Explain various terms encountered during classification algorithm.](#toc.xhtml#c01q52a)

*Ans:* Classifier is an algorithm that maps the input data to a specific category.

**Classification model:** After analyzing input data, a classification model is made. The model can take new data as input and predict the class labels/categories.

**Feature:** A feature is an individual measurable property of a phenomenon being observed.

**Binary Classification:** Classification task with two possible outcomes.

**Multi class classification:** Classification with more than two classes is involved. In multi class classification each sample is assigned to one and only one target label.

E.g. an item can be classified as fruit or vegetable not both.

**Multi label classification:** Classification task where each sample is mapped to a set of target labels having more than one class.

Example: A fruit can be classified as sweet and sour both.

[Q53: Explain multi class classification?](#toc.xhtml#c01q53a)

*Ans:* Whenever we have more than two, that is, three or more classes to classify it is called multi class classification. This is also known as a multi nominal classification.

By default, all the algorithms of scipy are multi class.

Some of the strategies involved are:

One vs. rest (One vs. all) trains a single classifier per class. The samples that match with the class are positive, and that which does not match is negative.

One vs. One:

*   We pick a pair of classes from a set of n classes
*   Develop a binary classifier for each selected pair
*   For n classes, all possible combinations of pairs of classes from n are selected
*   Then, for each pair, we develop a binary support vector machine (SVM)

[Q54: Explain multi label classification?](#toc.xhtml#c01q54a)

*Ans:* Whenever we have more than one target variables associated with a problem, we call that as multi label classification.

For example: While classifying fruit, we can classify it as fruit, sweet, red-colored, and so on. As we can clearly see, we have assigned multi labels to the same object.

[Q55: Explain how multi label problem can be solved?](#toc.xhtml#c01q55a)

*Ans:* Following are different ways in which it can be achieved:

**Binary relevance:** In this technique, we treat each label as a separate single class classification problem.

Achieved with the help of skmultilearn.problem\_transform.BinaryRelevance sample:

`fromskmultilearn.problem_transform import BinaryRelevance`

`classifier = BinaryRelevance(any model)`

**Classifier Chains:** A chain of a classifier is formed in which input passed to the first classifier is trained and passed on to the next classifier and so on.

skmultilearn.problem\_transform.ClassifierChain is used for this purpose:

`fromskmultilearn.problem_transform import ClassifierChain`

`classifier = ClassifierChain(model)`

**Label power set:** In this we try to form a single model which would try to solve the multi class model problem.

skmultilearn.problem\_transform.LabelPowerset is used:

`fromskmultilearn.problem_transform import LabelPowerset`

`classifier = LabelPowerset(model)`

[Q56: Explain some important metrics with respect to testing a model?](#toc.xhtml#c01q56a)

*Ans:* True positive indicates that the model was able to predict the positive outcome correctly. It indicates that the model is able to identify the condition when the condition is present.

True negative indicates the model is able to properly predict the negative class. It indicates that the model does not find the condition when the condition is not present.

False positive indicates the model wrongly predicts the positive class. It indicates that the model finds or reports a condition when the condition is not present.

False negative indicates the model wrongly predicts the negative class. It indicates that the model does not report a condition when it is actually present.

All the four conditions are easily indicated by confusion metrics:

![](OEBPS/images/12.jpg)

**Figure 1**

Recall /Sensitivity / True Positive Rate (also known as TPR) ability to determine the condition when the condition is present. It can be found by:

**True Positive/ (True Positive + False Negative)**

**Specificity/ True Negative Rate (also known as TNR):** It indicates the ability to not detect the condition when the condition is not actually present. It can be found by

**True Negative/ (True Negative + False Positive)**

**Precision/ Predictive value positive:** This indicates the number of items correctly identified as positive from total items True Positive/ (True Positive + False Positive)

**False Positive Rate or Type I Error:** Number of items which are wrongly identified as positive from total true negatives

**False Positive/ (False Positive + True Negative)**

**False Negative Rate or Type II Error:** This indicates the number of items wrongly identified as negative out of total true positives

**False Negative/ (False Negative + True Positive)**

[Q57: What is logistic regression?](#toc.xhtml#c01q57a)

*Ans:* Logistic regression also known as logit model is most useful for understanding the influence of several independent variables on a single outcome variable.

Function representation:

*p* = 1/1 + *e*^(–(β0 + β1X1 + β2X2… β*n*X*n*))

It is a kind of predictive analysis.

In this algorithm, the probabilities describing the possible outcomes of a single trial are modeled using a logistic function.

**Disadvantages:**

Assumes all predictors are independent of each other which may not always be true.

Works only when the predicted or output variable is binary.

[Q58: Explain Naïve Bayes.](#toc.xhtml#c01q58a)

*Ans:* Naive Bayes algorithm based on Bayes’ theorem with the assumption of independence between every pair of features. This implies the predictors are independent of each other.

Let **P(c|x)** is the posterior probability of class (c, target) given predictor (**x**, attributes).

**P(c)** is the prior probability of class.

**P(x|c)** is the likelihood which is the probability of predictor given class.

**P(x)** is the prior probability of predictor.

![](OEBPS/images/13.jpg)

**Advantages:**

*   Are extremely fast
*   Training set required is less
*   Performs well for categorical values

**Disadvantages:**

*   Zero frequency problems will occur if some of the categories is missed and as a result the effect of same would be neglected
*   Assumes independence of predictors which is not always true in real world

[Q59: What is Stochastic Gradient Descent?](#toc.xhtml#c01q59a)

*Ans:* Gradient is an effective method to calculate parameters or co-efficient which would cause the cost to minimum. The process involves assuming some value as co-efficient and keeping on calculating the slope and adjusting the co-efficient till a minimum cost is found.

But when the logic is applied on very large data set, it becomes slow. Stochastic Gradient Descent is used for this purpose. In this, calculation is done based on batch instances rather than at the end.

**Advantages:**

*   The algorithm is extremely effective
*   Easy to use

**Disadvantages:**

*   Requires large number of parameters

[Q60: Explain decision tree algorithm.](#toc.xhtml#c01q60a)

*Ans:* Decision tree

Generates the set of rules which depends on attributes or features and based upon classes.

A decision tree is an inverse tree.

The node at the top is called root node and the one without any child is called leaves.

Each part of decision tree represents something which is indicated:

*   Each attribute/feature is represented by node
*   Rule or decision is represented by link
*   Leaf node or node without children represents an the output class

It uses a recursive approach.

The aim is to divide the given data to various groups or classes based upon cost function.

**Classification and Regression trees** are also known as **CART**.

![](OEBPS/images/14.jpg)

**Advantages:**

*   Requires small data preparation
*   Simple to understand and visualize
*   Can handle dataset which can contain numbers
*   Can handle dataset which can contain data in the form of categories

**Disadvantages:**

Outliers can have severe effect on output. Changes in input data does have an important effect on output.

[Q61: What is Gini index?](#toc.xhtml#c01q61a)

*Ans:* The Gini index is the cost function used to evaluate splits in the dataset.

It gives the measure of impurity.

How effective is the split of data based upon features can be easily determined by Gini index.

A Gini score of 0 is ideal expected result while one having half-half probability is not preferred.

![](OEBPS/images/15.jpg)

[Q62: Is Gini index the only means which can be used in decision tree?](#toc.xhtml#c01q62a)

*Ans:* Entrophy is another measure which can be used with decision tree.

[Q63: What is Pruning w.r.t. decision tree?](#toc.xhtml#c01q63a)

*Ans:* Pruning refers to the removal of branches having low importance in terms of classification or regression. The advantages are reduced complexity and reducing over fitting.

The algorithm basically calculates whether removing a particular node causes an impact on prediction precision of the tree.

[Q64: What is random forest?](#toc.xhtml#c01q64a)

*Ans:* Random forest is a meta-estimator that fits a number of decision trees.

It makes use of average to improve the ability to predict the model.

The output from each decision tree is used to finally predict the final model and for doing this, it makes use of majority voting. The data is classified on the class which has majority voting.

To generate this forest, sub samples are used and using sub samples from original data set sub trees are created.

![](OEBPS/images/16.jpg)

**Advantages:** Over fitting is reduced.

**Disadvantages:** It’s slow as real time updates take time.

[Q65: Explain the difference between Random forest and decision tree.](#toc.xhtml#c01q65a)

*Ans:*

![](OEBPS/images/17.jpg)

[Q66: What is overfitting and underfitting?](#toc.xhtml#c01q66a)

*Ans:* Following is the explanation for overfitting and underfitting:

**Overfitting:**

*   Refers to a model which performs very well w.r.t. training set. Such model is able to predict the noise and randomness w.r.t. training set very well but would not perform well when it comes to newly arrived data.
*   Occurs with nonparametric and nonlinear models.

**Underfitting:**

*   Refers to a model that does not perform well both with training set and newly arrived data.
*   An underfitted model would be directly rejected due to its performance via benchmark and accuracy.

[Q67: What are the reasons for under fitting occurrences?](#toc.xhtml#c01q67a)

*Ans:* Under fitting is said to happen when a model is unable to capture or understand the nature of data. This has a direct impact on the accuracy of the model.

The reason for this could be:

*   Less data available to analyze
*   Wrong data
*   Wrong features considered
*   It could be also be due to wrong formed model

The solution to under fitting is to make use of more data and possibly even clean data by removing unwanted features or columns.

Shown below is how under fitting looks when plotted

![](OEBPS/images/18.jpg)

**Figure 2**

[Q68: Does over fitting get affected by noise?](#toc.xhtml#c01q68a)

*Ans:* Over fitting is said to happen when a model gets easily affected by noise or outliers.

The details available in such a case are more, and as a result of this, model gets affected.

Following is the over fitting diagram when plotted:

![](OEBPS/images/19.jpg)

**Figure 3**

**Over fitting can be overcome by:**

*   **Pruning:** Pruning as the name suggests, is cutting. We prune wanted data in addition to nodes that gets easily affected by wrong data.
*   **Cross-Validation:** Sample prediction error is one way that helps on the problem of over fitting. This is generally accomplished with the help of k fold validation. In k fold validation, the original sample data is categorized into k subsets. One of the samples is used for testing, and remaining subsets are used to form the model. The output results which would be collected and then averaged out get the final estimation.
*   **Regularization:** The aim of this is to find out features that align with the objective of the problem and thus removing features that do not contribute to the final output.

[Q69: Explain KNN (K Nearest Neighbour) steps involved, advantage and disadvantage.](#toc.xhtml#c01q69a)

*Ans:* KNN abbreviation is K Nearest Neighbor and is explained down below:

*   Not an eager learner i.e. learns lazily
*   It stores instances of training set.
*   The output is determined by majority vote which is given by k nearest neighbors of each point.

Steps involved are as follows:

1.  Calculate the distance.
2.  Find the closest neighbors.
3.  Vote for labels.

**Advantages:**

*   Much faster.
*   No need to train a model for generalization.
*   Can be used for nonlinear data and regression problems.

**Disadvantages:**

*   Large memory foot print.
*   Performance decreases with increase in number of dimensions.

[Q70: Explain selection bias.](#toc.xhtml#c01q70a)

*Ans:* Selection bias is the bias introduced by the selection of individuals, groups or data for analysis in such a way that proper randomization is not achieved, thereby ensuring that the sample obtained is not representative of the population intended to be analyzed.

They are systematic in nature and produced by the measurement or sampling process.

[Q71: What does selection bias indicate w.r.t. algorithm?](#toc.xhtml#c01q71a)

*Ans:* It indicates that some important variable has been left off or not considered during the algorithm.

[Q72: What is Bootstrap sample?](#toc.xhtml#c01q72a)

*Ans:* Bootstrap sample is used to estimate the distribution. A sample taken with replacement from an observed data set is called bootstrap sample.

![](OEBPS/images/20.jpg)

[Q73: What is Resampling?](#toc.xhtml#c01q73a)

*Ans:* Resampling combines shuffling and bootstrapping.

[Q74: Explain tail.](#toc.xhtml#c01q74a)

*Ans:* Tail is the portion of frequency distribution where extreme values are observed at a very low frequency.

[Q75: Explain the difference between one way test and two way test.](#toc.xhtml#c01q75a)

*Ans:* **One-way test**

It is the hypothesis test where results occur only in one direction.

**Two-way test**

It is the hypothesis test where results occur in two directions.

[Q76: Explain degree of freedom.](#toc.xhtml#c01q76a)

*Ans:* It indicates how much value from given samples are supposed to vary to give the required result.

In a sample of 5 we can say 4 values can vary if the mean is known and 4 values are known.

[Q77: What is predictive modeling?](#toc.xhtml#c01q77a)

*Ans:* Prediction modeling involves building a model which will allow predicting a result/events/behavior whether value of input variables are given. To find out the relationship of input variables and how they affect the output forms the part of regression study.

[Q78: What is time series analysis?](#toc.xhtml#c01q78a)

*Ans:* Analysis which makes use of data in a particular time interval or periods is called time series analysis. Temporal aspects continue in this type of analysis. It may involve observation of a variable at different time instances (time series data) or collecting different data at same point of time (cross sectional data) or a combination of both (pooled data).

[Q79: What is deep learning?](#toc.xhtml#c01q79a)

*Ans:* Deep learning makes it possible to learn by existing examples. The models are generated by computer by using existing examples.

The underlying relationship of data can be determined with the help of neural network

Neural network consists of various nodes or computers interconnected to perform complex/vast computation.

To achieve deep learning we require large amount of labeled data set as well as large computing capability.

Again, deep learning is a part of machine learning where the scale of operation is much higher.

![](OEBPS/images/21.jpg)

[Q80: What is Convolutional Neural Network?](#toc.xhtml#c01q80a)

*Ans:* CNN or ConvNet stands for Convolutional neural network, is a type of learning in which model learns to perform classification of models. It eliminates the need to perform manual feature extraction. It allows this with the help of many layers many of which can be hidden.

[Q81: What are different ways to determine optimal value of clusters?](#toc.xhtml#c01q81a)

*Ans:* **Elbow method:** makes use of sum of squares of each cluster is calculated. The calculated values is then plotted in the form of graph. The best solution is selected based on graph by looking at the slope

**Gap method:** This makes use of gap value which is determined by looking at the variation between clusters for various values of k under null reference

**Silhouette method:** makes use of silhouette average to compute the best performing cluster. The above average is determined by looking at consistency within cluster

[Q82: What are various distance related functions for similarity measures?](#toc.xhtml#c01q82a)

*Ans:* Some of the common ones are Euclidean Distance, Cosine Similarity, Pearson’s Coefficient and Jaccard Similarity.

# [CHAPTER 2](#toc.xhtml#c02)

# [Python Programming Questions](#toc.xhtml#c02)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: Is Python Object oriented?](#toc.xhtml#c02q1a)

*Ans:* Yes, Python is an object oriented programming language since we can deal with classes and objects.

[Q2: Is Python case sensitive?](#toc.xhtml#c02q2a)

*Ans:* Yes

[Q3: What kind of language is Python?](#toc.xhtml#c02q3a)

*Ans:* Python is interpreted programming language.

[Q4: What are different versions of Python?](#toc.xhtml#c02q4a)

*Ans:* Python comes with two major versions 2.x and 3.x.

There are lots of differences between both of them. Following are some of them:

![](OEBPS/images/22.jpg)

[Q5: Explain different implementations of Python?](#toc.xhtml#c02q5a)

*Ans:* Following are different implementations:

*   **CPython:** Reference implementation written in C and native Python.
*   **Stackless Python:** is an addition or improvement over CPython to support micro threads.
*   **PyPy:** is just in time compiler where program is executed on fly rather than compile time.
*   MicroPython and CircuitPython supports Microcontrollers.
*   Jython compiles into Java byte code, which can then be executed by every Java virtual machine implementation.
*   IronPython allows running Python programs on the .NET Common Language Runtime.
*   The RPython language can be compiled to C, Java bytecode, or Common Intermediate Language, and is used to build the PyPy interpreter of Python.
*   Pyjs compiles Python to JavaScript.
*   Cython compiles Python to C and C++.
*   Pythran compiles Python to C++.

[Q6: Is Python loosely typed?](#toc.xhtml#c02q6a)

*Ans:* Python is loosely typed programming language since the same variable can hold different data at different points of time.

For example:

`a = 20 (holds int)`

`a = ”rahul” (holds string now)`

Same variable can be used to store different value or data belonging to different data types.

[Q7: How to start a new block in Python?](#toc.xhtml#c02q7a)

*Ans:* A new block begins when the line is intended by 4 spaces.

[Q8: How to get data type of a particular variable?](#toc.xhtml#c02q8a)

*Ans:* Type function is used in the data type of enclosed variable.

For example:

`>>> a = 10`

`>>> type(a)`

`<class ‘int’>`

[Q9: How many ways can Python program be run?](#toc.xhtml#c02q9a)

*Ans:* Python programs can be run using IDLE which is the integrated IDE or it can also be run from outside using **python.exe** in windows or **python.sh** in UNIX/LINUX based environment.

[Q10: Explain the importance of Pylint and Pychecker.](#toc.xhtml#c02q10a)

*Ans:* Pylint is used to check coding standards w.r.t. modules.

Pychecker is a static analysis tool that helps find out bugs in the source code.

[Q11: Explain Zen of Python.](#toc.xhtml#c02q11a)

*Ans:* Long time Pythoneer Tim Peters succinctly channels the BDFL’s guiding principles for Python’s design into 20 aphorisms, only 19 of which have been written down.

The Zen of Python

Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren’t special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one-- and preferably only one --obvious way to do it.

Although that way may not be obvious at first unless you’re Dutch.

Now is better than never.

Although never is often better than \*right\* now.

If the implementation is hard to explain, it’s a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea – let’s do more of those!

[Q12: How to print Zen in Python?](#toc.xhtml#c02q12a)

*Ans:* We can print Zen of Python by using:

`import this`

`print(this)`

[Q13: Explain Python data types.](#toc.xhtml#c02q13a)

*Ans:*

*   **Integers:** Represent numbers without decimals
*   **Floating point:** Represent number with decimals
*   Complex numbers represents numbers having real and imaginary part
*   String collection of characters
*   Boolean represents the value as True or False

For example:

`a = 5`

`print(a, “belongs to this type”, type(a))`

`a = 2.0`

`print(a, “belongs to this type”, type(a))`

`a = 1+2j`

`print(a, “ has type”,type(a))`

`a = ‘Hello world’`

`print(a,” has type”,type(a))`

`a = True`

`print(a, “ has type”,type(a))`

`a = 1+2j`

`print(“Is complex number?”, isinstance(a,complex))`

**Output:**

5 belongs to this type <class ‘int’>

2.0 belongs to this type <class ‘float’>

(1+2j) has type <class ‘complex’>

Hello world has type <class ‘str’>

True has type <class ‘bool’>

Is complex number? True

[Q14: How can we switch variables in Python?](#toc.xhtml#c02q14a)

*Ans:*

![](OEBPS/images/23.jpg)

[Q15: What is the use of pass statement in Python?](#toc.xhtml#c02q15a)

*Ans:* Pass statement indicates no operation statement. It is generally used to complete the body of classes or functions for alter use.

[Q16: Is Python pass by value or pass by reference?](#toc.xhtml#c02q16a)

*Ans:* Neither of them is used.

Python passes arguments by value where all values are references to actual objects.

[Q17: Does Python supports chained operations?](#toc.xhtml#c02q17a)

*Ans:* Yes, chained operations are supported by Python.

`no = 8`

`if 16 > no > 2:`

`print(“Chained comparison “)`

In the above example, 16 is compared with 8 which is further compared with 2.

[Q18: Explain ALL and ANY.](#toc.xhtml#c02q18a)

*Ans:* ALL returns TRUE, only when all the conditions are TRUE.

Any return TRUE even when one condition is TRUE.

`lst= range(20)`

`print(all(value > 18 for value in lst)) # returns false since range starts with 0`

`lst = range(21,100)`

`print(all(value > 18 for value in lst)) # returns true because range starts with 21`

`print(any(value > 18 for value in lst)) # returns true since 22 is greater than 18 and is true`

`print(any(value < 18 for value in lst)) # return false since not a single value exists which satisfies given`

`#condition`

[Q19: Explain the difference between IS and ==.](#toc.xhtml#c02q19a)

*Ans:* **IS:** True only if 2 variables point to same object.

\==: True if objects which are referred by objects are equal.

![](OEBPS/images/24.jpg)

[Q20: Explain supported collection of data type w.r.t. Python?](#toc.xhtml#c02q20a)

*Ans:* Python supports four collections of data types:

**List:**

*   Stores data in a fashion similar to array in other programming language.
*   It is mutable and item can be added subtracted or deleted.
*   Index starts with zero.
*   \[\] is used to indicate that collection is list.
*   It can be homogenous and heterogeneous i.e. store data of same or different data type.
*   It can contain duplicates.

**Tuples:**

*   Immutable collection i.e. changes to elements are not possible.
*   Indicated by ().
*   Again can be homogenous and heterogeneous i.e. store data of same or different data type.
*   Duplicates can be present.

**Set:**

*   Duplicates are absent in set.
*   It makes use of {} symbol.

**Dictionary:**

*   Stores data in form of key value pair.
*   Indicated by {} with each item having : between
*   Key has to be immutable object.

[Q21: Create a simple number list?](#toc.xhtml#c02q21a)

*Ans: a* = \[1,22,33\]

Above creates a simple list having three values.

![](OEBPS/images/25.jpg)

[Q22: Can you create nested list?](#toc.xhtml#c02q22a)

*Ans:* Following is a nested list of three elements having list again at index 1 and nested list at location 2:

*   *nestedLst = \[“hello”, \[100,101\], \[‘aAA’,\[‘pAA’,’rAA’\]\]\]*
*   *print(‘ Nested list’,nestedLst)*
*   *print(nestedLst\[0\])#prints hello*
*   *print(nestedLst\[2\]\[1\]\[1\])) #prints rAA*

[Q23: Explain CRUD (Create, Update, and Delete) operations from list.](#toc.xhtml#c02q23a)

*Ans:* **Creation:**

`lst = [11,22,33, 44]`

Above statement creates a list with the name lst.

**Empty list creation:**

`lst =[]`

The above statement creates an empty list.

**Adding single element in list:**

`lst.append(55)`

**Adding elements of another list:**

`lst.extend([44,44,33])`

**Concatenate list:**

Concatenate is to join two list.

Following code adds two list and creates a new list c containing elements from both list.

`a =[1,2,3,4]`

`b=[5,65]`

`c = a + b`

`print(c) #Outputs 1,2,3,4,5,65`

**Remove element using value:**

`a =[1,2,3,4]`

`a.remove(3)`

`print(a) #[1,2,4]`

In above code, element with value 3 is removed.

**Delete elements by using index:**

`a =[1,2,3,4]`

`del a[2] #removes element at index 2`

`print(a) #[1,2,4]`

**Clear or Empty a list:**

`a=[1,2,3,4]`

`a.clear()`

`print(a) # prints []`

**Length of list:**

`To print size of list len, function is used.`

`a=[1,2,3,4]`

`print( len(a)) #prints 4`

[Q24: Explain operations in dictionary.](#toc.xhtml#c02q24a)

*Ans:* **Creation:**

`sdict ={1:’one’,2:’two’}`

The above statement creates a dictionary of two items having keys 1 and 2 and corresponding values as one and two respectively.

**Creation of empty**

`sdict={}`

`Add key value pair`

`sdict={}`

`sdict[3] =’three’`

The above statement adds an item in the dictionary with the key as 3 and value as three.

**Add or Update elements from another dictionary**

Addition of new elements from another dictionary.

`dict1 ={1:’one’,2:’two’}`

`dict2 ={5:’five’}`

`dict1.update(dict2)`

`print(dict1) //prints 1:one,2:two,5:five`

Updating of existing element from another dictionary.

`dict1 ={1:’one’,2:’two’,5:’FIVE’}`

`dict2 ={5:’five’}`

`dict1.update(dict2)`

`print(dict1) # 1:one 2: two 5: five`

In the above example the value of key 5 is replaced from FIVE to five.

Thus, update is taken from dict2.

**Clear or Empty dictionary**

`dict1 ={1:’one’,2:’two’,5:’FIVE’}`

`dict1.clear()`

`print(dict1) #prints {}`

`Length of dictionary`

`len(dict) get length of dictionary`

[Q25: Explain operation with tuples.](#toc.xhtml#c02q25a)

*Ans:* **Creation**

`tup = (3, 4)`

Creation of empty tuple:

`tup = ()`

Creation of tuple with single element

This is a bit of challenge because since (1) is taken as number as compared to tuple.

So, to create tuple with one element we make use of the following:

`tup = (1,)`

Adding new elements or removing elements from tuples are not possible since tuples are immutable.

**Length of tuples:**

`len(a)`

[Q26: Explain del?](#toc.xhtml#c02q26a)

*Ans:* The del is used to remove variables from memory.

`a= (1,2,3)`

`print(a) #prints 1 2 3`

`del a`

`print(a) # gives a not defined error`

[Q27: If del can remove variable can it remove tuple variable?](#toc.xhtml#c02q27a)

*Ans:* Yes, **del** can remove tuple variable. A tuple has to be immutable till it lives in memory. While **del** removes the object or variable from memory itself hence **del** can remove tuple.

`a =(1,2)`

`del a`

But if we try to remove an element from tuple using del, it won’t work.

`a =(1,2)`

`del a[2] #TypeError: ‘tuple’ object doesn’t support item deletion`

[Q28: Delete last element in a list.](#toc.xhtml#c02q28a)

*Ans:*

![](OEBPS/images/26.jpg)

[Q29: Predict the output of following code.](#toc.xhtml#c02q29a)

`a =(1,2,3,4)`

`b=(5,65)`

`c = a + b`

`print(c)`

*Ans:* This question is tricky, mainly because it involves tuples which are immutable. So, the general answer given by many is, it would raise an error which is incorrect. The above code adds two tuples to generate new tuple. Existing tuples are untouched which satisfies immutability property. Hence, output is

(1, 2, 3, 4, 5, 65). So, while reading such questions see if the immutability is affected or not. If not then operation would be successful.

[Q30: What do you mean by list comprehension?](#toc.xhtml#c02q30a)

*Ans:* The process of creating a list while performing some operation on the data so that it can be accessed using an iterator is referred to as list comprehension.

[Q31: Explain the preferred way for looping through list?](#toc.xhtml#c02q31a)

*Ans:* The preferred way of looping through list is with the help of enumerate function.

Enumerate function returns index and corresponding value:

![](OEBPS/images/27.jpg)

**Output**

`0 a`

`1 b`

`2 c`

[Q32: Find the reverse of the dictionary?](#toc.xhtml#c02q32a)

*Ans:* Reverse of dictionary means key becomes value and value becomes the key.

It is easily achievable in Python.

![](OEBPS/images/28.jpg)

[Q33: How to sort dictionary by value?](#toc.xhtml#c02q33a)

*Ans:* `import operator as o`

`countryDict ={‘CN’: 4, ‘FR’: 5,’UK’: 1, ‘USA’: 2, ‘IN’: 3, ‘GM’: 6}`

`print(sorted(countryDict.items(), key=o.itemgetter(1)))`

[Q34: What is the use of shuffle function?](#toc.xhtml#c02q34a)

*Ans:* It is used to arrange the values within the list randomly.

[Q35: What is the preferred way to get a value based on key in Python?](#toc.xhtml#c02q35a)

*Ans:* The preferred way to get a value based on key is to use get method with default value.

The default value will be used whenever key is absent in the dictionary.

![](OEBPS/images/29.jpg)

[Q36: Explain alternate way of merging 2 or more dictionaries without using update method?](#toc.xhtml#c02q36a)

*Ans:*

![](OEBPS/images/30.jpg)

[Q37: What is the preferred way of fetching last element/second last and so on from a list?](#toc.xhtml#c02q37a)

*Ans:* Python supports negative indexes on list.

*   \-1 refers to last element
*   \-2 refers to second last element
    
    `l = [1, 2, 3, 4, 5]`
    
    `print(l[-1]) #prints 5`
    
    `print(l[-2]) #prints 4`
    

[Q38: What is the preferred way for reversing a list?](#toc.xhtml#c02q38a)

*Ans:* The preferred way for returning a list is with help of reversed function.

![](OEBPS/images/31.jpg)

The above code will print the following:

`5,4,3,2,1`

[Q39: Explain various string utility functions in Python.](#toc.xhtml#c02q39a)

*Ans:* **capitalize():** Capitalizes the first letter of string.

**isalnum():** Returns true if string has at least 1 character and all characters are alphanumeric and false otherwise.

**isdigit():** Returns true if string contains only digits and false otherwise.

**islower():** Returns true if string has at least 1 cased character and all cased characters are in lowercase and false otherwise.

**isnumeric():** Returns true if a unicode string contains only numeric characters and false otherwise.

**isspace():** Returns true if string contains only whitespace characters and false otherwise.

**isupper():** Returns true if string has at least one cased character and all cased characters are in uppercase and false otherwise.

**lower():** Converts all uppercase letters in string to lowercase.

**lstrip():** Removes all leading whitespace in string.

**max(str):** Returns the max alphabetical character from the string str.

**replace(old, new \[, max\]):** Replaces all occurrences of old in string with new or at most max occurrences if max given.

**strip(\[chars\]):** Performs both lstrip() and rstrip() on string.

**swapcase():** Inverts case for all letters in string.

[Q40: How to check whether two strings are equal.](#toc.xhtml#c02q40a)

*Ans:* == operator can be used to check whether strings are equal or not.

[Q41: Can string use single quote or double quote?](#toc.xhtml#c02q41a)

*Ans:* Both single quote or double quote is allowed but combination of both is not.

[Q42: Explain type conversions on collection types.](#toc.xhtml#c02q42a)

*Ans:*

![](OEBPS/images/32.jpg)

[Q43: Explain set theory operations supported by set data type.](#toc.xhtml#c02q43a)

*Ans:*

![](OEBPS/images/33.jpg)

Sample code for above operations:

`setA = {11,22,33,44,5}`

`setB = {44,22,1}`

`setC = {55}`

`setD = {44,22,1,447}`

`print(‘isdisjoint’,setA.isdisjoint(setC))`

`print(‘Is setB subset of setD ‘,setB.issubset(setD))`

`print(‘Is setD superset of setD ‘,setD.issuperset(setB))`

`print(‘common elements are ‘,setA & setB)`

`print(‘common elements are ‘,setA.`

`intersection(setB))`

`print(‘Elements in A but not in B ‘, setA-setB)`

`print(‘Elements in B but not in A ‘, setB-setA)`

`print(‘Elements in A but not in B ‘, setA.difference(setB))`

`print(‘Elements in B but not in A ‘, setB.difference(setA))`

**Output:**

`isdisjoint True`

`Is setB subset of setD True`

`Is setD superset of setD True`

`common elements are {44, 22}`

`common elements are {44, 22}`

`Elements in A but not in B {33, 11, 5}`

`Elements in B but not in A {1}`

`Elements in A but not in B {33, 11, 5}`

`Elements in B but not in A {1}`

[Q44: Explain frozenset?](#toc.xhtml#c02q44a)

*Ans:* frozenset gives immutability to set i.e. nothing in it can be modified.

[Q45: Explain functions in Python?](#toc.xhtml#c02q45a)

*Ans:* A function is a group of statements intended to do particular task. In Python we can define functions with the help of **def**.

`def fun():`

`print(‘hello’)`

Above creates a function fun which prints **hello** message.

`def fun1(ip):`

`print(‘hello’,ip)`

Above creates a function with the name fun1 which takes parameter ip and prints corresponding hello message with parameters.

`def area(r):`

`return 3.14* r * r`

Above creates a function which returns result with the help of return type.

[Q46: What is a Boolean function?](#toc.xhtml#c02q46a)

*Ans:* Boolean function is one which either returns True or False.

`def isdivisble(num,den):`

`if num%den==0:`

`return True`

`else:`

`return False`

`print(isdivisble(10,2))`

The above functions returns true or false based upon whether the numerator is divisible by denominator.

[Q47: Can we specify data type for arguments as well as return types in Python?](#toc.xhtml#c02q47a)

*Ans:* Recent version of Python has support for type annotations which allows doing the same.

![](OEBPS/images/34.jpg)

[Q48: Explain variable arguments?](#toc.xhtml#c02q48a)

*Ans:* Variable arguments in Python can be achieved with the help of \*args.

![](OEBPS/images/35.jpg)

[Q49: Write a program to find occurrences or count of characters in given word.](#toc.xhtml#c02q49a)

*Ans:*

![](OEBPS/images/36.jpg)

[Q50: What is \*\*kwargs?](#toc.xhtml#c02q50a)

*Ans:* \*\*kwargs is also variable arguments but in the form of dictionary input also known as keyworded, variable-length argument.

![](OEBPS/images/37.jpg)

[Q51: Write a simple Lambda expression?](#toc.xhtml#c02q51a)

*Ans:* `sumlambda = lambda x, y : x + y`

`print(sumlambda(2, 3))`

In the above example, we have defined lambda expression which takes two parameters and performs the addition. The return result is x+ y but no need to return explicitly since it contains single statement only.

[Q52: Lambda forms in Python contain statements? True or False?](#toc.xhtml#c02q52a)

*Ans:* Statement is true as lambdas in Python have to be single line expressions.

[Q53: Explain filter function?](#toc.xhtml#c02q53a)

*Ans:* The filter function is a utility function which can skip values based on some condition.

![](OEBPS/images/38.jpg)

[Q54: Explain steps involved in reading and writing a file?](#toc.xhtml#c02q54a)

*Ans:* In both the case, three steps are involved.

1.  Opening the file.
2.  Reading or writing the file using corresponding functions (read or write).
3.  Closing the file.

Write example:

`a =open(‘hello.txt’,’a’) # opens a file in write mode`

`a.write(‘welcome to files with python’) # writes this line in file`

`a.close() # closes the file`

The above code writes the welcome message to **hello.txt** file.

Read example:

`a =open(‘hello.txt’,’r’) # opens a file in read mode`

`text = a.read() # reads the entire contents of file in memory`

`print(text) #prints the read text`

`a.close()# closes the file`

[Q55: Explain the term “withstatement”?](#toc.xhtml#c02q55a)

*Ans:* The **with** statement would be useful whenever there are related operations block on each other.

`with expression [as variable]:`

`with-block`

In the above statement, we see that **with** block would be used within the context of variable opened with the help of **with** statement.

`with open(‘output.txt’, ‘w’) as f:`

`f.write(‘|Python!’)`

In the above example, the file would be closed as soon as the scope of **with** block gets over the advantage of being not to close the file explicitly using close block.

[Q56: Explain the preferred way of reading a big file?](#toc.xhtml#c02q56a)

*Ans:* ` with open(“sampleread.txt”, “r+”) as ip:`

`for singleLine in ip:`

`print(singleLine)`

The above code opens the file in read mode with the help of with statement. So, as soon as file operations get over, the file would be automatically closed.

Further the above code loads only a single line in memory at a time thus saving memory or making it possible to run, this program even with computer having lower memory footprint.

[Q57: Explain modules in Python.](#toc.xhtml#c02q57a)

*Ans:* Modules both inbuilt and user defined are ways of writing reusable set of code or reusing common set of code.

Python provides set of many inbuilt modules like mathos, sys etc.

To use a module, we will have to import the same with the help of import statement or “from ..import” statement.

[Q58: Explain different ways of importing modules.](#toc.xhtml#c02q58a)

*Ans:* Modules can be imported using import statement or *from ..import* statement.

The difference lies in fact whether we want the entire module or particular part of it.

The *from..import*statement is preferred when we want to import particular module.

`from math import pi`

`print(pi)`

The **import** statement is preferred when the entire module is to be imported.

`import math`

`print(math.pi)`

As you can see in import statement we have to use the module name wherever we want to get variables or methods from modules.

[Q59: Can we create our own module?](#toc.xhtml#c02q59a)

*Ans:* Yes, we can create our own module. Any Python file itself is a module.

Consider for example following **mathop.py** file containing following code:

`def sum(a,b):`

`return a+b`

`def sub(a,b):`

`return (a-b)`

In another file named **usage.py** we can write the following code:

`import mathop`

`print(mathop.sum(99,100))`

`print(mathop.sub(99,100))`

`print(dir(mathop))`

The above code reads from the modules and performs the required operations.

If the files were in different directory, for example, com folder then we could have imported by giving:

`com.modulename`

[Q60: Explain in brief about os module and its corresponding functions.](#toc.xhtml#c02q60a)

*Ans:* os module provides various functions to perform operating system related functions especially w.r.t. file operations.

Following are some of the important functions:

**os.chdir(“D:/pythoneg/intro/pyFolder”):** It is used to change the current working directory.

**os.mkdir(‘pyFolder’):** It is used to create new directory.

**os.remove():** It removes a particular file.

**os.getcwd():** It gets the current working directory.

**os.environ:** It prints environment related details.

**os.system(‘ dir>>1.txt’):** It execute a command line related command. For example, executes dir command which is windows command prompt command, to list directories.

**os.walk(dir):** It lists down sub directory and files within a particular directory.

[Q61: Using os module print the directory structure.](#toc.xhtml#c02q61a)

*Ans:* `import os`

`rootDir = ‘D:/nodejstraining/NodeJSExample/NodeJSExample’`

`for dirName, subdirList, fileList in os.walk(rootDir):`

`print(‘Found directory: %s’ % dirName)`

`for fname in fileList:`

`print(‘\t%s’ % fname)`

In the above example we print the directory structure with the help of **os.walk** function which can list down directory name, sub directory list and file list within a particular directory.

[Q62: Explain dir function.](#toc.xhtml#c02q62a)

*Ans:* The dir function is used to print various functions which are exposed by a module.

For e.g dir(math) prints all the functions within math module.

`import math`

`print(dir(math))`

**Output:**

`[‘__doc__’, ‘__loader__’, ‘__name__’, ‘__package__’, ‘__spec__’, ‘acos’, ‘acosh’, ‘asin’, ‘asinh’, ‘atan’, ‘atan2’, ‘atanh’, ‘ceil’, ‘copysign’, ‘cos’, ‘cosh’, ‘degrees’, ‘e’, ‘erf’, ‘erfc’, ‘exp’, ‘expm1’, ‘fabs’, ‘factorial’, ‘floor’, ‘fmod’, ‘frexp’, ‘fsum’, ‘gamma’, ‘gcd’, ‘hypot’, ‘inf’, ‘isclose’, ‘isfinite’, ‘isinf’, ‘isnan’, ‘ldexp’, ‘lgamma’, ‘log’, ‘log10’, ‘log1p’, ‘log2’, ‘modf’, ‘nan’, ‘pi’, ‘pow’, ‘radians’, ‘sin’, ‘sinh’, ‘sqrt’, ‘tan’, ‘tanh’, ‘tau’, ‘trunc’]`

[Q63: Explain exception handling in Python.](#toc.xhtml#c02q63a)

*Ans:* Exception handling is supported with the help of **try..except** block.

Any statements which can logically cause problems would be placed in **try** block.

In case of exception occurring, corresponding handling is done in except block.

A single try can contain multiple except block.

![](OEBPS/images/39.jpg)

In the above example, we place the code of accepting input from user and type casting the same to **int** within the try block. We have two except block one catching except block and another generic Exception. Based upon the exception raised, the corresponding except block would be called.

To print the complete details of Exception we make use of alias i.e. *except Exception as e :*makesalias of the exception.

In case of no exception, the else block would be executed.

[Q64: How to create user defined exception?](#toc.xhtml#c02q64a)

*Ans:* User defined exceptions are supported in Python.

To create our own exception, we will have to create class with the name of Exception we want, which extends from Exception and correspondingly use it with the help of **raise** statement.

![](OEBPS/images/40.jpg)

[Q65: What is the use of raise statement?](#toc.xhtml#c02q65a)

*Ans:* The **raise** statement is used to generate exception at run time, based upon some condition or constraint imposed.

[Q66: How to create own class in Python? Explain constructors.](#toc.xhtml#c02q66a)

*Ans:* We can create our own class in Python. The constructor of the class is specified with the help of **\_\_init\_\_ method**.

Any function created as a part of class which is a non-static and non-class method, should have **self** as the first argument which represents the object.

Following is the code to create a class with the name Complex which consists of two members **real** and **img** and one display function.

![](OEBPS/images/41.jpg)

[Q67: Is it necessary to have the first argument of class function as self? Can’t we rename it to any other variable?](#toc.xhtml#c02q67a)

*Ans:* The name of the variable can be anything but it always represents the object. The self is the preferred and a general practice naming convention.

[Q68: Explain inheritance in Python.](#toc.xhtml#c02q68a)

*Ans:* Python supports inheritance with classes. A class extending another class needs to use ().

Also, super method needs to be used to call base class constructor and methods.

![](OEBPS/images/42.jpg)

[Q69: How to determine whether a particular class is sub class?](#toc.xhtml#c02q69a)

*Ans:* **issubclass(ChildClass,ParentClass)**

The above function would return true only if the **ChildClass** has inherited from **ParentClass**.

[Q70: Does Python support multiple inheritance?](#toc.xhtml#c02q70a)

*Ans:* Yes, Python supports multiple inheritance.

A particular class can extend from any number of super classes.

class Child(Parent1,Parent2,…..,ParentN):

[Q71: How is diamond problem resolved in case of Python?](#toc.xhtml#c02q71a)

*Ans:* Diamond problem occurs whenever Child class inherits same method with different body from two different parents.

In the case of Python this is resolved by order in which parent is inherited. Parent which is inherited first is given more importance. In the following example we have two parents both having hello method.

![](OEBPS/images/43.jpg)

[Q72: Does Python support private method and variables?](#toc.xhtml#c02q72a)

*Ans:* Private method and variables are supported in Python. Any variable or method having \_\_ becomes private in nature and cannot be accessed directly by using object.

To get their value we will have to use class name reference from the object.

The main aim of these variables and functions is to ensure that the sub classes do not accidentally override them.

[Q73: Can \_\_ be used for other purpose than creating private variables or functions?](#toc.xhtml#c02q73a)

*Ans:* \_\_ has many use cases.

Following are some of them:

1.  Ignoring while assigning values from tuples or list.
    
    `a, _, b = (11, 220,54)`
    
    In the above example, a gets value 11 and b gets 54. The \_\_ is used for ignoring the central value 220.
    
2.  Used to separate numbers *no = 3\_200*. This gives better understanding and readability. The number represented here is 3200.

[Q74: Does Python support abstract classes?](#toc.xhtml#c02q74a)

*Ans:* Python supports abstract classes with the help of module named **abc**.

An abstract class contains abstract functions and cannot be instantiated.

The abc module contains ABC which stands for Abstract base class and abstract method to do necessary things.

![](OEBPS/images/44.jpg)

The classes which extend the above class have to give body to abstract method else even they cannot be instantiated.

[Q75: Differentiate between static methods and class methods in Python.](#toc.xhtml#c02q75a)

*Ans:*

![](OEBPS/images/45.jpg)

[Q76: What are named tuple?](#toc.xhtml#c02q76a)

*Ans:* Named tuple allows us to create classes at run time with attributes.

![](OEBPS/images/46.jpg)

[Q77: How to sort using lamdas?](#toc.xhtml#c02q77a)

*Ans:*

![](OEBPS/images/47.jpg)

[Q78: Explain Generators?](#toc.xhtml#c02q78a)

*Ans:* Generators are used to save memory as they store only some values in memory at a time rather than storing entire dataset in memory.

Generators make use of yield function which stores the previous state to remember.

Generators are invoked using next function.

For example, if we want to process the entire file having million records, generator function would bring only one record at a time in the memory.

![](OEBPS/images/48.jpg)

[Q79: What is generator expression?](#toc.xhtml#c02q79a)

*Ans:* The above generators concept can also be applied to expressions.

![](OEBPS/images/49.jpg)

[Q80: When Python program exits, all the memory is released? Say true or false?](#toc.xhtml#c02q80a)

*Ans:* **The answer is false because** objects that are referenced from global namespaces of Python modules are not always de-allocated when Python exits.

[Q81: Can a function be passed as parameter to another function?](#toc.xhtml#c02q81a)

*Ans:* Yes, it is possible to do the same in Python.

![](OEBPS/images/50.jpg)

[Q82: Can a function be retuned as result from another function?](#toc.xhtml#c02q82a)

*Ans:* Yes, the result of a function can be another function.

![](OEBPS/images/51.jpg)

[Q83: Explain decorator function.](#toc.xhtml#c02q83a)

*Ans:* Decorator function allows performing wrapper around a function. It acts as an interceptor which allows performing pre-processing and post-processing.

![](OEBPS/images/52.jpg)![](OEBPS/images/53.jpg)

[Q84: How can we represent big text in Python?](#toc.xhtml#c02q84a)

*Ans:* Representation of big text is quite simple w.r.t. Python, unlike other programming language.

![](OEBPS/images/54.jpg)

[Q85: What is PEP 8?](#toc.xhtml#c02q85a)

*Ans:* PEP 8 is a coding convention, a set of recommendation, about how to make your Python code more readable. It can be said as globally accepted standards for Python programming.

[Q86: What is anaconda?](#toc.xhtml#c02q86a)

*Ans:* Anaconda is easy to use distribution which comes bundled up with lot of modules used in data science world. It provides a packaged environment to get started easily. It also manages dependencies.

[Q87: How to install external modules?](#toc.xhtml#c02q87a)

*Ans:* External modules can be easily installed with the help of pip tool which comes bundled with Python.

The command to execute is **python –m pip install module name**.

`For e.g. python –m pip install numpy`

In anaconda environment we can install with **conda** command.

`conda install --name environment_name module`

[Q88: What is Jupyter notebook?](#toc.xhtml#c02q88a)

*Ans:* Jupyter Notebook is a web application that allows you to create and share documents that contain:

*   Python code
*   visualizations
*   explanatory text of code

It can be installed as an external module with the help of **pip**.

`python –m pip install jupyter`

Once installed, it can be started by executing command **jupyter notebook**.

The above command will start the web server with notebook opened on web browser.

Notebooks consist of a linear sequence of cells. There are four basic cell types:

*   **Code cells:** Input and output of live code that is run in the kernel
*   **Markdown cells:** Narrative text with embedded LaTeX equations
*   **Heading cells:** 6 levels of hierarchical organization and formatting
*   **Raw cells:** Unformatted text that is included

[Q89: What is pickling and unpickling?](#toc.xhtml#c02q89a)

*Ans:* Pickling is the process of converting from Python format to intermediate string formats which can be then be stored on file.

Unpickling is the process of bringing or loading the stored Python objects back into memory.

[Q90: Explain the importance of setup.py?](#toc.xhtml#c02q90a)

*Ans:* The setup.py allows setting up dependencies easily. While generating one project, it is quite natural to use various libraries. When the same code is shipped to another developer or deployment environment we can make use of setup.py which stores the dependencies on various modules which were used in project.

[Q91: Is it possible to make connections to database using Python?](#toc.xhtml#c02q91a)

*Ans:* Python supports connection to database with Db-Api modules.

The mechanism to query remains same but difference lies in the classes to be imported to suit various databases.

To connect to database (in our case MYSQ L) we use the following code:

![](OEBPS/images/55.jpg)

To fetch data from database table:

![](OEBPS/images/56.jpg)

**Delete example:**

![](OEBPS/images/57.jpg)

**Insert example:**

Insert can be done using **execute** or **executemany**. Difference lies in fact that execute just takes one record while **executemany** takes many records.

![](OEBPS/images/58.jpg)

**Update example:**

![](OEBPS/images/59.jpg)

[Q92: Explain meta programming?](#toc.xhtml#c02q92a)

*Ans:* This is a programming technique in which program itself is treated as data. Such languages do have knowledge of itself, and can change or manipulate itself during run time.

Following are some of the examples of meta programming in Python:

1.  Adding attribute and method to class.
    
    ![](OEBPS/images/60.jpg)
    
    `print(x1.f) # prints 42 the default value.`
    
2.  Creating inheritance chain using type.
    
    The type method can not only be used to get the type of variable but can also be used for meta programming.
    
    Details of overloaded type, is as follows:
    
    ![](OEBPS/images/61.jpg)
    
    For example:
    
    `B = type(B, (A,), dict(f=100))`
    
    The above statement creates class B which inherits from Class A and has field f with value 100.
    
3.  Creating dynamic constructor or linking constructor.
    
    ![](OEBPS/images/62.jpg)
4.  Complete meta class example:
    
    ![](OEBPS/images/63.jpg)

[Q93: Explain Python memory model.](#toc.xhtml#c02q93a)

*Ans:*

![](OEBPS/images/64.jpg)

# [CHAPTER 3](#toc.xhtml#c03)

# [Numpy Interview Questions](#toc.xhtml#c03)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: What is numpy?](#toc.xhtml#c03q1a)

*Ans:* The **numpy** is a module which is responsible for effectively storing and processing the same at a faster rate as compared to normal array. The advantage of **numpy** is support of large number of in built mathematical operations as compared to other programming language. Also, the support to represent n dimensions is also possible with **numpy**.

[Q2: How to install numpy?](#toc.xhtml#c03q2a)

*Ans:* Since **numpy** is an external module it can be installed using **pip**.

`python –m pip install numpy`

[Q3: How to create single dimension numpy array?](#toc.xhtml#c03q3a)

*Ans:*

![](OEBPS/images/65.jpg)

[Q4: Explain different attributes provided by numpy?](#toc.xhtml#c03q4a)

*Ans:* **numpy** provides the following attributes:

**ndim:** As **numpy** provides **n** dimensions, we can get how many dimensions currently the array is having with **ndim**.

**shape:** Indicates number of rows and columns which again can be in different dimensions.

**dtype:** Indicates data type of elements stored in **numpy**.

![](OEBPS/images/66.jpg)

**Output:**

![](OEBPS/images/67.jpg)

[Q5: Explain some utility methods provided by numpy for creating different elements?](#toc.xhtml#c03q5a)

*Ans:* **np.zeros(length)** creates a numpy array at all zeroes occupying the length specified. Can also take rows and columns and create **n** dimensions filled with zeroes.

![](OEBPS/images/68.jpg)

**Output:**

`[[0. 0. 0.]`

`[0. 0. 0.]`

**np.ones:** Can create either single dimension or **n** dimension, all filled with ones.

`ip4 =np.ones((2, 3))`

`print(ip4)`

**Output:**

`[[1. 1. 1.]`

`[1. 1. 1.]]`

**np.eye:** Creates a representation in which diagonal elements are zeroes.

`ip8 =np.eye(3,3)`

`print(ip8)`

**Output:**

`[[1. 0. 0.]`

`[0. 1. 0.]`

`[0. 0. 1.]]`

**np.arange:** Create a single or **n** dimension array in which numbers are populated starting from 0 to the number specified as parameter.

`ip6=np.arange((5))`

`print(ip6)`

**Output:**

`[0 1 2 3 4]`

[Q6: How can we change shape of an object?](#toc.xhtml#c03q6a)

*Ans:* Shape of the object can be changed with shape attribute or reshape method.

**Shape attribute:**

![](OEBPS/images/69.jpg)

**Output:**

`shape (2, 3)`

Before,

`[[1 2 3]`

`[4 5 6]]`

After change,

`[[1 2]`

`[3 4]`

`[5 6]]`

**reshape:**

Allows the dimensions to be specified based on which, the shape can be changed.

`a = np.array([[1,2,3],[4,5,6]])`

`b = a.reshape(3,2)`

`print(‘reshape’, b)`

**Output:**

`[[1 2]`

`[3 4]`

`[5 6]]`

[Q7: Which all data types are supported in Python?](#toc.xhtml#c03q7a)

*Ans:* int8, uint8 i1, u1 int16, uint16 i2, u2 int32, uint32 i4, u4 int64, uint64 : Signed and unsigned 8-bit (1 byte) 16-bit integer types or 32-bit or 64-bit integer types

float16 float32 float64, float128 Floating point with 16.32,64 or 128 bits

complex64, complex128, complex256 Complex numbers represented by two 32, 64, or 128

bool ?: Boolean type storing True and False values

object O : Python object type

string\_ S : Fixed-length string type (1 byte per character)

unicode\_U : Fixed-length unicode type ( platform specific number of bytes)

[Q8: Explain various simple mathematical operations which can be done on numpy?](#toc.xhtml#c03q8a)

*Ans:*

![](OEBPS/images/70.jpg)

[Q9: Explain slicing operation in numpy?](#toc.xhtml#c03q9a)

*Ans:* Slicing means getting data from **numpy** array via row or columns or both.

General slicing on single dimension \[start:end\].

Start element is inclusive end element is exclusive.

![](OEBPS/images/71.jpg)

**Output:**

`[5 6 7]`

For 2 dimensions and more than 2 dimensions, we can specify slicing by row and column indexes. In such case, following is the slicing.

\[rowStart:rowEnd,columnStart:columnEnd\]

*   If **rowStart** is not specified, starts from zero
*   If **rowEnd** is not specified, goes all the way till end
*   If **columnStart** not specified, starts from zero
*   If **columnEnd** not specified, goes till end

For example:

![](OEBPS/images/72.jpg)![](OEBPS/images/73.jpg)

[Q10: Explain Boolean indexing?](#toc.xhtml#c03q10a)

*Ans:* Boolean indexing return True or False based on some condition.

Consider the following numpy array with names.

![](OEBPS/images/74.jpg)

**Output:**

`[False True False False True]`

![](OEBPS/images/75.jpg)

Boolean Indexing can also be masked that is, it can have more than one condition.

`(names == ‘Rahul’) | (names == ‘Raj’)`

The above code returns true for both Rahul and Raj.

[Q11: Perform matrix multiplication using numpy?](#toc.xhtml#c03q11a)

*Ans:* Matrix multiplication can be easily achieved with the help of dot function.

![](OEBPS/images/76.jpg)

[Q12: Explain various functions available with numpy?](#toc.xhtml#c03q12a)

*Ans:* **numpy** supports the following function. The advantage of given functions are that they are applied on all the elements of **numpy** array.

**abs, fabs:** Returns the absolute value element-wise for.

Fabs can be used for non-complex-valued data with additional speed.

**sqrt:** Square root of each element is calculated.

**squar e:** Square of each element is calculated.

**exp:** Exponent ex of each element is calculated.

**log:** log10, log2, log1p Natural logarithm (base e), log base 10, log base 2, and log(1 + x), respectively.

**sign:** sign of each element: 1 (positive), 0 (zero), or -1 (negative) is calculated.

**ceil:** Determines the ceiling of each element,

**floor:** Determines the floor of each element,

**rint:** Round elements to the nearest integer, preserving the dtype.

**modf:** Return fractional and integral parts of given input

**isnan:** Returns true if the value is NaN else false

**isfinite, isinf:** Return true indicating whether each element is finite or infinite, respectively.

**Regular and hyperbolic trigonometric functions**

cos, cosh, sin, sinh, tan, tanh, arccos, arccosh, arcsin, arcsinh, arctan, arctanh

maximum, fmax Element-wise maximum. fmax ignores NaN

minimum, fmin Element-wise minimum. fmin ignores NaN

mod Element-wise modulus (remainder of division)

copysign Copy sign of values in second argument to values in first argument

[Q13: What is broadcast?](#toc.xhtml#c03q13a)

*Ans:* The ability of **numpy** to treat arrays with different dimensions or shape in a uniform way is known as broadcasting.

We can do broadcasting with the help of broadcast method.

![](OEBPS/images/77.jpg)

**Output:**

`(4, 1)`

`(5, 1)`

`(6, 1)`

`(4, 2)`

`(5, 2)`

`(6, 2)`

`(4, 3)`

`(5, 3)`

`(6, 3)`

[Q14: Explain rules of broadcasting.](#toc.xhtml#c03q14a)

*   Whenever two arrays have different dimensions the shape of the one with fewer dimensions is adjusted by padding with ones on its leading (left) side.
*   If there is a difference in the shape of the two arrays, it does not match in any dimension, then dimension is stretched to match the other shape for that array with shape one.
*   An error is raised in case the dimension and sizes disagree, and neither is equal to 1.

[Q15: Explain some statistical measures supported by numpy.](#toc.xhtml#c03q15a)

*Ans*: **amin:** Find the minimum value row wise or column wise

**mean:** Finds the mean value of given dataset

**std:** Finds standard deviation of given dataset

**var:** Finds variance of given dataset

**average:** Finds weighted average in which average is calculated based upon frequency of occurrence of variables

**percentile:** Calculates various percentile intervals mostly around 25,50 and 75%

**ptp:** Calculates peak to peak values in a given dataset

**median:** Calculates median from given dataset

![](OEBPS/images/78.jpg)

`print (np.ptp(a, axis = 0) )`

`print(‘percentile axis 1’)`

`print (np.percentile(a,50, axis = 1) )`

`print(‘percentile axis 0’)`

`print (np.percentile(a,50, axis = 0) )`

`print(‘median’)`

`print (np.median(a, axis = 0) )`

`print(‘mean’)`

`print (np.mean(a, axis = 0) )`

`a = np.array([1,2,3,4])`

`wts = np.array([4,3,2,1])`

`print(‘average’)`

`print (np.average(a,weights = wts) )`

`print(‘std’)`

`print (np.std([1,2,3,4]))`

`print(‘var’)`

`print (np.var([1,2,3,4]))`

**Output:**

`a`

`[[3 7 5]`

`[8 4 3]`

`[2 4 9]]`

`amin 1`

`[3 3 2]`

`amin 0`

`[2 4 3]`

`ptp`

`7`

`ptp axis 0`

`[6 3 6]`

`percentile axis 1`

`[5. 4. 4.]`

`percentile axis 0`

`[3. 4. 5.]`

`median`

`[3. 4. 5.]`

`mean`

`[4.33333333 5. 5.66666667]`

`average`

`2.0`

`std`

`1.118033988749895`

`var`

`1.25`

[Q16: Explain functions available in numpy.linalg.](#toc.xhtml#c03q16a)

*Ans:* **dot(a, b\[, out\]):** Dot product of two arrays.

**linalg.multi\_dot(arrays):** Compute the dot product of two or more arrays in a single function call, while automatically selecting the fastest evaluation order.

**vdot(a, b):** Return the dot product of two vectors.

**inner(a, b):** Inner product of two arrays.

**outer(a, b\[, out\]):** Compute the outer product of two vectors.

**matmul(a, b\[, out\]):** Matrix product of two arrays.

**tensordot(a, b\[, axes\]):** Compute tensor dot product along specified axes for arrays >= 1-D.

**einsum(subscripts, \*operands\[, out, dtype, •\]):** Evaluates the Einstein summation convention on the operands.

**linalg.matrix\_power(M, n):** Raise a square matrix to the (integer) power **n**.

**kron(a, b):** Kronecker product of two arrays.

**linalg.cholesky(a):** Cholesky decomposition.

**linalg.qr(a\[, mode\]):** Compute the qr factorization of a matrix.

**linalg.svd(a\[, full\_matrices, compute\_uv\]):** Singular Value Decomposition.

**Matrix eigenvalues linalg.eig(a):** Compute the eigenvalues and right eigenvectors of a square array.

**linalg.eigh(a\[, UPLO\]):** Return the eigenvalues and eigenvectors of a Hermitian or symmetric matrix.

**linalg.eigvals(a):** Compute the eigenvalues of a general matrix.

**linalg.eigvalsh(a\[, UPLO\]):** Compute the eigenvalues of a Hermitian or real symmetric matrix.

**linalg.norm(x\[, ord, axis, keepdims\]):** Matrix or vector norm.

**linalg.cond(x\[, p\]):** Compute the condition number of a matrix.

**linalg.det(a):** Compute the determinant of an array.

**linalg.matrix\_rank(M\[, tol\]):** Return matrix rank of array using SVD method.

**linalg.slogdet(a):** Compute the sign and (natural) logarithm of the determinant of an array.

**trace(a\[, offset, axis1, axis2, dtype, out\]):** Return the sum along diagonals of the array.

**linalg.solve(a, b):** Solve a linear matrix equation, or system of linear scalar equations.

**linalg.tensorsolve(a, b\[, axes\]):** Solve the tensor equation a x = b for x.

**linalg.lstsq(a, b\[, rcond\]):** Return the least-squares solution to a linear matrix equation.

**linalg.inv(a):** Compute the (multiplicative) inverse of a matrix.

**linalg.pinv(a\[, rcond\]):** Compute the (Moore-Penrose) pseudo-inverse of a matrix.

**linalg.tensorinv(a\[, ind\]):** Compute the ‘inverse’ of an N-dimensional array.

[Q17: How to save numpy data from memory to flat file?](#toc.xhtml#c03q17a)

*Ans:* numpy data can be stored in **npy** format files which are custom serialized or they can be stored in text file.

![](OEBPS/images/79.jpg)

[Q18: What is the use of where and extract?](#toc.xhtml#c03q18a)

*Ans:* Both **where** and **extract** are used to match data based on the conditions.

Where sample:

![](OEBPS/images/80.jpg)

**Extract:** Specifies data and corresponding condition.

![](OEBPS/images/81.jpg)

[Q19: What is the use of ndenumerate?](#toc.xhtml#c03q19a)

*Ans:* **ndenumerate** return the co-ordinates and corresponding values in the co-ordinates.

`A = np.array([[11, 22], [33, 43]])`

`for index, x in np.ndenumerate(a):`

`print(index, x)`

**Output:**

`(0, 0) 11`

`(0, 1) 22`

`(1, 0) 33`

`(1, 1) 43`

[Q20: Explain how can we draw a histogram using numpy?](#toc.xhtml#c03q20a)

*Ans:* Consider the following code:

![](OEBPS/images/82.jpg)

The output given will be as follows:

![](OEBPS/images/83.jpg)

**The print(be) method** in the above prints bin while the hist prints the corresponding count.

# [CHAPTER 4](#toc.xhtml#c04)

# [Pandas Interview Questions](#toc.xhtml#c04)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: What is Pandas?](#toc.xhtml#c04q1a)

*Ans:* Pandas is a third party module which helps in easier representation of data in memory to perform analysis. Pandas help in faster representation and processing of data.

[Q2: How does Pandas represent data?](#toc.xhtml#c04q2a)

*Ans:* Pandas data representation is in similar line to an excel sheet which consists of row and columns.

Columns in Pandas are known as series.

Collection of series is called data frame.

Thus, data frame is the unit of representation

of data which is collection of various series.

Shown is the representation of data frame:

![](OEBPS/images/84.jpg)

[Q3: How to create Series?](#toc.xhtml#c04q3a)

*Ans:*

![](OEBPS/images/85.jpg)

[Q4: How to create Data frame?](#toc.xhtml#c04q4a)

*Ans:* Data frame can be created directly from dictionary or it can also be created by combining various series.

![](OEBPS/images/86.jpg)

**Output:**

![](OEBPS/images/87.jpg)

[Q5: How are missing values represented in data frame?](#toc.xhtml#c04q5a)

*Ans:* Consider the following example:

![](OEBPS/images/88.jpg)

[Q6: Explain the process of creating indexes w.r.t. pandas?](#toc.xhtml#c04q6a)

*Ans:* Indexes can be created using pd.Index function. Indexes support intersection and union.

![](OEBPS/images/89.jpg)

[Q7: Explain various attributes associated with series.](#toc.xhtml#c04q7a)

*Ans:* **axes:** Stands for row.

**dtype:** The data type of the object is given by this attribute.

**empty:** Checks if series is empty.

**ndim:** The dimensions of data are given back.

**size:** Size or number of elements from data are given.

**values:** Gets the values in the form of ndarray.

**head():** The first n rows are returned.

**tail():** The last n rows are returned.

`import pandas as pd`

`import numpy as np`

`s = pd.Series(np.random.randn(4))`

`print(‘series’,s)`

`print(‘axes’,s.axes)`

`print(‘Empty’,s.empty)`

`print(“Dimensions:”)`

`print(s.ndim)`

`print (“Size of the object:”)`

`print (s.size)`

`print (“Underlying data is:”)`

`print (s.values)`

`print (“Top 2 rows:”)`

`print (s.head(2))`

`print (“Last 2 rows:”)`

`print (s.tail(2))`

**Output:**

`eries 0 -0.200094`

`1    0.923716`

`2    -0.565540`

`3    -0.895206`

`dtype: float64`

`axes [RangeIndex(start=0, stop=4, step=1)]`

`Empty False`

`Dimensions:`

`1`

`Size of the object:`

`4`

`Underlying data is:`

`[-0.20009423 0.92371595 -0.56554023 -0.89520616]`

`Top 2 rows:`

`0    -0.200094`

`1    0.923716`

`dtype: float64`

`Last 2 rows:`

`2     -0.565540`

`3     -0.895206`

`dtype: float64`

[Q8: Explain various statistical measures supported by pandas.](#toc.xhtml#c04q8a)

*Ans:* **axes:** Print row index as well as column index.

**sum:** Calculates the sum of all series.

**mean:** Calculates mean of all series.

**median:** Calculates the median of all series.

**std:** Calculates standard deviation.

**count:** Calculates sum of various series.

**cumsum:** Calculates cumulative sum.

**import pandas as pd**

**importnumpy as np**

`d = {‘Name’:pd.Series([‘Raja’, ‘Raju’, ‘Ricky’, ‘Shiv’, ‘Vishnu’, ‘Ramesh’, ‘Mahender’,`

`‘Lious’, ’Salman’, ’SRK’, ’VV’, ’MM’]),`

`‘Age’:pd.Series([25, 26, 25, 23, 30, 29, 23, 34, 40, 30,51, 46]),`

`‘Rating’:pd.Series ([4.23, 3.24, 3.98, 2.56, 3.20, 4.6, 3.8, 3.78, 2.98, 4.80, 4.10, 3.65])}`

![](OEBPS/images/90.jpg)

**Output:**

![](OEBPS/images/p84.jpg)

`axes`

`[RangeIndex(start=0, stop=12, step=1), Index([‘Age’, ‘Name’, ‘Rating’], dtype=’object’)]`

`sum`

`sum Age 382`

`Name`

`RajaRajuRickyShivVishnuRameshMahenderLiousSalm•`

`Rating 44.92`

`dtype: object`

`sum of axis 1 0 29.23`

`1   29.24`

`2   28.98`

`3   25.56`

`4   33.20`

`5   33.60`

`6   26.80`

`7   37.78`

`8   42.98`

`9   34.80`

`10   55.10`

`11   49.65`

`dtype: float64`

`mean Age 31.833333`

`Rating 3.743333`

`dtype: float64`

`std Age 9.232682`

`Rating 0.661628`

`dtype: float64`

`count Age 12`

`Name 12`

`Rating 12`

`dtype: int64`

`median Age 29.50`

`Rating 3.79`

`dtype: float64`

`cumsum Age Name Rating`

`0 25 Raja 4.23`

`1 51 RajaRaju 7.47`

`2 76 RajaRajuRicky 11.45`

`3 99 RajaRajuRickyShiv 14.01`

`4 129 RajaRajuRickyShivVishnu 17.21`

`5 158 RajaRajuRickyShivVishnuRamesh 21.81`

`6 181 RajaRajuRickyShivVishnuRameshMahender 25.61`

`7 215 RajaRajuRickyShivVishnuRameshMahenderLious 29.39`

`8 255 RajaRajuRickyShivVishnuRameshMahenderLiousSalman 32.37`

`9 285 RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 37.17`

`10 336 RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 41.27`

`11 382 RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 44.92`

Most of the measures can be easily made available with the help of describe function.

`import pandas as pd`

`import numpy as np`

`d = {‘Name’:pd.Series ([‘Raja’, ’Raju’, ’Ricky’, ’Shiv’, ’Vishnu’, ’Ramesh’, ’Mahender’,`

`‘Lious’, ’Salman’, ’SRK’, ’VV’, ’MM’]),`

`‘Age’:pd.Series([25.00, 26, 25, 23, 30, 29, 23, 34, 40, 30, 51, 46.00]),`

`‘Rating’:pd.Series ([4.2320, 3.274, 3.98, 2.5628, 3.20,4.600, 3.800, 3.780, 2.980, 4.8000, 4.1000,3.65])}`

`df = pd.DataFrame(d)`

`print (df.describe())`

**Output:**

![](OEBPS/images/p86.jpg)

[Q9: Explain reindexing.](#toc.xhtml#c04q9a)

*Ans:* Reindexing allows us to modify the index of one data frame by keeping the other data frame as reference.

It can also be achieved by passing index and corresponding columns.

![](OEBPS/images/91.jpg)

**Output:**

![](OEBPS/images/p87.jpg)

[Q10: Explain bfill and ffill.](#toc.xhtml#c04q10a)

*Ans:* While reindexing NaN can be introduced .bfill and ffill are used to handle NaN.

![](OEBPS/images/92.jpg)

**Output:**

![](OEBPS/images/p87a.jpg)

**Bfill:**

Fills the value from ahead value into the previous NaN value.

**FFill:**

Fills the value from behind value into the missing NaN value.

**print(df2.reindex\_like(df1,method=’ffill’))**

![](OEBPS/images/93.jpg)

[Q11: What all type of iterations are provided in pandas data frame?](#toc.xhtml#c04q11a)

*Ans:* **iteritems():** To iterate over the (key,value) pairs.

**iterrows():** Iterate over the rows as (index,series) pairs.

**itertuples():** Iterate over the rows as namedtuples.

Consider the following data frame sample:

![](OEBPS/images/p88.jpg)

**forkey,value in df.iteritems():**

**print(key,value)**

**Output:**

![](OEBPS/images/p88a.jpg)

`Name: Age, dtype: int64`

`Name 0 Raja`

`1 Raju`

`2 Ricky`

`3 Shiv`

`4 Vishnu`

`5 Ramesh`

`6 Mahender`

`7 Lious`

`8 Salman`

`9 SRK`

`10 VV`

`11 MM`

`Name: Name, dtype: object`

`Rating 0 4.23`

`1 3.24`

`2 3.98`

`3 2.56`

`4 3.20`

`5 4.60`

`6 3.80`

`7 3.78`

`8 2.98`

`9 4.80`

`10 4.10`

**forrow\_index,row in df.iterrows():**

**print (row\_index,row)**

`0 Age 25`

`Name Raja`

`Rating 4.23`

`Name: 0, dtype: object`

`1 Age 26`

`Name Raju`

`Rating 3.24`

`Name: 1, dtype: object`

`2 Age 25`

`Name Ricky`

`Rating 3.98`

`Name: 2, dtype: object`

`3 Age 23`

`Name Shiv`

`Rating 2.56`

`Name: 3, dtype: object`

`4 Age 30`

`Name Vishnu`

`Rating 3.2`

`Name: 4, dtype: object`

`5 Age 29`

`Name Ramesh`

`Rating 4.6`

`Name: 5, dtype: object`

`6 Age 23`

`Name Mahender`

`Rating 3.8`

`Name: 6, dtype: object`

`7 Age 34`

`Name Lious`

`Rating 3.78`

`Name: 7, dtype: object`

`8 Age 40`

`Name Salman`

`Rating 2.98`

`Name: 8, dtype: object`

`9 Age 30`

`Name SRK`

`Rating 4.8`

`Name: 9, dtype: object`

`10 Age 51`

`Name VV`

`Rating 4.1`

`Name: 10, dtype: object`

`11 Age 46`

`Name MM`

`Rating 3.65`

`Name: 11, dtype: object`

**for row in df.itertuples():**

**print (row)**

**Output:**

`Pandas(Index=0, Age=25, Name=’Raja’, Rating=4.23)`

`Pandas(Index=1, Age=26, Name=’Raju’, Rating=3.24)`

`Pandas(Index=2, Age=25, Name=’Ricky’, Rating=3.98)`

`Pandas(Index=3, Age=23, Name=’Shiv’, Rating=2.56)`

`Pandas(Index=4, Age=30, Name=’Vishnu’, Rating=3.2)`

`Pandas(Index=5, Age=29, Name=’Ramesh’, Rating=4.6)`

`Pandas(Index=6, Age=23, Name=’Mahender’, Rating=3.8)`

`Pandas(Index=7, Age=34, Name=’Lious’, Rating=3.78)`

`Pandas(Index=8, Age=40, Name=’Salman’, Rating=2.98)`

`Pandas(Index=9, Age=30, Name=’SRK’, Rating=4.8)`

`Pandas(Index=10, Age=51, Name=’VV’, Rating=4.1)`

`Pandas(Index=11, Age=46, Name=’MM’, Rating=3.65)`

[Q12: Explain how sorting is supported in pandas?](#toc.xhtml#c04q12a)

*Ans:* **sort\_index:** Allows sorting on index(row) or column wise.

**sort\_values:** Allows sorting on values.

Consider the following data frame:

![](OEBPS/images/p91.jpg)

**sorted\_df = unsorted\_df.sort\_values(by=’col1’)**

**print (sorted\_df)**

![](OEBPS/images/94.jpg)

**sorted\_df=unsorted\_df.sort\_index(axis=1)**

**print (sorted\_df)**

![](OEBPS/images/95.jpg)

**sorted\_df=unsorted\_df.sort\_index()**

**print (sorted\_df)**

![](OEBPS/images/96.jpg)

**sorted\_df=unsorted\_df.sort\_index(ascending=False)**

**print (sorted\_df)**

![](OEBPS/images/p93.jpg)

[Q13: How to override default reload option in pandas?](#toc.xhtml#c04q13a)

*Ans:*

![](OEBPS/images/97.jpg)

[Q14: Explain various slicing options available with pandas?](#toc.xhtml#c04q14a)

*Ans:* Pandas supports the following slicing:

**.loc()** Label based

**.iloc()** Integer based

**.ix()** Both Label and Integer based

Consider the following data frame:

![](OEBPS/images/98.jpg)![](OEBPS/images/99.jpg)![](OEBPS/images/100.jpg)![](OEBPS/images/101.jpg)

**Output:**

![](OEBPS/images/102.jpg)![](OEBPS/images/103.jpg)![](OEBPS/images/104.jpg)![](OEBPS/images/105.jpg)![](OEBPS/images/106.jpg)

[Q15: Explain advanced statistics with pandas.](#toc.xhtml#c04q15a)

*Ans:* Pandas support peak to peak, percentage change, covariance, and correlation on different series in data frame.

![](OEBPS/images/107.jpg)

**Output**

Data frame

![](OEBPS/images/p95.jpg)

**Pct change**

![](OEBPS/images/p96a.jpg)

**Covariance:**

![](OEBPS/images/p96b.jpg)

**Correlation:**

![](OEBPS/images/p96c.jpg)

[Q16: Explain rolling function.](#toc.xhtml#c04q16a)

*Ans:* Rolling function allows us to define window size and perform various operations w.r.t. the window.

Expanding function is an alternative to rolling statistics is to use an expanding window, which yields the value of the statistic with all the data available up to that point in time.

Consider the following data frame:

![](OEBPS/images/p96d.jpg)![](OEBPS/images/108.jpg)![](OEBPS/images/109.jpg)

**print (df.expanding(min\_periods=3).mean())**

![](OEBPS/images/110.jpg)

[Q17: How can we handle NA in pandas?](#toc.xhtml#c04q17a)

*Ans:* We can handle NA in three ways:

1.  dropna: Removes the data where NA is present.
2.  pad
3.  backfill

Consider the following dataframe:

![](OEBPS/images/111.jpg)

dropna output

**print (df.dropna())**

![](OEBPS/images/112.jpg)

**Pad output**

![](OEBPS/images/113.jpg)

**Backfill:**

![](OEBPS/images/114.jpg)

[Q18: Explain group by function.](#toc.xhtml#c04q18a)

*Ans:* **group\_by** allows us to group data based on single or multiple columns.

It is equivalent to *Group by* clause supported in **Structured Query language (SQL)**.

Consider the following dataframe:

![](OEBPS/images/115.jpg)![](OEBPS/images/116.jpg)![](OEBPS/images/117.jpg)

2015

![](OEBPS/images/p99.jpg)

2016

![](OEBPS/images/p99a.jpg)

2017

![](OEBPS/images/p99b.jpg)

[Q19: Explain merge functions w.r.t data frame.](#toc.xhtml#c04q19a)

*Ans:* Data frame in pandas support merge operations in which two related data from diverse data frames can be brought in single view.

Consider the following left and right data frame:

**Left**

![](OEBPS/images/118.jpg)

**Right**

![](OEBPS/images/119.jpg)![](OEBPS/images/120.jpg)![](OEBPS/images/121.jpg)

**Left merge:**

In left merge, all data from left side will come and only those matching from right would come.

![](OEBPS/images/122.jpg)

**Right merge:**

In right merge everything from right side comes and only matching in left would come else it would come as NaN.

**print (‘right’,pd.merge(left, right, on=’id’, how=’right’))**

![](OEBPS/images/123.jpg)

**Outer merge:**

Data from both left and right would come.

**print (‘outer’,pd.merge(left, right, on=’subject\_id’, how=’outer’))**

![](OEBPS/images/124.jpg)

[Q20: Explain concat method.](#toc.xhtml#c04q20a)

*Ans:* **Concat** method allows combining two different data frames either at row level or at column level.

Consider the following left and right data frame:

**Left**

![](OEBPS/images/125.jpg)

**Right**

![](OEBPS/images/126.jpg)

**print (pd.concat(\[left,right\]))**

![](OEBPS/images/127.jpg)

**print (pd.concat(\[left,right\],axis=1))**

![](OEBPS/images/128.jpg)

[Q21: Explain how time related range can be generated in pandas.](#toc.xhtml#c04q21a)

*Ans:* Pandas support generating date range with the help of two functions **date\_range** and **bdate\_range** (business date range).

Periods and frequency can be specified as attribute to the ranges.

**start = pd.datetime(2018, 1, 1)**

**end = pd.datetime(2020, 1, 5)**

**print (pd.bdate\_range(start, end))**

**Output:**

`DatetimeIndex([‘2018-01-01’, ‘2018-01-02’, ‘2018-01-03’, ‘2018-01-04’,`

`‘2018-01-05’, ‘2018-01-08’, ‘2018-01-09’, ‘2018-01-10’,`

`‘2018-01-11’, ‘2018-01-12’,`

`•`

`‘2019-12-23’, ‘2019-12-24’, ‘2019-`

`12-25’, ‘2019-12-26’,`

`‘2019-12-27’, ‘2019-12-30’, ‘2019-12-31’, ‘2020-01-01’,`

`‘2020-01-02’, ‘2020-01-03’],`

`dtype=’datetime64[ns]’, length=525, freq=’B’)`

**print (pd.date\_range(‘1/1/2011’, periods=5,freq=’M’))**

**Output:**

DatetimeIndex(\[‘2011-01-31’, ‘2011-02-28’, ‘2011-03-31’, ‘2011-04-30’,

‘2011-05-31’\],

dtype=’datetime64\[ns\]’, freq=’M’)

[Q22: Explain which all data sources can pandas retrieve values.](#toc.xhtml#c04q22a)

*Ans:* Pandas are capable of reading and writing from variety of sources.

Following are the sources and the corresponding read or write methods:

![](OEBPS/images/129.jpg)![](OEBPS/images/130.jpg)

[Q23: Can you compare some of the functions of R and Python?](#toc.xhtml#c04q23a)

Ans: **Filtering, sampling, and Querying**

![](OEBPS/images/p105.jpg)

**Sorting**

![](OEBPS/images/p105a.jpg)

**Transforming**

![](OEBPS/images/p105b.jpg)

**Aggregate/Grouping functions**

![](OEBPS/images/p105c.jpg)

[Q24: How to print a histogram using pandas?](#toc.xhtml#c04q24a)

*Ans:* Using **series.value\_counts()** functions we can easily generate the value and its corresponding count.

**import pandas as pd**

**importnumpy as np**

**s = pd.Series(\[1,1,100,120,30,40,60,60\])**

**print(s)**

**print(s.value\_counts())**

**Output:**

![](OEBPS/images/p106.jpg)

Histogram

Value count

![](OEBPS/images/p106a.jpg)

# [CHAPTER 5](#toc.xhtml#c05)

# [Scipy and its Applications](#toc.xhtml#c05)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: Explain Scipy library.](#toc.xhtml#c05q1a)

*Ans:* Scipy is used for scientific computation. It is a collection of components and provides eco system for scientific computing.

**Data and computation:**

*   pandas, provides ease of use and very high performing data
*   SymPy, for symbolic mathematics and computer algebra.
*   scikit-image used for image processing.
*   scikit-learn is used for machine learning.
*   h5py and PyTables can both access data stored in the HDF5 format.

[Q2: Explain how can we perform Normality Tests.](#toc.xhtml#c05q2a)

*Ans:* Normality tests are the ones which test for data distribution in the form of Gaussian.

Each of this has following assumptions on input and output:

**Input assumptions:**

*   Observations in each sample are independent and identically distributed.

**Output assumptions:**

*   H0: the sample has a Gaussian distribution
*   H1: the sample does not have a Gaussian distribution

There are three types of test within.

All the three types are supported as a part of scipy.

`import scipy.stats as ss`

`Shapiro-Wilk Test`

`stat, p = ss.shapiro(data)`

`D’Agostino’s K^2 Test`

`stat, p = ss.normaltest(data)`

`Anderson-Darling Test`

`result =ss.anderson(data)`

**Conclusion:** If calculate p value < alpha, we can conclude null hypothesis rejected else it cannot be rejected.

[Q3: Explain how can we perform correlation test?](#toc.xhtml#c05q3a)

*Ans:* **Pearson’s Correlation Coefficient**

Tests have a linear relationship that exist between two data set.

**Input Assumptions:**

All these are made w.r.t Observations

*   They are independent and identically distributed
*   They are normally distributed
*   They have the same variance

**Output assumptions:**

*   H0: the two samples are independent.
*   H1: two samples have dependancy.

`import scipy.stats`

`corr, p = scipy.stats.pearsonr(data1, data2)`

Based on value of corr and p we can conclude whether their relationship between both columns.

Spearman’s Rank Correlation and Kendall’s Rank Correlation.

Both of them have same input and output assumptions.

Tests whether monotonic relationship exists between data set.

**Input assumptions:**

All assumptions are made w.r.t. observations:

*   They are independent and identically distributed
*   They can be ranked

**Output assumptions:**

*   H0: The two samples are independent
*   H1: There is a dependency between the samples

Spearman’s Rank Correlation

`import scipy.stats`

`corr, p = scipy.stats`

`.spearmanr(data1, data2)`

Kendall’s Rank Correlation

`import scipy.stats`

`corr, p = scipy.stats .kendalltau(data1, data2)`

Based on value of corr and p we can conclude whether their relationship between both columns.

Chi-Squared Test

Tests independence between two categorical variables:

**Input assumptions:**

*   Observations are independent.
*   25 or more examples in each cell are required w.r.t. the contingency table.

**Output assumptions:**

*   H0: the two samples are independent.
*   H1: there is a dependency between the samples.

`import scipy.stats`

`stat, p, dof, expected = scipy.stats .chi2_contingency(table)`

[Q4: Explain tests pertaining to Parametric Statistical Hypothesis Tests.](#toc.xhtml#c05q4a)

*Ans:* Comparison of data is done by the following test:

**Student’s t-test**

It tests whether the means of two independent samples are significantly different.

**Input assumptions:**

All assumptions are made w.r.t observation.

*   They are independent and identically distributed (iid).
*   They are normally distributed.
*   They have the same variance.

**Output assumptions:**

*   H0: the means of the samples are equal
*   H1: the means of the sam ples are unequal

`import scipy.stats as ss`

`stat, p = ss.ttest_ind(data1, data2)`

**Paired Student’s t-test**

Tests whether the significant difference exists between the means of two paired samples.

**Input assumptions:**

*   Observations in each sample are independent and identically distributed
*   Observations in each sample are normally distributed
*   Observations in each sample have the same variance
*   Observations across each sample are paired

**Output assumptions:**

*   H0: the means of the samples are equal
*   H1: the means of the samples are unequal

`import scipy.stats`

`stat, p = scipy.stats.ttest_rel(data1, data2)`

**Analysis of Variance Test (ANOVA)**

It tests whether the means of two or more independent samples are significantly different.

**Input assumptions:**

All assumptions are made w.r.t observation:

*   They are independent and identically distributed (iid).
*   They are normally distributed.
*   They have the same variance.

**Output assumptions:**

*   H0: the means of the samples are equal.
*   H1: one or more of the means of the samples are unequal.

`import scipy.stats`

`stat, p = scipy.stats.f_oneway(data1, data2, •)`

[Q5: Explain how to test Nonparametric Statistical Hypothesis Tests.](#toc.xhtml#c05q5a)

*Ans:* Mann-Whitney U Test:

It tests whether the two independent samples are equal or not.

**Input Assumptions:**

All assumptions are made w.r.t observation:

*   They are independent and identically distributed.
*   They can be ranked.

**Output Assumptions:**

*   H0: the distributions of both samples are equal.
*   H1: the distributions of both samples are not equal.

`import scipy.stats`

`stat, p = scipy.stats.mannwhitneyu(data1, data2)`

[Q6: Implement logistic regression in Python?](#toc.xhtml#c05q6a)

*Ans:* sklearn.linear\_model contains LogisticRegression which can be used to represent logistic regression.

![](OEBPS/images/131.jpg)

[Q7: Explain how to implement decision tree in Python.](#toc.xhtml#c05q7a)

*Ans:* sklearn.tree module contains DecisionTreeClassifier which can be used for classification.

![](OEBPS/images/132.jpg)

[Q8: How to implement Random forest in Python?](#toc.xhtml#c05q8a)

*Ans:* sklearn.ensemble module contains RandomForestClassifier which can be used for Random forest generation.

![](OEBPS/images/133.jpg)

For regression type we will use **RandomForestRegressor instead** of **RandomForestClassifier**.

[Q9: How to implement support vector machine in Python?](#toc.xhtml#c05q9a)

*Ans:* **sklearn.svm** module contains SVC which is used for svm.

**SVM for linear model code:**

![](OEBPS/images/134.jpg)

**SVM for non-linear/polynomial mode code**

![](OEBPS/images/135.jpg)

[Q10: Which all kernels are supported by svm in Python?](#toc.xhtml#c05q10a)

*Ans:* Linear, poly, sigmoid (which returns 0 or 1 kernel=’sigmoid’) and gaussian (to support gaussian distribution kernel=rbf)

[Q11: Implement KNN algorithm using Python.](#toc.xhtml#c05q11a)

*Ans:* **sklearn.neighbors** module contains **KNeighborsClassifier** which can be used for classification:

![](OEBPS/images/136.jpg)

[Q12: How to select k in KNN algorithm?](#toc.xhtml#c05q12a)

*Ans:* Finding an optimal value of **k** is very important in order to ensure success of KNN algorithm.

The value of **k** is heavily dependent on the data set.

A very small value of **k** implies noise can have a bigger influence on the result.

A large value of **k** implies more calculations which can be time and memory consuming.

Mostly Odd classes are preferred and **k= sqrt(noOfElements)** is generally taken as an approach to find **k**.

Alternatively, Elbow method can also be used. In the case of Elbow method. In Elbow method we calculate the sum of squared errors (SSE) for different values of k and plot the same.

The one which looks like an elbow is selected as the optimal.

[Q13: How to implement K means in Python?](#toc.xhtml#c05q13a)

*Ans:* We can implement K means with the help of **sklearn.cluster** module which contains KMeans.

![](OEBPS/images/137.jpg)

[Q14: How can accuracy of any model be calculated?](#toc.xhtml#c05q14a)

*Ans:* Following approaches can be used to determine accuracy:

![](OEBPS/images/138.jpg)![](OEBPS/images/139.jpg)![](OEBPS/images/140.jpg)![](OEBPS/images/141.jpg)![](OEBPS/images/142.jpg)![](OEBPS/images/143.jpg)

[Q15: Explain regression metrics.](#toc.xhtml#c05q15a)

*Ans:* Regression metrics gives an indication of how the regression algorithm performed.

Following are the important ones:

![](OEBPS/images/144.jpg)

[Q16: Explain how we can print a decision tree or see the rules of the decision tree?](#toc.xhtml#c05q16a)

*Ans:* export\_text can help us in achieving the above objective.

By passing the created model to the above function, we can get the rules printed out

`fromsklearn.tree.export import export_text`

`dcrules = export_text(model, feature_names=list(train))`

`print(dcrules)`

In the below example, dcrules is the extracted rule after passing the created model to export function:

`|---Age<=0.80`

`||---Salary<=0.65`

`|||---Age<=-0.19`

`||||---class:0`

`|||---Age>-0.19`

`||||---Salary<=-0.06`

`|||||---class:0`

`||||---Salary>-0.06`

`|||||---Salary<=0.40`

`||||||---Salary<=0.03`

`|||||||---class:1`

[Q17: What is the use of boosting techniques?](#toc.xhtml#c05q17a)

*Ans:* Boosting techniques fall under the family of ensemble algorithms. In boosting techniques, a collection of many classifiersthatcan be weak in nature can be combined together to form a new classifier thatcan be strong.

It can be said that in boosting, a series of various classifiers are made progressively in which each classifier tries to solve the reduced the error of earlier one. The end product after this would be a refined classifier with better performance as compared to earlier

![](OEBPS/images/145.jpg)

[Q18: Explain some of the advantages and disadvantages of boosting techniques?](#toc.xhtml#c05q18a)

*Ans:* **Advantages**

*   Since they are ensemble model, the predictions are easy to interpret.
*   Predictions are better are compared to normal classifiers.
*   Over fitting can be handled to a good extent with the help of this technique.

**Disadvantages:**

*   Outliers are important to consider. If not handled properly they can affect the entire model.
*   Other than XGBBoost, most other algorithms are sequential thus limiting the scope of running it in parallel.

[Q19: What is AdaBoost?](#toc.xhtml#c05q19a)

*Ans:* ADA, also known asthe Adaptive Boosting technique, was found by Yoav Freund and Robert Schapire. Since it is a boosting technique, the aim of this would be to find a new strong classifier from the collection of various weak classifiers.

It findsa major application with a decision tree or binary classification.

Generally, the ADA boost makes use of decision stumps, which are decision trees of one level.

The instance in the training data set is weighted. This is very important and distinct as compared to majority voting as the importance of each output is taken as per weightage.

Thus the process is to make use of decision stump to take input variable and predict binary values as classification.

By using the above misclassification rate is calculated.

Using the weighted sum, the stage value is then calculated.

Using this, training weights are updated, which gives more weightage to wrongly predicted instances and less weightage to properly predicted instances.

Weak models thatare added in the sequence are then trained using the weighted training data.

The above process is repeated until the desired accuracy is achieved, or no more improvements are possible.

Shown below is the code for Ada boosting

`fromsklearn.ensemble import AdaBoostClassifier`

`booster = AdaBoostClassifier() n_estimators = 50 (default value)`

`base_estimator = DecisionTreeClassifier (default value) booster.fit(x_train,y_train) booster.predict(x_test)`

[Q20: Explain Gradient boosting?](#toc.xhtml#c05q20a)

*Ans:* Gradient boosting makes use of the trained sequence model. It makes use of Gradient descent function, which calculates the local minimum of a given function. Thus we try to find the local minimum function for loss.

The procedure is to construct new learners whoare also known as the base and which can be correlated with negative gradient descent of the loss function,

`fromsklearn.ensemble import GradientBoostingClassifier #For Classification`

`#from sklearn.ensemble import GradientBoostingRegressor #For Regression`

`classifier = GradientBoostingClassifier(n_estimators, learning_rate, max_depth)`

`classifier.fit(X_train, y_train)`

**n\_estimators:** indicatesthe number of weak learners

**learning\_rate:** determines the contribution of weak learners in the final combination

**max\_depth:** maximum depth of the individual regression estimators. This limits the number of nodes in the tree.

[Q21: Explain XGBoost?](#toc.xhtml#c05q21a)

*Ans:* TheXGBoost, also known as eXtreme Gradient Boostingis a set of algorithms /library for developing fast and high-performance gradient boosting tree models.

It makes use of gradient boosting framework

Some of the features are:

*   Automatic handling of missing data values.
*   Parallelization of tree construction is possible
*   Makes use of the second partial derivatives of the loss function. This is the major difference as compared to other gradient algorithms. While other algorithms makes use of loss function which is first order derivative, XGB makes use of second order derivative which also gives the direction of the gradient
*   Advanced regularization techniques are used.

Sample snippet

`import pandas as pd`

`fromxgboost import XGBClassifier`

`fromsklearn.metrics import accuracy_score`

`model = XGBClassifier()`

`model.fit(x,y)`

`predict_train = model.predict(test_x)`

`accuracy_train = accuracy_score(train_y,predict_train)`

[Q22: Explain the differences/similarities between bagging and Boosting?](#toc.xhtml#c05q22a)

*Ans:* **Similarities:**

*   Both belong to the method of algorithms which are known as ensemble i.e. which generates gets 1 learner from N classifiers
*   Both work by dividing the original dataset into smaller units
*   Average of outputs are taken into consideration
*   Both try to increase performance

Following table shows the differences:

![](OEBPS/images/p119.jpg)

[Q23: Write a small snippet to perform operation with neural networks using tensorflow and keras?](#toc.xhtml#c05q23a)

*Ans:*

![](OEBPS/images/146.jpg)

# [CHAPTER 6](#toc.xhtml#c06)

# [Matplotlib Samples to Remember](#toc.xhtml#c06)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: Explain how to draw bar plot.](#toc.xhtml#c06q1a)

*Ans:*

![](OEBPS/images/149.jpg)![](OEBPS/images/150.jpg)

[Q2: How to draw histogram?](#toc.xhtml#c06q2a)

*Ans:*

![](OEBPS/images/151.jpg)![](OEBPS/images/152.jpg)

[Q3: How to draw line chart?](#toc.xhtml#c06q3a)

*Ans:* **importnumpy as np**

**frommatplotlib import pyplot as plt**

**frommatplotlib.backends.backend\_pdf import PdfPages**

![](OEBPS/images/153.jpg)![](OEBPS/images/154.jpg)

[Q4: Draw Pie chart.](#toc.xhtml#c06q4a)

*Ans:*

![](OEBPS/images/155.jpg)![](OEBPS/images/156.jpg)

[Q5: How to get the equation of the line printed line plot?](#toc.xhtml#c06q5a)

*Ans:* Using following snippet of code same can be achieved

`plt.title(‘$y= slope * x+ intercept))`

![](OEBPS/images/157.jpg)

[Q6: Draw scatter plot.](#toc.xhtml#c06q6a)

*Ans:*

![](OEBPS/images/158.jpg)![](OEBPS/images/159.jpg)

# [CHAPTER 7](#toc.xhtml#c07)

# [Statistics with Excel Sheet](#toc.xhtml#c07)

***Note:* \[Q: Question Number and Ans: Answer\]**

[Q1: Does Excel has any support for statistics?](#toc.xhtml#c07q1a)

*Ans:* Yes, Excel sheet do provide a lot of support for statistics with few add-ins like *Analysis Tool pack*. In order to enable this analysis tool pack, select excel options and the go to Add-ins option and enable *AnalysisToolPak*.

![](OEBPS/images/160.jpg)

Once done, the data analysis option is enabled in Data tab of excel, it can be seen under the **Data** tab as shown in the image down below:

![](OEBPS/images/161.jpg)

[Q2: Find correlation using Excel.](#toc.xhtml#c07q2a)

*Ans:* Correlation can be easily found with the help of **CORREL** function of Analysis Toolpak.

Select **Data Analysis** → Select **correlation** as an option.

![](OEBPS/images/162.jpg)

After selecting **Correlation** from Data Analysis select the corresponding input field and set output values to be displayed on the excel sheet by setting **Output Range** available under **Output options**,

![](OEBPS/images/163.jpg)

and after **OK** is clicked, the result for same of Covariance can be found on excel sheet.

[Q3: How to get Histogram in excel?](#toc.xhtml#c07q3a)

*Ans:* To get Histogram in excel we generally require values and corresponding bins. Bins represent the range in which frequency is calculated.

From **Data Analysis** → select **Histogram** function → we can select input range and bins range

![](OEBPS/images/164.jpg)![](OEBPS/images/165.jpg)![](OEBPS/images/166.jpg)

[Q4: Explain how to get Descriptive Statistics using Excel.](#toc.xhtml#c07q4a)

*Ans:* To get **Descriptive Statistics** select **Data Analysis** ⇒ Select **Descriptive Analysis** ⇒ then select different statistics you prefer.

![](OEBPS/images/167.jpg)![](OEBPS/images/168.jpg)![](OEBPS/images/169.jpg)

[Q5: Explain how to perform Anova in excel?](#toc.xhtml#c07q5a)

*Ans:* To perform **Anova** select **Data Analysis** ⇒ **Anova: Single factor**

![](OEBPS/images/170.jpg)

Select corresponding input and output values.

![](OEBPS/images/171.jpg)![](OEBPS/images/172.jpg)

Based upon the value of F and F critical, we can conclude whether null hypothesis is rejected or accepted.

[Q6: Explain how to perform Rank and Percentile in excel.](#toc.xhtml#c07q6a)

*Ans:* From **Data Analysis** → select **Rank and Percentile**

![](OEBPS/images/173.jpg)

Select the input and output range to get the answer:

![](OEBPS/images/174.jpg)