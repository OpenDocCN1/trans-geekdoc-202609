| notebook-name: david |
| EOF |

After the file is created, run the following code to set up the header filter in the admin namespace:

```
kubectl apply -f notebook_filter.yaml
```

Great! Now, let's create a pipeline that does the following:

+   * Processes data saved in the data lake, creates a training dataset, and saves it in a training bucket
* Runs a model training job
* Deploys the model using the Seldon Core model serving component

We will use Kubeflow Pipelines to track the overall pipeline status, and we will continue to track experiment details and manage models in the MLflow model registry. Specifically, we are going to build the following architecture:

![](bbox=[0.163, 0.458, 0.837, 0.755])

Figure 7.14 - Automation pipeline with Kubeflow Pipelines

You will create a new notebook for this portion of the exercise. On your Jupyter notebook screen, select Python 3 under the New dropdown on the screen to create a new blank notebook. You will install the Kubeflow Pipelines package in the new notebook by running the following command in a cell:

```
!python3 -m pip install kfp --upgrade --user
```