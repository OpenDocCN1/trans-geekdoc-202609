# Using the Vertex AI deployment with Flask 389

with the model, we need to explicitly remove it from its dictionary of features and values with the scoring_dict.pop('size_type') statement.

+   - The endpoint expects to get the features and values in a dictionary with the same format as we used to exercise the endpoint in the console in 10.4.04. That means the values in the dictionary need to be converted to lists of values, each of which contains exactly one value. This statement converts the dictionary to lists of values:

```
input_dict =[name: [value] for name, value in scoring_dict.items()]
```

+   - The predict_custom_trained_model_sample() function needs to be called with parameters specifying the project, endpoint, and key-value pairs for the features we want a prediction for.

In addition to updates to the Flask server module, we can also remove the methods that loaded the model from the local file system since we don't use the local model in this solution.

> NOTE An updated version of the Flask server module that uses the endpoint is available at https://mng.bz/Xx5a.

To run this version of the Flask server module, follow these steps:

+   1. Authorize the account you use to access Google Cloud with this application by running the following command on the command line in the local system where you are running the Flask server module:

```
gcloud auth application-default login
```

+   2. Start the Flask server module:

```
python flask_endpoint_deploy.py
```

If you get an error related to the protobuf (protocol buffer) level, try to the following command:

```
pip install protobuf==3.20.*n
```

This command adjusts the protobuf level to exactly what the endpoint requires.

> NOTE You don't need to know about the protobufs for the purposes of this application, but if you are curious, you can check out the documentation: https://protobuf.dev/

+   3. Once the Flask server module is running, go to localhost:5000 in a browser to exercise the deployment.