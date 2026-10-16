
The results on dataset A as depicted in `Table 10.2` present that the results with feature representation are mixed and there is not a clear best one. With an accuracy of 96.7%, `LSTM` is the best method with the last-fired feature and `HMM` is the worst one, while with a change-point feature, `HMM` is the best performing method. `CRF` gives the best accuracy (89.8%) when a binary feature is used, whereas `RNNs`, `NB` and `SVM` do not perform well with change-point representation and `HMM` and `HSMM` perform bad with a binary feature. In a nutshell, for the majority of the methods, except `HMM` and `HSMM`, last-fired representation is the best one. In terms of recall which reflects better on performance in the presence of imbalanced data, the highest value is obtained by `GRU` (80.6%). This means that `RNNs` are good at finding relevant class instances. `CRF` performs higher precision since it favours the most frequent-class instances while it is not good enough to detect infrequent classes. In general, `RNNs` outperform better than `HMM`, `NB` and `HSMM` for most of the cases, while `CRF` is slightly better than these recurrent architectures on dataset A.

`Table 10.3` refers to the results obtained on the dataset best method when adopting a binary representation achieving an accuracy of 81.6%. On the other hand, `CRF` is the best when using the change-point feature and last-fired representations with accuracies of 92.9% and 89.2% respectively. It can be noted that `HMM` is not as good as the other methods achieving the best case 81.0% with the change-point representation. The closest successful model to `CRF` is `Vanilla RNN` and again overall `RNNs` deliver high recall rates compared to the other methods. Change-point and last-fired representations give the highest recall results except for `CRF`.

TABLE 10.3 Activity Recognition Results for Household B of the Van Kasteren Dataset

| **Model** || **Feature** || **Precision** || **Recall** || **F-Measure** || **Accuracy** |

| --- | --- | --- | --- | --- | --- |

| NB || Binary || 33.6 ± 10.9 || 32.5 ± 8.4 || 32.4 ± 8.9 || 80.4 ± 18.9 |

|  || Change-point || 40.9 ± 7.2 || 38.9 ± 5.7 || 39.5 ± 5.9 || 67.8± 18.6 |

|  || Last-fired || 43.7 ± 8.7 || 44.6 ± 7.2 || 43.3 ± 4.8 || 86.2 ± 13.8 |

| HMM || Binary || 38.8 ± 14.7 || 44.7 ± 13.4 || 40.7 ± 12.4 || 63.2 ± 24.7 |

|  || Change-point || 48.2 ± 17.2 || 63.1 ± 14.1 || 53.6 ± 16.5 || 81.0 ± 14.2 |

|  || Last-fired || 38.5 ± 15.8 || 46.6 ± 19.5 || 41.8 ± 17.1 || 48.4± 26.9 |

| HSMM || Binary || 37.4 ± 16.9 || 44.6 ± 14.3 || 39.9 ± 14.3 || 63.8± 24.2 |

|  || Change-point || 49.8 ± 15.8 || 65.2 ± 13.4 || 55.7 ± 14.6 || 82.3 ± 13.5 |

|  || Last-fired || 40.8 ± 11.6 || 53.3 ± 10.9 || 45.8 ± 11.2 || 67.1 ± 24.8 |

| CRF || Binary || 35.7 ± 15.2 || 40.6 ± 12.0 || 37.5 ± 13.7 || 78.0 ± 25.9 |

|  || Change-point || 48.3 ± 8.3 || 51.5 ± 8.5 || 49.7 ± 7.9 || 92.9 ± 6.2 |

|  || Last-fired || 46.9 ± 12.5 || 47.8 ± 12.1 || 46.6 ± 12.9 || 89.2 ± 13.9 |

| Vanilla || Binary || 26.7 ± 13.5 || 46.9 ± 24.8 || 32.5 ± 17.9 || 65.2 ± 34.7 |

|  || Change-point || 39.6 ± 8 || 62.4± 15.3 || 48.3± 10.2 || 76.9± 13.9 |

|  || Last-fired || 41.2 ± 12.3 || 64.4 ± 17.8 || 49.7 ± 13.6 || 87.9 ± 13.1 |

| LSTM || Binary || 29.1 ± 12.0 || 44.0 ± 22.0 || 33.9 ± 16.2 || 63.5 ± 32.7 |

|  || Change-point || 40.0 ± 11.2 || 59.0 ± 16.4 || 47.5 ± 12.9 || 76.8± 14.2 |

|  || Last-fired || 40.8 ± 10.7 || 60.1 1 16.3 || 48.2 ± 12.3 || 87.2 ± 13.2 |

| GRU || Binary || 28.5 ± 15.9 || 36.3 ± 17.2 || 31.4 ± 16.2 || 64.5 ± 32.1 |

|  || Change-point || 37.7 ± 7.6 || 53.5 ± 9.2 || 44.9 ± 7.1 || 76.4 ± 11.5 |

|  || Last-fired || 41.7 ± 13.2 || 50.9 ± 17.9 || 47.5 ± 14.6 || 87.0 ± 12.9 |

| SVM || Binary || 39.6± 10.9 || 58.5± 17.4 || 46.7± 12.9 || 81.6 ± 18.5 |

|  || Change-point || 32.3 ± 6.5 || 53.6 ± 7.5 || 40.0 ± 6.2 || 67.9± 28.5 |

|  || Last-fired || 36.4 ± 5.4 || 54.0 ± 10.4 || 43.5 ± 6.6 || 86.2 ± 14.9 |

`Table 10.4` reports the results on dataset C showing that `CRF` performs best for change-point and binary representations obtaining 82.2% and 89.7% respectively. Overall, none of the methods performs well when adopting a binary representation. The results are slightly better with change-point but clearly better when applying the last-fired representation. `RNNs` again give the highest recall values for all representations. Overall, the results show that `RNNs` perform better than `HMM`, `NB` and `HSMM` in all cases, while `CRF` is slightly better than `RNNs`. But in terms of recall, `RNNs` outperform all methods for all feature representations. The reason behind this is that `RNNs` perform better for imbalanced data compared to `CRF`. `RNN` variants generally perform equally well.

TABLE 10.4 Activity Recognition Results for Household C of the Van Kasteren dataset.

| **Model** || **Feature** || **Precision** || **Recall** || **F-Measure** || **Accuracy** |

| --- | --- | --- | --- | --- | --- |

| NH || Binary || 19.61 ± 11.4 || 16.8 ± 7.5 || 17.8 ± 9.1 || 46.5 ± 22.6 |

| --- | --- | --- | --- | --- | --- |

|  || Change-point || 39.9 ± 6.9 || 30.8 ± 4.8 || 34.5 ± 4.6 || 57.6 ± 15.4 |

|  || Last-fired || 40.5 ± 7.4 || 46.4 ± 14.8 || 42.3 ± 6.8 || 87.0 ± 12.2 |

| HMM || Binary || 15.2 ± 9.2 || 17.2 ± 9.3 || 15.7± 8.8 || 26.5 ± 22.7 |

|  || Change-point || 41.4 ± 8.8 || 50.0 ± 11.4 || 44.9 ± 8.8 || 77.2 ± 14.6 |

|  || Last-fired || 40.7 ± 9.7 || 53.7 ± 16.2 || 45.9 ± 11.2 || 83.9 ± 13.9 |

| HSMM || Binary || 15.6 ± 9.2 || 20.4 ± 10.9 || 17.3 ± 9.6 || 31.2 ± 24.6 |

|  || Change-point || 43.8 ± 10.0 || 52.3 ± 12.8 || 47.4 ± 10.5 || 77.5 ± 15.3 |

|  || Last-fired || 42.5 ± 10.8 || 56.0 ± 15.4 || 47.9 ± 11.3 || 84.5 ± 13.2 |

| CRF || Binary || 17.8 ± 22.1 || I 21.8 ± 20.9 || 19.0 ± 21.8 || 46.3 ± 25.5 ' |

|  || Change-point || 36.7 ± 18.0 || 39.6 ± 17.4 || 38.0 ± 17.6 || 82.2 ± 13.9 |

|  || Last-fired || 37.7 ± 17.1 || 40.41 ± 16.0 || 38.9 ± 16.5 || 89.7 ± 8.4 |

| Vanilla || Binary || 15.4 ± 5.3 || 43.1 ± 18.1 || 22.2 ± 7.3 || 50.2 ± 22.4 |

|  || Change-point || 31.3 ± 7.1 || 54.9 ± 11.3 || 39.5 ± 8.3 || 72.2 ± 13.0 |

|  || Last-fired || 38.3± 16.3 || 59.6± 15.1 || 45.8± 14.8 || 86.7± 12.5 |

| LSTM || Binary || 16.8± 6.2 || 34.8 ± 12.5 || 22.1 ± 7.4 || 45.3 ± 21.2 |

|  || Change-point || 31.0 ± 5.1 || 53.3 ± 6.5 || 38.9 ± 5.0 || 72.0 ± 13.0 |

|  || Last-fired || 41.3 ± 17.2 || 57.3 ± 15.9 || 47.5 ± 16.1 || 87.4 ± 12.4 |

| CRU || Binary || 18.7 ± 8.3 || 33.2 ± 12.7 || 23.9 ± 9.6 || 46.7 ± 23.4 |

|  || Change-point || 31.2 ± 8.3 || 47. ± 10.9 || 31.2 ± 8.5 || 71.6 ± 12.6 |

|  || Last-fired || 40.4 ± 16.5 || 52.7 ± 16.4 || 45.4 ± 16.9 || 86.6 ± 12.3 |

| SVM || Binary || 19.4 ± 9.0 || 35.2 ± 12.7 || 24.0 ± 9.2 || 37.4 ± 19.0 |

|  || Change-point || 25.6 ± 6.2 || 51.4 ± 9.5 || 34.0 ± 7.2 || 57.8 ± 15.5 |

|  || Last-fired || 37.0 ± 7.9 || 55.5 ± 11.6 || 44.1 ± 8.5 || 87.5 ± 12.1 |

Abnormal activity recognition is tested with `LSTM` since it is the most promising one and it is compared against `NB`, `HSMM`, `HMM`, `SVM` and `CRF` (`Table 10.5`). We used only the last-fired feature in this experiment. The results indicate that `LSTM` is the best to prune false negatives compared to the other methods. Methods like `NB` and One-class `SVM`, which do not capture the data order, perform the worst. The models ignore the frequency of the activity, but apply the temporal and contextual information to make decisions. Results show that `LSTM` is capable of encoding the order of activities. Hence, when an activity is introduced in a different context or in a different order, `LSTM` can detect such anomalies.

TABLE 10.5 Abnormal Activity Detection Results for the Synthetic Dataset

| **Model** || **Sensitivity (TPR) (%)** || **Specificity (TNR) (%)** |

| --- | --- | --- |

| NB || 40.40 || 56.50 |

| --- | --- | --- |

| HMM || 58.36 || 3.80 |

| HSMM || 68.85 || 67.8 |

| CRF || 66.22 || 59.45 |
