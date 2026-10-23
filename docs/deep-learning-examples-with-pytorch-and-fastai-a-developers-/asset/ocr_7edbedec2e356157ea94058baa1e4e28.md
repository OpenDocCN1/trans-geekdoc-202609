```
import pandas as pd
from fastai.basics import Path
```

```
! git clone https://github.com/pcsanwald/kaggle-titanic.git path =
Path()/'kaggle-titanic'
list(path.ls())
```

```
[Path('kaggle-titanic/.git'), Path('kaggle-titanic/src'), titanic/doc'),
Path('kaggle-titanic/test.csv'), titanic/README.md'), Path('kaggle-titanic/.gitignore'), titanic/train.csv'), Path('kaggle-titanic/project.clj'),
titanic/test')]
Path('kagglePath('kagglePath('kagglePath('kaggle
```

We see that our dataset contains a train.csv and a test.csv. We will just use the training data for this chapter.
Now we can pass the train.csv to the read_csv-function and create a DataFrame from our csv-file.

```
df = pd.read_csv(path/'train.csv')
```

# 21.1 The Common Functionalities of DataFrame

We now want to look at some of the common functionalities of DataFrame.

# 21.1.1 Head and Tail

The functions head and tail are equivalents to the unix head and tail functions. They show the first rows of a dataframe and then the last rows of the dataframe respectively. You can pass a value n to show n rows – the default for n is 5. So both head and tail are handy functions to get a quick glance at your data before you start working with it.

```
df.head(n=4)
```

```
survived pclass name sex age sibsp parch ticket fare cabin embarked
0 0 3 Braund, Mr. Owen Harris male 22.0 1 0 A/5 21171 7.2500 NaN S
1 1 1 Cumings, Mrs. John Bradley female 38.0 1 0 PC 17599 71.2833 C85 C (Florence Briggs Thayer)
2 1 3 Heikkinen, Miss. Laina female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S
3 1 1 Futrelle, Mrs. Jacques Heath female 35.0 1 0 113803 53.1000 C123 S (Lily May Peel)
```