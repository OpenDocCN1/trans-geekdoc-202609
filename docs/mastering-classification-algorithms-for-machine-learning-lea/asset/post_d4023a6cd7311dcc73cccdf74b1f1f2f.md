
## Step 2: Form a data frame of extracted features.

We will call the function fillDataInDataFrame() for each type of file to create a data frame of features for that type.

```python
benignTestFileDF = fillDataInDataFrame(benignTestFileFeatures, featureList, BENIGN_FILE)

backdoorTestFileDF = fillDataInDataFrame(backdoorTestFileFeatures, featureList, BACKDOOR_FILE)

botnetTestFileDF = fillDataInDataFrame(botnetTestFileFeatures, featureList, BOTNET_FILE)

dosTestFileDF = fillDataInDataFrame(dosTestFileFeatures, featureList, DOS_FILE)

trojanTestFileDF = fillDataInDataFrame(trojanTestFileFeatures, featureList, TROJAN_FILE)

virusTestFileDF = fillDataInDataFrame(virusTestFileFeatures, featureList, VIRUS_FILE)
```

Next, we will concatenate these six data frames to form a single data frame. This is optional, and the contents of each of the six data frames can be tested individually. However, you will realize that the coding effort will increase if this strategy is chosen.

```python
import pandas as pd

dfTest = pd.concat([benignTestFileDF,
          backdoorTestFileDF,
          botnetTestFileDF,
          dosTestFileDF,
          trojanTestFileDF,
          virusTestFileDF], ignore_index = True)

dfTest[FILE_TYPE_COLUMN_NAME] = pd.to_numeric(dfTest[FILE_TYPE_COLUMN_NAME],
          downcast = 'integer')
```

So now we have all the extracted features from all the ELF Files in the Test dataset in the data frame dfTest.

## Step 3: Remove the NULL characters in the dataset.

We must remove the NULL character from the data in the data frame dfTest. Otherwise, the following programs may not read all the data in the data frame dfTest.

```python
# Remove NULL character from all the String
for col in dfTest.columns:
    if dfTest[col].dtype == 'object':
        dfTest[col].replace(chr(0), '', inplace = True)
```

## Step 4: Separate the numeric data and the non-numeric data.

We need to separate the non-numeric data in the dataset and convert that to numeric data using the TF-IDF Vectorizer.

```python
import numpy as np

dfNumeric = dfTest.select_dtypes(include=[np.number])
dfNonNumeric = dfTest.select_dtypes(exclude=[np.number])
print(dfTestNumeric.shape)
print(dfTestNonNumeric.shape)

(504, 2416)
(504, 124)
```

We have numeric data in the data frame dfTestNumeric and non-numeric data in the data frame dfTestNonNumeric.

## Step 5: From the numeric data, drop all the columns that are not present in the Training Dataset

The ELF Files in the Test dataset may contain features not present in the ELF Files in Training dataset. Since we have created the model on the Training dataset, we cannot have such features in the Test dataset. We need to drop all the features from the Test dataset that are not present in the Training dataset.

```python
columnsInModel = XTrain.columns
columnsToDrop = []
for col in dfTestNumeric.columns:
    if col not in set(columnsInModel):
        columnsToDrop.append(col)

dfTestNumeric.drop(columnsToDrop, axis = 1, inplace = True)

dfTestNumeric.shape

(504, 2273)
```

## Step 6: Create the TF-IDF vectors for the non-numeric data.

We will convert the non-numeric data to numeric data using the TF-IDF Vectorizer. Note that we have created the TF-IDF Vectorizer on the Training dataset. We need to transform the Test data using the same TF-IDF Vectorizer.

Before we can apply the TF-IDF Vectorizer, we need to form a single string out of all the non-numeric data for each data point.

```python
dfTestNumeric['ConcatenatedString'] = ""

for i in range(len(dfTestNumeric)):
    oneStr = ""
    for col in dfTestNumeric.columns:
        if type(dfTestNumeric[col][i]) == type("abc"):
            oneStr = oneStr + str(dfTestNumeric[col][i])
    dfTestNumeric.loc[i, 'ConcatenatedString'] = oneStr

dfTestNumeric['ConcatenatedString'].head()
```

0	SHT_PROBITS SHT_GNU_versym ELFCLASS64 SHT_PR...
1	SHT_PROBITS SHT_GNU_versym ELFCLASS64 SHT_PR...
2	SHT_PROBITS SHT_GNU_versym ELFCLASS64 SHT_PR...
3	SHT_PROBITS SHT_GNU_versym ELFCLASS64 SHT_PR...
4	SHT_PROBITS SHT_GNU_versym SHT_PROBITS ELFC...
Name: ConcatenatedString, dtype: object

Now we can apply the TF-IDF Vectorizer on the column ConcatenatedString data frame dfTestNumeric.

```python
arrTestNonNumericTFIDF = tdfidconverter.transform(dfTestNonNumeric.
ConcatenatedString).toArray()

dfTestNonNumericTFIDF = pd.DataFrame(arrTestNonNumericTFIDF, columns=tdfidconverter.get_feature_names())

print(dfTestNonNumericTFIDF.shape)

(504, 53)
```

## Step 7: Create a single data frame concatenating the numeric data and the TF-IDF vectors.

We now concatenate the data frame to contain the TF-IDF features.

```python
import pandas as pd

dfTest = pd.concat([dfNumeric, dfTestNonNumericTFIDF], axis = 1)

print(dfTest.shape)
```

## Step 8: Make the predictions.

Now that we have the data in the form that can be applied to the model, we can make the predictions.

```python
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn import metrics

y_pred = model.predict(XTest)
cm = metrics.confusion_matrix(yTest, y_pred)

plt.figure(figsize=(10,7))
sns.heatmap(cm, annot=True, fmt='d', ax=plt)
plt.xlabel('Predicted labels')
plt.ylabel('True labels')
plt.title('Confusion Matrix')
plt.show()

print("\nClassification Report:\n")
print(metrics.classification_report(yTest, y_pred))
```

Accuracy of the model: 0.86

Classification Report:

 | precision | recall | f1-score | support |
|---|---|---|---|
| 0 | 0.99 | 0.99 | 0.99 | 222 |
| 1 | 0.83 | 0.73 | 0.78 | 62 |
| 2 | 0.80 | 0.70 | 0.75 | 61 |
| 3 | 0.82 | 0.87 | 0.84 | 71 |
| 4 | 0.58 | 0.75 | 0.65 | 64 |
| 5 | 0.77 | 0.75 | 0.76 | 48 |
| macro avg | 0.80 | 0.80 | 0.79 | 504 |
| weighted avg | 0.87 | 0.86 | 0.86 | 504 |

accuracy: 0.86

![](img/11af2c4c7dddfed06ed008516c0c6dfb_259_0.png)
**Figure 7.5**: Confusion Matrix of the model on the Test dataset

## Conclusion

Random Forest algorithm is a very powerful algorithm mainly because the models built this algorithm generalize very well and thus make accurate predictions on the live data. Models built using the Random Forest algorithm generally do not overfit, mainly because the component models used in the Random Forest algorithm get to train on only a tiny part of the complete data used for training. In the next chapter, we will discuss Boosting Ensemble Models.

## Points to remember

- The Random Forest algorithm is a particular case of the Bagging Ensemble Model.
- The original dataset is split horizontally and vertically in the Random Forest algorithm.
- The key to splitting the original dataset in the Random Forest algorithm is that the data distribution in each subset should be nearly the same as in the original dataset.
- The Random Forest algorithm uses the Decision Tree algorithm to train the model for each subset of the original dataset.

## Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bponline.com
