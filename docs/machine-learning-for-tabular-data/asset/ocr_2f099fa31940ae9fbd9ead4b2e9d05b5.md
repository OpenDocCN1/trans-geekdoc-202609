# CHAPTER 8 Getting started with deep learning with tabular data

```
cont_names = cont,
y_names = dep_var,
valid_idx=\
```

Specifies the continuous features

```
list(range((merged_data.shape[0]-100000),
merged_data.shape[0])),
```

Specifies the target feature

```
bs=32
```

Specifies the batch size

Specifies the subset of the dataset for validation in the training process

We will use the TabularDataLoaders object defined in 8.5 to define the fastai
model shown in 8.7.

One of the characteristics of fastai is a set of convenience that makes it easy
to examine the dataset through the stages of training. The show_batch() statement
shown in the following listing is an example of such a convenience function.

# Listing 8.6 Statement to show a batch of the training data

```
dls.valid.show_batch()
```

The statement shown in 8.6 makes it easy to see what the data that is training
model looks like after transformations specified in the procs parameter of the
TabularDataLoaders definition. Figure 8.7 shows the output of this statement.

| neighbourhood_group neighbourhood room_type |
| Manhattan | Hell's Kitchen | Private room |
| Manhattan | Hell's Kitchen | Private room |
| Manhattan | Hell's Kitchen | Private room |
| Brooklyn | Bushwick | Private room |
| Brooklyn | Williamsburg | Private room |

| minimum_nights number_of_reviews reviews_per_month calculated_host_listings_count target |
| 1.000000 | 18.000000 | 2.490000e+00 | 0.300001 | 1 |
| 1.000000 | 16.000000 | 2.222000e+00 | 0.300001 | 1 |
| 1.000000 | 13.000000 | 1.820000e+00 | 0.300001 | 1 |
| 15.000000 | 0.00001 | 1.455204e-08 | 2.000000 | 0 |
| 19.999999 | 1.999999 | 4.200000e-01 | 1.000000 | 0 |

Figure 8.7 Output of the show_batch() statement

Now we have specified the data that will be used to train the model, it's time to
define and train the model.