```
<class 'pandas.core.frame.DataFrame'>nRangeIndex: 20640 entries, 0 to 20639
Data columns (total 10 columns):
longitude 20640 non-null float64
latitude 20640 non-null float64
housing_median_age 20640 non-null float64
total_rooms 20640 non-null float64
total_bedrooms 20433 non-null float64
population 20640 non-null float64
households 20640 non-null float64
median_income 20640 non-null float64
housing_value 20640 non-null float64
ocean_proximity 20640 non-null object
types: float64(9), object(1)
memory usage: 1.6 MB
```

Figure 2-6. Housing info

There are 20,640 instances in the dataset, which means it is fairly small by Machine Learning standards, but it's perfect to get started. Notice that the total_bedrooms attribute has 20,433 non-null values, meaning that 207 districts are missing this feature. We will need to take care of this.

All attributes are numerical, except the ocean_proximity field. Its type is object, so it could hold any kind of Python object, but since you loaded this data from a CSV file you know that it is a text attribute. When you looked at the top five rows, you probably noticed that the values in the ocean_proximity column were repetitive, which means that it is probably a categorical attribute. You can find out how many districts belong to each category by using the value_counts() method:

```
>>> housing['ocean_proximity'].value_counts()
<1H OCEAN        9136
INLAND            6555
NEAR OCEAN        2658
NEAR BAY          2290
ISLAND             5
Name: ocean_proximity, dtype: int64
```

Let's look at the other fields. The describe() method shows a summary of the numerical attributes (Figure 2-7).