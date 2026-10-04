# 10 Featured Examples

```
fc 19441 0.00009
* The clock frequency of the DL processor is: 220MHz
-, idx2] = max(scores, [], 2);
predTestLabelBatch = classnames(idx2);
% The micro-doppler signatures along with the ground truth and
% predictions.
for k = 1:num
index = listIndex(k);
imagesc(testDataNoCar(:, :, index));
axis xy\xlabel('Time (s)')
ylabel('Frequency (Hz)')ntitle(['Ground Truth: '+string(testLabelNoCar(index))+', Prediction FPGA: '+string(TestLabel
drawnow;
pause(3);
```

![](bbox=[0.148, 0.396, 0.755, 0.763])

The image shows the micro-Doppler signatures of two bicyclists (bic+bic) which is the ground truth. The ground truth is the classification of the image against which the network prediction is compared. The network prediction retrieved from the FPGA correctly predicts that the image has two bicyclists.

10-50