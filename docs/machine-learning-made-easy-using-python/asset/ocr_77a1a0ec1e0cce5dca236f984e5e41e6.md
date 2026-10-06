We have removed the Unnamed: 5 column

```
In [11]: import pandas as pan
dt = pan.read_excel("xlsx_data.xlsx")
del dt["Unnamed: 5"]

dt
```

| id | name | price | sales | brand |
|---|---|---|---|--|
| 0 101 | biscuits | 5.00 | 227 | HomeFoods |
| 1 102 | cookies | 7.25 | 158 | TBakery |
| 2 103 | cake | 12.00 | 50 | |
| 3 104 | whey_supplement | 34.90 | 24 | MusleUp |
| 4 105 | protein_bars | 4.90 | 85 | MusleUp |
| 5 106 | potato_chips | 1.75 | 121 | HomeFoods |

Now, we need to replace dt.value[2,5] i.e. 34 with TBakery. We can use the replace method

```
In [12]: import pandas as pan
dt = pan.read_excel("xlsx_data.xlsx")
del dt["Unnamed: 5"]
ndt.replace({34:"TBakery"})
```

| id | name | price | sales | brand |
|---|---|---|---|--|
| 0 101 | biscuits | 5.00 | 227 | HomeFoods |
| 1 102 | cookies | 7.25 | 158 | TBakery |
| 2 103 | cake | 12.00 | 50 | TBakery |
| 3 104 | whey_supplement | 34.90 | 24 | MusleUp |
| 4 105 | protein_bars | 4.90 | 85 | MusleUp |
| 5 106 | potato_chips | 1.75 | 121 | HomeFoods |

Our data is clean with errors. By recapping the chapter and attempt the Exercise, where you'll be provided with sample data files [links] with lots of errors and you have to perform all the data cleansing practised in the previous lesson, this will be a very good exercise to help you understand about data processing and cleansing more