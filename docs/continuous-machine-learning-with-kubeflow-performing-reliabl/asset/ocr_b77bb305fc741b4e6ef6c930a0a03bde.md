```
df_cancer = pd.DataFrame(np.c_[cancer['data'], cancer['target']],
columns = np.append(cancer['feature_names'], ['target']))

X = df_cancer.drop(['target'],axis=1)
y = df_cancer['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size =
0.1, random_state = 0)
data = json.dumps({"instances": X_test.iloc[7].to_list()})
data
```

![](bbox=[0.11, 0.31, 0.89, 0.36])

Figure 2.18: Sample Data

```
MODEL_NAME="kfserving-breast-model"
cluster_ip = YOUR CLUSTER IP HERE>
headers={"Host": "
{0}.Kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data,headers = headers)
response.json()
```

![](bbox=[0.3, 0.66, 0.7, 0.72])

Figure 2.19: Prediction output