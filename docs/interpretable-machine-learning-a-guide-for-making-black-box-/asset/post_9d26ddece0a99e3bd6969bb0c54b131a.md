
Psychology 2 (2). Educational Publishing Foundation: 175. (1998).

## Chapter 3 Datasets

Throughout the book, all models and techniques are applied to real datasets that are freely available online. We will use different datasets for different tasks: Classification, regression and text classification.

### 3.1 Bike Rentals (Regression)

This dataset contains daily counts of rented bicycles from the bicycle rental company Capital-Bikeshare in Washington D.C., along with weather and seasonal information. The data was kindly made openly available by Capital-Bikeshare. Fanaee-T and Gama (2013)13 added weather data and season information. The goal is to predict how many bikes will be rented depending on the weather and the day. The data can be downloaded from the UCI Machine Learning Repository.

New features were added to the dataset and not all original features were used for the examples in this book. Here is the list of features that were used:

- Count of bicycles including both casual and registered users. The count is used as the target in the regression task.
- The season, either spring, summer, fall or winter.
- Indicator whether the day was a holiday or not.
- The year, either 2011 or 2012.
- Number of days since the 01.01.2011 (the first day in the dataset). This feature was introduced to take account of the trend over time.
- Indicator whether the day was a working day or weekend.
- The weather situation on that day. One of:
  - clear, few clouds, partly cloudy, cloudy
  - mist + clouds, mist + broken clouds, mist + few clouds, mist
  - light snow, light rain + thunderstorm + scattered clouds, light rain + scattered clouds
  - heavy rain + ice pellets + thunderstorm + mist, snow + mist
- Temperature in degrees Celsius.
- Relative humidity in percent (0 to 100).
- Wind speed in km per hour.

For the examples in this book, the data has been slightly processed. You can find the processing R-script in the book's Github repository together with the final RData file.

13. Fanaee-T, Hadi, and Joao Gama. "Event labeling combining ensemble detectors and background knowledge." Progress in Artificial Intelligence. Springer Berlin Heidelberg, 1–15. doi:10.1007/s13748-013-0040-3. (2013).

### 3.2 YouTube Spam Comments (Text Classification)

As an example for text classification we work with 1956 comments from 5 different YouTube videos. Thankfully, the authors who used this dataset in an article on spam classification made the data freely available (Alberto, Lochter, and Almeida (2015)14).

The comments were collected via the YouTube API from five of the ten most viewed videos on YouTube in the first half of 2015. All 5 are music videos. One of them is "Gangnam Style" by Korean artist Psy. The other artists were Katy Perry, LMFAO, Eminem, and Shakira.

Check out some of the comments. The comments were manually labeled as spam or legitimate. Spam was coded with a "1" and legitimate comments with a "0".

| CONTENT | CLASS |
|---|---|
| Huh, anyway check out this youtube channel: kobyoshi02 | 1 |
| Hey guys check out my new channel and our first vid THIS IS US THE MONKEYS!!! I'm the monkey in the white shirt,please leave a like comment and please subscribe!!!! | 1 |
| just for test I have to say murdev.com | 1 |
| me shaking my sexy ass on my channel enjoy ^_^ | 1 |
| watch?v=vtRgGvGtWQ Check this out . | 1 |
| Hey, check out my new website!! This site is about kids stuff. kidsmediausa.com | 1 |
| Subscribe to my channel | 1 |
| i turned it on mute as soon as I came on i just wanted to check the views... | 0 |
| You should check my channel for Funny VIDEOS!! | 1 |
| and u should check my channel and tell me what I should do next! | 1 |
| You can also go to YouTube and take a look at the comment section. But please do not get caught in YouTube hell and end up watching videos of monkeys stealing and drinking cocktails from tourists on the beach. The Google Spam detector has also probably changed a lot since 2015. | |

Watch the view-record breaking video "Gangnam Style" here.

If you want to play around with the data, you can find the RData file along with the R-script with some convenience functions in the book's Github repository.

14. Alberto, Túlio C, Johannes V Lochter, and Tiago A Almeida. "Tubespam: comment spam filtering on YouTube." In Machine Learning and Applications (ICMLA), IEEE 14th International Conference on, 138–143. IEEE. (2015).

### 3.3 Risk Factors for Cervical Cancer (Classification)

The cervical cancer dataset contains indicators and risk factors for predicting whether a woman will get cervical cancer. The features include demographic data (such as age), lifestyle, and medical history. The data can be downloaded from the UCI Machine Learning repository and is described by Fernandes, Cardoso, and Fernandes (2017)15.

The subset of data features used in the book's examples are:

- Age in years
- Number of sexual partners
- First sexual intercourse (age in years)
- Number of pregnancies
- Smoking yes or no
- Smoking (in years)
- Hormonal contraceptives yes or no
- Hormonal contraceptives (in years)
- Intrauterine device yes or no (IUD)
- Number of years with an intrauterine device (IUD)
- Has patient ever had a sexually transmitted disease (STD) yes or no
- Number of STD diagnoses
- Time since first STD diagnosis
- Time since last STD diagnosis
- The biopsy results "Healthy" or "Cancer". Target outcome.

The biopsy serves as the gold standard for diagnosing cervical cancer. For the examples in this book, the biopsy outcome was used as the target. Missing values for each column were imputed by the mode (most frequent value), which is probably a bad solution, since the true answer could be correlated with the probability that a value is missing. There is probably a bias because the questions are of a very private nature. But this is not a book about missing data imputation, so the mode imputation will have to suffice for the examples.

To reproduce the examples of this book with this dataset, find the preprocessing R-script and the final RData file in the book's Github repository.

15. Fernandes, Kelwin, Jaime S Cardoso, and Jessica Fernandes. "Transfer learning with partial observability applied to cervical cancer screening." In Iberian Conference on Pattern Recognition and Image Analysis, 243–50. Springer. (2017).

## Chapter 4 Interpretable Models

The easiest way to achieve interpretability is to use only a subset of algorithms that create interpretable models. Linear regression, logistic regression and the decision tree are commonly used interpretable models.

In the following chapters we will talk about these models. Not in detail, only the basics, because there is already a ton of books, videos, tutorials, papers and more material available. We will focus on how to interpret the models. The book discusses linear regression, logistic regression, other linear regression extensions, decision trees, decision rules and the RuleFit algorithm in more detail. It also lists other interpretable models.

All interpretable models explained in this book are interpretable on a modular level, with the exception of the k-nearest neighbors method. The following table gives an overview of the interpretable model types and their properties. A model is linear if the association between features and target is modelled linearly. A model with monotonicity constraints ensures that the relationship between a feature and the target outcome always goes in the same direction over the entire range of the feature: An increase in the feature value either always leads to an increase or always to a decrease in the target outcome. Monotonicity is useful for the interpretation of a model because it makes it easier to understand a relationship. Some models can automatically include interactions between features to predict the target outcome. You can include interactions in any type of model by manually creating interaction features. Interactions can improve predictive performance, but too many or too complex interactions can hurt interpretability. Some models handle only regression, some only classification, and still others both.

From this table, you can select a suitable interpretable model for your task, either regression (regr) or classification (class):

| Algorithm | Linear | Monotone | Interaction | Task |
|---|---|---|---|---|
| Linear regression | Yes | Yes | No | regr |
| Logistic regression | No | Yes | No | class |
| Decision trees | No | Some | Yes | class, regr |
| RuleFit | Yes | No | Yes | class, regr |
| Naive Bayes | No | Yes | No | class |
| k-nearest neighbors | No | No | No | class, regr |
