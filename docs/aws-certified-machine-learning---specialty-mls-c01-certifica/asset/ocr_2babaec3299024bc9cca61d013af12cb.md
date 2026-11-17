+   * TrainingJobDefinition: Here, you can configure your training job. For example, the data channels, the output location, the resource configurations, the evaluation metrics, and the stop conditions.

In SageMaker, the main metric that you want to use to evaluate the models to select the best one is known as an **objective metric**.

In the following example, you are configuring `HyperParameterTuningJobConfig` for a decision tree-based algorithm. You want to check the best configuration for a `max_depth` hyperparameter, which is responsible for controlling the depth of the tree.

In `IntegerParameterRanges`, you have to specify the following:

+   * The hyperparameter name
+   * The minimum value that you want to test
+   * The maximum value that you want to test

# # IMPORTANT NOTE

*Each type of hyperparameter must fit in one of the parameter range sections, such as categorical, continuous, or integer parameters.*

In `ResourceLimits`, you are specifying the number of training jobs along with the number of parallel jobs that you want to run. Remember that the goal of the tuning process is to execute many training jobs with different hyperparameter settings. This is so that the best one will be selected for the final model. That's why you have to specify these training job execution rules.

You then set up our search strategy in `Strategy` and, finally, set up the objective function in `HyperParameterTuningJobObjective`:

```
tuning_job_config = {
    "ParameterRanges": {
        "CategoricalParameterRanges": [],
        "ContinuousParameterRanges": [],
        "IntegerParameterRanges": [
            {
                "MaxValue": "10",
                "MinValue": "1",
                "Name": "max_depth"
            }
        ]
    },
    "ResourceLimits": {
        "MaxNumberOfTrainingJobs": 10,
        "MaxParallelTrainingJobs": 2
    },
    "Strategy": "Bayesian",
    "HyperParameterTuningJobObjective": {

```