```
# result: string (in utf-8)
encoded_string = encoded_bytes.decode('utf-8')
samples.append(encoded_string)
```

```
# prepare test data
data = json.dumps({"instances": samples})
data_read = json.loads(data)
with open('data.json','w') as out:
json.dump(data_read, out)
```

```
%%bash
gcloud container clusters get-credentials --zone us-east1-d --project
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
echo $CLUSTER_IP
MODEL_NAME="kfserving-braintumor"
#Replace the cluster IP
cluster_ip = "COPY YOUR IP FROM ABOVE"
headers={"Host": "
{0}.kubeflow.example.com".format(MODEL_NAME),"Content-Type":
"application/json"}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data,headers = headers)
print(response.json())
```

```
{&#39;predictions&#39;: [&#39;No tumor inside Brain&#39;, &#39;Tumor inside Brain&#39;, &#39;Tumor inside Brain&#39;, &#39;Tumor inside Brain&#39;]}
```

Figure 3.10: Prediction output