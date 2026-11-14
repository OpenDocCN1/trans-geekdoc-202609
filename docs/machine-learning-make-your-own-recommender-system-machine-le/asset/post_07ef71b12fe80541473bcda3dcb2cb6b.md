

```python
import pandas as pd
from sklearn.naive_bayes import GaussianNB
df = pd.read_csv('~/Downloads/advertising.csv')
df.head()
```

| | Daily Time Spent on Site | Age | Area Income | Daily Internet Usage | Ad Topic Line | City | Male | Country | Timestamp | Clicked on Ad |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 68.95 | 35 | 61833.90 | 256.09 | Cloned 8th generation orchestration | Wightburgh | 0 | Tunisia | 2016-03-27 00:53:11 | 0 |
| 1 | 80.23 | 31 | 68441.85 | 193.77 | Monitored national standardization | West Jodi | 1 | Nauru | 2016-04-04 01:39:02 | 0 |
| 2 | 69.47 | 26 | 59765.94 | 236.50 | Organic bottom-line service-desk | Devildton | 0 | San Marino | 2016-03-13 20:35:42 | 0 |
| 3 | 74.15 | 29 | 54806.18 | 245.09 | Triple-buffered regional time-frame | West Terrifurt | 1 | Italy | 2016-01-10 02:31:19 | 0 |
| 4 | 60.37 | 35 | 73969.98 | 225.50 | Robust logistical utilization | South Manuel | 0 | Iceland | 2016-06-09 03:38:18 | 0 |

## Step 3

Next, let's remove discrete variables from the dataset using the delete method and inputting the names of the columns we wish to remove. (Our chosen algorithm only accepts continuous variables as independent variables.[20])

```python
del df['Ad Topic Line']
del df['Timestamp']
del df['City']
del df['Country']
del df['Male']
```

## Step 4

Let's now assign our X (independent variables) values and y value (dependent variable). The y variable is “Clicked On Ad” and the X variables consist of the remaining variables (Age, Area Income, Daily Internet Usage, and Daily Time Spent on Site).
Please note that in data science the lower case “y” and upper case “X” are standard conventions for denoting dependent variable and independent variables respectively.

```python
#Assign all columns in the dataset as X variables, excluding “Clicked On Ad”
X = df.drop('Clicked on Ad',axis=1)
#Assign “Clicked on Ad” as y variable
y = df['Clicked on Ad']
```

## Step 5

We now want to assign our X and y variables to the Gaussian Naive Bayes algorithm from Scikit-learn. Gaussian is the easiest and simplest version of this algorithm. It is used with continuous variables under the assumption of normal data distribution. The Bernoulli version of Naive Bayes, meanwhile, is a more suitable classification technique for use on multiple binary features. For more information regarding specific algorithms for Naive Bayes classification, please see: https://scikit-learn.org/stable/modules/classes.html#module-sklearn.naive_bayes

We also need to assign a variable to the algorithm, which in this case is model. The naming of the variable isn’t important as long as it’s an intuitive description and fits with the basic syntax for assigning variables in Python (i.e. no spaces, cannot begin with a number, etc.).

```python
model = GaussianNB()
```

Next, we need to fit the algorithm to our X and y data using the assigned variable name.

```python
model.fit(X, y)
```

## Step 6

The final step is to input the values of a sample user that we wish to test.

| Feature | Target Value |
|---|---|
| Daily Time Spent on Site | 66.00 |
| Age | 48 |
| Area Income | 24593.33 |
| Daily Internet Usage | 131.76 |

Table 6: Target user information

```python
target_user = [
66.00, #Daily Time Spent on Site
48, #Age
24593.33, #Area Income
131.76, #Daily Internet Usage
]
```

Lastly, apply the **predict** method to the **target_user** using the model developed in Step 5 and assign it as a new variable. Then **print** the new variable on a new line.

```python
pred_target_user = model.predict([target_user])
print("Prediction:", pred_target_user)
```

Let’s run the model by right-clicking and selecting “Run” or by navigating from the Jupyter Notebook menu to Cell > Run All. Wait one or two seconds for the computer to process the model. The results, as shown below, will then appear at the bottom of the cell.

**Prediction:** [1]

The outcome of this exercise for the y variable “Clicked on Ad” is **[1]**, which means that the target user is expected to click on the advertisement and the ad should therefore be recommended to this user. Conversely, an outcome of **[0]** signifies that the user is *not* expected to click on the advertisement based on the behavior of similar users.

A more advanced version of this exercise examining both discrete and continuous variables (using logistic regression) is available at: http://www.scatterplotpress.com/bonus-chapters/recommender-systems-for-absolute-beginners-chapter-7/

## CONTENT-BASED FILTERING

As established in Chapter 2, content-based filtering methods provide recommendations based on similar item attributes and the profile of an individual user's preferences. The content-based filtering system then attempts to recommend items similar to those that a user has liked or browsed in the past. After purchasing a book about “machine learning,” for example, Amazon's content-based filtering is likely to serve you other books:

- from the same author,
- from the same category, e.g., data science, and
- have similar title keywords, e.g., “machine learning.”

As expected, content-based filtering relies heavily on a description of the item's characteristics and the profiling of individual user preferences. Under this model, items such as documents, online posts, images, and videos need to be adequately described in the form of keywords/tagging/metadata or through more sophisticated methods such as image recognition (e.g., artificial neural networks) or text mining (e.g., TF.IDF).

A book, for example, could be described by the following metadata:

- 1. The author(s)
- 2. The genre, e.g., thriller, romantic, statistics & probability
- 3. The year of publication
- 4. The type of book, e.g., fiction, non-fiction
- 5. Book format, e.g., textbook, audiobook, e-book, hardcopy

Likewise, user preferences need to be known and recorded. Individual user preferences can be determined by examining:

- 1. Past purchasing/consumption behavior
- 2. Browsing history
- 3. Personal details, e.g., gender, location, nationality, and hobbies
- 4. The IP address to determine location and time zone

From information gleaned about the user, filtering techniques can then compare this data with the description of available items and identify items to recommend. Content-based filtering can be a highly effective approach given that the items are properly tagged and there’s sufficient data about the user.

## Advantages

### 1) Agnostic to crowd preferences

A major advantage of content-based filtering is that it aids the discovery of relevant but low-profile items. As content-based filtering doesn't take crowd preferences into account, relevant items with low exposure to the crowd can still be found.

### 2) Content items are stable

Items don't change over time as much as people and are generally more permanent. People, on the other hand, are fickle and tastes change dramatically over time. We're all guilty of following phases of consumption. But an item will always be an item, and content-based filtering is therefore less vulnerable (than collaborative filtering) to changes in crowd preferences.

### 3) Items are generally fewer than users

Most online platforms have fewer items than users, and content-based filtering can help to conserve computational resources by comparing a limited number of items rather than a larger volume of user relationships.

### 4) Compatible with new items

In cases where there are insufficient rating data for a new or existing item (cold-start), content filtering can be applied to gather information regarding other items rated/purchased/consumed by the target user that might share similar attributes. The item is therefore recommended based on the user's interaction with similar items despite the lack of direct historical data.

### 5) Mitigates cheating

The other notable benefit of content filtering is that it's generally more difficult to “game the system” because malicious actors have less control to manipulate or fabricate item-to-item relationships. This is not the case for item-to-user relationships, which can be easily inflated with a flood of fake reviews and purchases.

## Disadvantages

### 1) Low variety

The variety of recommended items can be limited and less diverse than other methods. This is because content-based filtering depends on matching a specific item with similar items. Thus, items with low to no exposure to the target user are not likely to surface, which limits item discoverability.

### 2) Ineffective for new users

