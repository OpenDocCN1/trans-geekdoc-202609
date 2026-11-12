| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| input_1 (InputLayer) | [(None, 187, 1)] | 0 | [] |
| conv1d (Conv1D) | [(None, 187, 32)] | 192 | ['input_1[0][0]'] |
| batch_normalization (BatchNo | (None, 187, 32) | 128 | ['conv1d[0][0]'] |
| relu (Relu) | (None, 187, 32) | 0 | ['batch_normalization[0][0]'] |
| conv1d_1 (Conv1D) | (None, 187, 32) | 5152 | ['relu[0][0]'] |
| batch_normalization_1 (BatchNo | (None, 187, 32) | 128 | ['conv1d_1[0][0]'] |
| re_lu (Relu) | (None, 187, 32) | 0 | ['batch_normalization_1[0][0]'] |
| conv1d_2 (Conv1D) | (None, 187, 32) | 5152 | ['re_lu[0][0]'] |
| batch_normalization_2 (BatchNo | (None, 187, 32) | 128 | ['conv1d_2[0][0]'] |
| concatenate (Concatenate) | (None, 187, 64) | 0 | ['batch_normalization[0][0]',
 'batch_normalization_2[0][0]'] |
| re_lu_1 (Relu) | (None, 187, 64) | 0 | ['concatenate[0][0]'] |
| max_pooling1d (MaxPooling1D) | (None, 96, 64) | 0 | ['re_lu_1[0][0]'] |
| conv1d_3 (Conv1D) | (None, 96, 32) | 18272 | ['max_pooling1d[0][0]'] |
| batch_normalization_3 (BatchNo | (None, 96, 32) | 128 | ['conv1d_3[0][0]'] |
| re_lu_2 (Relu) | (None, 96, 32) | 0 | ['batch_normalization_3[0][0]'] |
| conv1d_4 (Conv1D) | (None, 96, 32) | 5152 | ['re_lu_2[0][0]'] |
| batch_normalization_4 (BatchNo | (None, 96, 32) | 128 | ['conv1d_4[0][0]'] |
| concatenate_1 (Concatenate) | (None, 96, 96) | 0 | ['max_pooling1d[0][0]',
 'batch_normalization_4[0][0]'] |
| re_lu_3 (Relu) | (None, 96, 96) | 0 | ['concatenate_1[0][0]'] |
| max_pooling1d_1 (MaxPooling1D) | (None, 39, 96) | 0 | ['re_lu_3[0][0]'] |
| conv1d_5 (Conv1D) | (None, 19, 32) | 15592 | ['max_pooling1d_1[0][0]'] |
| batch_normalization_5 (BatchNo | (None, 19, 32) | 128 | ['conv1d_5[0][0]'] |
| fc_1_4 (Dense) | (None, 95, 25) | 0 | ['batch_normalization_5[0][0]'] |
| conv1d_6 (Conv1D) | (None, 95, 25) | 5552 | ['fc_1_4[0][0]'] |
| batch_normalization_6 (BatchNo | (None, 95, 25) | 128 | ['conv1d_6[0][0]'] |
| concatenate_2 (Concatenate) | (None, 95, 50) | 0 | ['fc_1_4[0][0]',
 'batch_normalization_6[0][0]'] |
| re_lu_4 (Relu) | (None, 95, 50) | 0 | ['concatenate_2[0][0]'] |
| max_pooling1d_2 (MaxPooling1D) | (None, 4, 58) | 0 | ['re_lu_4[0][0]'] |
| conv1d_7 (Conv1D) | (None, 4, 58) | 20912 | ['max_pooling1d_2[0][0]'] |
| batch_normalization_7 (BatchNo | (None, 4, 58) | 128 | ['conv1d_7[0][0]'] |
| re_lu_5 (Relu) | (None, 4, 58) | 0 | ['batch_normalization_7[0][0]'] |
| conv1d_8 (Conv1D) | (None, 4, 58) | 5452 | ['re_lu_5[0][0]'] |
| batch_normalization_8 (BatchNo | (None, 4, 58) | 128 | ['conv1d_8[0][0]'] |
| concatenate_3 (Concatenate) | (None, 4, 116) | 0 | ['max_pooling1d_2[0][0]',
 'batch_normalization_8[0][0]'] |
| re_lu_6 (Relu) | (None, 4, 116) | 0 | ['concatenate_3[0][0]'] |
| max_pooling1d_3 (MaxPooling1D) | (None, 1, 58) | 0 | ['re_lu_6[0][0]'] |
| conv1d_9 (Conv1D) | (None, 1, 58) | 20912 | ['max_pooling1d_3[0][0]'] |
| batch_normalization_9 (BatchNo | (None, 1, 58) | 128 | ['conv1d_9[0][0]'] |
| re_lu_7 (Relu) | (None, 1, 58) | 0 | ['batch_normalization_9[0][0]'] |
| conv1d_10 (Conv1D) | (None, 1, 58) | 5452 | ['re_lu_7[0][0]'] |
| batch_normalization_10 (BatchNo | (None, 1, 58) | 128 | ['conv1d_10[0][0]'] |
| concatenate_4 (Concatenate) | (None, 1, 116) | 0 | ['max_pooling1d_3[0][0]',
 'batch_normalization_10[0][0]'] |
| re_lu_8 (Relu) | (None, 1, 116) | 0 | ['concatenate_4[0][0]'] |
| max_pooling1d_4 (MaxPooling1D) | (None, 1, 116) | 0 | ['re_lu_8[0][0]'] |
| flatten (Flatten) | (None, 116) | 0 | ['max_pooling1d_4[0][0]'] |
| dense (Dense) | (None, 2) | 6176 | ['flatten[0][0]'] |
| dense_1 (Dense) | (None, 5) | 105 | ['dense[0][0]'] |

# Figure 14.4 Different layers present in the model.

will be the same 99% one rather than commencing again, as earlier we encountered some issues, those issues were noted and then solved in this updated model, another issue was of the time the model consumed to run 52000 entries, which was around 6 to 7 hours on eight epochs, in the updated model the situation is better as the model takes 2 to 3 hours to run and the number of epochs to reach the optimal solution were set to be 40, although the best outcome was touched at the epoch number 36, this made the entire model more fast and more optimal than before. As shown in Figure 14.4 different layers present in the model.

To check the optimum number of epochs we can use in a model and to use the least possible amount of those were calculated and a graph was produced which ensure that the performance of the epochs flatlined at the nearest previous possible point.

# 14.4 Results

The model was found to be 99% accurate and was able to distinguish and find if a particular sample showcased signs of heart arrhythmia. The model has 19 layers in total which further ensures that proper processing of samples and ensures accurate results. The model produced an f1 score of 0.99 with a recall value of 0.94.

# 14.5 Conclusion

As there were multiple classes to predict the results of irregularities, a precision, recall, and f1 score was calculated for each class to be predicted the results of as shown in Figure 14.5