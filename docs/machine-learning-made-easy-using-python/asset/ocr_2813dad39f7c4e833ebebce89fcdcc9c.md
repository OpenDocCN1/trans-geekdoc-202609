As you can see that we had the Questions as A-E and Answers as True or False. But we encoded the Answers label to be 0(False) or 1(True)

If we want we can get the label for the value or decode the 0 or 1 values using the inverse_transform() function

```
In [18]: import pandas
from sklearn import preprocessing
dt = pandas.DataFrame({'Questions':['A','B','C','D','E'],
                               'Answers':['True','True','False','True','False']})
Enc = preprocessing.LabelEncoder()
Enc.fit(dt['Answers'])
# Encoded labels
dt['Answers'] = Enc.transform(dt['Answers'])
# Decoding Labels
print(Enc.inverse_transform([0,1]))

['False' 'True']
```

By encoding we can hide the true values and perform a lot operations with them because they are numerical values. In this data we had less only two label values i.e. True and False, but when there are more values the encoding will range from 0 to their respective lengths