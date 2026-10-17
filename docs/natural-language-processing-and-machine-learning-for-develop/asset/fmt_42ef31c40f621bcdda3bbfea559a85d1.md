
*   `plt.xlabel()`

*   `plt.ylabel()`

*   `plt.annotate()`

*   `plt.legend()`

*   `plt.ylim()`

*   `plt.savefig()`

Seaborn supports various built-in datasets, just like `numpy` and `pandas`, including the Iris dataset and the Titanic dataset, both of which you will see in subsequent sections. As a starting point, the three-line code sample in the next section shows you how to display the rows in the built-in “tips” dataset.

## Seaborn Built-in Datasets

[Listing F.23](#appF.xhtml#listF.23) displays the contents of `seaborn_tips.py` that illustrates how to read the tips dataset into a data frame and display the first five rows of the dataset.

***LISTING F.23: seaborn_tips.py***

```python
import seaborn as sns
df = sns.load_dataset("tips")
print(df.head())
```

[Listing F.23](#appF.xhtml#listF.23) is very simple: after importing seaborn, the variable `df` is initialized with the data in the built-in dataset tips, and the `print()` statement displays the first five rows of `df`. Note that the `load_dataset()` API searches for online or built-in datasets. The output from [Listing F.23](#appF.xhtml#listF.23) is here:

```
total_bill tip sex smoker day time size 0 16.99 1.01 Female No Sun Dinner 2 1 10.34 1.66 Male No Sun Dinner 3 2 21.01 3.50 Male No Sun Dinner 3 3 23.68 3.31 Male No Sun Dinner 2 4 24.59 3.61 Female No Sun Dinner 4 
```

## **The Iris Dataset in Seaborn**

[Listing F.24](#appF.xhtml#listF.24) displays the contents of `seaborn_iris.py` that illustrates how to plot the Iris dataset.

***LISTING F.24: seaborn_iris.py***

```python
import seaborn as sns
import matplotlib.pyplot as plt  # Load iris data
iris = sns.load_dataset("iris")  # Construct iris plot
sns.swarmplot(x="species", y="petal_length", data=iris)  # Show plot
plt.show()
```

[Listing F.24](#appF.xhtml#listF.24) imports seaborn and `matplotlib.pyplot` and then initializes the variable `iris` with the contents of the built-in Iris dataset. Next, the `swarmplot()` API displays a graph with the horizontal axis labeled `species`, the vertical axis labeled `petal_length`, and the displayed points are from the Iris dataset.

[Figure F.20](#appF.xhtml#figF.20) displays the images in the Iris dataset based on the code in [Listing F.24](#appF.xhtml#listF.24).

![Figure F.20. ¶ The Iris Dataset.](images/figF.20.jpg)

Figure F.20. ¶ The Iris Dataset.

## **The Titanic Dataset in Seaborn**

[Listing F.25](#appF.xhtml#listF.25) displays the contents of `seaborn_titanic_plot.py` that illustrates how to plot the Titanic dataset.

***LISTING F.25: seaborn_titanic_plot.py***

```python
import matplotlib.pyplot as plt
import seaborn as sns  # titanic = sns.load_dataset("titanic") g = sns.factorplot("class", "survived", "sex", data=titanic, kind="bar", palette="muted", legend=False)  # Show plot
plt.show()
```

[Listing F.25](#appF.xhtml#listF.25) contains the same import statements as [Listing F.24](#appF.xhtml#listF.24), and then initializes the variable `titanic` with the contents of the built-in Titanic dataset. Next, the `factorplot()` API displays a graph with dataset attributes that are listed in the API invocation.

[Figure F.21](#appF.xhtml#figF.21) displays a plot of the data in the Titanic dataset based on the code in [Listing F.25](#appF.xhtml#listF.25).

![Figure F.21. ¶ A Histogram of the Titanic Dataset.](images/figF.21.jpg)

Figure F.21. ¶ A Histogram of the Titanic Dataset.

## **Extracting Data from the Titanic Dataset in Seaborn (1)**

[Listing F.26](#appF.xhtml#listF.26) displays the contents of `seaborn_titanic.py` that illustrates how to extract subsets of data from the Titanic dataset.

***LISTING F.26: seaborn_titanic.py***

```python
import matplotlib.pyplot as plt
import seaborn as sns  # titanic = sns.load_dataset("titanic") print("titanic info:") titanic.info()  # print("first five rows of titanic:") print(titanic.head())  # print("first four ages:") print(titanic.loc[0:3,'age'])  # print("fifth passenger:") print(titanic.iloc[4])  #print("first five ages:") #print(titanic['age'].head())  #print("first five ages and gender:") #print(titanic[['age','sex']].head())  #print("descending ages:") #print(titanic.sort_values('age', ascending = False).head())  #print("older than 50:") #print(titanic[titanic['age'] > 50])  #print("embarked (unique):") #print(titanic['embarked'].unique())  #print("survivor counts:") #print(titanic['survived'].value_counts())  #print("counts per class:") #print(titanic['pclass'].value_counts())  #print("max/min/mean/median ages:") #print(titanic['age'].max()) #print(titanic['age'].min()) #print(titanic['age'].mean()) #print(titanic['age'].median()) 

[Listing F.26](#appF.xhtml#listF.26) contains the same import statements as [Listing F.25](#appF.xhtml#listF.25), and then initializes the variable `titanic` with the contents of the built-in Titanic dataset. The next portion of [Listing F.26](#appF.xhtml#listF.26) displays various aspects of the Titanic dataset, such as its structure, the first five rows, the first four ages, and the details of the fifth passenger.

As you can see, there is a large block of “commented out” code that you can uncomment in order to see the associated output, such as age, gender, persons over 50, unique rows, and so forth. The output from [Listing F.26](#appF.xhtml#listF.26) is here:

`titanic info:` `<class 'pandas.core.frame.DataFrame'>` `RangeIndex: 891 entries, 0 to 890` `Data columns (total 15 columns): survived 891 non-null int64 pclass 891 non-null int64 sex 891 non-null object age 714 non-null float64 sibsp 891 non-null int64 parch 891 non-null int64 fare 891 non-null float64 embarked 889 non-null object class 891 non-null category who 891 non-null object adult_male 891 non-null bool deck 203 non-null category embark_town 889 non-null object alive 891 non-null object alone 891 non-null bool dtypes: bool(2), category(2), float64(2), int64(4), object(5) memory usage: 80.6+ KB` `first five rows of titanic:` `survived pclass sex age sibsp parch fare embarked class 0 0 3 male 22.0 1 0 7.2500 S Third 1 1 1 female 38.0 1 0 71.2833 C First 2 1 3 female 26.0 0 0 7.9250 S Third 3 1 1 female 35.0 1 0 53.1000 S First who adult_male deck embark_town alive alone 0 man True NaN Southhampton no False 1 woman False C Cherbourg yes True 2 woman False NaN Southhampton yes True 3 woman False C Southhampton yes False 4 man True NaN Southhampton no True`

`counts per class:` `3 491 1 216 2 184 Name: pclass, dtype: int64` `max/min/mean/median ages:` `80.0 0.42 29.69911764705882 28.0`

## **Extracting Data from the Titanic Dataset in Seaborn (2)**

[Listing F.27](#appF.xhtml#listF.27) displays the contents of `seaborn_titanic2.py` that illustrates how to extract subsets of data from the Titanic dataset.

***LISTING F.27: seaborn_titanic2.py***
