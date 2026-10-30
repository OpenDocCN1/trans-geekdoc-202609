Now, in the preceding Docker code, we have copied the service account for the storage bucket access, and saved it in Then, we copied the Python serving file in the same location and kept the working directory as Then, we build the image by using the above code. Similarly, we created the Docker image; please have a look at the GitHub **steps.md** file.

To deploy the model server using the **kubectl** command line, or using the KF Serving client SDK, you can do either of the following:

+   - Deploy using the command line
+   - Deploy using the KF Serving client SDK

# **Deploy using the command line:**

Now, let’s deploy it with the command line, and first let’s fill the yaml file:

```
```yaml
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
metadata:
annotations:
sidecar.istio.io/inject: "false"
name: kfserving-braintumor
namespace: kubeflow
spec:
```
```