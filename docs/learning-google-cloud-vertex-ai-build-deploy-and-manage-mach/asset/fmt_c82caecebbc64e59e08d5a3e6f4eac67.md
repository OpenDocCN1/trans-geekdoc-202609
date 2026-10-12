
The Python code consists of codes to import required packages. The function `get_args` contains the hyperparameters that need to be tuned, and hyperparameters will be passed as arguments. In our exercise, we are considering five hyperparameters for the tuning; they are:

*   `n_estimator`
*   `max_depth`
*   `min_samples_split`
*   `min_samples_leaf`
*   `max_features`

`max_features` takes a string value as input, and all the other hyperparameters take integer values.

Function `preprocess_data` reads the file, applies basic transformations, and returns the split data. The main function builds the model, initiates the hyperparameter tuning of the model, and saves the model to cloud storage.

[Image creation](#contents.xhtml#sc2_101a)

Now that we have completed the creation of the Dockerfile and Python code for the model building, we can proceed with image creation. Follow the given steps for the same.

### Step 1: Image creation using docker build

Type the following commands in the terminal, as shown in [Figure 5.9](#ch05.xhtml#fig5-9), for image creation:

```
PROJECT_ID=vertex-ai-gcp-1
IMAGE_URL="gcr.io/$PROJECT_ID/eye:v1"
docker build ./ -t $IMAGE_URL
```

![](images/Figure_5.9.png)

Figure 5.9: Image creation process

It will take a few minutes to build the image from the Dockerfile. Once the build is complete, a success message will be displayed in the terminal as shown in [Figure 5.10](#ch05.xhtml#fig5-10) (point number 1).

### Step 2: Pushing the docker image to the container registry

Now that the image is created (the success message for image creation can be seen in [Figure 5.10](#ch05.xhtml#fig5-10)), type the following command to push the image to the container registry:

```
docker push $IMAGE_URL
```

Refer to the following figure:

![](images/Figure_5.10.png)

Figure 5.10: Image to project container registry

The image will be available in the container registry of the project (for checking, follow the steps described in the previous chapter).

[Submitting the custom model training job](#contents.xhtml#sc2_102a)

Steps for the custom model training with hyperparameter tuning are very similar to the ones described in the previous chapter, except that we will be enabling the hyperparameter tuning option. Follow the given steps to submit the training job.

### Step 1: Training module of Vertex AI

Open the training module of Vertex AI, as shown in [Figure 5.11](#ch05.xhtml#fig5-11):

![](images/Figure_5.11.png)

Figure 5.11: Training module of Vertex AI

1.  Select the Training module.
2.  Select **HYPERPARAMETER TUNING JOBS**.
3.  Click on **CREATE**.

### Step 2: Selecting training method

The Train new model page will appear, as shown in [Figure 5.12](#ch05.xhtml#fig5-12):

![](images/Figure_5.12.png)

Figure 5.12: Training method selection for custom model

Follow the corresponding points to configure the training method:

1.  Select the training method.
2.  Select **No managed dataset** under the Dataset selection.
3.  Select **Custom Training**.
4.  Click on **Continue**.

### Step 3: Model details

Select the model details to train the model, as shown in [Figure 5.13](#ch05.xhtml#fig5-13):

![](images/Figure_5.13.png)

Figure 5.13: Model details for custom model

Follow the corresponding points:

1.  After training method selection, we have to enter the Model details.
2.  Select **Train new model**.
3.  Provide a Name for the model.
4.  Select the Service account associated with the compute (users can also choose the service account which we had created in [Chapter 2](#ch02.xhtml), Introduction to Vertex AI and AutoML Tabular, but roles to access cloud storage need to be added).
5.  Scroll down and click on **Continue**.

### Step 4: Training container details

Follow the numbers and their corresponding points in [Figure 5.14](#ch05.xhtml#fig5-14) to configure the training container:

![](images/Figure_5.14.png)

Figure 5.14: Container details for custom model

Follow the corresponding points:

1.  After Model details selection, we have to enter the Training container details.
2.  Select **Custom container**.
3.  Browse for the Container image that has been pushed to the container registry.
4.  Select the cloud storage bucket to store model artifacts (since we have already chosen the bucket in the code, this can be left blank).
5.  Click on **Continue**.

### Step 5: Hyperparameter tuning

The next step is for hyperparameters. Follow the corresponding steps to enable and configure the hyperparameter tuning for model training, as shown in [Figure 5.15](#ch05.xhtml#fig5-15):

![](images/Figure_5.15.png)

Figure 5.15: Configuring hyperparameter tuning

Follow the corresponding points:

1.  After Training container selection, an optional setting can be configured in Hyperparameters.
2.  Select the **Enable hyperparameter tuning** option.
3.  Provide the Parameter name (need to add the 5 parameters which we have included in the code, individually).
4.  Select the Type of the input provided for the hyperparameter. The type of hyperparameters it supports are categorical, discrete, double, and integer. Select **integer** for `n_estimator`.
5.  Provide the Value, as shown in [Figure 5.15](#ch05.xhtml#fig5-15) (this option changes as per the type).
6.  Select **No scaling** option (it supports linear, log, and reverse log scaling).
7.  Click on **Done** (one of the five hyperparameters is added).
8.  Click on **Add new parameter** to add the details of the other parameters.

Refer to Table 5.1 and add the details of the remaining four parameters:

| Parameter name | Type | Value | Scaling |
| :--- | :--- | :--- | :--- |
| `max_depth` | Discrete | 5,10,15,20 | No scaling |
| `min_samples_split` | Discrete | 5,10 | No scaling |
| `min_samples_leaf` | Discrete | 5,10 | No scaling |
| `max_features` | Categorical | auto, sqrt | N/A |

Table 5.1: Hyperparameter list

If needed, change the type of `max_depth`, `min_samples_split`, and `min_samples_leaf` to integer for seeing other options. Refer to [Figure 5.16](#ch05.xhtml#fig5-16):

![](images/Figure_5.16.png)

Figure 5.16: Configuring other parameters for hyperparameter tuning

Refer to the corresponding steps to complete the configuration of the hyperparameter:

1.  All the parameters that are added will be listed.
2.  In the code we are optimizing accuracy metrics (to maximize), provide **accuracy** as the input.
3.  The Goal is to maximize the accuracy.
4.  Maximum number of trials is kept as low as 2, since the model is very simple.
5.  Maximum number of parallel trials is kept to 1 for the same reason.
6.  Under Algorithm, choose **Default** (random search or grid search can also be chosen). Explanations of different algorithms are listed below:
    *   **Random search**: A straightforward random search of the realizable region.
    *   **Unspecified algorithm**: Not specifying an algorithm. Vertex AI picks between Gaussian process bandits, linear combination search, or its versions.
    *   **Grid search**: A viable grid search. This is important if users wish to specify more trials than viable points. If no grid search is specified, Vertex AI may create duplicate options.
7.  Click on **CONTINUE**.

> **Note**: GCP has restricted training CPUs for free accounts. Try to keep the maximum trials and parallel trials low. If you get an error such as quota metrics exceeded, try reducing the value of these two parameters.

### Step 6: Compute and pricing

The next step is to provide compute and pricing details. Refer to [Figure 5.17](#ch05.xhtml#fig5-17):

![](images/Figure_5.17.png)

Figure 5.17: Compute and pricing for custom model

Follow the corresponding steps to select the machine type for training:

1.  Select **Compute and pricing**.
2.  Select the Region where the model training is to happen.
3.  Select the Machine type for the model training (choose the machine type based on how complicated your model training is).
4.  Acceleration type is optional and can be chosen for complex model trainings.
