```
#print(titanic['age'].mean())
titanic info:
<class 'pandas.core.frame.DataFrame'>nRangeIndex: 891 entries, 0 to 890
Data columns (total 15 columns):
  survived      891 non-null int64
  pclass        891 non-null int64
  sex           891 non-null object
age           714 non-null float64
  sibsp        891 non-null int64
  parch         891 non-null int64
  fare          891 non-null float64
  embarked      889 non-null object
  class         891 non-null category
  who           891 non-null object
  adult_male   891 non-null bool
  deck          203 non-null category
  embark_town   889 non-null object
  alive         891 non-null object
  alone         891 non-null bool
types: bool(2), category(2), float64(2), int64(4)
memory usage: 80.6+ KB
first rows of titanic:
| survived pclass sex sibsp parch fare embarked class \ |
| 0 0 3 male 22.0 1 0 7.2500 S Third |
| 1 1 female 38.0 1 0 71.2833 C First |
| 2 1 female 26.0 0 0 7.9250 S Third |
| 3 1 female 35.0 1 0 53.1000 S First |
| 4 0 male 35.0 0 0 8.0500 S Third |

| who adult_male deck embark_town alive alone |
| 0 man True NaN Southampton no False |
| 1 woman False C Cherbourg yes False |
| 2 woman False NaN Southampton yes True |
| 3 woman False C Southampton yes False |
| 4 man True NaN Southampton no True |
first four ages:
0 22.0
1 38.0
```