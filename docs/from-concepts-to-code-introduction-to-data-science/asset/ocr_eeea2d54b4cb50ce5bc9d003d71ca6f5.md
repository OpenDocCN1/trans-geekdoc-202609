# Chapter Summary

# 6.3.4 Extreme Observations

From the statistical summary produced by describe(), systolic holds a negative value and a very high value of 200. Negative blood pressures do not make clinical sense, while the value of 200 is sense possible but concerning. There are different options for handling the negative value. Here, we set a rule where we temporarily replace negative values with missing, and then fill values with the previous measurement (that is, the LVCFW).

```
df.loc[df.bp_systolic < 0, 'bp_systolic'] = np.nan
df.bp_systolic.fillna(inplace=True)
```

Next, let's turn to the patient with the systolic measurement of 200. Unlike the prior case, we cannot simply reject it as incorrect. It is best to check for contextual information before taking action. If this data was from an electronic health record system, we might check for notes. In this case, the corresponding highly diastolic measurement of 120 offers supporting evidence. Acting conservatively, we leave the outlier measurement in place.

# 6.4 Chapter Summary

Variables store information to be used by a program, and their values are stored in a memory address. Strings are immutable data types that hold a sequence of characters. Sets, lists, and dictionaries are data types that store collections of data. Sets store unique objects. Dictionaries use key-value pairs to store their data.

We processed unstructured data, which involved the use of string operations. For the structured data that we processed, we used pandas dataframes. The dataframe provides nice functionality for manipulating rows and columns of data. In particular, we learned many techniques to perform common operations including subsetting, filtering, imputing, and handling extreme observations. For going deeper, these notebooks from the course recommend:

```
semester1/week_05_08_data_clean_prepare/pandas_dataframes.ipynb
semester1/week_05_08_data_clean_prepare/pandas_dataframes2.ipynb
```

Another resource is the "10 minutes to pandas" guide, which can be found here:

```
https://pandas.pydata.org/docs/user_guide/10min.html
```

We have made a lot of progress in building data processing skills. In the next chapter, we will learn about storing and retrieving data. The data might have