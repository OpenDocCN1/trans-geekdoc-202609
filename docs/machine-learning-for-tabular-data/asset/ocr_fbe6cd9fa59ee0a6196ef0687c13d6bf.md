# CHAPTER 8 Getting started with deep learning with tabular data

The definitions in listing 8.16 remind you of a similar block of code in the fastai solution (listing 8.3), where we defined the target feature along with lists for categorical and continuous features.

Next we use the values we just defined to define a TabularClassificationData object. This object specifies the minimum characteristics of the dataset that we will use to train the model.

```
Listing 8.17 Defining a TabularClassificationData
```

```
datamodule = TabularClassificationData.from_csv(
categorical_fields=cat,
numerical_fields=cont,
target_fields='target',
train_file='../data/train.csv',
val_file='../data/val.csv',
predict_file='../data/test.csv',
batch_size=64)
```

Defines the categorical features
Defines the continuous features
Defines the target feature
Defines the training dataset
Defines the validation dataset
Defines the test dataset

We should explain why the definition of the TabularClassificationData object shown in listing 8.17 uses separate CSV files for train, validation, and test. For all other solutions, the dataset is loaded from a pickle file that is the output of the data cleanup notebook (https://mgn.bz/XxN9), which is then split into train, validation, and test datasets in the model training notebook. The Lightning solution is different because it has distinct CSV files for each segment of the dataset. The reason for this is that the very specific installation requirements shown in listing 8.14 were incompatible with loading the pickle file that contains the dataframe from the data cleanup notebook. As a workaround, we loaded pickle file in a separate notebook into a pandas DataFrame and saved the separate CSV files for training, validation, and test that you see in the definition of the TabularClassificationData object in listing 8.17. As an exercise, you could update the data cleanup notebook for the Lightning solution so that it saves the cleaned-up dataset as three separate CSV files rather than a single pickle file.

Now that we have specified the details about the dataset, we are ready to define and train the model, as shown in the following listing:

```
Listing 8.18 Setting dataset parameters
```

```
model = TabularClassifier.from_data(datamodule,
learning_rate=0.1)
trainer = flash.Trainer(max_epochs=3,
gpus=torch.cuda.device_count())
trainer.fit(model, datamodule=datamodule)
```

Defines the model using the TabularClassifierData object defined in listing 8.18
Defines a Trainer object
Fits the model