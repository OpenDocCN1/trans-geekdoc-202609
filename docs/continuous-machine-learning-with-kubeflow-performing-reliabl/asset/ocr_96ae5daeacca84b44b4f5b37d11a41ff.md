This is the path to the S3 bucket where the Amazon SageMaker stores our training results as a default extension file.

This is the session object that will manage the interactions with SageMaker APIs and for any other AWS service that our training job will use.

So, we will set the hyperparameter values for our XGBoost training job by calling the **sdk** method **set_hyperparametersmethod** of the estimator class.

```
estimator.set_hyperparameters(base_score=0.5,
colsample_bylevel=1,num_round=150,
colsample_bynode=1, colsample_bytree=0.5,
learning_rate=0.02, gamma=0.025,
max_depth=4, n_estimators=1500, min_child_weight=2,
nthread=1, reg_alpha=0., reg_lambda=1, subsample=0.5,
objective='reg:linear', random_state=28)
```

Here, we have to create the training channels which will be used for the training job. We use both the train and the validation channels.

```
# content type can be libsvm or csv for XGBoost
training_input_config = sagemaker.session.s3_input(
s3_data=s3_training_file_location,
content_type='csv',
s3_data_type='S3Prefix')
```