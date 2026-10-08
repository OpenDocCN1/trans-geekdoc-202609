The model explainability report is also directly accessible Studio UI. You can navigate to the report by going to SageMaker Components and Registries | Experiments and trials | Unassigned trials. Then, right-click the latest clarify-explainability-XXXX job and select Open in trial details. Finally, on the Model explanation fact. In this example, you will see that this is the most important feature that influences predictions.

# Training privacy-preserving models

In this last part of the hands-on lab, you will learn how to use differential privacy for privacy-preserving training model:

+   Create a new folder differential privacy under the chapter 11 folder. Download the notebook at https://github.com/PackPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter11/churn_privacy.ipynb and upload it to the newly created differential privacy folder.

+   Run all the cells in the notebook and take note of the training losses at the end. We are not going to explain all the details in this notebook simply trains the simple neural network using the same churn dataset we have been using.

+   Now, we must modify this notebook to implement differential privacy model training using the PyTorch opacus package. You can also download the modified notebook from https://github.com/PackPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter11/churn_privacy-modified.ipynb.

+   Specify the parameters for the opacus package's PrivacyEngine object. Here, noise_multiplier is the ratio of the standard deviation of Gaussian noise to the sensitivity of the function to add to noise, while max_per_sample_grad_norm is the maximum value greater than this norm will be clipped. The sample_rate value is used for figuring out how to build batches for training:

```
max_per_sample_grad_norm = 1.5
sample_rate = batch_size/len(train_ds)
noise_multiplier = 0.8
```