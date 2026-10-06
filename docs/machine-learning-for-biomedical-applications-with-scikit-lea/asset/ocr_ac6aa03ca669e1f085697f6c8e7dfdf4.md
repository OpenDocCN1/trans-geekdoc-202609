![](bbox=[0.258, 0.088, 0.693, 0.318])

**Figure 11.11** Training UNet segmentation: training and validation losses over epochs.

set. We have previously created a data loader data_test_loader that we will now use. need to loop over test batches, predict the output for each batch of test data and then combine the two output maps into a label image by assigning label according to a maximum value. This is identical to a classification, but it is done on multiple output values (pixels). We will plot the predicted segmentation and the ground truth segmentation for each image in test batch with

```
plt.figure(figsize=(9,6))
for i, (data, labels) in enumerate(data_test_loader):
  # predict the labels
  data = data.to(device)
  pred = net(data).detach().cpu()
  l_pred = torch.argmax(pred, dim=1)
  # plot first subject from each batch
  plt.subplot(2,3,i+1)
  plt.title('Predicted: batch {}'.format(i))
  plt.imshow(l_pred[0,],cmap='gray')
  plt.subplot(2,3,i+3)
  plt.title('Ground truth: batch {}'.format(i))
  plt.imshow(labels[0,],cmap='gray')
```

From this plot, we can see in Fig. 11.12, that the network works very well and generalized well on the test set.

# Precision and recall

We have already said that binary segmentation is in fact a multi–output binary classification. The most common measure to evaluate classification is accuracy, together with