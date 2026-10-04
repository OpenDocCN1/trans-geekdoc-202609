# 9.2.1 Processing Bathrooms, Car Parks, Furnishing, Property Type, and Location columns

For a subset of columns in the dataset (Bathrooms, Car Parks, Property Type, Location), we can accomplish an effective cleanup by simply dealing with missing values. The config file contains default values to replace missing values for these columns that we determined based on their characteristics and domain knowledge.

> Listing 9.4 Defining the default replacement for missing values

| misc_col_dict: # default values to replace missing values for general columns
Bathrooms: median
Car Parks: 0
Furnishing: unknown_furnishing
Property Type: unknown_property
Location: unknown_location | For the Bathrooms columns, sets the median value for the column as the default value
For the Car Parks columns, sets the default value to zero
For the categorical columns, sets a placeholder category as the default value

Listing 9.4 shows that we set missing values for Bathrooms in this dictionary to the median value for the column. For the Car Parks column, we set missing values to zero. The reason for the difference between these is due to the specific use case of real estate listings. Residential properties rarely have no washrooms, so picking the median value as the default for Bathrooms makes sense. On the other hand, many residential properties have no parking space. If a property has a parking space, it is in the interests of the seller and the seller's agent to include this in the listing to ensure they get the best selling price for the property. Thus, when Car Parks is missing, it makes sense to assume that the property does not have any parking spaces, so we set missing values in this column to zero.

In this dictionary, we have distinct placeholder values for the categorical columns. The code for obtaining this simple cleanup is placed in the cleanup notebook's function `clean_up_misc_cols()`.

> Listing 9.5 Function to replace general missing values

```
def clean_up_misc_cols(df, misc_col_dict):
    for col in misc_col_dict:
        if misc_col_dict[col] == 'median':
            df[col] += df[col].fillna(df[col])
        else:
            df[col] = df[col].fillna(misc_col_dict[col])
    return(df)
```

![](bbox=[0.615, 0.735, 0.862, 0.915])