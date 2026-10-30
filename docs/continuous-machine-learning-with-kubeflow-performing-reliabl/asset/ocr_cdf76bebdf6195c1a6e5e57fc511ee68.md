# Sample Prediction:

Run the following command in Bash from the serving folder:

```
```bash
MODEL_NAME=kfserving-braintumor
HOST=$(kubectl get inferenceservice -n Kubeflow$MODEL_NAME -o jsonpath='{.status.url}' | cut -d "/" -f 3)
INPUT_PATH=@./data.json
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```
```

Now, the following is the Response prediction request: