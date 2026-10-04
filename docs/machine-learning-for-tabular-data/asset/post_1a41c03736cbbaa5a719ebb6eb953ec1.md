
# Introduction to the Kuala Lumpur real estate dataset

values in each column. If a column contains a large number of unique values, that may be an indication that we should treat it as continuous, and if it contains a relatively small number of values, that may be an indication that we should treat it as categorical. In, features presenting few unique values are often considered categorical because they typically represent discrete categories or groups rather than continuous numerical measurements. This is not a hard and fast rule, as we shall see. The output of the df.unique() command gives the number of unique values in each column of the dataset.

# Listing 9.1 Getting the count of unique values in each column

```python
counts = df.unique()
print("unique value counts:\n", counts)
```

Returns the number of unique values in each column of the dataframe

The output of the command in listing 9.1 looks like the following:

The limited number of values in this column reinforces our intuition that this column is categorical.

This column is continuous.

| unique value counts: | |
| :--- | :--- |
| Location | 112 |
| Price | 4280 |
| Rooms | 43 |
| Bathrooms | 17 |
| Car Parks | 21 |
| Property Type | 99 |
| Size | 6190 |
| Furnishing | |
| dtype: int64 | |

This column requires further investigation.

This column is continuous.

This column is categorical.

This column is continuous, but it requires special treatment, we will see this later in this chapter.

This column is categorical.

To summarize what the output of the command in listing 9.1 tells us about the dataset:

- Columns that appear to be categorical—Location, Property Type, Furnishing.
- Columns that appear to be continuous—Price, Bathrooms, Car Parks, Size. Of these columns, Size also requires further investigation.
- Columns that need further investigation to determine whether they should be treated as continuous or categorical—Rooms.

Two of these columns require further investigation: Rooms and Size. In the following section on processing the dataset, we will dig deeper into these two columns to determine how to deal with them.

Now that we have a sense of the columns in the dataset and what kind of information they offer, let's explore some more aspects of the dataset. First, let's check the dimensions of the dataset, as shown in the following listing.

# Listing 9.2 Code to check the dimensions of the dataset

```python
print("shape ", df.shape)
shape (53883, 8)
```

> Statement to get the dimensions of the input dataframe
Output of the statement

9.2 shows that this dataset has over 53,000 rows and eight columns. In chapter 12, we will examine the relationship between number of rows in a dataset, the nature of the columns in a dataset, and the applicability of a deep learning model to the data. For now, it is safe to say that while this dataset is on the small side, it is big enough for us to have a decent chance of training a deep learning model with it.

The following listing contains the statements that list the number of missing values in each column of the dataset.

# Listing 9.3 Statements to list missing values in each column

```python
missing_values_count = df.isnull().sum()
print("missing values before cleanup:\n", missing_values_count)
```

> Output of this statement is a count of the number of missing values by column.

The following is the output of the commands in listing 9.3:

missing values before cleanup:
Location 0
Price 248
Rooms 1706
Bathrooms 2013
Car Parks 17567
Property Type 25
Size 1063
Furnishing 6930
dtype: int64

> Location is the only column with no missing values.
Car Parks is the column with the most values.

From the output of the command in listing 9.3, we can see that all but one of the columns in this dataset has missing values. We will need to correct this get dataset ready to train with a deep learning model. In comparison, the Airbnb NYC dataset only had missing values in four columns:

Missing values:
id 0
name 16

> Missing values in the name column

# Processing the dataset

```python
host_id 0
host_name 21
neighbourhood_group 0
neighbourhood 0
latitude 0
longitude 0
room_type 0
price 0
minimum_nights 0
number_of_reviews 10052
last_review 10052
reviews_per_month 0
calculated_host_listings_count 0
availability_365 0
```

As shown here, almost every column in the Kuala Lumpur dataset is missing values, which warns us, as often happens with real-world data, we will have to perform a lot of work to clean this dataset before we can start it with a model.

In this section, we have taken a first look at the Kuala Lumpur real estate dataset. In the next section, we will review the process of preparing this dataset to train a deep learning model.

# 9.2 Processing the dataset

Now that we've looked at the Kuala Lumpur real estate dataset and seen that it has a large number of missing values, we have some idea that it will require a good deal of processing before we can use it to train a model. In this section, we will look at the features of the dataset by one to describe the cleanup required.

At this point, we haven't decided if we are going to use a subset or the full set of columns. Our approach defaults to utilizing all available features. As we progress and examine the model's performance and behavior, we may decide to exclude some features, for example, because these features have undetected invalid values that effect the model's performance. It is not just because we cannot anticipate what features will work and what won't that we strive to obtain the full set of features available to the model for training. It is also a way to get the most out of data, as we will learn more about the dataset through processing it entirely and rendering it readable. This comprehensive approach ensures better results than we would have obtained if we only cleaned the features that we utilize to train the model.

The code highlighted in this section is available at https://mng.bz/MDBQ and the config file is at https://mng.bz/avlj.

We will begin by addressing columns that only involve handling missing values: Bathrooms, Car Parks, Furnishing, Property Type, Location. Next, we will describe the process for the columns that require more cleanup than simply dealing with missing information: Price, Rooms, and Size.

# 9.2.1 Processing Bathrooms, Car Parks, Furnishing, Property Type, Location

For a subset of columns in the dataset (Bathrooms, Car Parks, Property Type, Location), we can accomplish an effective cleanup by simply dealing with missing values. The config file contains default values to replace missing values for these columns that we determined based on characteristics and domain knowledge.

> Listing 9.4 Defining the default replacement for missing values

| misc_col_dict: # default values to replace missing values for general columns | |
| :--- | :--- |
| Bathrooms | median |
| Car Parks | 0 |
| Furnishing | unknown_furnishing |
| Property Type | unknown_property |
| Location | unknown_location | For the Bathrooms columns, sets the median value for the column as the default value For the Car Parks columns, sets the default value to zero For the categorical columns, sets a placeholder category as the default |

Listing 9.4 shows that we set missing values for Bathrooms in this dictionary to the median value for the column. The reason for the difference between these is due to the specific case of real estate listings. Residential properties rarely have no washrooms, so picking the median value as the default for Bathrooms makes sense. On the other hand, many residential properties have no parking space. If a property has a parking space, it is in the interests of the seller and the seller's agent to include this in the listing to ensure they get the best selling price for the property. Thus, when Car Parks is missing, it makes sense to assume that the property does not have any parking spaces, so we set missing values in this column to zero.

In this dictionary, we have distinct placeholder values for the categorical columns. The code for obtaining this simple cleanup is placed in the cleanup notebook's function `clean_up_misc_cols()`.

> Listing 9.5 Function to replace general missing values

```python
def clean_up_misc_cols(df, misc_col_dict):
    for col in misc_col_dict:
        if misc_col_dict[col] == 'median':
            df[col] += df[col].fillna(df[col])
        else:
            df[col] = df[col].fillna(misc_col_dict[col])
    return(df)
```

![](img/def89cc476fa39f4c54bd34e78d91674_354_0.png)
