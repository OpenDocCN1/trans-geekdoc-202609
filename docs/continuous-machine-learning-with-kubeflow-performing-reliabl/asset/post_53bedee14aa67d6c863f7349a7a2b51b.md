
This is the path to the S3 bucket where the Amazon SageMaker stores our training results as a default extension file.

This is the session object that will manage the interactions with SageMaker APIs and for any other AWS service that our training job will use.

So, we will set the hyperparameter values for our XGBoost training job by calling the **sdk** method **set_hyperparameters** method of the estimator class.

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

```
validation_input_config = sagemaker.session.s3_input(
 s3_data=s3_validation_file_location,
 content_type='csv',
 s3_data_type='S3Prefix'
 )
 data_channels = {'train': training_input_config, 'validation':
 validation_input_config}
```

Now, to start the model training, we will call the estimator's fit method. XGBoost supports "train", "validation" channels.

### Reference: Supported channels by algorithm
https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-docker-registry-paths.html

```
estimator.fit(data_channels)
```

```
2020-04-05 16:42:08 Starting – Starting the training job...
2020-04-05 16:42:09 Starting – Launching requested ML instances.....
2020-04-05 16:43:12 Starting – Preparing the instances for training...
2020-04-05 16:44:06 Downloading – Downloading input data...
2020-04-05 16:44:37 Training – Downloading the training image...
2020-04-05 16:45:09 Uploading – Uploading generated training model
2020-04-05 16:45:09 Completed – Training job completed
Arguments: train
[2020-04-05:16:44:58:INFO] Running standalone xgboost training.
[2020-04-05:16:44:58:INFO] File size need to be processed in the node: 0.74mb. Available memory size in the node: 8508.11mb
[2020-04-05:16:44:58:INFO] Determined delimiter of CSV input is ','
[16:44:58] S3DistributionType set as FullyReplicated
[16:44:58] 1235x225 matrix with 277875 entries loaded from /opt/ml/input/data/train?format=csv&label_column=&delimiter=,
[2020-04-05:16:44:58:INFO] Determined delimiter of CSV input is ','
[16:44:58] S3DistributionType set as FullyReplicated
[16:44:58] 218x225 matrix with 49050 entries loaded from /opt/ml/input/data/validation?format=csv&label_column=&delimiter=,
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 0 pruned nodes, max_depth=4
[0]#011train-rmse:5.41071#011validation-rmse:5.58529
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[1]#011train-rmse:4.03268#011validation-rmse:4.23648
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[2]#011train-rmse:2.98134#011validation-rmse:3.15959
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 2 pruned nodes, max_depth=4
[3]#011train-rmse:2.26828#011validation-rmse:2.4225
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[4]#011train-rmse:1.67801#011validation-rmse:1.83374
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 20 extra nodes, 0 pruned nodes, max_depth=4
[5]#011train-rmse:1.33205#011validation-rmse:1.48437
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 12 extra nodes, 0 pruned nodes, max_depth=4
[6]#011train-rmse:1.10017#011validation-rmse:1.23461
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 24 extra nodes, 0 pruned nodes, max_depth=4
[16:44:59] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 6 pruned nodes, max_depth=4
[148]#011train-rmse:0.095235#011validation-rmse:0.693852
[16:44:59] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 4 pruned nodes, max_depth=4
[149]#011train-rmse:0.094575#011validation-rmse:0.694274
Training seconds: 63
Billable seconds: 63
```

### Figure 7.42: XG-Boost Model Fit Logs of RMSE of 0.6942 which is minimum

It is a synchronous operation. The method will display the progress logs and it waits until the training completes before returning.

Go to the training Jobs and Model in Amazon SageMaker service and you can check all the details of the model hyperparameter and the output artifacts location.

![](img/8f8a671916d96b455297952d0f37b96c_474_0.png)

### Figure 7.43: XG-Boost Model Training Job Dashboard

Now, the preceding screenshot is of the dashboard of the model which we have fitted; we will get all the output location and instance type and required information in the dashboard.

## 7.7 Amazon SageMaker model deployment

Now, we will deploy from the training job which was fitted earlier and give an endpoint name and instance type.

### Ref: http://sagemaker.readthedocs.io/en/latest/estimators.html

```
predictor = estimator.deploy(initial_instance_count=1,
instance_type='ml.m4.xlarge',endpoint_name = 'xgboost-house-v1')
```

Here, we will deploy the model that we have trained in create and run a Training Job by calling the deploy method of the **sagemaker.estimator.Estimator** object from SDK. So, now it is the same object which we have used to train our model. When we call the deploy method, it will specify the number and type of the ML instances that we want to use to host the endpoint for deployment.

If an error comes, please use **instance_type='ml.t2.medium'**.

![](img/8f8a671916d96b455297952d0f37b96c_476_0.png)

### Figure 7.44: XG-Boost Model Deployment Endpoint

In the preceding screenshot, we can see the endpoint deployment name and below that, we can call the endpoint, with **RealTimePredictor** API by passing the name.

```
endpoint_name = 'xgboost-house-v1'
predictor = 
sagemaker.predictor.RealTimePredictor(endpoint=endpoint_name)
```

![](img/8f8a671916d96b455297952d0f37b96c_477_0.png)

### Figure 7.45: XG-Boost Model End-Point Cloud-Watch Metrics

Now, the preceding screenshot shows the model CPU Utilization and its performance with respect to time and we can see those in CloudWatch and Cloud logs to track all the model performance.

```
class sagemaker.predictor.RealTimePredictor(endpoint, sagemaker_session=None, serializer=None, deserializer=None, content_type=None, accept=None)
```

Bases: object

Make prediction requests to an Amazon SageMaker endpoint.

Initialize a `RealTimePredictor`.

Behavior for serialization of input data and deserialization of result data can be configured through initializer arguments. If not specified, a sequence of bytes is expected and the API sends it in the request body without modifications. In response, the API returns the sequence of bytes from the prediction result without any modifications.

- Parameters:
  - endpoint (str) – Name of the Amazon SageMaker endpoint to which requests are sent.
  - sagemaker_session (sagemaker.session.Session) – A SageMaker Session object, used for SageMaker interactions (default: None). If not specified, one is created using the default AWS configuration chain.
  - serializer (callable) – Accepts a single argument, the input data, and returns a sequence of bytes. It may provide a content_type attribute that defines the endpoint request content type. If not specified, a sequence of bytes is expected for the data.
  - deserializer (callable) – Accepts two arguments, the result data and the response content type, and returns a sequence of bytes. It may provide a content_type attribute that defines the endpoint response's "Accept" content type. If not specified, a sequence of bytes is expected for the data.
  - content_type (str) – The invocation's "ContentType", overriding any content_type from the serializer (default: None).
  - accept (str) – The invocation's "Accept", overriding any accept from the deserializer (default: None).

```
predict(data, initial_args=None, target_model=None)
```

### Figure 7.46: SageMaker API Notes AWS SageMaker SDK)

Now we will set the environment variables.

```
from sagemaker.predictor import csv_serializer, json_deserializer
predictor.content_type = 'text/csv'
predictor.serializer = csv_serializer
predictor.deserializer = None
```

We need to pass an array; so the prediction can pass a numpy array or a list of values [[19,1],[20,1]]. Here, we will load the test
