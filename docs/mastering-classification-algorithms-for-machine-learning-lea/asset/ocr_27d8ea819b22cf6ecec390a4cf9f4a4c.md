```
ax.set_ylabel('True labels');
```

```
ax.set_title('Confusion Matrix');
```

```
ax.xaxis.set_ticklabels(['Benign', 'Backdoor', 'Botnet', 'DDOS',
'Trojan', 'Virus']);
```

```
ax.yaxis.set_ticklabels(['Benign', 'Backdoor', 'Botnet', 'DDOS',
'Trojan', 'Virus']);
```

```
print("\n\nAccuracy of the Model:", metrics.accuracy_score(yTrain, y_pred))
```

```
print("\n\nClassification Report\n");
```

```
print(metrics.classification_report(yTrain, y_pred))
```

Accuracy of the Model: 0.9868334968923782

Classification Report

| | precision | recall | f1-score | support |
|---|---|---|---||
| 0 | 1.00 | 1.00 | 1.00 | 2038 |
| 1 | 0.98 | 1.00 | 0.99 | 2038 |
| 2 | 1.00 | 0.98 | 0.99 | 2038 |
| 3 | 1.00 | 1.00 | 1.00 | 2038 |
| 4 | 0.96 | 0.99 | 0.97 | 2038 |
| 5 | 0.99 | 0.96 | 0.98 | 2038 |

| | | f1-score | support |
|---|---|---|--|
| accuracy | | 0.99 | 12228 |
| macro avg | 0.99 | 0.99 | 12228 |
| weighted avg | 0.99 | 0.99 | 12228 |