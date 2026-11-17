```
import time
instance_type = "ml.t2.medium"
model_name = "knn_%s" % instance_type
endpoint_name = "knn-baba-test-%s" % (str(time.time())).replace(".", "-"))
print("setting up the endpoint...")
predictor = predictor_from_estimator(
    knn_estimator, model_name, instance_type, endpoint_name=endpoint_name
)
```

setting up the endpoint..
-

Figure 9.10 – Creating the predictor object with endpoint details

10. Navigate to Inference > Endpoints. This will show you the endpoint that was created as a result of the previous paragraph's execution. This endpoint has a configuration and can be navigated and traced through Inference > Endpoint Configurations.

11. If you view the Inference section in the notebook, you will notice that it uses the test data to predict results. It uses the predictor object from the SageMaker API to make predictions. The predictor object contains the endpoint details, model name, and instance type.

12. The API call to the endpoint occurs in the Inference section and is authenticated via the IAM role with which the notebook instance is created. The same API calls can be traced through CloudWatch invocation metrics.

13. Finally, running the delete_endpoint method in the notebook will delete the endpoint. To delete the endpoint configurations, navigate to Inference > Endpoint Configurations and select the configuration on the screen. Click on Actions > Delete > Delete.

14. Now, please feel free to shut down the kernel and stop your notebook instance from the SageMaker console. This is a best practice to reduce costs.

In this section, you learned how to use the notebook instance, training instances, inference endpoints, and endpoint configurations to clean our data, train models, and generate predicted results from them. In the next section, you will learn about model tuning.

# Model tuning

In Chapter 7, Evaluating and Optimizing Models, you learned many important concepts about model tuning. Let's now explore this topic from a practical perspective.

In order to tune a model on SageMaker, you have to call create_hyper_parameter_tuning_job and pass the following main parameters:

+   - HyperParameterTuningJobName: This is the name of the tuning job. It is useful to track the training jobs that have been started on behalf of your tuning job.
+   - HyperParameterTuningJobConfig: Here, you can configure your tuning options. For example, which parameters you want to tune, the range of values for them, the type of optimization (such as random search or Bayesian search), the maximum number of training jobs you want to spin up, and more.