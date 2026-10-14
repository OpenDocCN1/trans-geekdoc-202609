
# Hyperparameter Tuning with Amazon SageMaker AMT

Upon defining the hyperparameter ranges dictionary object `hpt_ranges`—whose keys are also specific to the XGBoost algorithm—we are ready to optimize the hyperparameters using Bayesian optimization. This action is performed by creating a `tuner` object with this statement:

```
tuner = HyperparameterTuner(
    estimator=xgb,
    base_tuning_job_name='bayesian',
    objective_metric_name='validation:accuracy',
    hyperparameter_ranges=hpt_ranges,
    strategy='Bayesian',
    max_jobs=20,  # Increase to 20 max jobs
    max_parallel_jobs=3,  # Number of parallel jobs
    objective_type='Maximize'
)
```

and by fitting the tuner using the training dataset and the validation dataset:

```
tuner.fit({'train': train_data, 'validation': val_data})
```

Notice how the XGBoost hyperparameter `tuner` object is constructed by setting the `estimator` argument to the previously created `xgb` object, `validation:accuracy` as objective metric to be maximized, our hyperparameter ranges `hpt_ranges`, a `Bayesian` tuning strategy, and most importantly the maximum number of tuning and parallel jobs the tuner will utilize during the optimization process (respectively, 20 and 3). For more information about the `HyperparameterTuner` class, visit `https://sagemaker.readthedocs.io/en/stable/api/training/tuner.html`.

After the tuning job is complete, the best training job is identified:

```
best_training_job_name = tuner.best_training_job()
```

and the tuning results are analyzed to extract the best hyperparameter configuration. The results are finally visualized and plotted for better understanding.

Let’s see this program in action! [Figure 5.10](#c005.xhtml#c05-fig-10) shows the program at runtime.

![FIGURE 5.10 Running the program in Code Editor.](images/c05f010.png)

[FIGURE 5.10](#c005.xhtml#rc05-fig-10) Running the program in Code Editor.

As a result of running this program, three new training jobs appear in the list of training jobs, as displayed in [Figure 5.11](#c005.xhtml#c05-fig-11). Why three? Because we set the maximum number of parallel jobs to three in the `tuner` object’s constructor.

![FIGURE 5.11 Training jobs start.](images/c05f011.png)

[FIGURE 5.11](#c005.xhtml#rc05-fig-11) Training jobs start.

The program takes about 15 minutes to complete (45 seconds per job). It is always a good idea to proactively monitor the status of your training jobs in Amazon SageMaker Studio. Because we specified a maximum of 20 training jobs, 20 jobs are created in total.

Upon successful completion, all jobs are marked with Completed status, as shown in [Figure 5.12](#c005.xhtml#c05-fig-12).

![FIGURE 5.12 Training jobs completion.](images/c05f012.png)

[FIGURE 5.12](#c005.xhtml#rc05-fig-12) Training jobs completion.

The expected outcome is the plot illustrated in [Figure 5.13](#c005.xhtml#c05-fig-13), which is saved in the `images` folder in the EFS file system attached to my Amazon SageMaker Studio instance.

![FIGURE 5.13 Tuning evaluation plot.](images/c05f013.png)

[FIGURE 5.13](#c005.xhtml#rc05-fig-13) Tuning evaluation plot.

As displayed in [Figure 5.13](#c005.xhtml#c05-fig-13), the fourth job from the left—marked with a star—is the best training job: i.e., the job with the maximum accuracy. Its hyperparameter combination is displayed in the bottom of the plot.

When you are done using Amazon SageMaker Studio, remember to stop your instance to avoid incurring unwanted charges. Click the Stop button, as shown in [Figure 5.14](#c005.xhtml#c05-fig-14).

![FIGURE 5.14 Stopping the Amazon SageMaker Studio instance.](images/c05f014.png)

[FIGURE 5.14](#c005.xhtml#rc05-fig-14) Stopping the Amazon SageMaker Studio instance.

In this exercise, you learned how to use Amazon SageMaker AI AMT to optimize an XGBoost model using the Digits dataset. The program involved several steps: loading and splitting the dataset, saving the data locally and uploading it to an S3 bucket, defining the XGBoost estimator with required hyperparameters, and setting up a hyperparameter tuner with specified ranges for optimization. The tuner performed Bayesian optimization to find the best hyperparameter combination, and the program waited for the tuning jobs to complete. After tuning, the best training job and hyperparameter combination were identified, and the tuning results were visualized and saved as an image.

## Summary

In this chapter, we explored various facets of training ML models, including local, remote, and distributed training. We delved into monitoring and debugging techniques to ensure that model training runs smoothly and efficiently. These foundational concepts provide us with the necessary skills to manage and troubleshoot the training process, whether it’s conducted on local machines or distributed across cloud resources.

The chapter then transitioned into hyperparameter tuning, differentiating between model parameters and hyperparameters and examining strategies for exploring the hyperparameter space using Amazon SageMaker AI AMT. Evaluation metrics were covered in detail, tailored to both classification and regression problems. We investigated various hyperparameter tuning techniques, including manual search, grid search, random search, Bayesian search, and multi-algorithm optimization. Additionally, we learned how to manage bias and variance tradeoff, as well as addressing overfitting and underfitting through regularization methods (L1, L2, Elastic Net).

Next, we focused on model performance evaluation, discussing various performance evaluation methods like K-fold cross-validation, random train–test, holdout set, and bootstrap. Each method was compared and contrasted, highlighting their strengths and limitations. These techniques are crucial for validating the model’s performance and ensuring that it generalizes well to unseen data, which is the ultimate goal of any ML model.

We also provided insights into evaluating foundation models using Amazon Bedrock. We explored specific tools and methods for evaluating foundation models, including automatic evaluations, human evaluations, and knowledge base evaluations. This section emphasized the importance of a comprehensive evaluation framework to build and deploy generative AI applications with confidence and responsibility.

Finally, we concluded with a model tuning example, where we applied the concepts learned throughout the chapter. This practical example involved using Amazon SageMaker AI AMT configured with Bayesian optimization to perform hyperparameter tuning and model evaluation on the Digits dataset. By following the step-by-step instructions, we gained hands-on experience in optimizing ML models and evaluating their performance, reinforcing the theoretical knowledge acquired in the previous sections.

## Exam Essentials

**Know the difference between local, remote, and distributed training.** Local training involves training a machine learning model on a single machine using its available resources. Remote training, on the other hand, runs the training process on a cloud service (e.g., Amazon SageMaker) or remote server, leveraging external compute resources without overloading the local system. Distributed training involves spreading the training workload across multiple machines or nodes, either locally or remotely, to handle larger datasets and reduce training time by parallelizing the computations.
