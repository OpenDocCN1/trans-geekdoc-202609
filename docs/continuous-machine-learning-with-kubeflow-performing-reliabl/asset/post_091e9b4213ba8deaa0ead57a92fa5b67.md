
```
"--train-target", train_target,
"--test-target", test_target,
"--validation-target", validation_target,
"--epochs", epochs,
"--batch-size", batch_size,
"--learning-rate", learning_rate,

"--tensorboard-logs", tensorboard_logs,
"--tensorboard-gcs-logs", tensorboard_gcs_logs,
"--model-output-base-path", model_output_base_path,
"--gcs-path", gcs_path,
"--mode", mode],
pvolumes={"/mnt": data_processing_step.pvolume})
```

# evaluation_model
evaluation_model_step = dsl.ContainerOp(
name='evaluation_model',
image=evaluator_step_image,
command="python",
arguments=[
"/app/evaluator.py",
"--test-file", test_file,
"--test-target", test_target,
"--probability", probability,
"--model-output-base-path", model_output_base_path,
"--gcs-path", gcs_path,
"--gcs-path-confusion", gcs_path_confusion],
pvolumes={"/mnt": train_model_step.pvolume})

kfserving_template = Template("""{
"apiVersion": "serving.Kubeflow.org/v1alpha2",
```
"kind": "InferenceService",
"metadata": {
"labels": {
"controller-tools.k8s.io": "1.0"},
"name": "$name",
"namespace": "$namespace"},
"spec": {

"default": {
"predictor": {
"custom": {
"container": {
"image": "$image"}}}}})""")
kfservingjson = kfserving_template.substitute({'name':
str(serving_name),
'namespace': str(serving_namespace),
'image': str(image)})
kfservingdeployment = json.loads(kfservingjson)
serve = dsl.ResourceOp(
name="serve",
k8s_resource=kfservingdeployment,
action="apply",
success_condition="status.url")
serve.after(evaluation_model_step)

if __name__ == '__main__':
import kfp.compiler as compiler
pipeline_func = breast_cancer_tensorflow_pipeline
pipeline_filename = pipeline_func.__name__ + '.pipeline.zip'
compiler.Compiler().compile(pipeline_func,pipeline_filename)
```

Now, let’s break the pipeline code as follows:

Pipelines are expected to include a **@dsl.pipeline** decorator to provide the metadata about the pipeline.

The pipeline is defined in the **breast_cancer_tensorflow_pipeline** function. It includes a number of arguments, which are exposed in the Kubeflow Pipelines UI when creating a new Run. Although passed as strings, these arguments are of type

Each individual block defines one component like ‘train’, ‘evaluation’, and so on. A component is made up of a **kfp.dsl.ContainerOp** object with the container path and a specified name. The container image used is defined as the Docker file which we have created.

After defining the train component, we also set a number of environment variables for the training script.

At the bottom of the script is the main function. This is used to compile the pipeline when the script is run; next, the **.after** method will trigger the pipeline one after the other.

When you run the preceding code, it will dump a zip like the following:

![](img/8f8a671916d96b455297952d0f37b96c_159_0.png)

Figure 2.22: Pipeline zip

Next, we will create an experiment; under that, we can create multiple runs of a pipeline. The following code is for creating the experiment:

```
import kfp
from kfp import compiler
import kfp.components as comp
import kfp.dsl as dsl
from kfp import gcp
EXPERIMENT_NAME = 'Breast'
client = kfp.Client()
```

try:

```
experiment =
client.get_experiment(experiment_name=EXPERIMENT_NAME)
except:
experiment = client.create_experiment(EXPERIMENT_NAME)
print(experiment)
```

The following snippet will create a run for the zip that we have dumped in that location:

```
arguments = {}
run_name = pipeline_func.__name__ + 'breast_run'
run_result = client.run_pipeline(experiment.id, run_name,
pipeline_filename, arguments)
```

```
print(experiment.id)
print(run_name)
print(pipeline_filename)
print(arguments)
```

Click on the run link, once the pipeline is ready. The following is how our pipeline training looks:

![](img/8f8a671916d96b455297952d0f37b96c_161_0.png)

Figure 2.23: Training pipeline output

The following is how our pipeline Serving looks:

![](img/8f8a671916d96b455297952d0f37b96c_161_1.png)

Figure 2.24: Serving pipeline output

The following screenshot is of the pipeline which we have created and the Python visualizations, tables and static HTML plots:

![](img/8f8a671916d96b455297952d0f37b96c_162_0.png)

Figure 2.25: Serving pipeline output

Next, let’s find out how to Monitor an endpoint in Grafana.

## 2.7 Monitoring the performance with Grafana dashboard

Run the command in the Google Cloud shell after connecting the Cluster and then Create Namespace.

```bash
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
#create namespace
kubectl create namespace knative-monitoring
#setup monitoring components
kubectl apply --filename https://github.com/knative/serving/releases/download/v0.177.20/monitoring-metrics-prometheus.yaml
```

![](img/8f8a671916d96b455297952d0f37b96c_163_0.png)

Figure 2.26: Prometheus deploy

Next, run from the Local Terminal and open the `grafana` dashboard by using `localhost:8080` on the browser. Explore the different components of the grafana dashboard.

```bash
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```

Hit the Curl request from bash and see the output in the Dashboard.

```
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```

![](img/8f8a671916d96b455297952d0f37b96c_165_0.png)

Figure 2.27: Grafana Dashboard Contents

The preceding dashboard is for the contents of Grafana; we can click on the individual section and see the reports there.

The following Dashboard talks about the HTTP requests for Knative Serving Visualization which we serve per/sec request.

![](img/8f8a671916d96b455297952d0f37b96c_165_1.png)

Figure 2.28: Grafana Dashboard HTTP Request

So, the following is the Dashboard for the Control Plane which shows the CPU Usage and memory usage efficiency.

![](img/8f8a671916d96b455297952d0f37b96c_166_0.png)

Figure 2.29: Prometheus Dashboard

## 2.8 Conclusion

In this chapter, we learned how to build end-to-end Kubeflow Orchestrator Pipeline for a TensorFlow Model and how to Dockerize each component and build it in Google Platform.

Then, we learned how to build the pipeline with the kfp library package and triggered the pipeline from the Kubeflow Dashboard. We have now deployed the Kubeflow on the Kubernetes Platform and learned how to trigger the pipeline from the Notebook. We have also deployed the model in the Kubernetes cluster with the KF serving and monitored our prediction results in the Grafana Dashboard.

We have also learned how to leverage the power of Google Cloud Platform, and use our Devops knowledge with Machine Learning to become an MLops.

## 2.9 Reference

https://knative.dev/docs/serving/autoscaling/autoscaling-concepts/

https://v1-1-branch.Kubeflow.org/docs/

https://v1-1-branch.Kubeflow.org/docs/gke/

https://v1-1-branch.Kubeflow.org/docs/gke/monitoring/

## Designing Computer Vision Model in Kubeflow

In this chapter, we will build an end-to-end TensorFlow Computer Vision Model with OpenCV operation and deploy that with the Kubeflow Orchestration, which includes deploying Kubeflow in Kubernetes Cluster in GCP, building the pipeline components for the model with Docker and Kubeflow SDK, and then serving the Model with KF serving to have an endpoint for prediction. We will then perform the monitor and performance in Grafana Dashboard.

## Structure

In this chapter, we will cover the following topics:

- Problem statement
- Getting started in GCP Kubeflow and Docker setup
- Analytics behind the problem statement
- Building the Kubeflow Pipeline components for Computer Vision (CNN) TensorFlow model
- Serving the Model with KF Serving
- Building the pipeline end to end
- Auto-Scaling of the serving endpoint
