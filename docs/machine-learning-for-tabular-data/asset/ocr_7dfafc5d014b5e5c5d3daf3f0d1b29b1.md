# CHAPTER 11 Building a machine learning pipeline

The location of the training data (split into training, validation, and test subsets) is automatically assigned to environment variables that get set in the container when it is set up by the pipeline script. This is standard for all Vertex AI containers; see the documentation at https://mng.bz/2y70.

The way that the URI for the config file is passed to the model training script is not the default for Vertex AI. If we had a training script that has a small number of arguments, we could create an argparse list that contains the argument values and pass that list to the model training script. The config file for our application is too complex to be efficient, so instead of passing each argument individually, we pass a single argument: the URI for the Cloud Storage location where we have saved a copy of the config file. With that, all the model training script needs to get the Cloud Storage location from the argument and ingest the YAML file from there. Once the arguments have been pulled into the config dictionary in the model training script, the rest of the code that uses them can work unchanged. This is a major benefit.

# 11.3.5 Updating the training code to run in a container

In this section, we will review how we changed the model training notebook (https://mng.bz/1Xjj) that we ran in Colab in chapter 9 to get a model to predict Kuala luxury properties. By making these changes, we convert the model training notebook into a training script that can run in a Vertex AI built-in container.

The following are the key changes we made to the training notebook to create the training script:

+   - Removed extraneous library imports and associated code. For example, we don't need to generate a diagram of the model when we run the training script, so we removed the code associated with `plot_model`.
- Removed code that splits the dataset into training, validation, and testing subsets. In the ML pipeline, the Vertex AI SDK takes care of splitting the dataset prior to the testing script being started.
- Added code to interpret the `job.run` argument list, as shown in the following listing.

# 11.1 Loading the saved Keras model

```
parser = argparse.ArgumentParser()
parser.add_argument(
    '--config_bucket',
    help='Config details',
    required=True
)
args = parser.parse_args().dict_
config_bucket = args['config_bucket']
```

| Defines an argparse object for the arguments passed by the Vertex AI SDK |

| Adds the config_bucket argument to the argparse object |

| Ingest the arguments passed by the Vertex AI SDK as a dictionary |