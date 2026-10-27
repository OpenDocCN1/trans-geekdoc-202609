![](bbox=[0.13, 0.13, 0.82, 0.48])

Figure 7.3 Individual counting via face detection.

Table 7.1 Confusion matrix of individual counting via face detection.

| N=25 | Predicted No | Predicted Yes |
|---|---|---|
| Actual No | 4 | 1 |
| Actual Yes | 1 | 19 |

In Table 7.1, you can see the results of our proposed method. A rectangle appears on a face when it is correctly identified or detected. We assign a value of ‘1’ to the correctly identified number of people and ‘2’ to those incorrectly detected shown in Figure 7.4.

As per the formula for the error rate and accuracy, here, we showed the results of individual counting via face detection using this confusion matrix:

```
Err = 2/25= 0.08
Accuracy = 1-error
      = 1-0.08
      = 0.92
Accuracy (in percentage) = 92%
```