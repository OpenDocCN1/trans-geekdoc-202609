
# 28 CHAPTER 2 INTERPRETABILITY

additional questions, otherwise the probability of passing depends on the student's level of preparation and the resulting probability of answering the questions correctly.

Scenario 1: The teacher usually asks the students additional questions (e.g. 95 out of 100 times). A student who did not study (10% chance to pass the question) was not one of the lucky ones and gets additional questions that he fails to answer correctly. Why did the student fail the course? I would say that it was the student's fault to not study.

Scenario 2: The teacher rarely asks additional questions (e.g. 2 out of 100 times). For a student who has not studied for the questions, we would predict a high probability of passing the course because questions are unlikely. Of course, one of the students did not prepare for the questions, which gives him a 10% chance of passing them. He is unlucky and the teacher asks additional questions that the student cannot answer and fails the course. What is the reason for the failure? I would argue that, the better explanation is “because" the teacher tested the student. It was unlikely that the teacher would test, so the teacher behaved abnormally.

What it means for interpretable machine learning: If one of the features for a prediction was abnormal in any sense (like a rare of a categorical feature) and the feature influenced the prediction, it should be included in an explanation, even if ‘normal’ features have the same influence on the prediction as others. An abnormal feature in our price prediction example might be that a more expensive house has two balconies. Even if some attribution method shows that the balconies contribute to the price difference as the above average house size, the neighborhood or the recent renovation, the abnormal feature “two balconies” might be the best explanation for why the house is expensive.

Explanations are truthful. Good explanations prove to be true in reality (i.e. in other situations). But disturbingly, this seems to be more important than truthfulness. An explanation that selects one or two possible cases rarely covers the entire list of relevant cases. Selectivity omit part of the truth. It is not true that one or two factors, for example, have caused a stock market crash, but the truth is that there are millions of cases that influence people to act in such a way that the crash was caused.

What it means for interpretable machine learning: The explanation should predict the event as truthfully, which in machine learning is sometimes called fidelity. If we say that a balcony increases the price of a house, then that should also apply to other houses (or at least to similar houses). For humans, fidelity of an explanation is not as important as its selectivity, and its social aspect.

What it means for interpretable machine learning: Good explanations are consistent with prior beliefs. This is difficult to integrate into machine learning and would probably drastically compromise predictive performance. Our prior belief for the effect of house size on predicted price is that the larger the house, the higher the price. Let us assume that a model also shows a negative effect of house size on the predicted price for a few houses. The model has learned this because it improves predictive performance (due to some complex interactions), but this behavior strongly contradicts our prior beliefs. You can enforce monotonicity constraints (a feature can only affect the prediction in one direction) or use something like a linear model that has this property.

**Good explanations are general and probable.** A cause that can explain many events is very general and could be considered a good explanation. Note that this contradicts the claim that abnormal causes make good explanations. As I see it, abnormal causes beat general causes. Abnormal cases are by definition rare in the given scenario. In the absence of an abnormal event, a general explanation is considered a good explanation. Also remember that people tend to misjudge probabilities of joint events. (Joe is a librarian. Is he likely a shy person who likes to read books?) A good example is “The house is expensive because it is big”, which is a very general, good explanation of why houses are expensive or cheap.

**What it means for interpretable machine learning:** Generality can easily be measured by the feature's support, which is the number of instances to which the explanation applies divided by the total number of instances.

## 2.6 HUMAN-FRIENDLY EXPLANATIONS

## 3 Datasets

Throughout the book, all models and techniques are applied to real datasets that are freely available online. We will use different datasets for different tasks: Classification, regression and text classification.

### 3.1 Bike Rentals (Regression)

This dataset contains daily counts of rented bicycles from the bicycle rental company Capital-Bikeshhare¹ in Washington D.C., along with weather and seasonal information. The data was kindly made openly available by Capital-Bikeshhare. Fanee-T and Gama (2013)² added weather data and season information. The goal is to predict how many bikes will be rented depending on the weather and day. The data can be downloaded from the UCI Machine Learning Repository³.

New features were added to the dataset and not all original features were used for the examples in this book. Here is the list of features that used:

- Count of bicycles including both casual and registered users. The count is used as the target in the regression.
- The season, spring, summer, fall or winter.
- Indicator whether the day was a holiday or not.
- The year, 2011 or 2012.
- Number of days since the 01.01.2011 (the first day in the dataset).
- Relative humidity in percent (0 to 100).
- Wind speed in km per hour.
- Temperature in degrees Celsius.
- Indicator whether the day was a working day or weekend.
- The weather situation.
- Clear, few clouds, partly cloudy, broken clouds, scattered clouds, light rain, heavy rain, ice pellets, thunderstorm, mist clouds.
- Trend over time.

### Table 3.1: Sample of comments from the YouTube

| CONTENT | CLASS |
|---|---|
| Huh, anyway check out [tube]: koboshi02 | 1 |
| Guys check out my new channel: THIS IS | 1 |
| THE MONKEYS!!! I'm the monkey in the white shirt,please leave a comment and please subscribe!!! murdev.com | 1 |
| me shaking my sexy ass on my channel enjoy kidsmediausa | 1 |
| Hey, check out my new website! This site is about kids. | 1 |
| Subscribe to me i turned it mute as i came on | 0 |
| You should check my channel for Funny VIDEOS and tell me what I do! | 1 |

### 3.2 YouTube Comments (Text Classification)

As an example for text classification we work with 1956 comments from 5 different YouTube videos. The authors who used this dataset in an article on spam classification made the data freely available⁶ (Alberto, Loch, and Almeida (2015)).

The comments were collected via the YouTube API from the ten most viewed videos on YouTube in the first half of 2015. All 5 are music videos. One of them is “Gangnam Style” by Korean artist Psy. The other artists were Katy Perry, LIMFao, Eminak, and Shakira.

The comments were manually labeled as spam or legitimate. Spam was coded with a “1” and legitimate with a “0”.

> ¹²Nickerson, Raymond S. “Confirmation Bias: A ubiquitous phenomenon in many guises.” Review of General Psychology 2 (2). Educational Publishing: 175, (1998).
> ¹https://www.capitalbikhare.com
> ²Fanee-T, Hadi, and Joao. "Event labeling combining ensemble detectors." Progress in Artificial Intelligence. Springer Berlin, 13–45. doi:10.1007/s13748-013-0040
> ³http://archive.uci.edu/datasets/Bike+Sharing-Dataset
> ⁴https://github.com/christoph/interpretable-ml-book/blob/master/R/bike-sharing-dataset.R
> ⁵https://github.com/christoph/interpretable-ml-book/blob/master/data/bike.RData
> ⁶https://archive.ics.uci.edu/datasets/YouTube+Spam+Collection
> ⁷Alberto, Túlio C, Johannes V Lochter, and João Almeida. “Tubespam: spam filtering on YouTube.” In Machine Learning and Applications (Icmla), ieec 14th International Conference on, 138–43. IEEE. (2015).
