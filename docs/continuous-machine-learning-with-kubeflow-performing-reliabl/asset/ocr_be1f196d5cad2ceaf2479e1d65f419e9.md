Optionally, we can connect the TensorBoard to the Trainer to analyze our model's training curves. Get the URI of the output artifact representing the training logs, which is a directory:

```
model_dir = trainer.outputs['model'].get()[o].uri
%load_ext tensorboard
%tensorboard --logdir {model_dir}
```

![](bbox=[0.12, 0.29, 0.88, 0.72])

Figure 4.21: Tensorboard Output

Here, we will visualize the Batch Accuracy and Batch loss and Epoch Loss and epoch accuracy in our TensorBoard.