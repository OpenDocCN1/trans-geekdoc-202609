```
headers={"Host": "
{0}.kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data1,headers = headers)
response.json()
```

```
{'predictions': 'Negative Equity'}
```

Figure 6.37: KF serving Prediction O/P Python