# PyTorch with fastai

| calculated_host_listings | availability_365 (latitude, longitude) | target |
|---|---|---|
| 6 | 365 (40.64749, -73.97237) | 0 |
| 2 | 355 (40.75362, -73.98377) | 1 |
| 1 | 365 (40.80902, -73.94199) | 0 |
| 1 | 194 (40.68514, -73.95976) | 0 |
| 1 | 0 (40.79851, -73.94399) | 0 |

Figure 8.6 Sample batch values when the target column is explicitly converted to string values

Now that we have examined why it's critical to convert the values in the target column to strings, let's review the rest of the code to create a trained fastai model. Listing 8.5 shows the block of code that defines the TabularDataLoaders object. This object is a tabular-data wrapper around the PyTorch DataLoader (https://mng.bz/6eDe) object, which is an iterable encapsulation of the samples and labels in a dataset.

# Listing 8.5 Defining the TabularDataLoaders object

| | Defines the transformations procedures to be applied to the dataset in the implemented pipeline | Specifies that the TabularDataLoaders object is based on the merged_data dataframe |
|---|---||
| | Sets a placeholder value for the path object | Specifies the list of transformations to apply with the TabularDataLoaders object |
| path = '.'
procs = [FillMissing, Categorify, Normalize]
dls = TabularDataLoaders.from_df(dtrain,
path,
procs=procs,
cat_names=cat,| Specifies the categorical features |